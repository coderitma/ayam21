# Passing Data ke Parent Component

command line:

```
ng generate component antrian
ng generate i data-emit
```

app → data-emit.ts:

```
export interface DataEmit {
  antrian: string[];
  total: number;
}
```

app → antrian → antrian.component.ts:

```
import { Component, **EventEmitter**, **Input**, OnInit, **Output** } from '@angular/core';
**import { DataEmit } from '../data-emit';**

@Component({
  selector: 'app-antrian',
  templateUrl: './antrian.component.html',
  styleUrls: ['./antrian.component.css']
})
export class AntrianComponent implements OnInit {
  **counter: number = 1;
  @Input()
  antrian: string[];
  
  @Output() onAntrianBerubah: EventEmitter<DataEmit> = new EventEmitter();**

  constructor() {
    **this.antrian = [];**
  }

  **tambahAntrian(): void {
    this.antrian.push(`Antrian ke ${this.counter++}`);
    let dataEmit: DataEmit = {
      total: this.antrian.length,
      antrian: this.antrian
    };

    this.onAntrianBerubah.emit(dataEmit);
  }

  kurangiAntrian(): void {
    this.antrian.pop();
    let dataEmit: DataEmit = {
      total: this.antrian.length,
      antrian: this.antrian
    };
    this.onAntrianBerubah.emit(dataEmit);
  }**

  ngOnInit(): void {
  }

}
```

app → antrian → antrian.component.html:

```
<h1>Antrian Component</h1>
<p>
  <button (click)="tambahAntrian()">Tambah</button>
</p>
<p>
  <button (click)="kurangiAntrian()">Kurang</button>
</p>
```

app → app.component.ts:

```
import { Component } from '@angular/core';
**import { DataEmit } from './data-emit';**

@Component({
  selector: 'app-root',
  templateUrl: './app.component.html',
  styleUrls: ['./app.component.css']
})
export class AppComponent {
  **antrian: string[] = [];
  total: number = this.antrian.length;**

  **onAntrianBerubah(dataEmit: DataEmit): void {
    this.antrian = dataEmit.antrian;
    this.total = dataEmit.total;
  }**
}
```

app → app.component.html:

```
<h1>App Component</h1>
<app-antrian 
  [antrian]="antrian" 
  (onAntrianBerubah)="onAntrianBerubah($event)"></app-antrian>
<table>
  <tbody>
    <tr>
      <td>Jumlah Antrian</td>
      <td>{{ total }}</td>
    </tr>
    <tr *ngFor="let item of antrian; if total > 0">
      <td colspan="2">{{ item }}</td>
    </tr>
  </tbody>
</table>
```

Hasil:

![Animation 07.gif](Passing%20Data%20ke%20Parent%20Component%20d0fe77273ea1406bb29ee6145717b87c/Animation_07.gif)

app → antrian → antrian.component.ts:

```
tambahAntrian(): void {
  **if (this.antrian.length === 0) {
    this.counter = 1;
  }**
  this.antrian.push(`Antrian ke ${this.counter++}`);
  let dataEmit: DataEmit = {
    total: this.antrian.length,
    antrian: this.antrian
  };

  this.onAntrianBerubah.emit(dataEmit);
}
```

result:

![Animation 08.gif](Passing%20Data%20ke%20Parent%20Component%20d0fe77273ea1406bb29ee6145717b87c/Animation_08.gif)