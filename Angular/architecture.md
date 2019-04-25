# Angular Architecture

- One way data flow
  - Architectural construct in which data and data changes flow from parent to child components
  
- Dependency Injection
  - 
  
- Custom Components
  - 
  
- Directives
  - Add new capabilities to an element of display
  - e.g.
    - Draggable
    - Appear on hover
  - Implemented as HTML attribute
    ```html
    <div hover-trigger>
      Hover over me
    </div>
    <div appear-on-hover>
      Some content
    </div>
    ```
    
  - Templates
    - The visual display of the app rendered through HTML
    - Specified in the TS file with the template's path or with in-line HTML
    
  - Change Detection
    - User interaction
    - HTTP requests
    - Timer
    - Process
      - State change > cascading changes > re-render
      - Unlike other frameworks which re-render on any change, angular waits for cascading changes before re-rendering
    - Done through zone.js
    
  - Rendering Targets
    - Can be rendered to any number of devices by changing the rendering engine
    - Options
      - Browser-platform
      - Browser-platform-dynamic
    - Targets
      - Browser/DOM
      - Server-side
      - Native mobile apps
      - Native desktop apps
      - Other
