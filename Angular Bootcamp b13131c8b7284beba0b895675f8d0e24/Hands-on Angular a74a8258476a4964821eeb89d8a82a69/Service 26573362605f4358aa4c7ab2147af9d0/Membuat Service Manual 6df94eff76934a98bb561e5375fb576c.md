# Membuat Service Manual

/src/app/produk.ts

```
export class Galeri {
  id: number;
  url: string;

  constructor(id: number, url: string) {
    this.id = id;
    this.url = url;
  }
}
```

/src/app/galeri.service.ts

```
import { Galeri } from "./Galeri";

export class GaleriService {
  public getGaleri(): Galeri[] {
    let daftarGaleri: Galeri[];
    daftarGaleri = [
      new Galeri(1, "https://via.placeholder.com/150/92c95"),
      new Galeri(2, "https://via.placeholder.com/150/771796"),
      new Galeri(3, "https://via.placeholder.com/150/24f355"),
    ]

    return daftarGaleri;
  }
}
```

/src/app/app.component.ts

```
import { Component } from '@angular/core';
import { Galeri } from './Galeri';
import { GaleriService } from './galeri.service';
import { User } from './user';

@Component({
  selector: 'app-root',
  templateUrl: './app.component.html',
  styleUrls: ['./app.component.css']
})
export class AppComponent {
  daftarGaleri: Galeri[] = [];
  galeriService: GaleriService;

  constructor() {
    this.galeriService = new GaleriService();
  }

  getGaleri() {
    this.daftarGaleri = this.galeriService.getGaleri();
  }
}
```

/src/app/app.component.html

```
<h2>Foto Galeri</h2>
<button (click)="getGaleri()">Get Galeri</button>
<ul>
  <li *ngFor="let galeri of daftarGaleri" style="list-style: none;">
    <img [src]="galeri.url" />
    <p>ID: {{ galeri.id }}</p>
  </li>
</ul>
```

A:

![Animation 05.gif](Membuat%20Service%20Manual%206df94eff76934a98bb561e5375fb576c/Animation_05.gif)