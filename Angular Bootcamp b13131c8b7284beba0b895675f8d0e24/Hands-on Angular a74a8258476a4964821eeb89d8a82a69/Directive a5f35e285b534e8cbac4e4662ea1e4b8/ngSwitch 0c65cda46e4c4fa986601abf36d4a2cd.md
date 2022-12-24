# ngSwitch

A

```tsx
export class AppComponent {
  **grading: string = "A";**
}
```

A

```html
<h2>ngSwitch Directive</h2>

<ul [ngSwitch]="grading">
  <li *ngSwitchCase="'A'">
    Excelent
  </li>
  <li *ngSwitchCase="'B'">
    Good Job
  </li>
  <li *ngSwitchCase="'C'">
    Coba Lagi
  </li>
  <li *ngSwitchDefault>
    Heuum...
  </li>
</ul>
```

A

![Untitled](ngSwitch%200c65cda46e4c4fa986601abf36d4a2cd/Untitled.png)