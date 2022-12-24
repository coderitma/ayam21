# Passing Data ke Child Component

Command line:

```
ng g component counter
```

app/counter/counter.component.ts:

```
import { Component, **Input**, OnInit } from '@angular/core';

@Component({
  selector: 'app-counter',
  templateUrl: './counter.component.html',
  styleUrls: ['./counter.component.css']
})
export class CounterComponent implements OnInit {

  **@Input()
  count: number = 0;**

  **increment() {
    this.count++;
  }

  decrement() {
    this.count--;
  }**

  constructor() { }

  ngOnInit(): void {
  }

}
```

app/counter/counter.component.html

```
<p>Counter: <strong>{{ count }}</strong></p>
<button (click)="increment()">Add</button>
<button (click)="decrement()">Substract</button>
```

app/app.component.ts:

```
@Component({
  selector: 'app-root',
  template: `
    **<div class="app">
      <counter [count]="initialCount"></counter>
    </div>**
  `
})
export class AppComponent {
  **initialCount: number = 10;**
}
```

app/app.component.html

```
<h2>Click to count</h2>
<p>initialCount: {{ initialCount }}</p>
<app-counter [count]="initialCount"></app-counter>
```

result:

![Animation 06.gif](Passing%20Data%20ke%20Child%20Component%205619a8bec6cb45beb9d3970b8a330ef7/Animation_06.gif)

### Contoh kedua

app → app.component.ts:

```
import { Component } from '@angular/core';

@Component({
  selector: 'app-root',
  templateUrl: './app.component.html',
  styleUrls: ['./app.component.css']
})
export class AppComponent {
  initialCount: number = 10;

  **counting() {
    this.initialCount++;
  }**
}
```

app → app.component.html:

```
<h2>Click to count</h2>
<p>initialCount: {{ initialCount }}</p>
**<button (click)="counting()">Klik me</button>**
<app-counter [count]="initialCount"></app-counter>
```

result:

![Animation 07.gif](Passing%20Data%20ke%20Child%20Component%205619a8bec6cb45beb9d3970b8a330ef7/Animation_07.gif)