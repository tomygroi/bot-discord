# 📜 Historial de Cambios (Changelog)

Todos los cambios notables, actualización de comandos y correcciones del bot se documentan en este archivo.

---

## [v0.70] - Sistema Avanzado de Tickets, Filtros & Sanciones por Categoría
### ➕ Añadido
* **Sistema de Reclamación y Gestión de Tickets:**
  * **Interacción mediante Botones:** Integración de botones interactivos (`Reclamar Ticket` y `👥 Gestionar Staff`) en los paneles de soporte por MD.
  * **Indicador en Tiempo Real (Escribiendo...):** Transmisión bidireccional del estado de escritura (`typing`) entre el usuario por mensaje privado y el canal de ticket correspondiente.
  * **Soporte Multimedia e Imágenes:** Reenvío nativo e instantáneo de imágenes, capturas de pantalla y archivos adjuntos en ambas direcciones (Usuario ↔ Staff).
  * **Control de Asignación Exclusiva:** Restricción de respuestas no autorizadas en tickets asignados para garantizar un trato ordenado y evitar solapamientos.

* **Filtros Automáticos & Moderación Activa:**
  * **Filtro Anti-Multimedia:** Restricción de fotos y videos en canales de texto generales con excepciones configurables (compatibilidad nativa con GIFs de Tenor, Giphy y Discord CDN).
  * **Filtro de Mayúsculas Sustanciales (Caps):** Detección y purga automática de mensajes que contengan más de 6 palabras consecutivas redactadas en mayúsculas sostenidas.
  * **Filtro de Extensión y Flood:** Eliminación de mensajes masivos superiores a 400 caracteres y aplicación de advertencias automáticas bajo la categoría `flood`.

* **Sistema Segmentado de Advertencias (Warns):**
  * **Sanciones por Categoría (Targets):** Clasificación del historial de advertencias en categorías explícitas (`general`, `staff`, `flood`, `links`, `spam` y `honeypot`).
  * **Aislamiento Automático por Umbral (Timeout):** Aplicación automatizada de aislamientos temporales al alcanzar el número máximo de advertencias en una categoría específica.
  * **Sanción con Evidencia Citada:** Captura automática del mensaje o archivo adjunto como prueba al aplicar sanciones mediante respuesta a mensajes.
  * **Limpieza Flexibilizada (`clearwarn`):** Posibilidad de purgar el historial por advertencia individual (`last`), por categoría o completo (`all`).

* **Convocatorias e Interacciones:**
  * **Reacciones Automatizadas:** Asignación de flujos de interacción al reaccionar a convocatorias e instructivos oficiales del servidor.
  * **Módulo Antispam por MD:** Sistema de registro temporal para evitar la duplicación de notificaciones al interactuar repetidamente con botones o reacciones.

### 🛠️ Cambios & Correcciones
* Optimización de rendimiento en la captura de eventos parciales (`Partials.Reaction` y `Partials.Message`) para respuestas en mensajes antiguos.
* Mejoras en el formateo de horarios dinámicos adaptados automáticamente a la zona horaria de cada usuario.
* Refuerzo en la jerarquía de moderación para evitar la alteración no autorizada de advertencias o estados protegidos.

---

## [v0.50] - Mejoras en Comandos & Módulos
### ➕ Añadido
* **Comando `clearwarn`:** Ahora requiere verificación de permisos antes de limpiar advertencias.
* **Módulo de Mantenimiento:** Persistencia del estado de mantenimiento en la base de datos SQLite (`guild_settings`) para mantener el estado entre reinicios del bot.
* **Notificaciones de Mantenimiento:** Mensajes claros al activar/desactivar el modo mantenimiento, indicando que solo el Staff autorizado puede usar comandos.
* **Registro de Honeypots:** Mensajes de advertencia en consola al cargar canales honeypot para mayor visibilidad.
* **Alias de Comandos:** Registro de alias directamente al objeto del comando para evitar problemas de referencia y mejorar la gestión de comandos.
* **Validación de Jerarquía:** Antes de cambiar apodos, se verifica si el bot tiene permisos de jerarquía (`manageable`) para evitar errores.
* **Migración de Esquemas:** Detección y adición automática de columnas faltantes en tablas SQLite sin pérdida de datos.
* **Módulo `maxLengthFilter`:** Control de mensajes extensos para prevenir spam y mantener la calidad del chat.
* **Fix en el Sistema Anti-Crash:** Mejor manejo de errores y validaciones para evitar que el bot se caiga por comandos mal formateados o permisos insuficientes.
* **Mejoras en la Persistencia de Datos:** Optimización de consultas y almacenamiento en SQLite para mejorar el rendimiento y la confiabilidad del bot.

---

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
