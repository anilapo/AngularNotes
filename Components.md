# COMPONENTS:
#component
Generating components using angular CLI:
terminal :
`ng g c component-name`


`
ng serve
`

`
ng g c comp-name
`


Basic block of angular apps.
Handles the view part of the app and has the core logic of the page.
Can render the view by itslef based on dependency injection.

1. Create a component
2. Register in a module
3. Add an element in HTML markup


A decorator called component is attached to a class to make the class a component.
Import decorator on the top.
eg:
```
import {component}  from '@angular/core'
@component({
selector:'app-root',  // custom html tag used to represent the component
`templateUrl: `  //represents the view part
styles:        // gives the styles 
```

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

# Bootstrap:
install bootstrap
npm install --save bootstrap@3
then in angular.json file > in styles=[] add bootstrap folder path ie, node_modules/bootstrap/dist/css/bootstrap.min.css

Sourcemaps for debugging:
It is an addition ,the CLI adds to our bundles which allow the browser to translate our js code ts, or simply map the js code to our ts files.
We can place break points in the ts code and if clicked somewhere it indeed pauses.
