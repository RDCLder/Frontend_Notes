# Angular

## General

- Angular is a front-end JavaScript framework used to create single page applications (SPAs)
  - The single page is an index page in which DOM elements are changed based on user interaction
  - The DOM elements can be rendered without changing or reloading the page making for a more seamless UX
  - Unlike React, Angular is much more opinionated on how it should be used

- Angular versions
  - Angular 1 is the original version and has been renamed to AngularJS.
  - Angular 2+ is the modern version of Angular.  Angular 7 is the latest version with a new major update every 6 months.

- Benefits
  - Reduction of cost
    - Using a framework drastically reduces the setup and overhead developers have to deal with for building apps
  - Standards compliance
    - Runs in more browsers and reaches more users
    - Uses ES6 and TypeScript
    - Modules
    - Internalization and accessibility support
  - Performant
  - Open Source
  - Popular with wide community support
  - Good documentation

- Subjective/Situational Benefits
  - Framework has core functionality set up
    - Router, http, forms, rxjs, etc.
    - Less decisions required but also less customizability
  - Uses TypeScript
  
- Basic Features
  - Easily creates progressive web app
  - Lazy loading
    - Reduces size of data initally required in browser for app to work
  - Forms library that can support complex data transaction
  - RXJS supports async
  - Fully featured router
  - Animations library

- Advanced Features
  - Server-side rendering
  - Mobile-friendly
    - Frameworks such as ionic can be used to make mobile apps
  - Angular language service
    - Provides better intellisense, debugging, and templating
  - ngUpgrade
    - Updates angularJS to angular
    - Supports both angularJS and angular simultaneously

## New Project

- Create new project
  - Move to the directory of the new project and use the following terminal commands from the angular CLI
  ```ng new app-name```
  - This will create the app directory and install all dependencies
  - It also creates the following workspace and starter project files:
    - A new workspace, with a root folder named my-app
    - An initial skeleton app project, also called my-app (in the src subfolder)
    - An end-to-end test project (in the e2e subfolder)
    - Related configuration files

- Create new component
  - In the root directory launch the following command
  ```ng g c component-name```
  
- Launch project
  ```ng serve```
