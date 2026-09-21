# britez.tobias.-progra-III
# Sistema de automóviles: cliente weB

Cliente web para administrar automóviles a través de una API REST externa: permite consultar, agregar, modificar y eliminar autos desde el navegador.

- **Autor/a:** _(completar nombre y legajo)_
- **API utilizada:** <https://api-autos-tgwd.onrender.com> (ruta base `/autos`)

## Tecnologías utilizadas

| Capa | Tecnología |
| --- | --- |
| Frontend | HTML5, CSS3, JavaScript (sin librerías ni frameworks) |
| Comunicación | `fetch` y JSON |
| Backend (externo) | Node.js, Express.js, MongoDB, Mongoose |
| Pruebas de la API | Postman |

No se utilizan jQuery, frameworks frontend ni Bootstrap.

## Estructura del proyecto

```
├── index.html          Página principal y menú
├── consulta.html       Listado general y búsqueda por ID
├── alta.html           Alta con ID manual o automático
├── modificar.html      Búsqueda y modificación
├── eliminar.html       Búsqueda y eliminación con confirmación
├── css/
│   └── estilos.css     Hoja de estilos única para todas las páginas
    ├── api.js          Comunicación con la API (único archivo que conoce las URLs)
    ├── ui.js           Validaciones, mensajes, tabla y diálogo de confirmación
    ├── inicio.js       Estado del servidor
    ├── consulta.js
    ├── alta.js
    ├── modificar.js
    └── eliminar.js
```

## Funcionalidades

| Página | Operación | Método y endpoint |
| --- | --- | --- |
| Consultar | Listado general | `GET /autos` |
| Consultar | Búsqueda por ID | `GET /autos/:id` |
| Agregar | Alta con ID manual o automático | `POST /autos` |
| Modificar | Cambio de marca, precio y color | `PUT /autos/:id` |
| Eliminar | Baja con confirmación | `DELETE /autos/:id` |

### Validaciones

Se aplican en dos niveles: atributos HTML5 (`required`, `min`, `pattern`) y JavaScript (`validarAuto` y `validarId` en `ui.js`).

- Marca obligatoria.
- Precio obligatorio y mayor que cero.
- Color obligatorio, en formato hexadecimal (`#RRGGBB`).
- ID opcional en el alta; si se informa, debe ser un entero mayor que cero.
- El ID no se puede modificar en la pantalla de edición.

### Manejo de respuestas

Cada operación informa el resultado con un mensaje: `✓ Automóvil agregado correctamente.`, `✗ Ya existe un automóvil con ese ID.`, `✗ No existe un automóvil con ese ID.`, entre otros. Los errores de conexión también se informan.

## Colección de Postman
