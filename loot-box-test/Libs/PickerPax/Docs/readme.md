### Readme

> [![](https://img.shields.io/badge/Main-readme‌‌‌‌‌‌‌-white)](../../readme.desc.md) [![](https://img.shields.io/badge/usage‌‌‌‌‌‌‌-orange)](usage.md)

### PickerPax

[![Progress](https://img.shields.io/badge/Demo-✔☐☐☐☐‌‌‌‌‌‌‌-blue)](https://krsln.github.io/NgLootBox/Beta/PickerPax)  

#### Dependencies
import {Guid} from '@qrsln/utils/Core';  
import {FadeInOut} from '@qrsln/utils/Animations';

```shell
# BrowserAnimationsModule for animations

npm install --save @qrsln/utils
npm install --save @fortawesome/fontawesome-free
```

#### Properties

Name | Description
 --- | ---  
PaxList: PaxListItem[] | Check usage page
Label: string | default value is 'Passengers'
OnChanged: EventEmitter<Pax[]> | {Code: string; Value: number;}[]

#### Screenshots

![](Screenshots/PickerPax.png "PickerPax")  
