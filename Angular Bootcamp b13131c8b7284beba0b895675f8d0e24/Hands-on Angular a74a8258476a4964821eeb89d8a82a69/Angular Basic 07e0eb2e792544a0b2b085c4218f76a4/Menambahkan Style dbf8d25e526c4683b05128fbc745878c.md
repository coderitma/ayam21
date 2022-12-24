# Menambahkan Style

## External CSS

Buka file `app.component.css` dan tambahkan kode css berikut:

```css
h2 {
  color: blue;
}

p {
  background-color: blueviolet;
  color: #fff;
}
```

Buka file `app.component.ts` dan pastikan properti `styleUrl` sudah di atur ke referensi file css `app.component.css`:

```tsx
@Component({
  // ...
  styleUrls: ['./app.component.css']
})
```

Jalankan aplikasi dan hasilnya:

![Untitled](Menambahkan%20Style%20dbf8d25e526c4683b05128fbc745878c/Untitled.png)

## Internal CSS

Buka kembali file `app.component.html` dan ubah pada bagian style menjadi:

```tsx
@Component({
  // ...
  styles: [
    `h2 {
      color: blue;
    }`,
    `
    p {
      background-color: blueviolet;
      color: #fff;
    }
    `
  ]
})
export class AppComponent {
  title = 'Web Angularian';
}
```

Jalankan aplikasi, hasilnya:

![Untitled](Menambahkan%20Style%20dbf8d25e526c4683b05128fbc745878c/Untitled.png)