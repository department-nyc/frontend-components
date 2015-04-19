# frontend-components
Frontend web components

This is a library / repository of reusable JS components usable on any website with minimal dependencies.

The pattern used for  here is a simple function which accepts a jQuery DOM element.

	`plugin = function($element) {};`

We can invoke these plugins manually, or with minimal code, invoke them automatically upon detection in the DOM.

	function initializeComponents() {
		$("[js-component]").each(function() {
			var $element = $(this);
			if (!$element.data('js-component-loaded')) {
				var handler = $(this).attr('js-component');
				var handlerFunc = new components[handler]($element);
				$element.data('js-component-loaded', true);
				console.log("Loaded JS component: ", handler);
			} else {
				console.log("JS component already loaded.");
			}
		})
	}

	$(function() {
		initializeComponents();
		// safe to call multiple times, e.g. after DOM change
	})

