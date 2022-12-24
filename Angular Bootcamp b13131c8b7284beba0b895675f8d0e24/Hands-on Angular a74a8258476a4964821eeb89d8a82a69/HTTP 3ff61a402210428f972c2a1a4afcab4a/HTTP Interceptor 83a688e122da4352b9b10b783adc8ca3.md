# HTTP Interceptor

Buat beberapa file yang dibutuhkan:

```
ng generate interceptor interceptors/auth
ng generate interface interfaces/profile-interface
ng generate service services/profile
ng generate component components/profile
```

Buka file `auth.interceptor.ts` dari folder `src\app\interceptors` dan tambahkan:

```
import { Injectable } from '@angular/core';
import {
  HttpRequest,
  HttpHandler,
  HttpEvent,
  HttpInterceptor
} from '@angular/common/http';
**import { Observable } from 'rxjs';**

@Injectable()
export class AuthInterceptor implements HttpInterceptor {
  **// For sample (gdn)
  token: string = "eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9....";**
  constructor() {}

  intercept(request: HttpRequest<unknown>, 
		next: HttpHandler): Observable<HttpEvent<unknown>> {
    **// prefer token from localstorage or another service**
    **if (this.token) {
      request = request.clone({ 
        headers: request.headers.set("Authorization", `JWT ${this.token}`) 
      });
    }**
    return next.handle(request);
  }
}
```

Buka file `profile-interface.ts` dari folder `src\app\interfaces` dan tambahkan:

```
export interface CorporatePartnerInterface {
  description?: string;
  logo?: string;
  nik?: string;
}

export interface MyValueInterface {
  id?: string;
  point: number;
}

export interface ProfileInterface {
  accountType: string;
  birthDate: "2018-04-20";
  corporatePartner: CorporatePartnerInterface;
  favouriteCategory?: string[];
  email: string;
  firstName: string;
  gender: string;
  hoby?: string[];
  isSocialLogin: boolean;
  lastName: string;
  myvalue: MyValueInterface;
  occupation: string;
  phoneNumber: string;
  username: string;
  verified: boolean;
}
```

Buka file `profile.service.ts` dari folder `src\app\services` dan tambahkan:

```
**import { HttpClient } from '@angular/common/http';**
import { Injectable } from '@angular/core';
import { Observable } from 'rxjs';
**import { ProfileInterface } from '../interfaces/profile-interface';**

@Injectable({
  providedIn: 'root'
})
export class ProfileService {
  **private baseURL: string = "https://www.gramedia.com/api/user/profiles/";**

  constructor(**private http: HttpClient**) { }

  **public getProfile(): Observable<ProfileInterface> {
    return this.http.get<ProfileInterface>(this.baseURL);
  }**
}
```

Buka file `profile.component.ts` dari folder `src\app\components\profile` dan tambahkan:

```
import { Component, OnInit } from '@angular/core';
**import { ProfileInterface } from 'src/app/interfaces/profile-interface';
import { ProfileService } from 'src/app/services/profile.service';**

@Component({
  selector: 'app-profile',
  templateUrl: './profile.component.html',
  styleUrls: ['./profile.component.css']
})
export class ProfileComponent implements OnInit {
  **profile!: ProfileInterface;**

  constructor(**private profileService: ProfileService**) {}

  ngOnInit(): void {
    **this.getProfile();**
  }

  **public getProfile(): void {
    this.profileService.getProfile()
      .subscribe((response: ProfileInterface) => {
        this.profile = response;
      });
  }**

}
```

Buka file `profile.component.html` dari folder `src\app\components\profile` dan tambahkan:

```
<table *ngIf="profile" border="1">
  <tbody>
    <tr>
      <th>Account Type</th>
      <td>{{ profile.accountType }}</td>
    </tr>
    <tr>
      <th>Birth Date</th>
      <td>{{ profile.birthDate }}</td>
    </tr>
    <tr>
      <th>Email</th>
      <td>{{ profile.email }}</td>
    </tr>
  </tbody>
</table>

<table *ngIf="profile && profile.corporatePartner" border="1">
  <tbody>
    <tr>
      <th>Logo</th>
      <td>
        <img [src]="profile.corporatePartner.logo" 
          [alt]="profile.corporatePartner.logo" />
      </td>
    </tr>
  </tbody>
</table>
```

Buka file `app.module.ts` dari folder `src\app` dan tambahkan:

```
import { NgModule } from '@angular/core';
import { BrowserModule } from '@angular/platform-browser';
**import { HttpClientModule, HTTP_INTERCEPTORS } from '@angular/common/http';**
import { AppRoutingModule } from './app-routing.module';
import { AppComponent } from './app.component';
import { FormsModule } from '@angular/forms';
**import { ProfileService } from './services/profile.service';
import { AuthInterceptor } from './interceptors/auth.interceptor';**
**import { ProfileComponent } from './components/profile/profile.component';**

@NgModule({
  declarations: [
    AppComponent,
    **ProfileComponent**
  ],
  imports: [
    BrowserModule,
    AppRoutingModule,
    HttpClientModule,
    FormsModule,
  ],
  providers: [**ProfileService, {
    provide: HTTP_INTERCEPTORS,
    useClass: AuthInterceptor,
    multi: true
  }**],
  bootstrap: [AppComponent]
})
export class AppModule { }
```

Buka file `app.component.html` dari folder `src\app` dan tambahkan:

```
<h1>New Product</h1>

<div class="container">
  <div>
    ...
  </div>
  **<div>
    <app-profile></app-profile>
  </div>**
  <div>
    ...
  </div>
</div>
```

Jalankan aplikasi dan hasilnya:

![Animation 6.gif](HTTP%20Interceptor%2083a688e122da4352b9b10b783adc8ca3/Animation_6.gif)