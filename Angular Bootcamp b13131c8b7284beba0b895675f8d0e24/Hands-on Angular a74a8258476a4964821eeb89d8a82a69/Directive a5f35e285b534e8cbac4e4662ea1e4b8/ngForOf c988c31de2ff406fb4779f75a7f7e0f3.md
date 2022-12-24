# ngForOf

a

```
export class AppComponent {
  buah: string[] = [
    "Mangga", "Apel",
    "Jeruk", "Anggur"
  ];
}
```

a

```
<ul>
  <ng-template ngFor let-item [ngForOf]="buah" let-i="index">
    <li>{{ i }}. {{ item }}</li>
  </ng-template>
</ul>
```

a

![Untitled](ngForOf%20c988c31de2ff406fb4779f75a7f7e0f3/Untitled.png)