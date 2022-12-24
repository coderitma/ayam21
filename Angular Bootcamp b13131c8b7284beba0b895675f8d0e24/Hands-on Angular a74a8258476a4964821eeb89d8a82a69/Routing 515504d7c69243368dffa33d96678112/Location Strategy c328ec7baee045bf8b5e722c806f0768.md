# Location Strategy

Jika kita ingin path url selalu dimulai dengan `my/apps` (path location strategy), kita bisa menambahkan kode berikut di dalam file `src\app\app-routing.module.ts`:

```
**import { APP_BASE_HREF } from '@angular/common';**
// ...

const routes: Routes = [
  // ...
];

@NgModule({
  imports: [RouterModule.forRoot(routes)],
  exports: [RouterModule],
  **providers: [{provide: APP_BASE_HREF, useValue: '/my/apps'}]**
})
export class AppRoutingModule { }
```

Jalankan dan hasilnya:

![Animation 8.gif](Location%20Strategy%20c328ec7baee045bf8b5e722c806f0768/Animation_8.gif)

Jika kita ingin bentuk path url seperti `/#/<path>` kita bisa menambahkan kode berikut di dalam file 

```
@NgModule({
  imports: [RouterModule.forRoot(routes, **{useHash: true}**)],
  exports: [RouterModule],
  providers: [{provide: APP_BASE_HREF, useValue: '/my/apps'}],
})
export class AppRoutingModule { }
```

Jalankan dan hasilnya:

![Animation 9.gif](Location%20Strategy%20c328ec7baee045bf8b5e722c806f0768/Animation_9.gif)