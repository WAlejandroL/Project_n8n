# Email Classifier & Calendar Assistant (n8n Workflow)

Este workflow de **n8n** automatiza la gestión de correos electrónicos utilizando IA para clasificarlos, resumirlos y, si es necesario, sugerir eventos que pueden ser agendados en un calendario.

---

## Funcionalidades 1

- Monitoreo automático de correos con Gmail
- Clasificación inteligente usando IA (OpenAI)
- Extracción de:
  - Categoría
  - Prioridad (1–10)
  - Resumen
  - Lugar, fecha y hora (si aplica)
- Notificación por Telegram
- Validación de disponibilidad en Google Calendar
- Procesamiento automático de fechas y horas

---

## Flujo del Workflow

### 1. Gmail Trigger
- Revisa nuevos correos cada minuto.
- Extrae datos como:
  - Asunto
  - Remitente
  - Fragmento del mensaje

---

### 2. Clasificación con IA
- Se envía el contenido del correo a un modelo (`gpt-5-mini`).
- El modelo responde en formato JSON con:

```json
{
  "Categoria": "",
  "Prioridad": "",
  "Resumen": "",
  "Lugar": "",
  "Hora": "",
  "Fecha": ""
}
