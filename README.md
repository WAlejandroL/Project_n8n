# 🤖 Asistente Inteligente para Gestión de Eventos

## 📌 Descripción del Proyecto

Este proyecto consiste en el desarrollo de un asistente automatizado capaz de interpretar mensajes en lenguaje natural y convertirlos en eventos agendados de forma automática.

El sistema integra automatización de flujos mediante n8n, procesamiento con un modelo de lenguaje (LLM) y comunicación interactiva con el usuario a través de Telegram, permitiendo confirmar o cancelar la creación de eventos en Google Calendar.

---

## 🎯 Objetivo

Desarrollar un sistema funcional que combine:

- Automatización de procesos  
- Uso de inteligencia artificial  
- Integración con servicios externos  

para resolver el problema de **gestión automática de eventos a partir de lenguaje natural**.

---

## 🧩 Arquitectura del Sistema

El proyecto está dividido en dos flujos principales dentro de n8n:

---

### 🔵 Workflow A – Procesamiento de Entrada

1. Recepción de mensaje (Telegram / Email)  
2. Envío del texto a un modelo de lenguaje (LLM)  
3. Extracción de datos estructurados:
   - Fecha  
   - Hora  
   - Categoría  
   - Lugar  
   - Resumen  
4. Normalización de datos mediante JavaScript  
5. Generación de mensaje de confirmación  
6. Envío de botones interactivos (Confirmar / Cancelar)  

---

### 🟢 Workflow B – Confirmación del Usuario

1. Recepción del evento mediante Telegram Trigger (callback)  
2. Procesamiento del `callback_data`  
3. Evaluación de la acción:
   - Confirmar → Crear evento  
   - Cancelar → Terminar flujo  
4. Creación del evento en Google Calendar  

---

## 🛠️ Tecnologías Utilizadas

- n8n (automatización de workflows)  
- Telegram Bot API  
- Google Calendar API  
- Modelo de lenguaje (LLM)  
- JavaScript (Code Node)  

---

## 🧠 Uso de Inteligencia Artificial

El modelo de lenguaje se utiliza para:

- Interpretar mensajes en lenguaje natural  
- Convertir texto libre a formato estructurado (JSON)  
- Clasificar el tipo de evento  
- Generar descripciones claras

---

## ⚙️ Ejemplo de Funcionamiento

### Entrada del usuario:

```text
Reunión mañana a las 4 en la oficina

{
  "Categoria": "Junta / Reunión",
  "Fecha": "2026/04/18",
  "Hora": "16:00",
  "Lugar": "Oficina",
  "Resumen": "Reunión en la oficina a las 16:00"
}
```
---
## 💬 Interacción con el Usuario

El sistema envía un mensaje de confirmación:

```
📅 Junta / Reunión  
🕒 16:00  
📍 Oficina  

¿Deseas agendar este evento?
```

Opciones:
- ✅ Confirmar
- ❌ Cancelar

---

## ⚠️ Retos Técnicos Abordados

- Conversión de fechas en distintos formatos
- Interpretación de horas no estructuradas (ej: "antes de las 17:00")
- Manejo del límite de callback_data en Telegram
- Separación de workflows sin pérdida de información
- Validación de datos antes de crear eventos
- Parsing de respuestas generadas por la IA

---

## 📌 Limitaciones

- No se utiliza base de datos para persistencia de eventos
- Dependencia del formato generado por la IA
- Manejo básico de expresiones de tiempo complejas

---

## 🔮 Posibles Mejoras

- Implementar base de datos (SQLite, Google Sheets, etc.)
- Soporte multiusuario
- Interpretación avanzada de lenguaje natural
- Generación automática de títulos más precisos
- Historial de eventos creados

---

## 📷 Flujo General del Sistema

- Usuario envía mensaje
- IA interpreta el contenido
- Sistema propone evento
- Usuario confirma
- Evento se crea en Google Calendar

---

## 🧑‍💻 Autor

Proyecto desarrollado con fines académicos para explorar automatización, inteligencia artificial e integración de sistemas.

---
