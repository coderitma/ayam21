# Router Auxiliary Outlet

Buka file `src\app\app.component.html` dan tambahkan:

```
<app-navigation></app-navigation>
<router-outlet></router-outlet>
**<router-outlet name="a"></router-outlet>
<router-outlet name="b"></router-outlet>**
```

Buka file `src\app\app-routing.module.ts` dan ubah:

```
const routes: Routes = [
  **{ path: 'home', component: HomeComponent, outlet: 'a' },
  { path: 'about/:name', component: AboutComponent, outlet: 'b' },**
  **{ path: '', redirectTo: "home", pathMatch: "full", outlet: 'a' },**
  { path: '**', component: ErrorComponent },
];
```

Buka file `src\app\components\navigation\navigation.component.html` dan ubah:

```
<h4>Navigation</h4>
<ul>
  <li>
    <a **[routerLink]="[{outlets: { a: ['home'] }}]"**>Home</a>
  </li>
  <li>
    <a **[routerLink]="[{outlets: { b: ['about', 'ayam'] }}]"**>About</a>
  </li>
</ul>
```

Buka file `src\app\components\about\about.component.ts` dan ubah:

```
export class AboutComponent implements OnInit {
  // ...

  back(): void {
    **this.router.navigate([{outlets: { a: ['home'] }},]);**
  }

}
```

Jalankan dan hasilnya:

![Animation 11.gif](Router%20Auxiliary%20Outlet%20124d42ee8eb2458cb3a7a3e02fd05954/Animation_11.gif)

Link outlet b dibuat di dalam component yang menggunakan outlet a, bisa menyebabkan error.

Buka file `src\app\components\home\home.component.html` dan ubah:

```
<h1>Welcome to my web</h1>
<p>
  <a **[routerLink]="[{outlets: { b: ['about', 'Yanwar Solahudin'] }}]"**>
    Link to about me
  </a>
</p>
<p>
  ...
</p>
<p>
  ...
</p>
```

Jalankan dan hasilnya:

![Animation 12.gif](Router%20Auxiliary%20Outlet%20124d42ee8eb2458cb3a7a3e02fd05954/Animation_12.gif)