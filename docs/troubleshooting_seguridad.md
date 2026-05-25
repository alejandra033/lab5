# Laboratorio 5 — Self-hosted runners y troubleshooting

## 🔍 Parte 3 y 4: Registro de Troubleshooting y Logs
Aquí documentaré los errores forzados y cómo se identificaron usando los logs detallados.

### 1. Error de Label Incorrecto
* **Síntoma:** El job se queda colgado en estado "Queued".
* **Solución:** Corregir las etiquetas en el archivo YAML para que coincidan con las del runner activo.

### 2. Error de Runner Offline
* **Síntoma:** GitHub indica que no hay runners disponibles para procesar la cola.
* **Solución:** Levantar el servicio en la terminal local con `./run.sh` o `./run.cmd`.

---

## 🔒 Parte 5: Análisis de Seguridad
* **Riesgos de runners persistentes:** A diferencia de las instancias efímeras de GitHub, un runner persistente almacena datos de ejecuciones anteriores, lo que puede causar contaminación de entornos o fugas de caché si no se limpia adecuadamente.
* **Riesgos de acceso a red:** Un runner dentro de la red corporativa puede ser un vector de ataque; si el repositorio se ve comprometido, un atacante podría ejecutar comandos para escanear y atacar la infraestructura interna.
* **Aislamiento insuficiente:** Si el proceso corre con altos privilegios (ej. Administrador o Root), cualquier script malicioso dentro del pipeline podría comprometer el sistema operativo completo de la máquina anfitriona.