# Angular Router

Angular Router is useful concept for navigation screen from one page to another page.

![Angular Router](https://flexmanu.files.wordpress.com/2018/01/screen-shot-2018-01-27-at-1-19-55-pm.png?w=730)

In Angular, Router is basically divided into the 3 type
1. Primary Router
2. Secondary Router
3. Child or Children Router

Useful for navigation purpose from one screen to another screen and also added if user comes from direct link.

**Primary Route** should have once in the Application. It’s Should be define in the main module.
```
RouterModule.forRoot(Routes);
```
**Secondary Route** can be multiple

 ```
 RouterModule.forChild(Routes);
```
**Child Route** is used for the code of separation in the multiple featured modules. This is also called a lazyLoading of the modules. this login route path and associated children module will load on demand and should have chunk of the code in js.
```
{ path:"login",loadChildren:'./user/user.module#UserModule'},
```
`Import Code in the Module`

```
import { RouterModule,Routes } from '@angular/router';

const appRoute:Routes=[

{path:"login", component:user.LoginComponent},
{path:"register",component: user.RegistrationComponent},
{path:"resetpassword",component: ResetpasswordComponent},
{path:"pagenotfound",component:user.PagenotfoundComponent},
{path:'',redirectTo:'/login',pathMatch:'full'}
]

@NgModule({
imports: [
RouterModule.forRoot(appRoute)
],
exports:[
RouterModule
]
})
export class AppRoute { }
Import Code for the Component TypeScript file

import {Router} from '@angular/router'; Constructor(private _router:Router){}
```
`Code for content holder after routing in the app.component.html `
```
<router-outlet></router-outlet>
```
This is a default router-outlet and also can use multiple router-outlet in your app with the help of name property like:
```
<router-outlet name="popup"></router-outlet>
```
Code for the Component ts script for the different path:

```
 this._router.naviagte(['/register',<Add Additional Parameter>]);
```
or
```
this._router.navigateByUrl('/register');
```
Code for the Component HTML Template
```
<a routerLink="register" routerLinkActive="active">Register</a>
```
`routerLinkActive` is for the active CSS class to the selected routing path.

Suppose create product list and then detail screen on selection and then edit or delete functionality. Let’s how would be Routes
```
const route:Routes=[
    { path:"products", component:products.component},
    { path:"product/{id}", component:productDetail.component},
    { path:"product/{id}/edit", component:productEdit.component},
]
```
In case of productEdit component class

```
import { ActivatedRoute } form '@angular/router';
    constructor(private route:ActivatedRoute){
        this.route.params.subscribe(params=>{
            console.log(params['id']);
        });
    }
```

Alternative code of Param Subscribe

```
this.route.snapshot.params['id'];
```

or

```
this.route.snapshot.paramMap.get('id');
```
or

```
this.route.snapshot.paramMap.subscribe( params =>{
    params.get('id');
});
```

productEdit component template

```
<a [routeLink]="['/product', product.id,'edit']">Edit</a>
```

Hope you guys enjoy the angular routing concepts and practice.



