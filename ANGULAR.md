Angular installation:
npm install -g @angular/cli
ng --version -> to check the version installed.

create new angular project:
ng new project-name --no -strict -> to create in not strict mode.

Updating CLI:
* sudo npm uninstall -g angular-cli @angular/cli
* npm cache verify
* sudo npm install -g @angular/cli


COMPONENTS:

Basic block of angular apps.
Handles the view part of the app and has the core logic of the page.
Can render the view by itslef based on dependency injection.

1. Create a component
2. Register in a module
3. Add an element in HTML markup


A decorator called component is attached to a class to make the class a component.
Import decorator on the top.
eg:
import {component}  from '@angular/core'
@component({
selector:'app-root',  // custom html tag used to represent the component
templateUrl:   //represents the view part
styles:        // gives the styles 
})


Generating components using angular CLI:
terminal : ng g c component-name
A directory with the component-name will be created with 4 files:
* .css - storing the stylesheet
*  .html - storing the template
*  .spec - writing unit testing for component
*  .component.ts - component file
 
Component can be created by omitting the spec file for testing by the command:
ng g c component-name --skipTests true

For navigating into a folder and creating component inside another component directory use / 
eg:
ng g c recipes/recipe-list --skipTests true

Bootstrap:
install bootstrap
npm install --save bootstrap@3
then in angular.json file > in styles=[] add bootstrap folder path ie, node_modules/bootstrap/dist/css/bootstrap.min.css

Sourcemaps for debugging:
It is an addition ,the CLI adds to our bundles which allow the browser to translate our js code ts, or simply map the js code to our ts files.
We can place break points in the ts code and if clicked somewhere it indeed pauses.


INTERPOLATION:
{{  }}

Property or expression in double curly braces is called interpolation.
Angular will evaluate the content in the curly braces and display the value when the component is rendered in the browser.
It is the simplest way to bind data from a class to a template.


eg :
@Component({
selector:'app-test',
template:`
<h2> Welcome {{name}} <h2>
`,
styles:[]
})

Limitation:
Interpolation works only with string values, but sometimes we need boolean values to bind.


PROPERTY BINIDNG:

Attribute Binding                        											Property Binding

* HTML defined.																	* DOM  defined.

* Initialize DOM property and they 									  * Property values can be 
   are done.																			 changed.
   Attribute values cannot be changed 
   once they are initialized.
   
   
 EVENT BINDING:  
 Event binding is of type one-way data binding i.e., the communication happens from the template to typescript class when event (user-initiated) occurs in the template.
 User events like Mouseclick,keyboard events etc.
 
 
 	                |-->Template---|
	    Data  | 		     |Event binding
      Binding |--- Class <--|
 
 
 **server.component.html**
 
 <p>{{'Server'}} with ID {{serverId}} is {{getServerStatus()}}</p>
<p>{{ serverRefreshStatus }}</p>
<button class="btn btn-primary" (click)="onRefresh()">Refresh</button>
<!-- <button class="btn btn-primary" (click)="onRefresh($event)">Refresh</button> -->
<!-- <button class="btn btn-primary" on-click="onRefresh($event)">Refresh</button> -->
 
   
  **server.component.ts**
  
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


