# Creating Basic Attribute Directive

- First create a file with filename.directive.ts
- Then add `import {Directive} from '@angular/core';`

```
import {Directive} from '@angular/core';
@Directive({
selector:'[appBasicHighlight]'
})

export class BasicHighlightDirective implements OnInit{
constructor(private elementRef : ElementRef){}
ngOnInit(){
this.elementRef.nativeElement.style.backgroundColor = 'green';
}
}
```
here we are getting access to the exact element and adding style to that element.
- To use Directives first inform Angular,
   So in app.module.ts -> in Declarations -> add the Directive.
 ` declarations:[BasicHighlightDirective`
  also import the directive from the folder
  `import {BasicHighlightDirective} from ./`
  now in the html file we can add the content 
  `<p appBasicHighlight> Style Me </p>` without using any square brackets or anything.