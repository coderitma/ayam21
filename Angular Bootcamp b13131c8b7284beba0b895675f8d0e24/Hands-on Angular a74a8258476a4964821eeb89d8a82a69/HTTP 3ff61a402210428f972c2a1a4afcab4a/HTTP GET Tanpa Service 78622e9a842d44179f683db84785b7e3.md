# HTTP GET Tanpa Service

app → app.module.ts

```
import { NgModule } from '@angular/core';
import { BrowserModule } from '@angular/platform-browser';

import { AppRoutingModule } from './app-routing.module';
import { AppComponent } from './app.component';
**import { HttpClientModule } from '@angular/common/http';**

@NgModule({
  declarations: [
    AppComponent,
  ],
  imports: [
    BrowserModule,
    AppRoutingModule,
    **HttpClientModule,**
  ],
  providers: [],
  bootstrap: [AppComponent]
})
export class AppModule { }
```

```
ng g i interfaces/Todo
```

src\app\interfaces\todo.ts

```
export interface Todo {
  userId: number;
  id: number;
  title: string;
  completed: boolean;
}
```

src\app\app.component.ts

```
**import { HttpClient, HttpErrorResponse } from '@angular/common/http';**
import { Component, **OnInit** } from '@angular/core';
**import { catchError, throwError } from 'rxjs';**
**import { Todo } from './interfaces/todo';**

@Component({
  selector: 'app-root',
  templateUrl: './app.component.html',
  styleUrls: ['./app.component.css']
})
export class AppComponent implements OnInit {
  **baseURL: string = "https://jsonplaceholder.typicode.com";
  todos: Todo[] | undefined;**

  constructor(**private http: HttpClient**) {

  }

  **ngOnInit(): void {
    this.getTodos();
  }**

  **public handleError(error: HttpErrorResponse) {
    if (error.status === 0) {
      // A client-side or network error occurred. Handle it accordingly.
      console.error('An error occurred:', error.error);
    } else {
      // The backend returned an unsuccessful response code.
      // The response body may contain clues as to what went wrong.
      console.error(
        `Backend returned code ${error.status}, body was: `, error.error);
    }
    return throwError(() => new Error('Something bad happened; please try again later.'));
  }

  public getTodos() {
    return this.http.get<Todo[]>(`${this.baseURL}/todos`)
    .pipe(catchError(this.handleError))
      .subscribe(
        (resp: Todo[]) => {
        this.todos = resp;
      })
  }**

}
```

src\app\app.component.html

```
<table>
  <thead>
    <tr>
      <th>UserID</th>
      <th>ID</th>
      <th>Title</th>
      <th>Completed</th>
    </tr>
  </thead>
  <tbody>
    <tr *ngFor="let todo of todos">
      <td>{{ todo.userId }}</td>
      <td>{{ todo.id }}</td>
      <td>{{ todo.title }}</td>
      <td>{{ todo.completed }}</td>
    </tr>
  </tbody>
</table>
```

output

![Untitled](HTTP%20GET%20Tanpa%20Service%2078622e9a842d44179f683db84785b7e3/Untitled.png)