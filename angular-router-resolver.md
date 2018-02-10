# Angular Router Resolver

![Angular Router Resolver](https://flexmanu.files.wordpress.com/2018/01/screen-shot-2018-01-30-at-8-07-50-pm.png)
In Module Router

```
const appRoute:Routes=[
{path:"login", component:common.LoginComponent},
{path:"register", component:common.RegistrationComponent},
{path:"forgotpassword", component:common.ForgotpasswordComponent,data:{ preload:false}},
{path:"profile",component:profile.UserComponent,resolve:{users:UserResolverService}},
{path:'',redirectTo:'/login',pathMatch:'full'},
{ path:"**", component:common.PagenotfoundComponent}
]
```

<b>UserResolverService</b>

```
import { Injectable } from '@angular/core';
import { Resolve,ActivatedRouteSnapshot, RouterStateSnapshot } from '@angular/router';
import { Observable } from 'rxjs/Observable';
import { ProfileService } from './profile.service';
import 'rxjs/add/observable/of';

@Injectable()
export class UserResolverService implements Resolve{
constructor(privateprofile:ProfileService) { }
resolve(route:ActivatedRouteSnapshot,routeState:RouterStateSnapshot):Observable{
let userId=+route.params['id'];
    if(userId){
        return this.profile.getUsers(userId);
    }else{
         Observable.of(null);
    }
  }
}
```

<b>UserProfile Component ts </b>:

1. Using Snapshot

```
import {ActivatedRouter} from '@angular/router';
userList;
Constructor(private route:ActivatedRouter){
this.userList = this.route.snapshot.data['users'];
}
```

Using Observable:

```
import {ActivatedRouter} from '@angular/router';
userList;
Constructor(private route:ActivatedRouter){
    this.route.data.subscribe(result=>{
    this.userList = result['users];
 }
}
```

<b>Advantage</b>: 

This techniques help us to prefetch the data in the routing itself. means data is fetched first from the service and then navigate to the screen. that gives a better user experience.

I hope you enjoy the Resolver concept and implement an application and make application faster
