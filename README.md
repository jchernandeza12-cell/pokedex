# pokedex
Proyecto PokeDex: aplicación web estática desplegada en la nube usando Azure, con implementación de encabezados de seguridad HTTP.
Actualización de seguridad


🐾 PokeDex - Aplicación Web Estática
Proyecto: Despliegue en la nube con seguridad HTTP
Empresa cliente: Pueblo Paleta Inc.
Desarrollado por: PumasLab
Institución: Fundación Universitaria Tecnológico Comfenalco
Integrantes: Fher Hernández · Cristian Fuentes · Jesús Vuelvas
Profesor: Ronald Cuello
Fecha: 12 de abril de 2026
📌 Descripción
PokeDex es una aplicación web estática desarrollada con HTML, CSS y JavaScript que permite a los usuarios explorar diferentes especies de Pokémon, visualizando información detallada sobre sus características y habilidades. Los datos son consumidos desde la PokéAPI.
🔗 Enlaces del Proyecto
Recurso
URL
Aplicación desplegada
https://pokedex-alpha-eight-50.vercel.app/
Repositorio GitHub
https://github.com/jchernandeza12-cell/pokedex/tree/main
☁️ Plataforma de Despliegue
La aplicación fue desplegada en Vercel, una plataforma de nube enfocada en sitios estáticos y aplicaciones frontend. Se eligió por su integración nativa con GitHub, soporte automático de HTTPS y facilidad para configurar encabezados HTTP de seguridad mediante el archivo vercel.json.
Pasos para crear la cuenta en Vercel
Ingresar a https://vercel.com y seleccionar Sign Up.
Autenticarse con la cuenta de GitHub.
Autorizar a Vercel el acceso al repositorio del proyecto.
Desde el dashboard, seleccionar Add New Project → importar el repositorio pokedex.
Dejar la configuración por defecto (sin framework, directorio raíz /).
Hacer clic en Deploy.
🛠️ Tecnologías Utilizadas
HTML5
CSS3
JavaScript (ES6+)
PokéAPI (https://pokeapi.co/)
Vercel (hosting)
🔒 Seguridad HTTP
Para cumplir con las buenas prácticas de seguridad web exigidas por Pueblo Paleta Inc., se configuraron los siguientes encabezados HTTP mediante el archivo vercel.json en la raíz del repositorio:
Encabezado
Propósito
Strict-Transport-Security
Obliga el uso de HTTPS en todas las conexiones
Content-Security-Policy
Controla qué recursos puede cargar la aplicación (previene XSS)
X-Content-Type-Options: nosniff
Evita la detección automática de tipos de archivo
X-Frame-Options: DENY
Impide que la app se muestre en iframes externos
Referrer-Policy
Minimiza la fuga de información en cabeceras HTTP
Permissions-Policy
Restringe el acceso a APIs del navegador (cámara, micrófono, geolocalización)
Resultado del escaneo en securityheaders.com
La aplicación fue evaluada en https://securityheaders.com obteniendo la siguiente calificación tras la implementación de los encabezados.
🧪 Reflexión Técnica
¿Qué vulnerabilidades previenen los encabezados implementados?
Content-Security-Policy previene ataques de tipo Cross-Site Scripting (XSS), limitando las fuentes desde las que se pueden cargar scripts, estilos e imágenes.
X-Frame-Options: DENY evita ataques de Clickjacking, impidiendo que la aplicación sea embebida en iframes maliciosos.
Strict-Transport-Security protege contra ataques de downgrade a HTTP y secuestro de conexión.
X-Content-Type-Options previene ataques basados en MIME sniffing, donde el navegador podría interpretar un archivo de forma incorrecta.
Referrer-Policy reduce el riesgo de fuga de URLs internas o tokens en las cabeceras de solicitud.
¿Qué aprendimos sobre la relación entre despliegue y seguridad web?
El despliegue no termina cuando la aplicación está disponible públicamente. Un ingeniero responsable debe asegurarse de que la aplicación exponga el menor riesgo posible. Aprendimos que plataformas como Vercel permiten configurar encabezados HTTP a nivel de infraestructura sin modificar el código fuente, lo cual es una práctica eficiente y profesional.
¿Qué desafíos encontramos en el proceso?
El principal desafío fue configurar correctamente el Content-Security-Policy, ya que un valor demasiado restrictivo puede romper la funcionalidad de la aplicación (por ejemplo, bloquear llamadas a la PokéAPI o fuentes externas). Fue necesario identificar todos los dominios externos utilizados por la app para incluirlos en la política sin comprometer la seguridad.
