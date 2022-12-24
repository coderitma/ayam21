# ngClass

A

```
ng generate interface User
```

A

```
export interface User {
  username: string;
  email: string;
}
```

A

```
import { Component } from '@angular/core';
**import { User } from './user';**

@Component({
  selector: 'app-root',
  templateUrl: './app.component.html',
  styleUrls: ['./app.component.css']
})
export class AppComponent {
  **users: User[] = [
    {
      username: "budi",
      email: "budi@mail.com",
      level: 'staff',
    },
    {
      username: "ani",
      email: "ani@mail.com",
      level: 'admin'
    },
  ]

  seleksi(user: User): boolean {
    return user.level === 'admin';
  }**
}
```

A

![Untitled](ngClass%208d8c2afa1b6f40368f395e20f7c512fe/Untitled.png)

A

```
<h2>ngClass</h2>
<ul>
  <li *ngFor="let user of users" 
    **[ngClass]="{seleksi: user.level === 'admin'}"**>
    {{ user.email }}
  </li>
</ul>
```