## Summary

This is an implementation of the Angular [Tour of Heroes tutorial](https://angular.io/tutorial).
It was generated with the Angular CLI and demonstrates some fundamentals of Angular 2.

Demo - [AngularHeroes](https://angular-heroes-demo.herokuapp.com "AngularHeroes")
![angularheroes](https://github.com/demesvardestin/angular-heroes/raw/master/src/assets/images/angular_heroes.png "AngularHeroes")


## Specs

#### Modularity
The app focuses on modularity and reusability. Which means that every major part
of it, such as the dashboard, the heroes' list, and individual hero details, are
broken down into components, generated individually with ```ng g component <component-name>```.

#### Services
The app also implements the use of Angular's service modules, used to read/write
data from remote servers. Conventionally, components shouldn't have any part
in the retrieval/modification of data, so all CRUD functionalities are relayed to
custom services.

#### HTTP
Angular comes with its httpClient module, which was used to perform related CRUD
operations for fetching, updating and deleting heroes from a live server. The
latter was simulated by the Angular InMemoryDataService module, which intercepts
http requests and returns data in JSON format.

#### Observables
When retrieving data from a server, the browser typically will have to wait until
something is returned, before displaying it to the user (as opposed to simply terminating
the request). Observables are RxJs tools used to listen for and manipulate data
from remote servers.

#### Less
The Angular CLI conveniently provides the option of choosing CSS preprocessors
during the initial app setup. I chose Less due to its more robust features, such
as variables and mixins. It also provided a good opportunity for me to practice
with it.