# Kirim Parameter

Buka file `src\app\app-routing.module.ts` dan tambahkan:

```
// ...

const routes: Routes = [
  { path: 'home', component: HomeComponent },
  **{ path: 'about/:name', component: AboutComponent },**
  { path: '', redirectTo: "home", pathMatch: "full" },
  { path: '**', component: ErrorComponent },
];

@NgModule({
  // ...
})
export class AppRoutingModule { }
```

Buka file `src\app\components\home\home.component.html` dan tambahkan:

```
<h1>Welcome to my web</h1>
**<p>
  <a [routerLink]="['/about', 'Yanwar Solahudin']">
    Link to about me
  </a>
</p>**
<p>
  ...
</p>
<p>
  ...
</p>
```

Buka file `src\app\components\about\about.component.ts` dan tambahkan:

```
import { Component, OnInit } from '@angular/core';
**import { ActivatedRoute, Router } from '@angular/router';**

@Component({
  selector: 'app-about',
  templateUrl: './about.component.html',
  styleUrls: ['./about.component.css']
})
export class AboutComponent implements OnInit {
  **nameParam: string | null;
  sub: any;**

  **constructor(private actiavtedRoute: ActivatedRoute, 
    private router: Router) {
    this.nameParam = "";
  }**

  ngOnInit(): void {
    **this.sub = this.actiavtedRoute.paramMap.subscribe((params) => {
      this.nameParam = params.get('name');
    })**
  }

  **ngOnDestroy() {
    if (this.sub) {
      this.sub.unsubscribe();
    }
  }**

  **back(): void {
    this.router.navigate(['home']);
  }**

}
```

Buka file `src\app\components\about\about.component.html` dan tambahkan:

```
<h1>About me</h1>
**<h3 *ngIf="nameParam">
  Parameter: {{ nameParam }}
  <button (click)="back()">Kembali ke home</button>
</h3>**
<p>
  ...
</p>
```

Jalankan dan hasilnya:

![Animation 10.gif](Kirim%20Parameter%20c9b025d03ae548539bff4afc8a189a45/Animation_10.gif)