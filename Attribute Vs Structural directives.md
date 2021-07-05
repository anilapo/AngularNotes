# Attribute Directives:
- Looks like normal HTML attribute( possibly with data binding or event binding).
- Only affect or change the element they are added to.

 eg. background color
  ngStyle, ngClass.

# Structural Directives:
- Looks like normal HTML attribute but have a leading * ( for desugaring)
- Affect a whole area in the DOM (elements get added or removed).
 eg. ngFor, ngIf 