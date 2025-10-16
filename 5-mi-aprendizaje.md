# COMPLETAR  
Comparando sus conocimientos antes de hacer la práctica con sus conocimientos después de hacer la tarea, explicar los principales aprendizajes logrados para beneficio de su formación profesional.  
Si solucionó un problema presentado al realizar la práctica también se debe documentar.

Antes de realizar la práctica tenía conocimientos generales sobre Docker, pero no sabía cómo se manejaban los datos confidenciales dentro de los contenedores. Al desarrollarla, aprendí a usar Docker Secrets para proteger información sensible como contraseñas y claves, comprendiendo cómo se crean, almacenan y asignan de forma segura a los servicios. Además, solucioné un problema al intentar acceder a un secreto, descubriendo que se encuentra en la ruta /run/secrets/. Gracias a esta experiencia, reforcé mis conocimientos sobre seguridad en entornos Docker y comprendí la importancia de manejar correctamente los datos sensibles en proyectos profesionales.


Consultar: Cómo se gestionan datos confidenciales con los secretos de Docker (Docker Secrets).

Los Docker Secrets son una herramienta de seguridad que permite gestionar y proteger datos confidenciales dentro de los entornos Docker, especialmente en el modo Swarm. Estos datos pueden ser contraseñas, certificados, claves API, tokens de autenticación o cualquier información sensible que las aplicaciones necesiten para funcionar. Su principal finalidad es evitar incluir esta información en las imágenes Docker o en variables de entorno, donde podría ser fácilmente expuesta o leída por usuarios no autorizados.

Cuando se crea un secreto mediante el comando docker secret create, Docker lo almacena de forma cifrada en el nodo administrador (manager) del clúster Swarm. A diferencia de los archivos o variables comunes, los secretos son distribuidos únicamente a los contenedores o servicios que tienen permiso explícito para acceder a ellos. Esto garantiza que los datos confidenciales se mantengan protegidos y solo estén disponibles donde realmente se necesiten.

Al ejecutarse un servicio que utiliza secretos, Docker los monta dentro del contenedor en una ubicación temporal y segura, normalmente en la ruta /run/secrets/. Desde allí, las aplicaciones pueden leer su contenido sin necesidad de exponerlo públicamente. Además, los secretos nunca se incluyen en las imágenes, no aparecen en los registros de ejecución ni en los resultados de comandos como docker inspect.

Una vez que el contenedor o servicio deja de ejecutarse, Docker elimina automáticamente los secretos asociados, evitando que queden rastros en el sistema. Gracias a este enfoque, Docker Secrets proporciona un nivel avanzado de seguridad y control de acceso, asegurando la confidencialidad, integridad y disponibilidad de la información sensible que utilizan las aplicaciones dentro del entorno de contenedores.
