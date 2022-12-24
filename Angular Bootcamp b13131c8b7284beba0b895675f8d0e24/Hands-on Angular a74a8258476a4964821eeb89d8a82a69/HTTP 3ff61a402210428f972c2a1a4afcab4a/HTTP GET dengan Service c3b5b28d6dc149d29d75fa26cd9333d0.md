# HTTP GET dengan Service

Buat interface dengan nama `post-interface` di dalam folder `interfaces`:

```
ng generate interface interfaces/post-interface
```

Tambahkan kode berikut di dalam file `src/app/interfaces/post-interface.ts`:

```
export interface PostInterface {
  userId: number;
  id: number;
  title: string;
  body: string;
}
```

Buat service dengan nama `post` di dalam folder `services`:

```
ng generate service services/post
```

Tambahkan kode berikut ke dalam file `src/app/services/post.service.ts`:

```
**import { HttpClient } from '@angular/common/http';**
import { Injectable } from '@angular/core';
**import { Observable } from 'rxjs';
import { PostInterface } from '../interfaces/post-interface';**

@Injectable({
  providedIn: 'root'
})
export class PostService {
  **private baseURL: string = "https://jsonplaceholder.typicode.com";**

  constructor(**private http: HttpClient**) { }

  **public all(): Observable<PostInterface[]> {
    return this.http.get<PostInterface[]>(`${this.baseURL}/posts`);
  }**
}
```

Tambahkan kode berikut ke dalam file `src/app/app.component.ts`:

```
import { Component, **OnInit** } from '@angular/core';
**import { PostInterface } from './interfaces/post-interface';
import { PostService } from './services/post.service';**

@Component({
  selector: 'app-root',
  templateUrl: './app.component.html',
  styleUrls: ['./app.component.css']
})
export class AppComponent **implements OnInit** {
  **posts: PostInterface[] | undefined;**

  **constructor(private postService: PostService) {
  }**

  **ngOnInit(): void {
    this.postService.all()
      .subscribe((response: PostInterface[]) => {
        this.posts = response;
      })  
  }**
}
```

Tambahkan kode berikut ke dalam file `src/app/app.component.html`:

```
<h1>Posting</h1>
<div *ngFor="let post of posts">
  <h2>{{ post.title }}</h2>
  <p>{{ post.body }}</p>
</div>
```

Jalankan aplikasi dan hasilnya:

![Untitled](HTTP%20GET%20dengan%20Service%20c3b5b28d6dc149d29d75fa26cd9333d0/Untitled.gif)

Q Params GET:

```
export class App {
  name:string;
  constructor(private httpClient: HttpClient) {
    this.httpClient.get('/url', {
      params: {
        appid: 'id1234',
        cnt: '5'
      },
      observe: 'response'
    })
    .toPromise()
    .then(response => {
      console.log(response);
    })
    .catch(console.log);
  }
}
```

```
const headerDict = {
  'Content-Type': 'application/json',
  'Accept': 'application/json',
  'Access-Control-Allow-Headers': 'Content-Type',
}

const requestOptions = {                                                                                                                                                                                 
  headers: new Headers(headerDict), 
};

return this.http.get(this.heroesUrl, requestOptions)
```