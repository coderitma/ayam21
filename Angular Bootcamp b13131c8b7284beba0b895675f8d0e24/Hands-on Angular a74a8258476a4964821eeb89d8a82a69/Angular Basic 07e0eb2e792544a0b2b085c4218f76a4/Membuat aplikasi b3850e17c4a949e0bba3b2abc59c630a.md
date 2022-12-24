# Membuat aplikasi

Command line:

```
ng version
```

Output:

```
Angular CLI: 14.2.6
Node: 16.17.1
Package Manager: npm 8.15.0
OS: win32 x64

Angular:
...

Package                      Version
------------------------------------------------------
@angular-devkit/architect    0.1402.6 (cli-only)
@angular-devkit/core         14.2.6 (cli-only)
@angular-devkit/schematics   14.2.6 (cli-only)
@schematics/angular          14.2.6 (cli-only)
```

Buat project dengan nama `angularian`:

```
ng new angularian

? Would you like to add Angular routing? Yes
? Which stylesheet format would you like to use? CSS
```

Output:

```
...
CREATE angularian/src/environments/environment.prod.ts (51 bytes)
CREATE angularian/src/environments/environment.ts (658 bytes)
CREATE angularian/src/app/app-routing.module.ts (245 bytes)
CREATE angularian/src/app/app.module.ts (393 bytes)
CREATE angularian/src/app/app.component.html (23115 bytes)
CREATE angularian/src/app/app.component.spec.ts (1085 bytes)
CREATE angularian/src/app/app.component.ts (214 bytes)
CREATE angularian/src/app/app.component.css (0 bytes)
√ Packages installed successfully.
```

Jalalankan aplikasi:

```
ng serve
```

Buka browser dan akses http://localhost:4200:

![Untitled](Membuat%20aplikasi%20b3850e17c4a949e0bba3b2abc59c630a/Untitled.png)

Buka app.component.ts dan ubah isi `title`menjadi:

```tsx
export class AppComponent {
  title = 'Web Angularian';
}
```

Buka `app.component.html` dan ubah menjadi:

```html
<h2>{{ title }}</h2>
<p>Angular web framework</p>
```

Output:

![Untitled](Membuat%20aplikasi%20b3850e17c4a949e0bba3b2abc59c630a/Untitled%201.png)