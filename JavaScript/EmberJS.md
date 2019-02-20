# EmberJS

`beforeModel` will execute before the page is rendered

`replaceWith` will replace the current URL in the browser history, such that it can redirect and replace the previous URL history

`transitionTo` will add tom the history

`{{outlet}}` in the **application.hbs** route is where the routes display their template. The **application.hbs** template displays content on each route, and the `{{outlet}}` is related only to the content of a specific route.

An Ember **hook** is a term for methods that are called *automatically* rather than on a certain action
* The `model()` function acts as a hook and is called automatically at different times of the applications

Data for a page is called a **model**

The handelbars files serve as a template, arranging the content similar to html 

An **Adapter** is used by *Ember Data* to communicate with the back end


### Components

consist of 2 files: the js file that determines the behavior and the handlebars template that determines the markup

A dash "-" is *required* for every **component** so it doesn't conflict with html elemnets. i.e. vegetable-garden, not vegetable

An **Actions Hash** is an object within a component that contains a function

### Handlebars Helpers

These helpers are contained in `{{helper}}`. Indicate an opening helper tag with "#" like so `{{#helper}}`. They also act similar to `div` and can take on `id` or `class`, and require a closing `{{/helper}}`

`{{each}}` loops through objects in a given model

