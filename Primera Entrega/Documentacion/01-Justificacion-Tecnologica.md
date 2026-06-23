# Justificación Tecnológica

El sistema resuelve dos problemas bien distintos del Hospital de Clínicas: la entrega en papel de indicaciones y estudios a pacientes, y el seguimiento manual (básicamente por teléfono) de los traslados en ambulancia. Las tecnologías que elegimos van atadas a esos dos problemas, no a gusto personal del grupo.

## Frontend: HTML, CSS y JavaScript

Esta es la base que estamos viendo en la materia, así que fue la elección natural. JavaScript ya se dio en clase, pero todavía no lo metimos en este prototipo — el acordeón de preguntas frecuentes y documentos del portal, por ejemplo, se resuelve con `<details>`/`<summary>`, que es HTML5 puro y no necesita ni una línea de JS.

El portal del paciente tiene que andar bien en un celular, porque a ese módulo se entra escaneando un QR desde la sala. Para el responsive usamos CSS puro con `flex-wrap` y `grid` (`auto-fit`/`minmax`) más un par de `@media`, que son las herramientas que se dieron en la Unidad 1. No metimos Bootstrap ni nada parecido porque todavía no lo dimos en clase.

El CSS quedó dividido en `layout.css` y `components.css` para todas las pantallas del sistema (login, dashboard, admin, documentos, traslados), comentado por página/sección para que cualquiera del equipo encuentre rápido lo que busca. El portal del paciente tiene su propio `portal.css`, aparte de los otros dos: es una pantalla pública, sin login, con una identidad visual distinta, así que no tenía sentido mezclarla con el resto. Ahí sí usamos BEM (`.portal__header`, `.documento__acciones`, etc.) porque es un único archivo chico y queda prolijo; en el resto del sistema usamos nombres de clase más simples y planos (`.card`, `.btn-primary`) porque son muchas pantallas tocadas por las cuatro personas del equipo y BEM completo en todas hubiese sido más trabajo de mantener que beneficio real.

## Acceso por QR, sin login para el paciente

El relevamiento es claro en esto: el paciente no inicia sesión. Hay un QR único, sin datos personales, que lo lleva directo al portal. Así no le pedimos que instale nada ni que recuerde una contraseña, que para mucha gente (sobre todo gente mayor) sería una barrera más que una ayuda.

## Git, GitHub y VS Code

Somos cuatro personas tocando el mismo proyecto, así que necesitamos historial de cambios y la posibilidad de volver atrás si algo se rompe. Usamos GitHub porque además es donde está el repositorio oficial del equipo (`QuadNet-ISBO/SIGSM`). Cómo manejamos las ramas y los commits está detallado en [Control de Versiones y Repositorio](03-Control-Versiones-Repositorio.md).

Como editor usamos VS Code: es liviano, anda igual en Windows y Linux (el equipo usa los dos) y tiene extensiones para todo lo que necesitamos (HTML, CSS, Git). El detalle de qué extensiones usamos está en [Configuración del Entorno de Desarrollo](02-Configuracion-Entorno-Desarrollo.md).

## Lo que queda para más adelante

Para producción la idea es usar Docker sobre GNU/Linux, con acceso por SSH a los servidores del DTI (piso 6 del hospital). Esto ya lo estamos armando, pero como parte de otra materia, no de esta entrega: empaquetar el backend en un contenedor permite levantar exactamente el mismo entorno ahí que en la máquina de cada uno, evitando el clásico "en mi compu funciona".
