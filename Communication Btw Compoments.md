# Splitting apps into Components
Splitting the data from one component file to another.
Data should be passed btw the components.
 - If properties should be accessible to parent components or other components to be bind, then something should be added to that property called a decorator.
 - Decorators are not only available for classes.
    @Input()- adding this decorator makes properties bindable from outside.
	import{Input} from '@angular/core';
	now any parent component or other component hosting our component is now able to bind data.
	eg.
	`@Input() element:{type : string, name : string, content : string}
	`
	
	# Assigning Alias to custom properties
	
	- Sometimes you does not want to use the same property outside of the component as you use inside of it.
	- So you can add an alias here, ny passing any argument to @Input() decorator with property name as you want to have it outside of the component.
	  eg.
	  `@Input('srvElement') element:{type : string, name : string, content : string}
	  `
	  
	  # Binding to custom Event
	  - If we have a component and something changes in there, and we want to inform our parent component , so the component which implements the other component.
	    * Make the change or add the method/or any change in the app.component.ts
	    * Then create event in the root component html 
	      
		   app.component.html
		   
		   ```
		   <app-cockpit
		   (severCreated)="onServerAdded($event)"
		   (blueprintCreated)="onBlueprintAdded($event)"
		   ></app-cockpit>
		   ```
		   * Then add event in root component ts file
		   
		 app.component.ts
		   
		  ```
		  onServerAdded(serverData: {ServerName : string, ServerContent : string})
		   {
		   this.serverElements.push(
		   {
		   type:'server',
		   name: ServerData.serverName,
		   content: ServerData.servercontent
		   });
		   
		   onBlueprintAdded(blueprintData: {ServerName : string, ServerContent : string})
		   {
		   this.serverElements.push(
		   {
		   type:'blueprint',
		   name: blueprintData.serverName,
		   content:  blueprintData.servercontent
		   }
		   );
		  }
		  ```
		  
		  
		
* child component :
		    - Create new properties ie events.
		    - 
		        serverCreated;
				blueprintCreated;
				to make these properties/events we have to assign a new value , new eventEmitter and import eventEmitter.
				- EventEmitter is a generic type indicated by using this smaller than (<) and greater than(>) sign and in between, define the type of event data you are going to emit and add parenthesis at the end to call the constructor of eventEmitter and create a new Event emitter object which is now stored in server created.
eg.			
 ``` 
 cockpit.component.ts
 
  serverCreated = new EventEmitter < { serverName : string, serverContent: string }>();
  blueprintCreated = new EventEmitter < { serverName : string, serverContent: string }>();
  newServerName = ' ';
  newServerContent = ' ';
  
  onAddServer(){
  this.serverCreated.emit(
  {
  serverName : this.newServerName,
  severContent : this.newServerContent
     });
  }
  onAddBlueprint(){
  this.blueprintCreated.emit(
 {
  serverName : this.newServerName,
  severContent : this.newServerContent
    })
   } 
  }  
  ```
  
  
  To make property listenable from outside we need to add decorator called - @Output
  Also should import { Output } from '@angular/core';
  eg.
  ```
  cockpit.component.ts
  
  @Output( )serverCreated = new EventEmitter < { serverName : string, serverContent: string }>( );
  @Output( )blueprintCreated = new EventEmitter < { serverName : string, serverContent: string }>( );
  ```
  
  
 # Assigning an Alias to custom Events:
 First change in child component ts file 
 ```
  cockpit.component.ts
  
  @Output( )serverCreated = new EventEmitter < { serverName : string, serverContent: string }>( );
  @Output('bpCreated' )blueprintCreated = new EventEmitter < { serverName : string, serverContent: string }>( );
  ```
  
  Then change in app.component.ts 
  
  `
  (bpCreated) = 'onblueprintAdded($event)
  `
  
  