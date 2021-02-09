### Usage

> [![](https://img.shields.io/badge/Main-readme‌‌‌‌‌‌‌-white)](../../../readme.desc.md)
> [![](https://img.shields.io/badge/readme-white)](readme.md)

### Timeline

Component (lb-timeline, _lb-timeline-card_)  
~~Directive ()~~  
~~Service ()~~

#### app.module.ts

```typescript
import {TimelineModule} from '@qrsln/loot-box/Libs/Timeline';

@NgModule({
  imports: [TimelineModule, /*...*/],
})
```  

#### Usage

```html

<lb-timeline [Header]="Header" [Description]="Description" [Layout]="'Default'" [Steps]="steps"
             [Animation]="'shake'"></lb-timeline>
<lb-timeline [Header]="Header" [Description]="Description" [Layout]="'Side'" [Steps]="steps"></lb-timeline>
<lb-timeline [Header]="Header" [Description]="Description" [Layout]="'Snake'" [Steps]="steps"></lb-timeline>

<lb-timeline [Header]="Header" [Description]="Description" [Layout]="'Branch'" [Steps]="steps"></lb-timeline>
<lb-timeline [Header]="Header" [Description]="Description" [Layout]="'Zigzag'" [Steps]="steps"></lb-timeline>
``` 

```typescript
Header = 'Timeline';
Description = 'Showcase of my latest works, projects and developments.';
// steps: TimelineStep[] = [];

ngOnInit()
{
  this.steps = [
    {
      Card: {
        Title: 'Beginning',
        Content: 'Lorem ipsum dolor sit amet, conectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat.',
        Subtitle: '11 hours ago via Twitter'
      },
      Badge: {
        FaClass: 'far fa-flag',
        BgColor: 'red',
      } as TimelineBadge
    } as TimelineStep,
    {
      Right: true,
      Card: {
        Title: 'Second Item',
        Content: 'Lorem ipsum dolor sit amet, conectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat.',
      },
      Badge: {
        FaClass: 'fas fa-gift',
        BgColor: 'blue',
      } as TimelineBadge
    } as TimelineStep,
    {
      Card: {
        Title: 'Third Item',
        Content: 'Lorem ipsum dolor sit amet, conectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat.Lorem ipsum dolor sit amet, conectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat.',
      },
      Badge: {
        FaClass: 'far fa-map',
        BgColor: 'orange',
      } as TimelineBadge
    } as TimelineStep,
    {
      Right: true,
      Card: {
        Title: 'Last Item',
        Image: 'https://via.placeholder.com/200x60.png',
        Subtitle: '11 hours ago via Twitter',
        Content: 'Lorem ipsum dolor sit amet, conectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Lorem ipsum dolor sit amet, conectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat.',
      },
      Badge: {
        FaClass: 'far fa-paper-plane',
        BgColor: 'red',
      } as TimelineBadge
    } as TimelineStep,
  ];
}
```   