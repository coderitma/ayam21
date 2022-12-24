# Property Binding

Tambahkan kode berikut ke dalam `app.component.ts`:

```tsx
import { Component } from '@angular/core';

@Component({
  selector: 'app-root',
  templateUrl: './app.component.html',
  styleUrls: ['./app.component.css']
})
export class AppComponent {
  image: string = "https://picsum.photos/id/220/200/90";

  gantiGambar(): void {
    this.image = "https://picsum.photos/id/237/200/90";
  }
}
```

Buka file `app.component.html` dan tambahkan kode berikut:

```html
<h2>Property Binding</h2> 
<img [src]="image" alt="">
<p>Tekan tombol berikut untuk mengganti gambar</p>
<button (click)="gantiGambar()">Ganti Gambar</button>
```

Jalankan aplikasi dan hasilnya:

![Untitled](Property%20Binding%203b8f5f80b2834851bd38dac848f9e9b4/Untitled.png)

Tekan tombol ************Ganti Gambar************ dan hasilnya:

![Untitled](Property%20Binding%203b8f5f80b2834851bd38dac848f9e9b4/Untitled%201.png)