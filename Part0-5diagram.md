# Diagrama para crear una nueva nota 

```mermaid
sequenceDiagram
    participant user as Usuario
    participant browser as Navegador
    participant server as Servidor

    Note over user, browser: El usuarios accede a la SPA de la aplicacion de notas

    user->>browser: Navega a https://studies.cs.helsinki.fi/exampleapp/spa
    browser->>server: HTTP GET (200) /exampleapp/spa
    activate server
    server-->>browser: Documento HTML
    deactivate server

    Note over browser: El navegador carga el HTML y solicita todo recusrso adicional (CSS, JavaScript)

    Note over browser: CSS

    browser->>server: HTTP GET (200) /exampleapp/main.css
    server-->>browser: main.css

    Note over browser: JavaScript (JS)

    browser->>server: HTTP GET (200) /exampleapp/spa.js
    server-->>browser: main.js

    Note over browser: 

    browser->>server: Realiza solicitudes AJAX para cargar datos adicionales (JSON)
    server-->>browser: Respuesta JSON 
    server-->>browser: [{ "content": "Yikes, I did it again", "date": "2024-06-16T15:46:47.698Z" }]
    browser-->>server: Realiza más solicitudes AJAX según sea necesario
    server-->>browser: Respuestas JSON adicionales
    browser-->>user: Renderiza la aplicación de una sola página (SPA) en el navegador