# Getting access to template and DOM with @ViewChild:
# @ViewChild

Some times we want the access before we call the method.

eg.
```
 cockpit.component.ts

 serverCreated = new EventEmitter < { serverName : string, serverContent: string }>();
 blueprintCreated = new EventEmitter < { serverName : string, serverContent: string }>();
 //newServerName = ' ';
 //newServerContent = ' ';
 @ViewChild('serverContentInput', {static: true}) serverContentInput: ElementRef;
 
 onAddServer(){
 this.serverCreated.emit(
 {
 serverName : this.newServerName,
 serverContent : this.serverContentInput.nativeElement.value;
    });
 }
 onAddBlueprint(){
 this.blueprintCreated.emit(
{
 serverName : this.newServerName,
 serverContent : this.serverContentInput.nativeElement.value;
   })
  } 
 }  



```

Create a local reference here and use this in the @ViewChild in ts file
```
cockpit.component.html
<input type = "text" class = "form-control" 
 #serverContentInput>
```

In **Angular 8+**, the `@ViewChild()` syntax which you'll see in the next lecture needs to be changed slightly:

Instead of:

`  @ViewChild('serverContentInput') serverContentInput: ElementRef;
`
use
 ` @ViewChild('serverContentInput', {static: true}) serverContentInput: ElementRef;
 `
The same change (add `{ static: true }` as a second argument) needs to be applied to ALL usages of `@ViewChild()` (and also `@ContentChild()` which you'll learn about later) IF you plan on accessing the selected element inside of `ngOnInit()`.

If you DON'T access the selected element in `ngOnInit` (but anywhere else in your component), set `static: false` instead!

If you're using Angular 9+, you only need to add `{ static: true }` (if needed) but not `{ static: false }`.