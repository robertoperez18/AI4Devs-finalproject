> Detalla en esta sección los prompts principales utilizados durante la creación del proyecto, que justifiquen el uso de asistentes de código en todas las fases del ciclo de vida del desarrollo. Esperamos un máximo de 3 por sección, principalmente los de creación inicial o  los de corrección o adición de funcionalidades que consideres más relevantes.
Puedes añadir adicionalmente la conversación completa como link o archivo adjunto si así lo consideras


## Índice

1. [Descripción general del producto](#1-descripción-general-del-producto)
2. [Arquitectura del sistema](#2-arquitectura-del-sistema)
3. [Modelo de datos](#3-modelo-de-datos)
4. [Especificación de la API](#4-especificación-de-la-api)
5. [Historias de usuario](#5-historias-de-usuario)
6. [Tickets de trabajo](#6-tickets-de-trabajo)
7. [Pull requests](#7-pull-requests)

---

## 1. Descripción general del producto

Eres un experto desarrollador IA en creación de agentes usando la herramienta Flowise (https://docs.flowiseai.com/). También tienes amplios conocimientos en documentación de proyectos y especificaciones técnicas.

Hemos desplegado una instancia de Flowise en AWS y la hemos bautizado como Orkestify, ya que nuestra intención es utilizar esta herramienta de cara a automatizar procesos dentro de nuestra empresa GooApps, especializada en el desarrollo de aplicaciones móviles.

Resumen de tu contexto Orkestify-Flowise
Versión: Flowise 3.0.4 (soporte para nodos modernos y buen ecosistema de integraciones).
Modelos: Usaréis LLMs de terceros (OpenAI, Gemini, Deepseek, Groq, etc.), lo que facilita modularidad y potencia.
Multimodalidad: Podéis incorporar imágenes y audio (no prioritario, pero posible).
Integraciones clave: Confluence, Jira, Slack, Figma, Github, Google Workspace (ideal para automatizar y extraer info de proyectos de desarrollo, comunicación interna y documentación).
Privacidad: Esencial; nada de información confidencial debe ser pública.
Automatización: No usáis herramientas tipo Zapier/Make por ahora.

---

## 2. Arquitectura del Sistema

### **2.1. Diagrama de arquitectura:**

Realizado a mano

### **2.2. Descripción de componentes principales:**

A partir del diagrama de arquitectura, me podrías describir cada una de las partes o de componente de AWS

### **2.3. Descripción de alto nivel del proyecto y estructura de ficheros**

N/A

### **2.4. Infraestructura y despliegue**

N/A

### **2.5. Seguridad**

N/A

### **2.6. Tests**

para el punto 2.6 de tests, puedes generarme un test plan general de la herramienta para su validacion?

---

### 3. Modelo de Datos

Para el punto de modelo de datos 3.2 descripcion de entidades, genera una breve explicación de cada tabla de este modelo DBML:
[orkestify.dbml](orkestify.dbml)
---

### 4. Especificación de la API

N/A

---

### 5. Historias de Usuario

La estructura de caso de uso es la siguiente:
Resumen ejecutivo del flujo
Objetivos del flujo
KPIs recomendados
Actores implicados
Desencadenante (trigger)
Pasos detallados (con decisiones y alternativos)
Ejemplo práctico
Notas/tips técnicos para implementación futura

Te dejo un ejemplo de flujo que ya has generado para que lo utilices de guía para los siguientes:
Automatización del flujo comercial con Orkestify
1. Resumen ejecutivo
   Automatizar el proceso comercial en GooApps desde la captación de leads hasta la generación de un borrador de contrato, integrando chatbot, reserva de cita, creación de deals en Productive, toma de requisitos, generación de propuestas (incluyendo estimación de esfuerzo) y contratos, todo orquestado con agentes IA sobre Flowise y conectando vuestras herramientas clave.

2. Objetivos
   Reducir el tiempo de respuesta y gestión desde el primer contacto hasta la entrega de la propuesta.

Estandarizar la recogida y traspaso de información.

Enriquecer los deals con research automático y estimación de esfuerzo IA.

Centralizar documentación y disminuir tareas manuales.

Mejorar la trazabilidad y control sobre el pipeline comercial.

Facilitar la integración con Productive, Google Calendar, Proposify y Google Drive.

3. KPIs sugeridos
   % de leads que completan el flujo hasta propuesta enviada.

Tiempo medio desde contacto inicial hasta propuesta.

Tiempo medio desde la toma de requisitos hasta propuesta generada.

Número de deals creados automáticamente vs manualmente.

Desviación entre estimación de esfuerzo y esfuerzo real (para ajustar la IA y plantillas).

Tasa de error en transferencia de datos.

% de propuestas generadas a través del flujo automatizado.

4. Actores implicados
   Cliente potencial: Inicia el contacto y provee datos.

Comercial: Realiza la reunión y valida propuesta y contrato.

Orkestify (Agente IA Flowise): Orquesta, recopila datos, reserva citas, crea deals, enriquece y genera documentación.

Herramientas externas: Productive, Google Calendar, Proposify, Google Drive, Fireflies/Gemini.

5. Desencadenante
   El contacto de un potencial cliente a través del chatbot web.

6. Flujo detallado (pasos + decisiones)
1. Recogida de información y reserva de cita
   Chatbot web recoge:

Nombre

Empresa

Tipo de proyecto

Presupuesto aproximado

Descripción breve

Chatbot presenta link de agenda de Google Calendar con disponibilidad real.

Datos recopilados se almacenan para siguiente paso.

2. Creación de deal en Productive
   El agente IA crea automáticamente un deal en Productive (API).

Si falla, envía email con todos los datos a los responsables.

Añade un research automático sobre la empresa potencial (web scraping, búsqueda de info relevante vía IA).

3. Toma de requisitos
   El comercial realiza reunión online (Google Meet).

Notas generadas automáticamente con Fireflies o Gemini, guardadas en sus sistemas y/o Google Drive.

4. Generación de propuesta (incluyendo estimación de esfuerzo)
   El agente recopila requisitos y notas.

El agente genera una estimación de esfuerzo en base a prompts IA, reglas predefinidas, plantillas o, si tenéis, modelos históricos (ejemplo: número de pantallas, funcionalidades, nivel de complejidad).

Estimación de esfuerzo: Horas, roles, plazos.

Estimación económica: Si aplica.

El agente genera una propuesta en la plantilla de Proposify (o estructura los apartados para facilitar el copiado manual).

Comercial revisa y valida la propuesta y la estimación antes de enviarla al cliente.

5. Borrador de contrato
   El agente prepara un borrador de contrato con la plantilla de Google Drive, añadiendo fechas y condiciones.

Comercial revisa y valida antes de enviarlo.

El documento se almacena en la carpeta correspondiente en Google Drive.

7. Ejemplo práctico (actualizado)
   Laura, responsable de producto de una startup, entra en la web de GooApps y contacta por el chatbot. Rellena sus datos, reserva una cita en Google Calendar. Orkestify crea el deal en Productive y adjunta un análisis sobre la empresa. Tras la reunión online (Google Meet), Orkestify recopila las notas, genera automáticamente una estimación de esfuerzo (ej: 400 horas, 2 desarrolladores, 10 semanas), estructura la propuesta en Proposify y prepara un borrador de contrato en Google Drive. El comercial valida y remite ambos al cliente.

8. Recomendaciones y notas técnicas
   Integración Productive: Usar API REST, autenticar con OAuth2, mapear campos del deal.

Fallback email: Configurar un nodo de correo en Flowise para envío automático si hay fallo de API.

Calendario Google: Usar API de Google Calendar para disponibilidad y reservas; OAuth2 para autenticación segura.

Research IA: Modularizar prompts para scrapear info de la empresa (ej: LinkedIn, Google, webs públicas).

Notas reunión: Integrar Fireflies/Gemini (API o email parse) para guardar/transcribir notas en Drive.

Estimación esfuerzo IA: Usar prompt IA con contexto de requisitos, o integrar hoja de cálculo con fórmulas, o alimentar modelo propio con históricos.

Proposify: Usar API para rellenar plantilla si es posible; si no, generar el contenido estructurado listo para copiar.

Contrato en Google Drive: Crear con plantilla Docs, rellenar variables (nombre, fechas, condiciones), guardar en Drive y dar permisos.

Logs y trazabilidad: Nodo logger para registrar todas las acciones (por auditoría y mejora continua).

9. Diseño de flujo en Flowise – Nodos recomendados
   Estructura básica de nodos (por fases)
   Input/Chatbot: Nodo de recogida de datos web (Input, Form o API si el frontend es externo).

Google Calendar: Nodo Calendar API para slots y reservas.

Productive API: Nodo HTTP Request configurado con endpoint de creación de deals.

Web Research: Nodo de búsqueda IA (Web Search, Bing Search API, o Web Scraping + LLM).

Fallback Email: Nodo SMTP/Email para enviar resumen del deal si falla integración.

Meeting Notes: Nodo de integración con Fireflies/Gemini para recoger y guardar transcripción.

Estimación de Esfuerzo:

Prompt Template: Nodo LLM para estimar esfuerzo basado en requisitos y prompts (“Con base en estos requisitos, calcula un estimado de esfuerzo en horas, roles y plazos…”).

Opcional: Nodo Sheets/API para integrar cálculo en Google Sheets.

Proposify: Nodo HTTP Request o API para rellenar/crear propuesta; o bien, generación de documento estructurado.

Google Drive Docs: Nodo de creación de Docs para contrato a partir de plantilla y rellenado de variables.

Output/Notificación: Nodo de output (email, Slack, log) para informar al equipo comercial de cada fase completada.

Logger: Nodo log para trazabilidad.

10. Consideraciones de privacidad y escalabilidad
    Usar scopes mínimos en OAuth2.

No almacenar datos personales más allá de lo necesario para el proceso.

Logs accesibles solo por el equipo autorizado.

Posibilidad de escalado modular por fases del flujo.


---

### 6. Tickets de Trabajo

respecto al bloque 6, todos los flujos van a ser desarrollados usando Flowise y su interfaz gráfica, en principio no van a ser tareas que programemos utilizando código, será simplemente usando los nodos de los flujos de flowise. Podrías rehacer los tickets de trabajo teniendo esto en cuenta?

---

### 7. Pull Requests

N/A
