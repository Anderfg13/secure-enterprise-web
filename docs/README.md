# Guía de evidencias (capturas de pantalla)

Guarda cada captura en esta carpeta (`docs/`) con el nombre indicado. Antes de subirlas, **tapa o recorta** tokens, secretos y claves: en las capturas solo deben verse datos que no sean sensibles.

| # | Archivo | Qué demuestra |
|---|---------|---------------|
| 1 | `01-auth0-application.png` | SPA registrada en Auth0 |
| 2 | `02-auth0-api.png` | API registrada en Auth0 |
| 3 | `03-api-401.png` | El backend rechaza peticiones sin token |
| 4 | `04-login-auth0.png` | Login de Auth0 en el frontend |
| 5 | `05-api-call.png` | Llamada autenticada exitosa (200) |
| 6 | `06-certificate.png` | Certificado HTTPS válido |
| 7 | `07-deployed-app.png` | Aplicación funcionando en el dominio público |
| 8 | `08-server-services.png` | Servicios corriendo en el servidor |

Las capturas 5 y 6 son las que el README principal enlaza como evidencia obligatoria.

---

## Imagen 1 — `01-auth0-application.png`
**Auth0 Dashboard → Applications → tu aplicación → Settings.**
Debe verse:
- Nombre de la aplicación y tipo **Single Page Application**.
- *Allowed Callback URLs*, *Allowed Logout URLs* y *Allowed Web Origins* con `http://localhost:5173` y `https://TU-SUBDOMINIO.duckdns.org`.
- Tapa el *Client Secret* si aparece (una SPA no lo usa).

## Imagen 2 — `02-auth0-api.png`
**Auth0 Dashboard → Applications → APIs → tu API → Settings.**
Debe verse:
- *Identifier* (audience): `https://enterprise-risk-api`.
- Algoritmo de firma **RS256**.

## Imagen 3 — `03-api-401.png`
Petición **sin token** al backend (local o desplegado), por ejemplo:
```
curl -i https://TU-SUBDOMINIO.duckdns.org/api/risk-status
```
Debe verse:
- El comando completo y la respuesta `HTTP/1.1 401` (o `401 Unauthorized`).

## Imagen 4 — `04-login-auth0.png`
Navegador en tu app, al pulsar *Log in*.
Debe verse:
- La pantalla de login de Auth0 (*Universal Login*).
- La barra de direcciones con tu dominio de Auth0 (`*.auth0.com`) y el candado.

## Imagen 5 — `05-api-call.png`  (evidencia principal)
La app ya con sesión iniciada, mostrando la respuesta de `/api/risk-status`.
Debe verse:
- Tu usuario autenticado en la interfaz.
- El resultado de la API en pantalla.
- Opcional pero recomendable: DevTools → pestaña **Network** con la petición `risk-status` mostrando **Status 200** y el header `Authorization: Bearer …` (**recorta o tapa el token**).

## Imagen 6 — `06-certificate.png`  (evidencia principal)
Navegador en `https://TU-SUBDOMINIO.duckdns.org`: clic en el candado → *La conexión es segura* → *El certificado es válido*.
Debe verse:
- Dominio al que se emitió el certificado.
- Emisor (**Let's Encrypt**).
- Fechas de validez (emitido / vence).

## Imagen 7 — `07-deployed-app.png`
Página completa de la aplicación desplegada.
Debe verse:
- La URL completa con `https://` y tu dominio DuckDNS en la barra de direcciones.
- La interfaz cargada (estado con sesión iniciada, si es posible).

## Imagen 8 — `08-server-services.png`
Terminal conectada a tu servidor, con estos comandos y su salida:
```
sudo systemctl status enterprise-risk-api
sudo systemctl status apache2
```
Debe verse:
- Ambos servicios en **active (running)**.
- Tu usuario/host del servidor en el prompt, para demostrar que es el servidor real.
