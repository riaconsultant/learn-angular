# Angular Router

Angular Router is useful concept for navigation screen from one page to another page.

![Angular Router](https://flexmanu.files.wordpress.com/2018/01/screen-shot-2018-01-27-at-1-19-55-pm.png?w=730)

Use case when it requires most

Navigation Menu and its router active states.
Router State based title and meta tag setup of each screen
Routing Guard condition to secure your pages for Authentication
lazy load configuration
Tracing from start navigation to end navigation via varsa.
What are event, Which I can access Navigation have 4 Event and Router have 3 Events

Navigation Start
Navigation End
Navigation Cancel
Navigation Error
Route Event

RouteRecognized
RouteConfigLoadStart
RouteConfigLoadEnd
Where and how to implement

In the component Typescript file

import { NavigationEnd,Router } from '@angular/router';
Constructor(private router:Router){}
ngOnInit(){
this.router.events.subscribe(events=>{
// In this events all the events will trigger. 
// Need to identify by using the InstanceOf
if(events instanceOf NavigationStart){
// access only NavigationStart

}
}.(error)=>{

});
or

ngOnInit(){
this.router.events
.filter(event =>{event instanceOf NavigationStart})
.subscribe(event=>{
// Router based logic
},(error)=>{
// Router error
})
}
I hope you enjoy the Router Event

Next Topic: Router Resolver and Configuration for the Prefetch Data

Thanks, Manoj

Rate this:
      Rate This
Share this:
PrintEmail
JANUARY 28, 2018
Angular Router
ANGULAR
LEAVE A COMMENT
EDIT
 
Screen Shot 2018-01-27 at 1.19.55 PMHi All,

Today I am going to cover the Angular Router and its Events.

Primary Route should have once in the Application. It’s Should be define in the main module.

RouterModule.forRoot(Routes);
Secondary Route can be multiple

 RouterModule.forChild(Routes);
Child Route is used for the code of separation in the multiple featured modules. This is also called a lazyLoading of the modules. this login route path and associated children module will load on demand and should have chunk of the code in js.

{ path:"login",loadChildren:'./user/user.module#UserModule'},
Import Code in the Module


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
Code for the Component ts script for the different path:

 this._router.naviagte(['/register',<Add Additional Parameter>]);
or

this._router.navigateByUrl('/register');
Code for the Component HTML Template

<a routerLink="register" routerLinkActive="active">Register</a>
routerLinkActive is for the active CSS class to the selected routing path.

Suppose create product list and then detail screen on selection and then edit or delete functionality. Let’s how would be Routes

const route:Routes=[
{ path:"products", component:products.component},
{ path:"product/{id}", component:productDetail.component},
{ path:"product/{id}/edit", component:productEdit.component},
]
In case of productEdit component class

import { ActivatedRoute } form '@angular/router';
constructor(private route:ActivatedRoute){
this.route.params.subscribe(params=>{
console.log(params['id']);
});
}
Alternative code of Param Subscribe

this.route.snapshot.params['id'];
or

this.route.snapshot.paramMap.get('id');
or

this.route.snapshot.paramMap.subscribe( params =>{
params.get('id');
});
productEdit component template

```
<a [routeLink]="['/product', product.id,'edit']">Edit</a>
```

Hope you guys enjoy the angular routing concepts and practice.



