# 🤖 N8N — Entregable de Clase
### Hoja de Ruta: Niveles de Dominio en n8n y Automatización

> Proyecto de aprendizaje progresivo de automatización con **n8n**, desarrollado como entregable para Campus Lands.  
> Cubre desde la manipulación básica de datos hasta la integración avanzada de Inteligencia Artificial.

**Autor:** Juan Felix Ballesteros Díaz  
**Institución:** Campus Lands  

---

## 📋 Tabla de Contenidos

- [Descripción General](#-descripción-general)
- [Estructura del Repositorio](#-estructura-del-repositorio)
- [Nivel Fácil — Fundamentos y Consumo de Datos](#-nivel-fácil--fundamentos-y-consumo-de-datos)
- [Nivel Medio — Lógica y Procesos Dinámicos](#-nivel-medio--lógica-y-procesos-dinámicos)
- [Nivel Difícil — Inteligencia Artificial y Sistemas Completos](#-nivel-difícil--inteligencia-artificial-y-sistemas-completos)
- [Progreso General](#-progreso-general)
- [Tecnologías y Herramientas](#-tecnologías-y-herramientas)
- [Cómo Importar un Flujo en n8n](#-cómo-importar-un-flujo-en-n8n)

---

## 📌 Descripción General

Este repositorio contiene una colección de flujos de trabajo desarrollados en **n8n**, organizados en tres niveles de dificultad creciente. Cada flujo representa un ejercicio práctico que cubre un concepto específico de automatización, desde el uso de nodos básicos hasta la construcción de sistemas autónomos con IA.

La hoja de ruta contempla **15 proyectos en total**, distribuidos así:

| Nivel | Proyectos | Enfoque |
|-------|-----------|----------|
| 🟢 Fácil | 1 – 5 | Fundamentos, APIs públicas, transformación de datos |
| 🟡 Medio | 6 – 10 | Lógica condicional, múltiples APIs, manejo de errores |
| 🔴 Difícil | 11 – 15 | IA con Gemini, clasificación, salidas estructuradas, sistemas autónomos |

---

## 📁 Estructura del Repositorio

```
N8N-Entregable-Clase/
│
├── 📂 Nivel Facil/
│   ├── Flujo_con_datos_estáticos.json
│   ├── Consumo_de_API_pública.json
│   ├── Transformación_de_datos.json
│   ├── Ejecución_programada.json
│   └── Persistencia_de_datos.json
│
├── 📂 Nivel Medio/
│   ├── Parámetros_dinámicos.json
│   ├── Combinación_de_APIs.json
│   ├── Filtrado_de_datos.json
│   ├── Manejo_de_errores.json
│   └── Decisiones_automatizadas.json
│
├── 📂 Nivel Dificil/
│   ├── IA+API_Data.json
│   ├── Clasificación_por_IA.json
│   ├── Salida_estructurada.json
│   ├── Decisiones_basadas_en_IA.json
│   └── Sistema_Autónomo_Final.json
│
└── README.md
```

---

## 🟢 Nivel Fácil — Fundamentos y Consumo de Datos

> **Objetivo:** Comprender el manejo de datos, nodos básicos y las primeras interacciones con APIs externas.

---

### 1. Flujo con Datos Estáticos
**Archivo:** `Nivel Facil/Flujo_con_datos_estáticos.json`

Introduce el uso del nodo **Set** para definir variables estáticas dentro de un flujo. En este caso se definen el nombre del autor (`Juan Felix Ballesteros Diaz`) y su país (`Colombia`), visualizando el resultado al final del flujo.

**Nodos utilizados:** `Manual Trigger` → `Set (Edit Fields)` → `No Operation`  
**Resultado:** Visualización de datos estructurados al ejecutar el flujo manualmente.

---

### 2. Consumo de API Pública
**Archivo:** `Nivel Facil/Consumo_de_API_pública.json`

Realiza una petición HTTP a la API pública de **Chuck Norris Jokes** para obtener un chiste aleatorio en formato JSON. El campo `value` es extraído y mapeado con un nodo Set.

**API utilizada:** `https://api.chucknorris.io/jokes/random`  
**Nodos utilizados:** `Manual Trigger` → `HTTP Request` → `Set (Edit Fields)` → `No Operation`  
**Resultado:** Lectura y extracción de datos de una API REST externa.

---

### 3. Transformación de Datos
**Archivo:** `Nivel Facil/Transformación_de_datos.json`

Extiende el flujo anterior aplicando una **transformación al texto** obtenido de la API: el chiste se convierte a mayúsculas usando la expresión `$json.value.toUpperCase()` directamente en el nodo Set.

**API utilizada:** `https://api.chucknorris.io/jokes/random`  
**Nodos utilizados:** `Manual Trigger` → `HTTP Request` → `Set (Edit Fields)` → `No Operation`  
**Resultado:** Manipulación y transformación de datos con expresiones de n8n.

---

### 4. Ejecución Programada
**Archivo:** `Nivel Facil/Ejecución_programada.json`

Automatiza la consulta a la API de Chuck Norris mediante el nodo **Schedule Trigger**, configurado para ejecutarse cada minuto sin intervención humana.

**Nodos utilizados:** `Schedule Trigger` → `HTTP Request` → `Set (Edit Fields)` → `No Operation`  
**Resultado:** Automatización periódica y ejecución desatendida de un flujo.

---

### 5. Persistencia de Datos
**Archivo:** `Nivel Facil/Persistencia_de_datos.json`

Genera un ID aleatorio con JavaScript (entre 1 y 826), consulta la **Rick and Morty API** para obtener información de ese personaje, y guarda el nombre y estado del personaje en un **Google Sheets**.

**API utilizada:** `https://rickandmortyapi.com/api/character/{id}`  
**Destino de datos:** Google Sheets (`personajes`)  
**Nodos utilizados:** `Manual Trigger` → `Code (JS)` → `HTTP Request` → `Google Sheets (Append)` → `No Operation`  
**Resultado:** Registro exitoso de datos externos en una fuente de almacenamiento externo.

---

## 🟡 Nivel Medio — Lógica y Procesos Dinámicos

> **Objetivo:** Integrar múltiples fuentes de datos y aplicar lógica condicional compleja.

---

### 6. Parámetros Dinámicos
**Archivo:** `Nivel Medio/Parámetros_dinámicos.json`

Demuestra el uso de **Query Parameters verdaderamente dinámicos** en un HTTP Request. El flujo presenta un **formulario web** al usuario donde ingresa el nombre y la especie a buscar. Esos valores viajan como parámetros a la Rick and Morty API y el nodo Set final muestra cuántos personajes se encontraron y los parámetros utilizados.

**API utilizada:** `https://rickandmortyapi.com/api/character/`  
**Nodos utilizados:** `Form Trigger` → `HTTP Request` → `Set (Resumen de resultados)` → `No Operation`  
**Resultado:** Consultas personalizadas y parametrizadas por el usuario en tiempo real.

---

### 7. Combinación de APIs
**Archivo:** `Nivel Medio/Combinación_de_APIs.json`

Realiza **dos peticiones HTTP en paralelo**: un personaje aleatorio de Rick and Morty (ID generado en nodo Code separado) y un consejo de vida de **Advice Slip API**. Combina ambas respuestas con el nodo **Merge** y arma un objeto final limpio con nombre del personaje, estado y consejo del día.

**APIs utilizadas:** `rickandmortyapi.com` + `api.adviceslip.com/advice`  
**Nodos utilizados:** `Manual Trigger` → `Code (JS)` → `HTTP Request` + `HTTP Request` → `Merge` → `Set (Armar objeto combinado)` → `No Operation`  
**Resultado:** Dominio del nodo Merge con datos coherentes y objeto combinado estructurado.

---

### 8. Filtrado de Datos
**Archivo:** `Nivel Medio/Filtrado_de_datos.json`

Obtiene la primera página de personajes de Rick and Morty, los descompone con **Split Out**, aplica un **Filter** para quedarse solo con los de especie `Alien`, y finalmente agrega los nombres y orígenes con el nodo **Aggregate**.

**API utilizada:** `https://rickandmortyapi.com/api/character/`  
**Nodos utilizados:** `Manual Trigger` → `HTTP Request` → `Split Out` → `Filter` → `Aggregate` → `No Operation`  
**Resultado:** Uso efectivo de filtros y agregaciones sobre colecciones de datos.

---

### 9. Manejo de Errores
**Archivo:** `Nivel Medio/Manejo_de_errores.json`

Implementa un flujo **robusto y resiliente** que apunta intencionalmente a una **URL rota** para demostrar el manejo real de errores. Con `onError: continueRegularOutput` el flujo no se detiene, y un nodo **IF** evalúa si existe error. La rama de error registra el mensaje, timestamp y acción tomada con un nodo Set; la rama exitosa confirma el estado OK.

**URL de prueba:** `https://api-que-no-existe-para-prueba.xyz/data` (rota intencionalmente)  
**Nodos utilizados:** `Manual Trigger` → `HTTP Request` → `IF (¿Hubo error?)` → `Set (Registrar error)` / `Set (Confirmar éxito)`  
**Resultado:** Flujo resiliente con manejo explícito y visible de errores en ambas ramas.

---

### 10. Decisiones Automatizadas
**Archivo:** `Nivel Medio/Decisiones_automatizadas.json`

Flujo disparado por un **formulario web** que solicita la edad del usuario. Aplica validación (rechaza edades fuera del rango 0–150), y con nodos **IF encadenados** determina si el usuario es mayor o menor de edad, respondiendo con un mensaje personalizado en cada caso.

**Trigger:** Formulario n8n (`On form submission`)  
**Nodos utilizados:** `Form Trigger` → `IF` → `Set` (edad inválida) / `IF` → `Set` (mayor de edad) / `Set` (menor de edad)  
**Resultado:** Automatización con bifurcaciones lógicas basadas en datos reales del usuario.

---

## 🔴 Nivel Difícil — Inteligencia Artificial y Sistemas Completos

> **Objetivo:** Implementar agentes de IA y automatizaciones inteligentes que analicen y decidan.

---

### 11. IA + API Data
**Archivo:** `Nivel Dificil/IA+API_Data.json`

Lee el **feed RSS de TechCrunch**, filtra solo los artículos que contengan "AI" en el título, limita a los 3 más recientes y los envía a **Gemini 2.5 Flash** para generar un resumen en español con título, relevancia, categoría y link original. El resumen es enviado automáticamente por **Telegram**.

**Fuente de datos:** RSS de TechCrunch (`techcrunch.com/feed/`)  
**IA utilizada:** Google Gemini 2.5 Flash  
**Salida:** Bot de Telegram  
**Nodos utilizados:** `Manual Trigger` → `RSS Read` → `Filter` → `Limit` → `Gemini` → `Telegram` → `No Operation`  
**Resultado:** Integración completa de IA con flujos de contenido y notificaciones automáticas.

---

### 12. Clasificación por IA
**Archivo:** `Nivel Dificil/Clasificación_por_IA.json`

Obtiene una cita aleatoria de `dummyjson.com/quotes/random` y la envía a **Gemini 2.5 Flash** con un prompt especializado para clasificar el texto según: sentimiento (`positivo/negativo/neutral`), categoría (`motivacional/reflexivo/crítico/informativo/otro`), nivel de confianza y razón. La respuesta JSON es parseada con un nodo **Code** en JavaScript.

**API utilizada:** `https://dummyjson.com/quotes/random`  
**IA utilizada:** Google Gemini 2.5 Flash  
**Nodos utilizados:** `Manual Trigger` → `HTTP Request` → `Gemini` → `Code (JS)` → `No Operation`  
**Resultado:** Análisis de sentimiento y clasificación automatizada de textos mediante prompts de IA.

---

### 13. Salida Estructurada
**Archivo:** `Nivel Dificil/Salida_estructurada.json`

Obtiene una cita aleatoria, la envía a **Gemini 2.5 Flash Lite** forzando una respuesta exclusivamente en JSON (sin markdown). El nodo **Code** parsea y limpia la respuesta, y un nodo **IF** filtra por sentimiento: si es negativo, guarda el registro completo en **Google Sheets**; si no, lo descarta. El JSON estructurado alimenta un proceso posterior real.

**API utilizada:** `https://dummyjson.com/quotes/random`  
**IA utilizada:** Google Gemini 2.5 Flash Lite  
**Salida:** Google Sheets (solo sentimientos negativos)  
**Nodos utilizados:** `Manual Trigger` → `HTTP Request` → `Gemini` → `Code (JS)` → `IF (¿Es negativo?)` → `Google Sheets` / `No Operation`  
**Resultado:** Parsing estructurado de respuestas de IA con proceso posterior real basado en los datos.

---

### 14. Decisiones Basadas en IA
**Archivo:** `Nivel Dificil/Decisiones_basadas_en_IA.json`

Obtiene una cita aleatoria y la envía a **Gemini 2.5 Flash Lite** con un prompt que fuerza respuesta binaria (`NEGATIVO` o `NO_NEGATIVO`). Un nodo **IF** compara la respuesta exacta: si es negativa, envía un **correo Gmail** con el texto original; si no, pasa a un NoOp.

**API utilizada:** `https://dummyjson.com/quotes/random`  
**IA utilizada:** Google Gemini 2.5 Flash Lite  
**Salida:** Gmail  
**Nodos utilizados:** `Manual Trigger` → `HTTP Request` → `Gemini` → `IF` → `Gmail` / `No Operation`  
**Resultado:** Automatización inteligente real con acción concreta basada en análisis de IA.

---

### 15. Sistema Autónomo Final
**Archivo:** `Nivel Dificil/Sistema_Autónomo_Final.json`

Workflow end-to-end completamente autónomo: consume noticias reales de **NewsData.io** cada minuto, filtra por idioma español, envía cada noticia a **Gemini 2.5 Flash** para clasificar el sentimiento, y según el resultado guarda en dos hojas separadas de **Google Sheets**: `Negativas` y `No_Negativas`, usando `appendOrUpdate` para evitar duplicados.

**Fuente de datos:** NewsData.io API  
**IA utilizada:** Google Gemini 2.5 Flash  
**Salida:** Google Sheets (dos hojas: Negativas / No_Negativas)  
**Nodos utilizados:** `Schedule Trigger` → `HTTP Request` → `Split Out` → `Filter` → `Gemini` → `IF` → `Google Sheets (Negativas)` / `Google Sheets (No_Negativas)`  
**Resultado:** Sistema autónomo de nivel profesional con clasificación inteligente y almacenamiento diferenciado.

---

## 📊 Progreso General

| # | Proyecto | Nivel | Estado |
|---|----------|-------|--------|
| 1 | Flujo con datos estáticos | 🟢 Fácil | ✅ Completado |
| 2 | Consumo de API pública | 🟢 Fácil | ✅ Completado |
| 3 | Transformación de datos | 🟢 Fácil | ✅ Completado |
| 4 | Ejecución programada | 🟢 Fácil | ✅ Completado |
| 5 | Persistencia de datos | 🟢 Fácil | ✅ Completado |
| 6 | Parámetros dinámicos | 🟡 Medio | ✅ Completado |
| 7 | Combinación de APIs | 🟡 Medio | ✅ Completado |
| 8 | Filtrado de datos | 🟡 Medio | ✅ Completado |
| 9 | Manejo de errores | 🟡 Medio | ✅ Completado |
| 10 | Decisiones automatizadas | 🟡 Medio | ✅ Completado |
| 11 | IA + API Data | 🔴 Difícil | ✅ Completado |
| 12 | Clasificación por IA | 🔴 Difícil | ✅ Completado |
| 13 | Salida estructurada | 🔴 Difícil | ✅ Completado |
| 14 | Decisiones basadas en IA | 🔴 Difícil | ✅ Completado |
| 15 | Sistema Autónomo Final | 🔴 Difícil | ✅ Completado |

**Progreso: 15 / 15 flujos completados (100%) ✅**

---

## 🛠 Tecnologías y Herramientas

| Herramienta | Uso |
|-------------|-----|
| **n8n** | Plataforma principal de automatización |
| **Chuck Norris API** | API pública de prueba (chistes aleatorios) |
| **Rick and Morty API** | API pública para datos de personajes |
| **Advice Slip API** | API de consejos para combinación de fuentes |
| **DummyJSON** | API de citas aleatorias |
| **TechCrunch RSS** | Feed de noticias tecnológicas |
| **NewsData.io** | API de noticias reales en múltiples idiomas |
| **Google Gemini 2.5 Flash** | Modelo de IA para clasificación y resumen |
| **Google Sheets** | Persistencia y almacenamiento de datos |
| **Telegram Bot** | Canal de notificaciones automatizadas |
| **Gmail** | Notificaciones por correo ante sentimientos negativos |

---

## 📥 Cómo Importar un Flujo en n8n

1. Abre tu instancia de **n8n**.
2. En el panel principal, haz clic en **"New Workflow"** o abre uno existente.
3. Haz clic en el menú (**⋮**) en la esquina superior derecha.
4. Selecciona **"Import from File"**.
5. Elige el archivo `.json` correspondiente de este repositorio.
6. Configura las credenciales necesarias (Google Sheets, Telegram, Google Gemini, etc.).
7. ¡Ejecuta el flujo!

> **Nota:** Algunos flujos requieren credenciales de terceros (Google Sheets OAuth2, Telegram Bot Token, Google Gemini API Key, Gmail OAuth2). Deberás configurarlas en tu propia instancia de n8n antes de ejecutarlos.
