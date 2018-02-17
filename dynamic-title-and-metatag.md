# Dynamic Title and MetaTag

Make a Application Dynamic Title and MetaTags for the SEO (Search Engine Optimization) pupose.

There three techniques to achieve this functionality in the angular 4 or 5 version.

![Angular SEO Dynamic Meta Tag and Title](https://flexmanu.files.wordpress.com/2018/01/screen-shot-2018-02-16-at-8-30-43-pm.png)

`Component-based`: Every Component have Separated functionality, Display of the Data and Search Engine Keywords and Meta Tags for the Social Media or Title of the screen.
Router-based: Every Router has a set of functionality to display or represent on the screen and should be direct access to the router navigation that may have multiple setups of the component on the one screen.

`Combination`: That is also possible where SEO strategy is the mixer of both solution.
Component based: Use the Title and Meta class of Platform
```
import { Title,Meta } from '@angular/platform-browser';
....
constructor(private _title:Title,private _meta:Meta){}
ngOnInit(){
 this._title.setTitle("Welcome To Angular Tutorial");
this._meta.addTag({name:"author",content:"Manoj Chaurasiya"});
    this._meta.addTags([
        {name:"description",content:"Society Management Solution"},
        {name:"keywords",content:"Angular4, Angular5, Society Management Solution"}
         ]);
}
```
will get the output in the below screen.


Angular SEO Dynamic Meta Tag and Title
Router Based: Using Router can set the data attribute and access in the component using router event. follow the below code.

Router Should have data property defined.

{path:"login", component:LoginComponent, data: { title: 'Login' }},
{path:"pagenotfound",component:PagenotfoundComponent, data: { title: 'Page Not Found'}}

Component.ts:
import{Router, ActivatedRoute, NavigationEnd} from '@angular/router';
import { Title } from '@angular/platform-browser';
constructor(private route:Router, private activateRoute:ActivatedRoute, private titleService: Title){}
ngOnInit : can be performed in any of the event in the component.
ngOnInit(){
this.route.events
.filter((event) => event instanceof NavigationEnd)
.map(() => this.activateRoute)
.mergeMap((route) => route.data)
.subscribe((event) => this.titleService.setTitle(event['title']));
}
Combination: combination of strategy is the real solution, which I believe because Solution 1. Can not write every SEO  purpose tag in the router data property and can not make this router dynamic.

Solution 2: Can not write title and meta tag code in the every component.

Solution 3: what we can do make a service which return us a meta tag and title values. and approach the solution 2 . Instead of taking data from router, use the service and make it dynamic. So any time we can change the SEO meta tag and title based our requirement. Just a service which have component name as input and return the title and meta tag.


