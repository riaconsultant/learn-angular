# Angular Router Guard

![Angular Router Guard](https://flexmanu.files.wordpress.com/2018/01/screen-shot-2018-01-30-at-8-31-45-pm.png)

Guard is useful when you have some secure page or authentication based functionality need to display. Likewise, If you are is not authorized this guard will auto-redirect to the login page. To Achieve such functionality Guard is introduced by Angular.

Using Angular CLI create a guard

ng g guard service/auth
this will create auth.guard.ts and auth.guard.specs.ts. specs are unit testing jasmine coded generated file. Just need to add some unit case scenario and code.

In the Module add guard in the providers

```
import {AuthGuard} from './service/auth.guard'
....
provider:[AuthGuard]
```

Auth.guard.ts

```
import { Injectable } from '@angular/core';
import { 
    Router,CanActivateChild,
    CanActivate, ActivatedRouteSnapshot, 
    RouterStateSnapshot } from '@angular/router';

@Injectable()
export class AuthGuard implements CanActivate,CanActivateChild {

constructor(private router:Router){

}

canActivate(
next:ActivatedRouteSnapshot,
state:RouterStateSnapshot):Observable<boolean> |Promise<boolean> |boolean {

if(// Conditions){
    this.router.navigate(['/login']);
        return false;
    }
        returntrue;
}
canActivateChild(
next:ActivatedRouteSnapshot,
state:RouterStateSnapshot):Observable<boolean> |Promise<boolean> |boolean {

    if(// conditions ){
        this.router.navigate(['/login']);
        return false;
    }
    return true;
    }
}
```

Guard has some defined method, can be authorization logic code based on our requirement, can implement one method and multiple methods.

1. CanActivate
2. CanLoad
3. CanActivateChild
4. CanDeactivate
5. Resolve
This Guard always be used by the Router

<b>How to Apply on the router</b>

```{path:"home", component:HomeComponent,canActivate:[AuthGuard]}```

to access the home component user should pass the true condition of the guard. Then it will accessible otherwise it will auto-reject by the guard itself.