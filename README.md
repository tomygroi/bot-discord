# 🤖 Bot de Soporte General & Moderación

Bot de Discord desarrollado de forma personalizada para la gestión integral de soporte, moderación automática, filtros de seguridad y sistemas de presencia (AFK).

---

## 🛠️ Información del Desarrollador & Proyecto
* **Creador / Desarrollador:** Tony / tonymonrrow
* **Entorno de Ejecución:** Node.js / Discord.js v14
* **Base de Datos:** SQLite3 (`sqlite3` nativo con migraciones automáticas)

---

## 🖥️ Arquitectura & Servidor de Alojamiento
El bot se encuentra alojado y desplegado sobre una infraestructura dedicada autogestionada:
* **Entorno Virtualizado:** Proxmox VE
* **Sistema Operativo:** Ubuntu Server
* **Contenerización:** Docker & Docker Compose
* **Red & Acceso Remoto:** Red privada segura mediante Tailscale

---

## 🚀 Funcionalidades Principales
* **Módulo AFK:** Registro de ausencia con cálculo de tiempo, gestión automática de nicknames (`[AFK]`) y resumen interactivo de menciones al regresar.
* **Sistema de Moderación & Warns:** Base de datos persistente con registro de evidencia, almacenamiento de límites y limpieza dinámica de advertencias.
* **Seguridad Avanzada:** Módulos de Anti-Spam, filtro de enlaces, filtro de longitud máxima de mensaje y canales *Honeypot*.
* **Soporte & Tickets:** Sistema de gestión de tickets prioritarios mediante colas de tareas asíncronas (`queueManager`).
