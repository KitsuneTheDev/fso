# NEW NOTE | 0.4

## What
* Diagram for adding new note feature on example app.
---

## Diagram
```mermaid
sequenceDiagram
    participant browser
    participant server

    browser->>server: POST https://studies.cs.helsinki.fi/exampleapp/notes body:{"content": "My New Note", "date": "2026-11-27"}
    activate server
    server-->>browser: Response 302
    deactivate server

    browser->>server: GET https://studies.cs.helsinki.fi/exampleapp/notes
    activate server
    server-->>browser: Return HTML
    deactivate server
    
    Note right of browser: Javascript refreshes the page. (Form action default behavior)

    browser->>server: GET https://studies.cs.helsinki.fi/exampleapp/main.css
    activate server
    server-->>browser: the css file
    deactivate server

    browser->>server: GET https://studies.cs.helsinki.fi/exampleapp/main.js
    activate server
    server-->>browser: the JavaScript file
    deactivate server

    browser->>server: GET https://studies.cs.helsinki.fi/exampleapp/ddata.json
    activate server
    server-->>browser: [..., { "content": "My New Note", "date": "2026-11-27" }]
    deactivate server
```
---

## Notes
* Notes page contains an HTML form with one input.
    - Input (content): Notes to be saved. Can be empty.
* When form submitted date created by using Date class.
* Page reloads and render notes with new note.