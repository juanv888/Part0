# Nueva nota en diagrama de aplicación de una sola pagina

```mermaid
sequenceDiagram
    participant user as Usuario
    participant browser as Navegador
    participant server as Servidor

    user->>browser: Debes acceder a https://studies.cs.helsinki.fi/exampleapp/spa
    browser->>server: HTTP GET (200) /exampleapp/spa
    server-->>browser: HTML: Aplicacion de una sola pagina (SPA)

    Note over browser: El navegador carga el HTML y solicita todo recusrso adicional (CSS, JavaScript)

    Note over browser: CSS

    browser->>server: HTTP GET (200) /exampleapp/main.css
    server-->>browser: main.css

    Note over browser: JavaScript (JS)

    browser->>server: HTTP GET (200) /exampleapp/spa.js
    server-->>browser: spa.js

    browser->>server: Realiza solicitudes AJAX para cargar datos adicionales (JSON)
    server-->>browser: Respuesta JSON 
    server-->>browser: [{ "content": "Yikes, I did it again", "date": "2024-06-16T15:46:47.698Z" }]
    browser-->>server: Realiza las suficientes y necesarias solitudes AJAX (JSON)
    server-->>browser: Respuestas JSON adicionales
    browser-->>user: Renderiza la aplicación de una sola página (SPA) en el navegador

    Note over user, browser: El usuario crea la nueva nota
    
    user->>browser: El usuario hace click en "Save"
    browser->>server: HTTP POST (302) exampleapp/new_note con contenido de la nota
    server-->>browser: Respuesta HTTP (Exitosa)