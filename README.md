# Evaluación práctica: Campus Córdoba

Evaluación web interactiva que cierra un **Plan de Capacitación** sobre el uso de [Campus Córdoba](https://campuscordoba.cba.gov.ar), el portal de capacitaciones gratuitas del Gobierno de la Provincia de Córdoba.

**Demo:** [https://fpm22.github.io/evaluacion-campus-cordoba/](https://fpm22.github.io/evaluacion-campus-cordoba/)

> Trabajo práctico de la materia electiva **Comunicación Multimedial en el Desarrollo de Sistemas de Información**, Ingeniería en Sistemas de Información, UTN Facultad Regional Córdoba (2026).
> Material educativo independiente: no es un sitio oficial del Gobierno de la Provincia de Córdoba.

---

## Contexto

En la materia trabajamos en modalidad taller para diseñar un **Plan de Capacitación** dirigido a usuarios finales de un sistema de información. El sistema elegido es **Campus Córdoba**, porque:

- Reúne todas las capacitaciones gratuitas de los ministerios y agencias de la Provincia, y funciona desde marzo de 2021.
- Entre septiembre de 2024 y agosto de 2025 tuvo **605 capacitaciones**, **169.300 inscripciones** y el **69% de los accesos desde el celular** (fuente: Gobierno de Córdoba, publicado en diciembre de 2025).
- Muchas personas, incluso estudiantes de Sistemas, no lo conocen o se traban en pasos concretos: ingresar con Ciudadano Digital (CiDi), encontrar el aula o descargar el certificado.

### Etapas del plan

| Etapa | Producto |
|---|---|
| 1. Relevamiento de requerimientos | Instrumento de recolección de datos (encuesta) |
| 2. Diagnóstico | Informe con la interpretación de los resultados |
| 3. Plan de capacitación | Objetivos, actividades, duración, modalidad y participantes |
| 4. Material didáctico | Guía paso a paso en PowerPoint (14 diapositivas, unos 15 minutos) |
| **5. Evaluación** | **Esta página** |

### Objetivos de aprendizaje que se evalúan

Al terminar la capacitación, cada participante debería poder:

1. **Encontrar** un curso gratuito e **inscribirse** desde la portada del portal.
2. **Ingresar con CiDi** y entender por qué es obligatorio (valida la identidad oficial).
3. **Acceder al aula** del curso desde "Mis Cursos" / "Mis Aulas".
4. **Resolver** el problema más común: el mensaje "No tenés cursos activos".
5. **Obtener el certificado**: cumplir los requisitos (actividades aprobadas y CiDi nivel 2) y descargarlo en PDF.

---

## Qué hace la página

- **Datos del participante:** nombre y apellido, CUIL (con máscara `XX-XXXXXXXX-X` y validación del dígito verificador) y fecha (se completa sola con la de hoy).
- **6 preguntas de opción múltiple**, una por cada paso del recorrido, con barra de progreso.
- **Validación antes de corregir:** si falta un dato o una respuesta, lo marca y lleva a ese lugar de la página.
- **Corrección inmediata con devolución:** cada pregunta muestra si estuvo bien, cuál era la correcta y por qué.
- **Puntaje y condición:** *Logrado* con 5–6 correctas, *En revisión* con menos de 5.
- **Imprimir / guardar en PDF** el resultado, como evidencia para el aula virtual o el portafolio.
- **Diseño adaptable** (pensado primero para el celular) y **modo claro/oscuro**.
- **Accesibilidad:** cada pregunta usa `fieldset`/`legend`, se puede usar solo con teclado, el foco es visible y los resultados se anuncian a los lectores de pantalla (`aria-live`).

### Clave de corrección

| Pregunta | Tema | Respuesta |
|---|---|---|
| 1 | Inscripción a un curso | b |
| 2 | Por qué se abre CiDi | b |
| 3 | Dónde ver las clases | a |
| 4 | "No tenés cursos activos" | b |
| 5 | Requisito del certificado | a |
| 6 | Dónde descargar el certificado | b |

---

## Decisiones de diseño

**¿Por qué una página web y no Google Forms o Kahoot?**

| Criterio | Esta página | Google Forms (cuestionario) | Kahoot |
|---|---|---|---|
| Se abre con un enlace, sin cuenta | Sí | Sí | Sí (con PIN o enlace) |
| Explicación de cada respuesta al corregir | Sí | Sí, si el docente la carga | No, solo correcto/incorrecto |
| El alumno se guarda el resultado en PDF | Sí, con un botón | Copia por mail, si se activa | No |
| Control total del diseño y la accesibilidad | Sí | No | No |
| Sirve también como pieza de portafolio (código propio) | Sí | No | No |
| Registro central de resultados para el docente | **No** | **Sí** | **Sí** |

Google Forms resuelve bien la parte de registrar notas, y por eso queda como alternativa si se necesita llevar un registro. La página web se eligió porque permite diseñar la experiencia completa (devolución, impresión, accesibilidad, uso en el celular) y además es un desarrollo propio, que encaja con el perfil de Sistemas.

Como el 69% de la gente entra a Campus Córdoba desde el celular, la evaluación tenía que funcionar bien en el teléfono y abrirse con un simple enlace. Kahoot queda como alternativa para el desafío en vivo dentro de la clase (así está planteado en la guía), y esta página sirve para la evaluación individual.

**Visual:** una sola paleta y dos tipografías (Fraunces para títulos, Inter para texto), con el mismo esquema en todas las preguntas, en línea con los criterios de la guía para evitar un material "caótico".

### Limitaciones conocidas

- **No guarda resultados en un servidor:** cada participante ve su nota, pero el docente no recibe un registro automático. Por eso se pide el PDF como evidencia.
- **Las respuestas están en el código fuente:** cualquiera que sepa abrir las herramientas del navegador puede verlas. Para una evaluación formativa alcanza; para una evaluación con nota haría falta corregir del lado del servidor.
- **El contenido del portal puede cambiar:** los nombres de las secciones ("Mis Cursos", "Mis Certificaciones") hay que revisarlos contra el portal antes de cada uso.

### Mejoras posibles

- Enviar los resultados a una planilla (por ejemplo, Google Sheets con Apps Script) para tener un registro central.
- Mezclar el orden de preguntas y opciones en cada intento.
- Agregar capturas del portal en cada pregunta.
- Un banco de preguntas más grande, para que cada intento sea distinto.

---

## Tecnologías

- HTML5, CSS3 (variables, `:has()`, `@media print`, `prefers-color-scheme`) y JavaScript sin librerías.
- Un solo archivo, `index.html`: no necesita servidor ni dependencias.
- Publicado con **GitHub Pages**.

```
evaluacion-campus-cordoba/
├── index.html   # página completa (estructura, estilos y lógica)
└── README.md    # este documento
```

---

## Créditos

**Equipo:**

- Figueroa Prada, Juan Uriel
- Fronte, Gastón
- Gómez Alameda, Romina Abigail
- Marengo, Francisco Pablo
- Zabala, Valentina

**Cátedra:** Mgter. Andrés Kabusch y Mgter. Karina Toranzo, Comunicación Multimedial en el Desarrollo de Sistemas de Información, UTN-FRC

## Fuentes

- Portal oficial: [campuscordoba.cba.gov.ar](https://campuscordoba.cba.gov.ar)
- El Objetivo (15/12/2025). *Campus Córdoba registró 169 mil inscripciones y entregó casi 40 mil certificados.* Datos de septiembre de 2024 a agosto de 2025.
- Hoy Día Córdoba (19/03/2022). *En un año, Campus Córdoba capacitó a más de 100.000 ciudadanos.*
- InfoNegocios (23/03/2021). *Campus Córdoba, un nuevo portal de capacitación integral para todos los cordobeses.*
