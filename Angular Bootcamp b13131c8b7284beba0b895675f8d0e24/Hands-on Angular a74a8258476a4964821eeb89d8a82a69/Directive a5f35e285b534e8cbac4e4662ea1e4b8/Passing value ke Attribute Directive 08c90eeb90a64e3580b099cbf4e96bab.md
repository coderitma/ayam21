# Passing value ke Attribute Directive

A

```
import { 
  Directive, 
  **ElementRef, 
  HostListener, 
  Input** 
} from '@angular/core';

@Directive({
  selector: '[appBigfont]'
})
export class BigfontDirective {
  **@Input() appBigfont: string = '';
  
  constructor(private el: ElementRef) {}

  private seleksi(color: string): void {
    this.el.nativeElement.style.color = color;
  }

  @HostListener('mouseenter') onMouseEnter () {
    this.seleksi(this.appBigfont || 'red');
  }

  @HostListener('mouseleave') onMouseLeave () {
    this.seleksi('');
  }**
}
```

A

```
<p [appBigfont]="'blue'">
  Lorem ipsum dolor sit amet consectetur adipisicing elit.
</p>
```

A

![Animation 05.gif](Passing%20value%20ke%20Attribute%20Directive%2008c90eeb90a64e3580b099cbf4e96bab/Animation_05.gif)