Visitar /proyectos/
→ Se hace una petición GET al servidor.
→ El servidor responde con el código 200 OK y entrega el listado de proyectos activos renderizado con lista.html.

Abrir el detalle de un proyecto
→ Se envía una petición GET a /proyectos/<id>/.
→ El servidor responde con 200 OK, mostrando la vista detallada del proyecto y sus tareas (detalle.html).

Enviar el formulario de nueva tarea
→ Se envía una petición POST a /proyectos/<id>/tareas/nueva/ con los datos del formulario.
→ El servidor crea la tarea asociada, responde con un 302 Found (redirect), y redirige automáticamente a la vista de detalle con una nueva petición GET 200 OK.

Recurso creado: una nueva instancia de Tarea relacionada al Proyecto correspondiente.
→ Se ve reflejado en la base de datos y aparece en la lista de tareas del proyecto (detalle.html).


Parte 6 — Hosting + dominios (plan breve)

Opción PaaS: Render.com
Se sube el proyecto a GitHub y se conecta a Render.
Se definen variables de entorno como SECRET_KEY, DEBUG=0, ALLOWED_HOSTS=['proyectos.ejemplo.cl'].
Render gestiona la base de datos PostgreSQL y HTTPS automático.
Se ejecutan los comandos: python manage.py migrate y python manage.py collectstatic en el dashboard de Render.

DNS personalizado: proyectos.ejemplo.cl
En el panel del dominio, se crea un registro CNAME que apunta a la URL pública de Render (por ejemplo: nombre-servicio.onrender.com).
Si Render lo solicita, se agrega un registro TXT para verificar propiedad del dominio antes de habilitar HTTPS.