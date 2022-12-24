# Menambahkan Component

Buka command line dan jalankan perintah berikut untuk membuat component bernama `employee`:

```html
ng generate component employee
```

Output:

```html
CREATE src/app/employee/employee.component.html (23 bytes)
CREATE src/app/employee/employee.component.spec.ts (613 bytes)
CREATE src/app/employee/employee.component.ts (283 bytes)
CREATE src/app/employee/employee.component.css (0 bytes)
UPDATE src/app/app.module.ts (483 bytes)
```

Tambahkan properti `judul` di `app/employee/employee.component.ts`:

```tsx
export class EmployeeComponent implements OnInit {
  judul: string;
  
  constructor() {
    this.judul = "Employee component";
  }

  ngOnInit(): void { }
}
```

Buka file `app.module.ts` dan pastikan component sudah terdaftar di dalam `declaration`:

```tsx
@NgModule({
  declarations: [
    AppComponent,
    EmployeeComponent
  ],
  imports: [ ],
  providers: [ ],
  bootstrap: [AppComponent]
})
export class AppModule { }
```

Selanjutnya, buka file `employee.component.html` dan ubah menjadi:

```html
<p>employee works!</p>
<p>{{ judul }}</p>
```

 Buka file `app.component.html` dan panggil component employee ke dalamnya:

```html
<h2>{{ title }}</h2>
<p>Angular web framework</p>
<app-employee></app-employee>
```

Jalankan aplikasi dan hasilnya:

![Untitled](Menambahkan%20Component%20e3a2a150904c4761b6a1258548b8ff4c/Untitled.png)