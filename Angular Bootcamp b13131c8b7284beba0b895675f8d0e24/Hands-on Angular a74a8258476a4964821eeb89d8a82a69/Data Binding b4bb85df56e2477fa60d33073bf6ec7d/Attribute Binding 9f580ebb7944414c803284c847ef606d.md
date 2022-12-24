# Attribute Binding

Buka file `app.component.ts` dan tambahkan properti bernama `colspan`:

```tsx
export class AppComponent {
  colspan: number = 2;
}
```

Buka file `app.component.html` dan tambahkan tabel berikut:

```html
<h2>Attribute Binding</h2>
<table border="1">
  <thead>
    <tr>
      <th [attr.colspan]="colspan">Nama Lengkap</th>
      <th>Saldo</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>Yanwar</td>
      <td>Solahudin</td>
      <td>1000000</td>
    </tr>
  </tbody>
</table>
```

Jalankan aplikasi dan hasilnya:

![Untitled](Attribute%20Binding%209f580ebb7944414c803284c847ef606d/Untitled.png)

Jika kita ubah seperti property binding:

```html
<th [colspan]="colspan">Nama Lengkap</th>
```

Hasilnya error:

![Untitled](Attribute%20Binding%209f580ebb7944414c803284c847ef606d/Untitled%201.png)

Tidak semua attribute bisa diterapkan dengan property binding, termasuk attribute `colspan`.