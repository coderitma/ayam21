# Custom Directive

A

```
ng generate directive bigfont
```

A

```
CREATE src/app/bigfont.directive.spec.ts (228 bytes)
CREATE src/app/bigfont.directive.ts (143 bytes)
UPDATE src/app/app.module.ts (625 bytes)
```

A

```
**import { BigfontDirective } from './bigfont.directive';**

@NgModule({
  declarations: [
    // ...
    **BigfontDirective**
  ],
  // ...
})
export class AppModule { }
```

A

```
import { Directive, **ElementRef** } from '@angular/core';

@Directive({
  selector: '[appBigfont]'
})
export class BigfontDirective {

  **constructor(el: ElementRef) {
    let style: any = el.nativeElement.style;
    style.fontSize = '30px';
    style.color = 'red';
  }**

}
```

A

```
<h2>Custom Directive</h2>
<p **appBigfont**>
  Lorem ipsum dolor sit, amet consectetur adipisicing elit.
</p>
```