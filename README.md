# js-clicker-moodle
Un clicker básico que hace clic en la página de Moodle cada un minuto.

Uso:
- F12 para abrir las herramientas de desarrollo, click en "consola"
- Copiar y pegar.

Actualizaciones:
- Intervalo aleatorio entre 10 y 35 min
- Envía un GET en lugar de click.

```javascript

const minMinutes = 10;
const maxMinutes = 35;

// Función para calcular un milisegundo aleatorio entre los rangos
function getNextInterval() {
  const minutes = Math.floor(Math.random() * (maxMinutes - minMinutes + 1)) + minMinutes;
  return minutes * 60000;
}

async function runKeepAlive() {
  try {
    const res = await fetch(location.href, {
      method: 'GET',
      credentials: 'include' // importante: envía las cookies de sesión
    });
    console.log(`✓ Keep-alive enviado [${res.status}] - ${new Date().toLocaleTimeString()}`);
  } catch (err) {
    console.error('✗ Error en keep-alive:', err);
  } finally {
    // Programa la siguiente ejecución con un tiempo nuevo y aleatorio
    const nextInterval = getNextInterval();
    console.log(`Próximo envío en: ${nextInterval / 60000} minutos.`);
    setTimeout(runKeepAlive, nextInterval);
  }
}

// Iniciar el primer ciclo
setTimeout(runKeepAlive, getNextInterval());

```
