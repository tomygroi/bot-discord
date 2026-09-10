# 📜 Historial de Cambios (Changelog)

Todos los cambios notables, actualización de comandos y correcciones del bot se documentan en este archivo.

---
## [v0.50] - Mejoras en Comandos & Módulos
### ➕ Añadido
* **Comando `clearwarn`:** Ahora requiere verificación de permisos antes de limpiar advertencias.
* **Módulo de Mantenimiento:** Persistencia del estado de mantenimiento en la base de datos SQLite (`guild_settings`) para mantener el estado entre reinicios del bot.
* **Notificaciones de Mantenimiento:** Mensajes claros al activar/desactivar el modo mantenimiento, indicando que solo el Owner puede usar comandos.
* **Registro de Honeypots:** Mensajes de advertencia en consola al cargar canales honeypot para mayor visibilidad.
* **Alias de Comandos:** Registro de alias directamente al objeto del comando para evitar problemas de referencia y mejorar la gestión de comandos.
* **Validación de Jerarquía:** Antes de cambiar apodos, se verifica si el bot tiene permisos de jerarquía (`manageable`) para evitar errores.
* **Migración de Esquemas:** Detección y adición automática de columnas faltantes en tablas SQLite sin pérdida de datos.
* **Módulo `maxLengthFilter`:** Control de mensajes extensos para prevenir spam y mantener la calidad del chat.
* **Fix en el Sistema Anti-Crash:** Mejor manejo de errores y validaciones para evitar que el bot se caiga por comandos mal formateados o permisos insuficientes.
* **Mejoras en la Persistencia de Datos:** Optimización de consultas y almacenamiento en SQLite para mejorar el rendimiento y la confiabilidad del bot.

## [v0.25] - Módulo AFK & Migraciones SQLite
### ➕ Añadido
* **Comando AFK Persistente:** Guardado del estado ausente en la tabla `afk_users`.
* **Notificador de Menciones:** Registro dinámico de usuarios que mencionaron al miembro ausente con resumen al retornar.
* **Migración Automática de Esquemas:** Detección y adición automática de columnas faltantes (`evidence` en `warns` y `mentions` en `afk_users`) sin pérdida de datos.

### 🛠️ Cambios & Correcciones
* Fix en la restricción de clave primaria para `afk_users` (`guild_id`, `user_id`).
* Validación de permisos de jerarquía (`manageable`) antes de intentar cambiar apodos en el servidor.

---

## [v0.15] - Canales Honeypot & Filtros
### ➕ Añadido
* **Módulo Honeypot:** Detección de bots/spammers en canales trampa guardados en SQLite (`guild_settings`).
* Carga automatizada de mapas Honeypot al inicio del cliente (`client.once('ready')`).
* Módulo `maxLengthFilter` para control de mensajes extensos.

---

## [v0.1] - Lanzamiento Inicial
* Estructura base del bot con `discord.js`.
* Manejador de comandos con soporte para aliases y *cooldowns* por usuario.
* Manejador de colas asíncronas (`queueManager`) para procesamiento prioritario de tickets.
* Módulos base de `antiSpam`, `linkFilter`, `tickets` y `welcome`.