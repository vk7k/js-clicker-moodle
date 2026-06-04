# js-clicker-moodle
Un clicker básico que hace clic en la página de Moodle cada un minuto.

Uso:
- F12 para abrir las herramientas de desarrollo, click en "consola"
- Copiar y pegar.

Nueva versión: genera un fetch, ya que Moodle cuenta desde el servidor el tiempo asi que da lo mismo usar un clicker en el navegador hoohho

```javascript

const INTERVAL_MS = 5 * 60 * 1000; // cada 5 min es más que suficiente

setInterval(async () => {
  try {
    const res = await fetch(location.href, {
      method: 'GET',
      credentials: 'include' // importante: envía las cookies de sesión
    });
    console.log(`✓ Keep-alive enviado [${res.status}] - ${new Date().toLocaleTimeString()}`);
  } catch (err) {
    console.error('✗ Error en keep-alive:', err);
  }
}, INTERVAL_MS);
```
