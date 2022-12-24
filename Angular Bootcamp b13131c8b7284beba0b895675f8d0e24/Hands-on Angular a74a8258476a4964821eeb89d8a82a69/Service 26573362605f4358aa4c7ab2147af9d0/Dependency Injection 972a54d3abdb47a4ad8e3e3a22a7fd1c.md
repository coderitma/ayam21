# Dependency Injection

A

![Animation 06.gif](Dependency%20Injection%20972a54d3abdb47a4ad8e3e3a22a7fd1c/Animation_06.gif)

command line:

```
ng generate interface post
```

src/app/post.ts

```
export interface Post {
  id: number;
  title: string;
  body: string;
}
```

command line:

```
ng generate class post-model
```

src/app/post-model.ts

```
import { Post } from "./post";

export class PostModel implements Post {
  id: number;
  title: string;
  body: string;

  constructor(id: number, title: string, body: string) {
    this.id = id;
    this.title = title;
    this.body = body;
  }
}
```

command line:

```
ng generate service post
```

src/app/post.service.ts

```
import { Injectable } from '@angular/core';
import { Post } from './post';
import { PostModel } from './post-model';

@Injectable({
  providedIn: 'root'
})
export class PostService {

  constructor() { }

  public all(): Post[] {
    let posts: Post[] = [
      new PostModel(
        1, 
        "sunt aut facere repellat",
        "sunt aut facere repellat provident occaecati excepturi optio reprehenderit"
      ),
      new PostModel(
        2, 
        "qui est esse",
        "est rerum tempore vitae sequi sint nihil reprehenderit dolor beatae"
      ),
    ];

    return posts;
  }
}
```

src/app/app.component.html

```
import { Component } from '@angular/core';
**import { Post } from './post';
import { PostService } from './post.service';**

@Component({
  selector: 'app-root',
  templateUrl: './app.component.html',
  styleUrls: ['./app.component.css']
})
export class AppComponent {
  **posts: Post[];

  constructor(private postService: PostService) {
    this.posts = [];
  }

  getPosts(): void {
    this.posts = this.postService.all();
  }**
}
```

src/app/app.component.html

```
<h2>Welcome to My Blog</h2>
<button (click)="getPosts()">Get Posts</button>

<ul>
  <li *ngFor="let post of posts" style="list-style: none;">
    <h3>{{ post.title }}</h3>
    <p>
      <small>{{ post.body }}</small>
    </p>
  </li>
</ul>
```