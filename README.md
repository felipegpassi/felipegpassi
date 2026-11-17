# Hola, soy Felipe

Estudio Ingeniería Civil Industrial con Diploma en Computación en la Pontificia Universidad Católica de Chile, en Santiago. Me interesa la inteligencia artificial aplicada a productos de uso diario.

Fundador y desarrollador de **Duplicia**, un estudio que construye apps con IA integrada. Hoy trabajo en la primera: **Momo**.

## Momo: tus gastos, sin anotarlos

App de finanzas personales para quien nunca llevó control de sus gastos. En vez de pedirte que anotes cada compra, lee los avisos que te manda el banco: los reenvías a tu dirección de Momo y cada compra aparece sola, con su comercio y su categoría.

![Pantallas de Momo: inicio, movimientos, agregar a mano, presupuesto y análisis del mes](img/momo-pantallas.png)

**Qué hace**

- Registra compras, transferencias y pagos desde los correos del banco, y lee cartolas en PDF.
- Aprende a categorizar: confirmas un comercio una vez y las compras siguientes ahí se resuelven solas, sin volver a llamar al modelo.
- Un asistente conversacional responde con tus datos reales ("¿cuánto gasté en comida este mes?"). Cuando hay que cambiar algo, lo propone y tú lo confirmas.
- Cuentas y tarjetas con saldo, compras en cuotas, presupuestos con avisos, resumen semanal y gastos compartidos con amigos.
- Inicio en bento editable: cada baldosa muestra una sola idea y las ordenas a tu gusto.

**Stack**

| | |
|---|---|
| App | React Native con Expo (Expo Router, Reanimated, Gesture Handler) y TypeScript |
| Backend | Supabase: Postgres con RLS, funciones en PL/pgSQL, Edge Functions (Deno) y pg_cron |
| Correo | Cloudflare Email Routing y Email Workers |
| IA | DeepSeek V4 Flash para extraer datos de los correos y para el asistente (tool calling) |
| Web | Cloudflare Pages y Turnstile |

**Algunas decisiones**

- **Reenvío de correo en vez de OAuth a Gmail.** Leer el correo con `gmail.readonly` es un permiso restringido que, pasado cierto número de usuarios, exige una auditoría de seguridad anual. Con un filtro de reenvío el usuario elige qué comparte, funciona con cualquier proveedor de correo y no hace falta esa auditoría.
- **Un modelo barato extrae y las reglas evitan repetir.** El LLM saca monto, comercio y fecha del correo. Cuando el usuario confirma un comercio queda una regla, y las compras siguientes ahí ya no pasan por el modelo.
- **El asistente no escribe en la base.** Consulta con funciones de Postgres limitadas a los datos del usuario, y para crear o cambiar algo devuelve una propuesta que la app muestra para confirmar. Un error del modelo nunca termina en datos inventados.
- **Expo para publicar sin Mac.** Desarrollo en Linux y pruebo en un iPhone: Expo compila iOS en la nube y deja actualizar la app sin pasar otra vez por la revisión de la tienda.
- **Un lenguaje de diseño propio.** Bento, grises neutros con pasteles planos y movimiento con resortes, a partir de componentes web de [000h](https://000h.cojeev.com/) (MIT) portados a nativo con Reanimated.

Momo está en desarrollo y ya registra gastos reales a diario. El código es privado: si quieres verlo para una entrevista, escríbeme por LinkedIn y lo revisamos juntos.

## Contacto

[LinkedIn](https://www.linkedin.com/in/felipe-alfonso-gonz%C3%A1lez-passi-922228388/)
