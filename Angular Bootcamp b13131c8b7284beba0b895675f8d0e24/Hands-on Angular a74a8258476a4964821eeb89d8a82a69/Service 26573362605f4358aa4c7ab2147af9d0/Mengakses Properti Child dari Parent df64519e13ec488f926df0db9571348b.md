# Mengakses Properti Child dari Parent

command line:

```
ng g c child
```

app child child.component.ts:

```
import { Component, OnInit } from '@angular/core';

@Component({
  selector: 'app-child',
  templateUrl: './child.component.html',
  styleUrls: ['./child.component.css']
})
export class ChildComponent implements OnInit {
  **randomNumber: number;**

  constructor() {
    **this.randomNumber = this.getRandom(1000);**
  }

  **getRandom(limit: number = 100): number {
    return Math.floor(Math.random() * limit) + 1;
  }**

  **onRandom() {
    this.randomNumber = this.getRandom(1000);
  }**

  ngOnInit(): void {
  }

}
```

child.component.html

```
<p>Number: <strong>{{ randomNumber }}</strong></p>
```

app.component.html

```
<h1>Random Number</h1>
<app-child #child></app-child>

<button (click)="child.onRandom()">Klik {{ child.randomNumber }}</button>
```

result:

![Animation 09.gif](Mengakses%20Properti%20Child%20dari%20Parent%20df64519e13ec488f926df0db9571348b/Animation_09.gif)