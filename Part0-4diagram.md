# Diagrama de Secuencia para crear una nueva nota

```mermaid
sequenceDiagram
    participant user as Usuario
    participant browser as Navegador
    participant server as Servidor

    Note over user, browser: El usuario escribe cuaquier nota y hace click en "Save"

    user->>browser: Click en "Save"
    browser->>server: HTTP POST (302) exampleapp/new_note con contenido de la nota
    server-->>browser: Respuesta HTTP (Redirecciona la respuesta al navegador)

    Note over browser: El navegador carga el HTML y solicita todo recusrso adicional (CSS, JavaScript)

    Note over browser: CSS

    browser->>server: HTTP GET (200) /exampleapp/main.css
    server-->>browser: main.css

    Note over browser: JavaScript (JS)

    browser->>server: HTTP GET (200) /exampleapp/main.js
    server-->>browser: main.js

    Note over browser: El navegador ejecuta el JS (main.js)

    browser->>server: HTTP GET (200) /exampleapp/data.json
    server-->>browser: data.json
    server-->>browser: [{ "content": "Yikes, I did it again", "date": "2024-06-16T15:46:47.698Z" }]

    Note over browser: El navegador procesa el data.json 
    Note over browser: El data.json actualiza el DOM para que muestre las notas creadas hasta el momento
    Note over browser: El data.json tambien muestra la nueva nota realizada

    