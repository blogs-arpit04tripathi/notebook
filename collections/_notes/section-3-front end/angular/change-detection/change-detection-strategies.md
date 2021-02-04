---
layout: post
title: Change Detection Strategies
permalink: /:collection/angular/change-detection-strategies
---

# Default Strategy
*	Every time you put or edit any data, Angular will run the change detector to update the DOM.
*	By default, Angular makes no assumptions about what the component depends on. Therefore, it must be prudent and will check every time something has changed, this is called dirty checking. 
*	In a more concrete way, it will perform checks for every browser event, timer, XHR and promises.
*	It is problematic when you start having a big application with many components, especially if you have focused on performance.

# onPush
*	Angular only performs the change detector when a new reference to the data of @Input () is passed.
*	Each component is provided its own change detector, which is responsible for tracking changes and updating the DOM.
*	Based only on the modification of the input references, some events activated by themselves (the component) or one of his children.
*	Developer, can explicitly ask Angular to do it with the componentRef.markForCheck () method.
*	With onPush, the component depends only on its inputs and covers immutability, the change detection strategy will be activated when:
  -	The input reference changes;
  -	An event originating from the member or one of his children;
  -	Execute change detection explicitly (componentRef.markForCheck ());
  -	Use the async pipe in the view.

# To be remember
*	If the Angular ChangeDetector is configured by default, for any change in any model properties, Angular will track changes through the component structure to update the DOM.
*	If the Angular ChangeDetetor is set to onPush, Angular only runs the change detector when a new reference to the component is passed.
*	If you pass observable to the onPush change detector's enabled component, Angular ChangeDetctor must be called manually to update the DOM.
