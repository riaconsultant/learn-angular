# Angular Component Communication

![Angular Component Communication](https://flexmanu.files.wordpress.com/2018/01/screen-shot-2018-02-17-at-11-26-22-pm.png)


`@Input `: based on the property of parent component to child component. Information will flow and can access the property from top to bottom.

selectedHero is the variable in the parent Component and hero is the child component variable. via this Parent to child variable value will pass or communicate.

`Component.html` :
```
<app-hero-detail [hero]="selectedHero"></app-hero-detail>
```
app-hero-detail Child Component.ts :
```
@Input() hero: Hero;
```
`@Output`: Using this Data Binding, Need to bind the EventEmitter of @angular/core.

_Please do not import EventEmitter from 'Events'_.
`Parent Component.html` :
```
<app-hero-detail (myClick)="selectedHero($event)"></app-hero-detail>
```

`Parent Component.ts`:
```
selectedHero(value:Model_Name){
   // Application logic
}
```
`Child Component.html` :
```
<button (click)="voteMe()">Agree</button>
```
`Component.ts` :
```
@Output() myClick= new EventEmitter<Model_Name>();
voteMe(){
    this.myClick.emit(<Model_Name>);
}
```
`Services` : Services are accessible in the modules of the application. This is Singleton Class so that it’s have only one instance in the application. But any of the property which is declared in the service class lost the store, when end-user refresh the browser. Hence Angular is based on the SPA (Single Page Application) concept. Still user have privileged to refresh the page any time.

So that we should have mechanism in place to store the data in the Session Storage or the Local Storage of Browser and should fetch from the local storage or Session Storage.
```
@Output() profileChange:EventEmitter = new EventEmitter();

updateProfile(){
    this.profileChange.emit(<Model_Name>);
}
```
`Component Code`: where you want to access the event, Just Subscribe the event and get the trigger whenever any component trigger from the user action. Subscribe will catch the changes. If you subscribe multiple place. That is accessible all the subscription place.

Add service in the constructor
```
Constructor(private service:UserService){}

ngOnInit(){

    this.service.profileChange.subscribe((result:Model_Name)=>{
            console.log(result);
},(error:any)=>{
    console.log(error.errorMessage);
})
```

:+1: