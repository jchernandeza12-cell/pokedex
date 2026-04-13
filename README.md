# 🐾 PokeDex - Aplicación Web Estática

**Proyecto:** Despliegue en la nube con seguridad HTTP
**Empresa cliente:** Pueblo Paleta Inc.
**Institución:** Fundación Universitaria Tecnológico Comfenalco
**Integrantes:** Fher Hernández · Cristian Fuentes · Jesús Vuelvas
**Profesor:** Ronald Cuello
**Fecha:** 12 de abril de 2026

---

## 📌 Descripción

PokeDex es una aplicación web estática desarrollada con HTML, CSS y JavaScript que permite explorar diferentes especies de Pokémon, visualizando información detallada sobre sus características y habilidades. Los datos son consumidos desde la [PokéAPI](https://pokeap

## 🔗 Enlaces del Proyecto

| Recurso | URL |
|--------|-----|
| 🌐 Aplicación desplegada | [pokedex-alpha-eight-50.vercel.app](https://pokedex-alpha-eight-50.vercel.app/) |
| 📁 Repositorio GitHub | [github.com/jchernandeza12-cell/pokedex](https://github.com/jchernandeza12-cell/pokedex/tree/main) |

---

## ☁️ Plataforma de Despliegue

La aplicación fue desplegada en **Vercel**, plataforma elegida por su integración nativa con GitHub, soporte automático de HTTPS y facilidad para configurar encabezados HTTP de seguridad mediante `vercel.json`.

**Pasos para crear la cuenta y desplegar:**

1. Ingresar a [vercel.com](https://vercel.com) → **Sign Up with GitHub**
2. Autorizar acceso al repositorio del proyecto
3. Desde el dashboard → **Add New Project** → importar repo `pokedex`
4. Configuración: Framework **Other**, directorio raíz `/`, sin build command
5. Clic en **Deploy** → Vercel genera la URL pública automáticamente

---

## 🛠️ Tecnologías Utilizadas

- HTML5 / CSS3 / JavaScript (ES6+)
- [PokéAPI](https://pokeapi.co/)
- [Vercel](https://vercel.com/) (hosting)

---

## 🔒 Seguridad HTTP

Se configuraron los siguientes encabezados HTTP mediante el archivo `vercel.json`:

| Encabezado | Propósito |
|-----------|-----------|
| `Strict-Transport-Security` | Obliga el uso de HTTPS en todas las conexiones |
| `Content-Security-Policy` | Controla qué recursos puede cargar la app (previene XSS) |
| `X-Content-Type-Options` | Evita la detección automática de tipos de archivo |
| `X-Frame-Options` | Impide que la app se muestre en iframes externos |
| `Referrer-Policy` | Minimiza la fuga de información en cabeceras HTTP |
| `Permissions-Policy` | Restringe acceso a APIs del navegador (cámara, micrófono, GPS) |

---

## 🧪 Reflexión Técnica

**¿Qué vulnerabilidades previenen los encabezados implementados?**

- `Content-Security-Policy` previene ataques XSS limitando las fuentes desde donde se cargan scripts, estilos e imágenes.
- `X-Frame-Options: DENY` evita ataques de Clickjacking impidiendo que la app sea embebida en iframes maliciosos.
- `Strict-Transport-Security` protege contra ataques de downgrade a HTTP y secuestro de conexión.
- `X-Content-Type-Options` previene MIME sniffing, donde el navegador podría interpretar archivos de forma incorrecta.
- `Referrer-Policy` reduce el riesgo de fuga de URLs internas o tokens en las cabeceras de solicitud.

**¿Qué aprendimos sobre la relación entre despliegue y seguridad web?**

El despliegue no termina cuando la aplicación está disponible públicamente. Un ingeniero responsable debe asegurarse de que la aplicación exponga el menor riesgo posible. Aprendimos que Vercel permite configurar encabezados HTTP a nivel de infraestructura sin modificar el código fuente, lo cual es una práctica eficiente y profesional.

**¿Qué desafíos encontramos en el proceso?**

El principal desafío fue configurar correctamente el `Content-Security-Policy`, ya que un valor demasiado restrictivo puede romper la funcionalidad de la aplicación (por ejemplo, bloquear llamadas a la PokéAPI o fuentes externas). Fue necesario identificar todos los dominios externos utilizados e incluirlos en la política sin comprometer la seguridad.
