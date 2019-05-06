# Angular Routing

- How Routing Works
  - Routing traditionally happened by loading different web pages from the server based on which URL was requested
  - Single page applicatiosn (SPAs) now load a single index.html which displays different content based on the route.
    - The page never gets reloaded when routing.  Instead, DOM elements are changed based on the route.
    - Frameworks like Angular abstract away the work that makes this happen allowing for routes to be easily implemented.

## Adding Multiple Pages

- Router components don't need selectors as they are encompassed by the ```routes.ts``` file

- Adding a Route
  - In the root app file, add a ```<route-outlet></route-outlet>``` element to the template
  - Create a ```routes.ts``` file.  This will hold all the routing information for the root app.
  - Inside the file, add the following
    ```ts
    import { Routes } from '@angular/router';
    
    export const appRoutes: Routes = [
      
    ];
    ```
  - For each route, add an object that includes a path and a component like the following
    ```ts
    import { Routes } from '@angular/router';
    import { EventsListComponent } from './events/events-list.component';
    import { EventDetailsComponent } from './events/event-details/event-details.component';

    export const appRoutes: Routes = [
      { path: 'events', component: EventsListComponent },
      { path: 'events/:id', component: EventDetailsComponent },
      { path: '', redirectTo: '/events', pathMatch: 'full' }
    ];
    ```
  - For every path that redirects, a ```redirectTo``` and a ```pathMatch``` property are required
    - ```redirectTo``` sets which route to to redirect to
    - ```pathMatch``` determines how the path must be matched for the redirect to happen
    - e.g. ```full``` requires the path to be identical

- Configure the root module file
  - In the imports property, add ```RouterModule.forRoot(<appRoutes>)``` to the array
    - ```<appRoutes>``` should be the variable exported by ```routes.ts``` file
    - In this example, it is ```appRoutes```

- Add the base URL
  - In the ```index.html``` file, go to the ```<head>``` tag
  - Add a ```<base href="/">``` tag as a child element
    - The route ```"/"``` is used if the app is hosted directly on the server

- Linking to Routes
  - Go to the element that you want to use as a link
  - Add the following property
    ```[routerLink]="['/path', addOn]"```
    - The addOn is added to the base path for the new route and usually corresponds to a parameter

- Programmatically Navigating to a Route
  - ```<a [routerLink]="['/path']">``` can be used for direct routing
  - If you need to perform some logic as a part of the routing, use ```this.router.navigate(['/path'])```
    - Template
      ```html
      <button (click)="cancel()"></button>
      ```
    - JavaScript
      ```ts
      cancel() {
        this.router.navigate(['/events']);
      }
      ```

## Miscellaneous

- Accessing Parameters
  - Import the following
    ```import { ActivatedRoute } from '@angular/router';```
  - Access params with the following
    ```ts
    this.route.snapshot.params['paramName']
    ```

- Guarding Against Route Activation
  - If a route doesn't exist or should only be accessible under certain conditions, a route guarder can be used
  - Create a route guarder service that checks for a certain condition
    - Create a component with the following imports and the path to the service
      ```ts
      import { ActivatedRouteSnapshot, CanActivate, Router } from '@angular/router';
      import { Injectable } from '@angular/core';
      ```
    - The component will implement the canActivate method which checks for the conditions to activate
      ```ts
      export class EventRouteActivator implements CanActivate {
        constructor(private: service: Service, private router: Router) {}
        
        canActivate(route: ActivatedRouteSnapshot) {
          // serviceLogic
        }
      }
      ```
