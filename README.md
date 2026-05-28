# js-clicker-moodle
Un clicker básico que hace clic en la página de Moodle cada un minuto.

Uso:
- F12 para abrir las herramientas de desarrollo, click en "consola"
- Copiar y pegar.

```javascript

const SELECTOR = '#page';
const INTERVAL_MS = 60 * 1000;

setInterval(() => {
  document.querySelector(SELECTOR)?.click();
  console.log('✓ Click realizado');
}, INTERVAL_MS);

```
