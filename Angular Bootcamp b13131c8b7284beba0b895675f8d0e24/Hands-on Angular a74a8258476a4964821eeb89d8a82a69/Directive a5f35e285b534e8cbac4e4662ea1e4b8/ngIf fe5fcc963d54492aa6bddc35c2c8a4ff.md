# ngIf

A

```tsx
export class AppComponent {
  pesan: string;
  tampil: boolean = false;
  constructor() {
    this.pesan = "Halo aku tampil";
  }

  toggle():void {
    this.tampil = !this.tampil;
  }
}
```

A

```html
<h2>ngIf Directive</h2>
<h5 *ngIf="tampil">
  {{ pesan }}
</h5>

<button>{{ tampil? "Hide":"Show" }}</button>
```

A

![Animation 05.gif](ngIf%20fe5fcc963d54492aa6bddc35c2c8a4ff/Animation_05.gif)

A

```html
<h2>ngIf Directive</h2>
<h5 *ngIf="tampil; else showDefault">
  {{ pesan }}
</h5>

<ng-template #showDefault>
  <h5>Data tidak tampil</h5>
</ng-template>

<button (click)="toggle()">{{ tampil? "Hide":"Show" }}</button>
```

A

![Animation 05.gif](ngIf%20fe5fcc963d54492aa6bddc35c2c8a4ff/Animation_05%201.gif)