# Routing Navigation

Buat beberapa component yang dibutuhkan:

```
ng generate component components/home
ng generate component components/about
ng generate component components/error
ng generate component components/navigation
```

Buka file `src\app\components\home\home.component.html` dan tambahkan:

```
<h1>Welcome to my web</h1>
<p>
  Lorem ipsum dolor sit amet consectetur adipisicing elit. 
  Officiis ex velit molestiae itaque nostrum dolor consequatur. 
  Neque illo repudiandae perferendis, adipisci consectetur, 
  quos error commodi soluta eaque, vero placeat provident.
</p>
<p>
  Lorem ipsum dolor sit, amet consectetur adipisicing elit. 
  Corporis quod nam provident libero velit voluptatum, accusamus autem, 
  sunt inventore ratione sed et recusandae distinctio nisi blanditiis 
  similique omnis laudantium exercitationem.
</p>
```

Buka file `src\app\components\about\about.component.html` dan tambahkan:

```
<h1>About me</h1>
<p>
  Lorem ipsum dolor sit amet consectetur adipisicing elit. Non doloribus sint, repudiandae veniam ullam voluptates eos quidem, recusandae laboriosam eius ut laudantium odio quos eaque ab excepturi atque vitae iure.
</p>
```

Buka file `src\app\components\error\error.component.html` dan tambahkan:

```
<h1>Error: Resource not found</h1>
```

Buka file `src\app\components\navigation\navigation.component.html` dan tambahkan:

```
<h4>Navigation</h4>
<ul>
  <li>
    <a [routerLink]="['home']">Home</a>
  </li>
  <li>
    <a [routerLink]="['about']">About</a>
  </li>
</ul>
```

Buka file `src\app\app-routing.module.ts` dan tambahkan:

```
import { NgModule } from '@angular/core';
import { RouterModule, Routes } from '@angular/router';
**import { AboutComponent } from './components/about/about.component';
import { ErrorComponent } from './components/error/error.component';
import { HomeComponent } from './components/home/home.component';**

const routes: Routes = [
  **{ path: 'home', component: HomeComponent },
  { path: 'about', component: AboutComponent },
  { path: '', redirectTo: "home", pathMatch: "full" },
  { path: '**', component: ErrorComponent },**
];

@NgModule({
  imports: [RouterModule.forRoot(routes)],
  exports: [RouterModule]
})
export class AppRoutingModule { }
```

Buka file `src\app\app.component.html` dan tambahkan:

```
<app-navigation></app-navigation>
<router-outlet></router-outlet>
```

Jika belum ada routing, jalankan perintah berikut untuk membuat routing:

```
ng generate module app-routing --flat --module=app
```

Pastikan `AppRoutingModule` sudah ada di dalam `imports` di `AppModule`:

```
**import { AppRoutingModule } from './app-routing.module';**

@NgModule({
  declarations: [
    // ...
  ],
  imports: [
    // ...
    **AppRoutingModule,**
    // ...
  ],
  providers: [
		// ...
	],
  bootstrap: [AppComponent]
})
export class AppModule { }
```

Jalankan dan hasilnya:

![Animation 7.gif](Routing%20Navigation%204c9c340a70ca4ce1bbbd42d717d7e968/Animation_7.gif)