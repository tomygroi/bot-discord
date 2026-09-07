# 📜 Historial de Cambios (Changelog)

Todos los cambios notables, actualización de comandos y correcciones del bot se documentan en este archivo.

---

## [v1.2.0] - Modulo AFK & Migraciones SQLite
### ➕ Añadido
* **Comando AFK Persistente:** Guardado del estado ausente en la tabla `afk_users`.
* **Notificador de Menciones:** Registro dinámico de usuarios que mencionaron al miembro ausente con resumen al retornar.
* **Migración Automática de Esquemas:** Detección y adición automática de columnas faltantes (`evidence` en `warns` y `mentions` en `afk_users`) sin pérdida de datos.

### 🛠️ Cambios & Correcciones
* Fix en la restricción de clave primaria para `afk_users` (`guild_id`, `user_id`).
* Validación de permisos de jerarquía (`manageable`) antes de intentar cambiar apodos en el servidor.

---

## [v1.1.0] - Canales Honeypot & Filtros
### ➕ Añadido
* **Módulo Honeypot:** Detección de bots/spammers en canales trampa guardados en SQLite (`guild_settings`).
* Carga automatizada de mapas Honeypot al inicio del cliente (`client.once('ready')`).
* Módulo `maxLengthFilter` para control de mensajes extensos.

---

## [v1.0.0] - Lanzamiento Inicial
* Estructura base del bot con `discord.js`.
* Manejador de comandos con soporte para aliases y *cooldowns* por usuario.
* Manejador de colas asíncronas (`queueManager`) para procesamiento prioritario de tickets.
* Módulos base de `antiSpam`, `linkFilter`, `tickets` y `welcome`.