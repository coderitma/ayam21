# Style Binding

Buka file `app.component.ts` dan tambahkan atribut bernama `success` dan `fail`:

```tsx
export class AppComponent {
  success: string = "green";
  fail: string = "red";
}
```

Selanjutnya, buka `app.component.html` dan tambahkan:

```html
<h2>Style Binding</h2>

<p [style.backgroundColor]="success">
  <strong>Sukses</strong>
  <span >
    Lorem ipsum, dolor sit amet consectetur adipisicing elit. 
    Quo, nostrum animi! Ducimus beatae corrupti reiciendis 
    consequatur maiores debitis velit incidunt, at quos ab 
    reprehenderit in modi optio sint iusto veritatis!
  </span>
</p>

<p [style.backgroundColor]="fail">
  <strong>Error</strong>
  <span >
    Lorem ipsum, dolor sit amet consectetur adipisicing elit. 
    Quo, nostrum animi! Ducimus beatae corrupti reiciendis 
    consequatur maiores debitis velit incidunt, at quos ab 
    reprehenderit in modi optio sint iusto veritatis!
  </span>
</p>
```

Jalankan dan hasilnya:

![Untitled](Style%20Binding%20d474ea3676ed4b97bf6c0755696d1fd2/Untitled.png)