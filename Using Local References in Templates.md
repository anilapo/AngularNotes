# Template reference variables
When there is user interactions we want some data to flow from view to class to perform operation.
eg. If we require value in input field to perform some validation.

To easily access Dom elements and their property angular provides template reference variables.

eg.1:
```
<input #myInput type = "text" >
<button (click) = "logMessage(myInput.value)">Log</button>

export class TestComponent implements OnInit(){

logMessage(value){
console.log(value);}
}
```
output:
 console: welcome  Log      //if welcome is input inside button

eg.2:
```
cockpit.component.html

<input type = "text" class = "form-control" 
 #serverNameInput>
 <label>Server Content</label>
 
 <button 
  class="btn btn-primary"
  (click)= "onAddServer(serverNameInput)">AddServer
 </button>
  

 cockpit.component.ts
 
 
 onAddServer(nameInput : HTMLInputElement){
 this.serverCreated.emit({
 serverName : nameInput.value,
 serverContent : this.newServerContent
 });
 }