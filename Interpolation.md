# INTERPOLATION:
{{  }}

Property or expression in double curly braces is called interpolation.
Angular will evaluate the content in the curly braces and display the value when the component is rendered in the browser.
It is the simplest way to bind data from a class to a template.


eg :
```
@Component({
selector:'app-test',
template:`
<h2> Welcome {{name}} <h2>
`,
styles:[]
})
```

Limitation:
Interpolation works only with string values, but sometimes we need boolean values to bind.

