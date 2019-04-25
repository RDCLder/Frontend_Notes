# Angular Tooling

## Angular CLI

- Running a JS app requires many moving pieces
  - Examples
    - Module handling
    - Bundle/minifying
    - Transpile from TypeScript/ES6/other
    - Browser shims
    - Wrappers (e.g. zone.js)
  - Angular CLI handles the setup for you

- CLI capabilities
  - Create new application
  - Create new component/service/pipe/etc
  - Web server
  - Linter
  - Testing
  - Building production app
  
  ## Server-side Rendering
  
- Benefits
  - Increases performance
    - Reduces initial download size by only requiring functionality for a single page
    - Reduces render time
  - Search engine optimization

- Operation Modes
  - Full pre-render
    - Runs development time process and creates HTML for each view
    - Creates CDN for each and 
  - Dynamic pre-render
    - Page is built by angular universal
  - Client-side switch
    - Download app
    - Hidden div
    - Boots
    - Replay events
    - Swap display
      
## Native Mobile & Desktop Applications

- Mobile
  - Ionic
  - NativeScript
  
- Desktop
  - Electron

## Testing Tools

- Karma
  - Unit-testing tool
  
- Protractor
  - Web automation testing tool for end-to-end tests
  
- Alternatives
  - Jest
  - theIntern
  - Cypress.io
  
- Angular Testing Utilities
  - TestBed
  - Async & fakeAsync
  - MockBackend
  
## AOT Compiler

