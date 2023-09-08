The following diagram shows a sequence of events that are happening when the user creates a new note on the page
https://studies.cs.helsinki.fi/exampleapp/notes by writing something into the text field
and clicking the Save button.

```mermaid
sequenceDiagram
	participant browser
	participant server

	browser->>+server: POST https://studies.cs.helsinki.fi/exampleapp/new_note
	server-->>-browser: HTML document (notes.html)

	Note right of browser: The browser starts parsing notes.html

	browser->>+server: GET https://studies.cs.helsinki.fi/exampleapp/main.css
	server-->>-browser: CSS file (main.css)

	browser->>+server: GET https://studies.cs.helsinki.fi/exampleapp/main.js
	server-->>-browser: JS file (main.js)

	Note right of browser: The browser starts executing the JavaScript code that fetches the JSON from the server

	browser->>+server: GET https://studies.cs.helsinki.fi/exampleapp/data.json
	server-->>-browser: [{ "content": "", "date": "2023-09-08T08:31:11.287Z" }, ...]

	Note right of browser: The browser executes callback function that renders notes
```
