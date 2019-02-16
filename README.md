## AngularHeroes

This is an implementation of the Angular [Tour of Heroes tutorial](https://angular.io/tutorial).
It was generated with the Angular CLI and demonstrates the key basics of Angular 2.


### Specs

##### Modularity
This app focuses on modularity and reusability. Which means that every major part
of it, such as the dashboard, the heroes' list, and individual hero details, are
broken down into components, generated individually with ```ng g component <component-name>```.

##### Services
The app also implements the use of Angular's service modules, used to read/write
data from remote servers. This is done because components shouldn't have any part
in the retrieval/modification of data.

##### Less
When generating the app from the CLI, I chose Less over Sass or CSS.