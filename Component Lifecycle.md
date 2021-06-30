# Component Lifecycle
Angular supports a couple of lifecycle Hooks.
 
 # LifeCycle
 * ngOnChanges - called after a bound input property changes.
 * ngOnIni t- called once the component is initialized.
 * ngDoCheck - called during every change detection done.
 * ngAfterContentInit - called after content (ng - content) has been projected into view.
 * ngAfterContentChecked - called everytime the projected content has been checked.
 * ngAfterViewInit - called after the component's view ( and the child's view) has been initialized.
 * ngAfterViewChecked - called every time the view ( and the child's view) have been checked.
 * ngOnDestroy - called once the component is about to be destroyed.
 
 
 
 # Hooks in detail: 
 - ngOnChanges : executed multiple times, it's executed right at the start when a new component is created but thereafter, it's also always called whenever one of our bound input properties changes , means properties decorated with @input, so whenever these properties received new values.
 - ngOnInit : this method gets executed once the component has been initialized.This does not mean that we can see it, it has not been added to the DOM yet so to say, it has not been displayed yet but Angular finished the basic initialization, our properties can now be accessed and initialized for example,so the object was created you could say, and ngOnInit will run after the constructor.
 - ngDoCheck : executed multiple times,actually this method will be executed a lot because this will run whenever change detection runs.
   Change detection  is the system by which Angular determines whether something changed on the template of a component or inside of a component ,so whether it needs to change something in the template. So whether some property value changed from
   1 to 2  and that property is output in the template, Angular needs to re-render that part of the template.
   ngDoCheck is a hook executed on every check Angular makes. On every check, so not just if something changed, a lot of times ngDoCheck will run because you clicked some button which doesn't change anything but still it's an event and on events, Angular has to check if something changed because how else would it know?
   so it has to check on certain triggering events like you clicked somewhere or a timer fired or an observable was resolved
   and on these occasions, it will check your code and ngDoCheck will be executed.
  Angular does this in a very efficient way, so change detection on Angular works great and doesn't cost a lot of performance. ngDoCheck is a great method to use if you want to do something on every change detection cycle, like maybe manually inform Angular about some change it would not be able to detect otherwise, though that is a very advanced use case.

- ngAfterContentInit : this is called whenever the content which is projected via ng-content has been initialized.
  So not the view of the component itself but instead the view of the parent component, especially the part which will get added to our component through ng-content.

- ngAfterContentChecked : is executed whenever change detection checked this content we're projecting into our component.
-  ngAfterViewInit : once the view of our own component has been finished initializing, so once our view has been rendered.
-  ngAfterViewChecked : whenever our view has been checked,
  so once we are sure that either all changes which had to be done were displayed in the view or no changes were detected by Angular.
- ngOnDestroy : if you destroy a component, for example if you placed ngIf on it and this gets then set to false and therefore it removes it from the DOM, ngOnDestroy is called and here's a great place to do some clean up work because this is called right before the object itself will be destroyed by Angular.