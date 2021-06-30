 # EVENT BINDING:  
 Event binding is of type one-way data binding i.e., the communication happens from the template to typescript class when event (user-initiated) occurs in the template.
 User events like Mouseclick,keyboard events etc.
 ```
 
 	          |-->Template---|
	    Data  | 		     |Event binding
      Binding |--- Class  <--|
 
 ```
 **server.component.html**
 ```
 <p>{{'Server'}} with ID {{serverId}} is {{getServerStatus()}}</p>
<p>{{ serverRefreshStatus }}</p>
<button class="btn btn-primary" (click)="onRefresh()">Refresh</button>
<!-- <button class="btn btn-primary" (click)="onRefresh($event)">Refresh</button> -->
<!-- <button class="btn btn-primary" on-click="onRefresh($event)">Refresh</button> -->
```
 
   
  **server.component.ts**
  ```
  import { Component } from '@angular/core';

@Component({
	
	selector:'app-server',
	templateUrl:'./server.component.html'
})

export class ServerComponent {

	serverRefreshStatus: string;
	serverId: number;
	serverStatus: string = 'online';

	constructor() {
		console.log('Inside ServerComponent class constructor');
		this.serverRefreshStatus = 'Server was not refreshed!';
		this.serverId = 10;
	} 

	getServerStatus(){
		return this.serverStatus;
	}

	onServerRefresh(){
		this.serverRefreshStatus = 'Server Refreshed!';
	}
}
```