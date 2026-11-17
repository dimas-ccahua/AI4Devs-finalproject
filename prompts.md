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

**Prompt 1 — Borrador del README de Nivelia**

- **Herramienta:** Claude Code.
- **Modelo:** opus 5.5.
- **Contexto:** ejecuté Claude Code desde la raíz del proyecto base de   AI4Devs. La plantilla `readme.md` ya estaba en el repositorio y se usó como referencia para redactar el README de Nivelia.

```text
Actúa como analista de producto y arquitecto de software. Redacta el primer
borrador del readme.md de Nivelia para la Entrega 1 de AI4Devs.

Esta entrega es de documentación técnica. Usa la plantilla adjunta como
estructura obligatoria: conserva su índice, títulos, subtítulos, numeración
y orden. Sustituye los textos guía por contenido del proyecto. Si falta un
dato, usa [POR COMPLETAR]. Distingue las decisiones acordadas, las propuestas
y lo que queda pendiente. No inventes código, pruebas ejecutadas, despliegues
ni enlaces.

## Contexto del producto

Nivelia ayuda a quienes estudian en distintas plataformas o instituciones
a organizar sus formaciones, retomar el estudio desde donde lo dejaron
y encontrar proyectos con los que aplicar lo aprendido.

Usa «Formación» como concepto principal y «Mis formaciones» y «Añadir
formación» como nombres en la interfaz. Distingue estos campos:

- Tipo de formación: Curso, Programa especializado, Diplomado, Maestría,
  Doctorado, Ruta de autoestudio u Otro.
- Categoría temática: área de estudio, por ejemplo IA, desarrollo de
  software, finanzas o exportación.
- Institución o plataforma: quién ofrece la formación o dónde se sigue,
  por ejemplo LIDR, Udemy, Udacity o YouTube.

Ejemplos: AI4Devs se puede registrar como Programa especializado; un curso
de Udemy, como Curso; y un plan de tres niveles creado con IA fuera de
Nivelia, como Ruta de autoestudio.

## Alcance del MVP

1. Registrar y consultar formaciones. El nombre y el tipo son obligatorios.
   La categoría temática, la institución o plataforma y la URL son
   opcionales. El usuario puede guardar una formación sin temario y
   completarla después. Si hay URL, puede abrir la formación original.
2. Organizar el temario manualmente como Formación → Bloques → Lecciones.
   Un bloque puede llamarse «Módulo 1» o «Nivel 1 — Fundamentos».
   Los subtítulos internos van en la descripción de la lección.
   Una maestría o doctorado se puede registrar, pero el MVP no modela
   jerarquías académicas adicionales como semestre → asignatura → unidad.
3. Marcar lecciones como completadas y consultar el avance y la próxima
   lección pendiente. Calcula el avance a partir de las lecciones
   completadas y el total; si no hay temario, muestra «Sin temario».
4. Sugerir proyectos de práctica con IA y explicar qué lecciones que el
   usuario marcó como completadas respaldan cada sugerencia. Completar
   lecciones no demuestra dominio. Si no hay lecciones completadas,
   explica qué necesita registrar el usuario para pedir una sugerencia.

Como mejora opcional, plantea pegar un índice en texto, revisar cómo quedó
organizado y confirmar antes de guardar. La edición manual es suficiente
para el MVP.

## Evolución futura

Distingue autocompletar la ficha desde una URL de importar el temario
completo. Propón empezar con una plataforma y preferir su API oficial
cuando exista. Considera la extracción de datos públicos de la página
solo cuando la plataforma lo permita. Propón una vista previa editable
y conserva el alta manual cuando falten datos o la URL no sea compatible.

Deja fuera del MVP la importación automática desde URL, el acceso a
contenido tras iniciar sesión, la extensión de navegador, la sincronización
de progreso, la generación de cursos completos con IA y el registro de costos.

## Stack acordado

- Frontend: React + TypeScript + Vite.
- Interfaz: Tailwind CSS 4 + shadcn/ui configurado con Radix.
- Backend: NestJS + TypeScript sobre Node.js.
- Base de datos: PostgreSQL + Prisma.
- API: REST con documentación OpenAPI.
- Pruebas planificadas: unitarias, de integración y un flujo de extremo a
  extremo.

## Qué completar en cada sección de la plantilla

0. Ficha del proyecto: redacta la descripción breve de Nivelia. Si el
   nombre del autor o la URL del repositorio no están disponibles, marca
   [POR COMPLETAR]. Indica que todavía no hay una URL de despliegue.

1. Descripción general del producto: explica el problema, el usuario
   objetivo y el valor de Nivelia. Enumera las cuatro funcionalidades
   imprescindibles. En diseño y experiencia de usuario, describe este
   recorrido previsto: guardar una formación → añadir el temario cuando
   esté disponible → marcar lecciones → consultar avance → solicitar una
   sugerencia de proyecto. Deja la instalación para cuando exista código.

2. Arquitectura del Sistema: incluye un diagrama Mermaid con el frontend,
   la API NestJS, Prisma, PostgreSQL y el servicio de IA previsto para
   sugerencias. Explica responsabilidades y propone una estructura de
   carpetas sencilla. Presenta infraestructura, seguridad y pruebas como
   planes, sin afirmar que están implementados.

3. Modelo de Datos: incluye un diagrama de entidades en Mermaid para
   Formación, Bloque y Lección. Describe sus campos, tipos, relaciones,
   claves y restricciones principales. Explica cómo se mantiene el orden
   del temario y cómo se identifica qué lecciones están completadas.
   Mantén el modelo coherente con los campos obligatorios y opcionales.

4. Especificación de la API: documenta POST /formations y GET /formations
   en OpenAPI. Incluye campos obligatorios y opcionales, validaciones,
   respuestas y errores. Usa los mismos nombres de campo que en el modelo
   de datos o explica su correspondencia. Identifica estos dos endpoints
   como el contrato del primer flujo de la Entrega 2.

5. Historias de Usuario: redacta una por cada funcionalidad imprescindible,
   con IDs HU-01 a HU-04 y criterios de aceptación verificables. En HU-01,
   incluye que se puede guardar una formación solo con nombre y tipo, y
   que seguirá apareciendo en el listado al recargar la página.

6. Tickets de Trabajo: detalla tres tickets para HU-01:
   - Base de datos: crear el modelo Formation y la migración de formations
     con Prisma en PostgreSQL.
   - Backend: implementar y validar POST /formations y GET /formations
     en NestJS.
   - Frontend: construir el formulario y el listado en React.
   Incluye objetivo, dependencias y criterio de aceptación por ticket.
   El flujo de la Entrega 2 termina cuando creo una formación desde el
   formulario y compruebo que sigue en el listado después de recargar.

7. Pull Requests: indica «No aplica para la Entrega 1».

Antes de responder, revisa que funcionalidades, historias, datos, API y
tickets sean coherentes. Devuelve únicamente el contenido completo de
readme.md en Markdown, listo para revisión humana.

Plantilla de readme.md:
Trabaja solo en la documentación de la Entrega 1. Usa la plantilla como referencia y modifica únicamente readme.md. No generes código, no instales dependencias ni crees commits. Al terminar, indica qué datos quedaron pendientes de mi revisión.
```

**Resultado y revisión humana:** Claude Code generó el primer borrador del README a partir de la plantilla de AI4Devs. Revisé el alcance y mantuve la estructura Formación → Bloques → Lecciones. Dejé el pegado de índices como mejora opcional y elegí Udemy como primera plataforma para evaluar la importación desde URL en una versión futura. También ajusté la
descripción de la arquitectura para distinguir el MVP completo del primer flujo de la Entrega 2.


**Prompt 2:**

**Prompt 3:**

---

## 2. Arquitectura del Sistema

### **2.1. Diagrama de arquitectura:**

**Prompt 1:**

**Prompt 2:**

**Prompt 3:**

### **2.2. Descripción de componentes principales:**

**Prompt 1:**

**Prompt 2:**

**Prompt 3:**

### **2.3. Descripción de alto nivel del proyecto y estructura de ficheros**

**Prompt 1:**

**Prompt 2:**

**Prompt 3:**

### **2.4. Infraestructura y despliegue**

**Prompt 1:**

**Prompt 2:**

**Prompt 3:**

### **2.5. Seguridad**

**Prompt 1:**

**Prompt 2:**

**Prompt 3:**

### **2.6. Tests**

**Prompt 1:**

**Prompt 2:**

**Prompt 3:**

---

### 3. Modelo de Datos

**Prompt 1:**

**Prompt 2:**

**Prompt 3:**

---

### 4. Especificación de la API

**Prompt 1:**

**Prompt 2:**

**Prompt 3:**

---

### 5. Historias de Usuario

**Prompt 1:**

**Prompt 2:**

**Prompt 3:**

---

### 6. Tickets de Trabajo

**Prompt 1:**

**Prompt 2:**

**Prompt 3:**

---

### 7. Pull Requests

**Prompt 1:**

**Prompt 2:**

**Prompt 3:**
