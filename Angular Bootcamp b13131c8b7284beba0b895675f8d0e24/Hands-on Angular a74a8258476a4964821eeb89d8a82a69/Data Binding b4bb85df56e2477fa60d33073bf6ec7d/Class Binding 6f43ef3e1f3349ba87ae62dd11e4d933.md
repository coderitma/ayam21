# Class Binding

Buka file `app.component.ts` dan tambahkan atribut bernama `cssClass` dan `terapkan` :

```tsx
export class AppComponent {
  cssClass: string = "red";
  terapkan: boolean = false;
}
```

Selanjutnya, tambahkan kode HTML berikut di dalam `app.component.html`:

```html
<h2>Class Binding</h2>
<p [class]="cssClass">Paragraf ini menjadi warna biru.</p>
<p [class.blue="terapkan"]>Paragraf ini tidak ada efek berwarna</p>
```

Kemudian, tambahkan kode CSS berikut di dalam `app.component.css`:

```css
.red { 
  color: red; 
} 
.blue { 
  color: blue; 
}
```

Jalankan aplikasi dan hasilnya:

![Untitled](Class%20Binding%206f43ef3e1f3349ba87ae62dd11e4d933/Untitled.png)

Coba ubah nilai pada properti `terapkan` menjadi `true` dan hasilnya:

![Untitled](Class%20Binding%206f43ef3e1f3349ba87ae62dd11e4d933/Untitled%201.png)