# Angular Router Event

![Angular Router Event](https://flexmanu.files.wordpress.com/2018/01/angular2-routing-diagram.png?w=730)

**Use case when it requires most**

Navigation Menu and its router active states.
Router State based title and meta tag setup of each screen
Routing Guard condition to secure your pages for Authentication
lazy load configuration
Tracing from start navigation to end navigation via varsa.

`What are event, Which I can access Navigation have 4 Event and Router have 3 Events`

* Navigation Start
* Navigation End
* Navigation Cancel
* Navigation Error

Route Event

* RouteRecognized
* RouteConfigLoadStart
* RouteConfigLoadEnd

In the component Typescript file

```
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
        console.log("Error",error);
    });
}
```
or

```
ngOnInit(){
    this.router.events
        .filter(event =>{event instanceOf NavigationStart})
        .subscribe(event=>{
            // Router based logic
            ...
        },(error)=>{
            // Router error
            console.log("Error",error);
    })
}
```
filter is just do the filteration of the NavigationStart event, Remaining all the events will prevent and can not come under the subscribe function.





