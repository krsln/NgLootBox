### Usage

> [![](https://img.shields.io/badge/Main-readme‌‌‌‌‌‌‌-white)](../../../readme.desc.md)
> [![](https://img.shields.io/badge/readme-white)](readme.md)

### Breadcrumb

Component (ql-breadcrumb)  
~~Directive ()~~  
~~Service ()~~

#### app.module.ts

```typescript
import {BreadcrumbModule} from '@qrsln/loot-box/Libs/Breadcrumb';

@NgModule({
  imports: [BreadcrumbModule, /*...*/],
})
```  

#### Usage

```html
<!--fas fa-angle-right <i class="fas fa-angle-right"></i>-->
<ql-breadcrumb [Home]="Home" [Items]="Items" [Chevron]="'fas fa-angle-right'" [Label]="Label"></ql-breadcrumb>

<!--fas fa-slash <i class="fas fa-slash"></i>-->
<ql-breadcrumb [Home]="Home" [Items]="Items" [Chevron]="'fas fa-slash'" [Label]="Label"></ql-breadcrumb>

```

```typescript
// Label?: string;
// Home?: BreadcrumbItem;
// Items: BreadcrumbItem[] = [];

ngOnInit()
{
  this.Home = {FaClass: 'fas fa-home', Url: '/'} as BreadcrumbItem;
  this.Label = 'Test current page';
  this.Items = [
    {Label: 'Sports'},
    {Label: 'Football'},
    {Label: 'Countries', Url: '/Piper'},
    {Label: 'Spain'},
    {Label: 'Squad'},
    {Label: 'google', Url: 'https://www.google.com', FaClass: 'fas fa-external-link-alt'}
  ] as BreadcrumbItem[];
}
```

#### Usage Auto

```html

<main>
  <ql-breadcrumb [Home]="Home" [Items]="Items" [Chevron]="'fas fa-angle-right'"></ql-breadcrumb>
  <router-outlet></router-outlet>
</main> 
```

```typescript
// **app-route**
const routes: Routes = [
  {
    data: {breadcrumb: null},
    path: '', component: AppComponent, children: [
      {path: '', redirectTo: '/Home', pathMatch: 'full'},
    ]
  },
  {path: 'Home', component: HomeComponent},
  {path: 'Mapper', data: {breadcrumb: 'Mapper'}, component: MapperComponent},
  {
    path: 'Timeline', data: {breadcrumb: 'Timeline'}, component: TimelineComponent, children: [
      {path: 'Piper', data: {breadcrumb: 'Piper'}, component: PiperComponent},
      {path: 'Notify', data: {breadcrumb: 'path'}, component: NotifyTestComponent, children: []},
    ]
  }
];

// **AppComponent**
export class AppComponent implements OnInit {
  readonly ROUTE_DATA_BREADCRUMB = 'breadcrumb';
  Home: BreadcrumbItem = {FaClass: 'fas fa-home', Url: '/'} as BreadcrumbItem;
  Items: BreadcrumbItem[];

  constructor(private router: Router, private activatedRoute: ActivatedRoute) {
  }

  ngOnInit(): void {
    this.Items = [];
    this.router.events
      .pipe(filter(event => event instanceof NavigationEnd))
      .subscribe(() => this.Items = this.createBreadcrumbs(this.activatedRoute.root));
  }

  private createBreadcrumbs(route: ActivatedRoute, url: string = '', breadcrumbs: BreadcrumbItem[] = []): BreadcrumbItem[] {
    const children: ActivatedRoute[] = route.children;

    if (children.length === 0) {
      return breadcrumbs;
    }

    // noinspection LoopStatementThatDoesntLoopJS
    for (const child of children) {
      const routeURL: string = child.snapshot.url.map(segment => segment.path).join('/');
      if (routeURL !== '') {
        url += `/${routeURL}`;
      }

      const label = child.snapshot.data[this.ROUTE_DATA_BREADCRUMB];
      if (!!label) {
        breadcrumbs.push({Label: label, Url: url} as BreadcrumbItem);
      }
      return this.createBreadcrumbs(child, url, breadcrumbs);
    }

  }
} 
```
