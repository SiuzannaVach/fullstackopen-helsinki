# Part 0 Exercises

## Exercise 0.4: New note diagram

```mermaid
sequenceDiagram
    participant browser
    participant server

    Note over browser: The user types a note into the text field and clicks "Save"

    browser->>server: POST https://helsinki.fi
    activate server
    Note over server: The server saves the new note to the database
    server-->>browser: HTTP 302 / Redirect to /exampleapp/notes
    deactivate server

    Note over browser: The browser receives the redirect and reloads the notes page

    browser->>server: GET https://helsinki.fi
    activate server
    server-->>browser: HTML document
    deactivate server

    browser->>server: GET https://helsinki.fi
    activate server
    server-->>browser: the CSS file
    deactivate server

    browser->>server: GET https://helsinki.fi
    activate server
    server-->>browser: the JavaScript file
    deactivate server

    Note right of browser: The browser starts executing the JavaScript code that fetches the updated JSON from the server

    browser->>server: GET https://helsinki.fi
    activate server
    server-->>browser: [{ "content": "Your new note", "date": "2026-9-29" }, ... ]
    deactivate server    

    Note right of browser: The browser executes the callback function that renders the full list of notes including the new one
```

## Exercise 0.5: Single page app diagram

```mermaid
sequenceDiagram
    participant browser
    participant server

    browser->>server: GET https://helsinki.fi
    activate server
    server-->>browser: HTML document
    deactivate server

    browser->>server: GET https://helsinki.fi.css
    activate server
    server-->>browser: the CSS file
    deactivate server

    browser->>server: GET https://helsinki.fi.js
    activate server
    server-->>browser: the JavaScript file
    deactivate server

    Note right of browser: The browser starts executing the JavaScript code that fetches the JSON from the server

    browser->>server: GET https://helsinki.fi
    activate server
    server-->>browser: [{ "content": "HTML is easy", "date": "2023-1-1" }, ... ]
    deactivate server

    Note right of browser: The browser executes the callback function that renders the notes using the DOM
```

## Exercise 0.6: New note in SPA diagram

```mermaid
sequenceDiagram
    participant browser
    participant server

    Note over browser: The user types a note into the text field and clicks "Save"
    Note over browser: The JavaScript code intercepts the form submission, adds the note to the local list, and updates the DOM

    browser->>server: POST https://helsinki.fi_spa
    activate server
    Note over server: The server saves the new note to the database
    server-->>browser: HTTP 201 Created (JSON confirmation)
    deactivate server

    Note over browser: The page does not reload, the new note is already visible on the screen
```
