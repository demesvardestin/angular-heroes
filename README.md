## Summary

This is an implementation of the Angular [Tour of Heroes tutorial](https://angular.io/tutorial).
It was generated with the Angular CLI and demonstrates some fundamentals of Angular 7.

Demo - [AngularHeroes](https://angular-heroes-demo.herokuapp.com "AngularHeroes")
![angularheroes](https://github.com/demesvardestin/angular-heroes/raw/master/src/assets/images/angular_heroes.png "AngularHeroes")

## Features
- Dashboard
- Realtime Hero Search
- Heroes Index
- Hero Creation
- Hero Profile View
- Hero Removal

## Specs

#### Modularity
The app focuses on modularity and reusability. Which means that every major part
of it, such as the dashboard, the heroes' list, and individual hero details, are
broken down into components, generated individually with `ng g component <component-name>`.

#### Services
The app also implements the use of Angular's service modules, used to read/write
data from remote servers. Conventionally, components shouldn't have any part
in the retrieval/modification of data, so all CRUD functionalities are relayed to
custom services.

#### HTTP
Angular comes with its **httpClient** module, which was used to perform related CRUD
operations for fetching, updating and deleting heroes from a live server. The
latter was simulated by the Angular **InMemoryDataService** module, which intercepts
http requests and returns data in JSON format.

#### Observables
When retrieving data from a server, the browser typically will have to wait until
something is returned, before displaying it to the user (as opposed to simply terminating
the request). Observables are RxJs tools used to listen for and manipulate data
from remote servers.

#### CSS
The Angular CLI conveniently provides the option of choosing CSS preprocessors
during the initial app setup. I chose Less due to its more robust features, such
as variables and mixins. It also provided a good opportunity for me to learn its
key features, though I ended up writing only vanilla css due to not finding any
practical use for Less in this particular project.

## Runtime Issues
When pushing this app to Heroku, I encountered a couple of problems. The first
couple of production commits failed to properly load the app. Heroku loaded the
'Application Error' page, and upon viewing the logs, I came across the following:
```
ng: not found
```
After doing some research on StackOverflow, I realized that this was due to
a couple of missing packages in the dependencies: **@angular-cli** and **@angular-compiler-cli**.
These two scripts are present in devDependencies for use during development, but
for some reason not automatically added to runtime dependencies. One commit later,
and the app still failed to load on Heroku. But this time, the logs revealed the
following error:
```
Error R10 (Boot timeout) -> Web process failed to bind to $PORT within 60 seconds of launch
```
To fix this, I had to use Express and run the app with Node. I added a
couple of scripts and dependencies to `package.json` so that it now looks like
this:
```
"scripts": {
    "ng": "ng",
    "start": "node server.js",
    "build": "ng build",
    "heroku-postbuild": "ng build --prod",
    "test": "ng test",
    "lint": "ng lint",
    "e2e": "ng e2e"
},
"private": true,
"dependencies": {
    "@angular-devkit/build-angular": "~0.13.0",
    "@angular/animations": "~7.2.0",
    "@angular/cli": "~7.3.0",
    "@angular/common": "~7.2.0",
    "@angular/compiler": "~7.2.0",
    "@angular/compiler-cli": "^7.2.5",
    "@angular/core": "~7.2.0",
    "@angular/forms": "~7.2.0",
    "@angular/platform-browser": "~7.2.0",
    "@angular/platform-browser-dynamic": "~7.2.0",
    "@angular/router": "~7.2.0",
    "angular-in-memory-web-api": "^0.8.0",
    "core-js": "^2.5.4",
    "express": "^4.16.4",
    "path": "^0.12.7",
    "rxjs": "~6.3.3",
    "tslib": "^1.9.0",
    "typescript": "~3.2.2",
    "zone.js": "~0.8.26"
}
```
The **heroku-postbuild** script handles the runtime production configuration of
Angular, which essentially helped solve the problem.

## Helpful Links and Resources

- [Medium Blog Post](https://medium.com/@hellotunmbi/how-to-deploy-angular-application-to-heroku-1d56e09c5147)
- [Angular-CLI Issue](https://github.com/angular/angular-cli/issues/7550)