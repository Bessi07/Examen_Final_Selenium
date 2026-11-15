# Evaluación Final QA Automation

Pruebas automatizadas de compra en la web https://teststore.automationtesting.co.uk/index.php.

| Script | Requerimiento | Escenarios |
|--------|---------------|------------|
| `EX001` | RF-001 Compra con usuario autenticado | Parametrizado: un producto / varios productos |
| `EX002` | RF-002 Compra como invitado (Guest Checkout) | Parametrizado: dos clientes ficticios |

Ambos escenarios validan que los productos estén en el carrito y finalizan verificando el mensaje
**"Your order is confirmed"**. EX001 además valida que el inicio de sesión fue exitoso.


## Incidencia observada en la aplicación

La tienda es pública y compartida. Durante las ejecuciones, el carrito llegó a mostrar productos que la prueba
no agregó, o a vaciarse entre pasos (estado compartido del lado del servidor por usuarios concurrentes).
Las aserciones del carrito detectan esta situación y la prueba falla con un mensaje descriptivo.
Para reducir el impacto, EX001 vacía el carrito del usuario registrado antes de agregar productos.
