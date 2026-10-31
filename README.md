# Ruta Opita · Turismo en el Huila

Landing page de **Ruta Opita**, una agencia de turismo **ficticia** con sede en Neiva (Huila, Colombia) que ofrece planes guiados al Desierto de la Tatacoa, al Parque Arqueológico de San Agustín, al Estrecho del Magdalena y al Salto de Bordones.

Proyecto de la **Parte 2 (práctica)** del taller individual *Investigación y desarrollo de un sitio web con Tailwind CSS e inteligencia artificial*.
Seminario en Gestión de Software Ágil Asistido por IA · Ingeniería de Software · Fundación Escuela Tecnológica de Neiva (FET).

- **Autor:** Adrian Rojas
- **Sitio publicado:** `[pega aquí el enlace de GitHub Pages o Netlify]`
- **Video:** `[pega aquí el enlace de YouTube]`

---

## 1. Planificación

| Aspecto | Decisión |
| --- | --- |
| Temática | Agencia de turismo del Huila (Tatacoa, San Agustín, Estrecho del Magdalena, Salto de Bordones) |
| Público objetivo | Viajeros nacionales y extranjeros de 20 a 40 años que planean su viaje desde el celular |
| Propósito | Mostrar destinos y planes, generar confianza y recibir solicitudes de reserva |
| Mapa del sitio | Navbar → Hero → Destinos → Planes (con modal) → Nosotros → Galería → Preguntas frecuentes → Contacto → Footer |

### Paleta (regla 60-30-10) y contraste

| Rol | Color | Uso | Contraste verificado |
| --- | --- | --- | --- |
| Dominante (60 %) | `#FBF6EE` arena | Fondo general | — |
| Secundario (30 %) | `#1F3B36` verde andino | Texto, navbar, sección de contacto | 11.2:1 sobre arena |
| Acento (10 %) | `#B23A16` terracota | Botones, precios, enlaces | 6.0:1 con texto blanco · 5.6:1 sobre arena |
| Éxito | `#15803D` | Toast de confirmación | 5.0:1 con texto blanco |
| Error | `#B91C1C` / `#FCA5A5` (oscuro) | Mensajes de error | 6.0:1 (claro) · 7.5:1 (oscuro) |
| Advertencia | `#A34A04` | Reservado para avisos | 5.5:1 sobre arena |
| Modo oscuro | `#13201D` fondo · `#F2EADF` texto · `#F0936D` acento | Tema oscuro | 14.1:1 · 7.3:1 |

### Tipografía (máximo dos fuentes)

- **Fraunces** (Google Fonts) para títulos.
- **Nunito Sans** (Google Fonts) para textos.

| Nivel | Clases |
| --- | --- |
| H1 | `font-titulos text-4xl md:text-5xl lg:text-6xl font-bold` |
| H2 | `font-titulos text-3xl md:text-4xl font-bold` |
| H3 | `font-titulos text-xl font-bold` (tarjetas) / `text-2xl` (planes) |
| Párrafo | `text-base` / `text-lg md:text-xl` en el hero, `leading-relaxed` |
| Caption | `text-sm` |

## 2. Tecnologías

- HTML5
- Tailwind CSS 4 mediante el Play CDN (`@tailwindcss/browser@4`), con el tema en `@theme`
- JavaScript puro (sin librerías)
- Ilustraciones SVG propias en `img/`

> Nota: el Play CDN está pensado para desarrollo y prototipos. En un sitio real se compilaría el CSS con Tailwind CLI o Vite.

## 3. Funcionalidades

- Navbar fija con menú hamburguesa en celular (se cierra al tocar un enlace).
- Modo oscuro con botón, que respeta la preferencia del sistema y se guarda en `localStorage`.
- Destinos en tarjetas con efecto hover (1, 2 y 4 columnas según el ancho).
- Planes con **modal** de itinerario (se cierra con botón, Esc o clic afuera; mantiene el foco dentro).
- Galería en grid (2 y 3 columnas).
- **Acordeón** de preguntas frecuentes.
- Formulario con validación en JavaScript (campos obligatorios, correo válido, personas de 1 a 10), errores junto a cada campo y **toast** de confirmación que desaparece a los 4 segundos.
- Etiqueta "Más vendido", fechas solo desde hoy y botón "Volver arriba".
- Accesibilidad: `lang="es"`, textos alternativos, etiquetas en todos los campos, `aria-expanded`, `aria-invalid`, `role="dialog"`, `role="status"`, foco visible y contraste de 4.5:1 o más.

## 4. Cómo verlo

1. Descarga o clona el repositorio.
2. Abre `index.html` en el navegador (necesita internet para cargar Tailwind y las fuentes).

## 5. Estructura

```
ruta-opita/
├── index.html            # sitio final
├── img/                  # ilustraciones SVG
├── docs/
│   └── prompt-maestro.md # prompt maestro completo
├── versiones/            # evidencia de cada iteración
│   ├── v1/               # resultado del prompt maestro
│   ├── ajuste-1 … ajuste-5/
│   └── cambios-personalizacion/
└── README.md
```

## 6. Prompt maestro

El prompt completo, con sus cinco partes (rol, contexto, tareas, restricciones y formato de salida), está en [`docs/prompt-maestro.md`](docs/prompt-maestro.md).

## 7. Bitácora de prompts

Herramienta de IA usada: **Claude (Anthropic)**. La versión 1 se probó en el navegador (modo responsive en 375, 768 y 1280 px, teclado y modo oscuro) y cada problema encontrado se corrigió con un prompt de ajuste.

| # | Prompt de ajuste enviado | Problema que buscaba resolver | Resultado obtenido | ¿Funcionó? |
| --- | --- | --- | --- | --- |
| 1 | "En celular, al abrir el menú hamburguesa los enlaces aparecen apretados en una columna al lado del logo, dentro de la misma barra, y el menú no se cierra cuando toco un enlace. El menú debe desplegarse como un panel debajo de la barra en celular, seguir en fila desde `md` y cerrarse al tocar un enlace." | Menú móvil roto y que no se cerraba | El menú es un panel `absolute top-full` debajo de la barra, con enlaces más grandes para tocar; se cierra al tocar un enlace y el `aria-label` cambia entre "Abrir" y "Cerrar menú". | Sí |
| 2 | "Los campos del formulario son invisibles: tienen fondo transparente y texto verde oscuro sobre la sección verde, y los mensajes de error rojos casi no se leen (contraste 1.87:1). Haz que los campos tengan fondo, borde y foco visibles, y que los errores cumplan 4.5:1 en modo claro y oscuro." | Formulario inutilizable y errores sin contraste | El formulario quedó dentro de una tarjeta clara; los campos tienen fondo, borde, placeholder y foco. Error: 6.0:1 en claro y 7.5:1 en oscuro (nuevo color `--color-error-claro`). | Sí |
| 3 | "Si el sistema operativo está en modo oscuro, la página igual carga en modo claro, y cuando la preferencia guardada es 'oscuro' se ve un parpadeo blanco antes de cambiar. Aplica el tema antes de pintar la página, respeta `prefers-color-scheme` cuando no hay preferencia guardada y agrega `aria-pressed` al botón." | Modo oscuro que ignoraba el sistema y parpadeaba | Script pequeño en el `<head>` que aplica la clase `dark` antes de pintar; el botón sincroniza su ícono y `aria-pressed`. | Sí |
| 4 | "El modal de 'Ver detalles' no es accesible: no tiene `role="dialog"`, el foco se queda en el botón de atrás y con Tab se sale del modal. Agrega `role` y `aria-modal`, mueve el foco al botón de cerrar, mantén el Tab dentro del modal, devuelve el foco al cerrar y bloquea el scroll del fondo. Además, que 'Quiero este plan' deje seleccionado ese plan en el formulario." | Modal inaccesible para teclado y lectores de pantalla | Modal con `role="dialog"`, `aria-modal` y `aria-labelledby`; el foco entra, se queda dentro y regresa al botón; el itinerario se crea con `textContent` en vez de `innerHTML`; el plan queda preseleccionado. | Sí |
| 5 | "Los lectores de pantalla no anuncian el toast, los campos con error no tienen `aria-invalid` y el foco con teclado casi no se ve. Agrega `role="status"` al toast, `aria-invalid` y `aria-describedby` a los campos, enfoca el primer campo con error y define un foco visible uniforme para enlaces, botones y campos." | Estados del formulario y foco poco accesibles | Toast con `role="status"` y animación; campos con `aria-invalid`/`aria-describedby` que se revalidan al corregir; foco al primer error; contorno terracota de 3 px con halo claro en todo el sitio. | Sí |

Las versiones de cada iteración están en la carpeta `versiones/`.

## 8. Cambios manuales (personalización del código)

Después de las cinco iteraciones con IA se hicieron tres cambios de personalización directamente en el código de `index.html`. Para cada uno se tomó una captura del antes y del después.

### Cambio 1 · Etiqueta "Más vendido" en el plan Ruta Agustiniana

- **Qué hace:** destaca el plan intermedio con un borde de color acento y una etiqueta en forma de píldora montada sobre el borde superior de la tarjeta.
- **Cómo se hizo:** al `<article>` de la tarjeta se le agregaron las clases `relative ring-2 ring-terracota`, y dentro de él un `<span>`:

```html
<span class="absolute -top-3 left-6 bg-terracota text-white text-xs font-bold px-3 py-1 rounded-full">Más vendido</span>
```

- **Clases clave:** `relative` en el padre y `absolute` en el hijo hacen que la etiqueta se ubique tomando la tarjeta como referencia; `-top-3` la sube 12 px para que quede sobre el borde y `left-6` la separa 24 px de la izquierda; `rounded-full` le da la forma de píldora; `ring-2 ring-terracota` dibuja el borde de acento.
- **Diseño:** aplica la regla 60-30-10, porque el terracota (acento, 10 %) se usa solo para llamar la atención sobre una tarjeta. El texto blanco sobre terracota tiene un contraste de 6.0:1.

### Cambio 2 · El formulario no acepta fechas pasadas

- **Qué hace:** si la persona elige una fecha anterior a hoy, aparece el error "Elige una fecha desde hoy en adelante." junto al campo, y el calendario ya no deja escoger días pasados.
- **Cómo se hizo:** se creó una función que devuelve la fecha de hoy en formato `AAAA-MM-DD` y se agregó la regla de la fecha en `validarCampo`:

```js
function fechaDeHoy() {
  const hoy = new Date();
  const mes = String(hoy.getMonth() + 1).padStart(2, "0");
  const dia = String(hoy.getDate()).padStart(2, "0");
  return `${hoy.getFullYear()}-${mes}-${dia}`;
}
document.getElementById("fecha").min = fechaDeHoy();

// dentro de validarCampo:
else if (campo.id === "fecha") hayError = valor === "" || valor < fechaDeHoy();
```

- **Detalles:** se usan `getFullYear`, `getMonth` y `getDate` en vez de `toISOString` porque este último usa la hora UTC y después de las 7:00 p. m. en Colombia ya devolvería el día siguiente. `getMonth()` empieza en 0, por eso se suma 1. `padStart(2, "0")` convierte `5` en `05`. Como las dos fechas quedan en formato año-mes-día, se pueden comparar como texto.
- **Diseño:** aplica la heurística de Nielsen de **prevención de errores**: el sistema evita que se haga una reserva para una fecha imposible.

### Cambio 3 · Botón flotante "Volver arriba"

- **Qué hace:** cuando la persona baja más de 600 px aparece, con una animación, un botón redondo con una flecha en la esquina inferior izquierda que la regresa al inicio de la página.
- **Cómo se hizo:** un enlace `<a href="#inicio">` con estas clases:

```html
fixed bottom-5 left-5 z-30 size-12 grid place-items-center rounded-full bg-andino text-arena
shadow-lg transition duration-300 opacity-0 translate-y-4 pointer-events-none hover:bg-terracota
```

y un evento `scroll` en JavaScript que quita o pone `opacity-0`, `translate-y-4` y `pointer-events-none` según `window.scrollY > 600`.

- **Clases clave:** `fixed bottom-5 left-5` lo deja fijo en la esquina; `opacity-0 translate-y-4` lo esconde un poco más abajo; `transition duration-300` anima la aparición en 300 ms; `pointer-events-none` evita que se pueda tocar mientras está oculto.
- **Accesibilidad:** tiene `aria-label="Volver al inicio de la página"` y se saca del orden de la tecla Tab (`tabIndex = -1`) mientras no se ve. En modo oscuro cambia a `dark:bg-terracota-claro`.

| # | Cambio | Dónde | Concepto que demuestra |
| --- | --- | --- | --- |
| 1 | Etiqueta "Más vendido" | Sección Planes | Posicionamiento `relative`/`absolute`, regla 60-30-10 |
| 2 | Fechas solo desde hoy | Formulario y `validarCampo` | Validación con JavaScript, prevención de errores |
| 3 | Botón "Volver arriba" | Antes del toast + script | Eventos de scroll, transiciones de Tailwind, accesibilidad |

## 9. Pruebas

- [ ] Responsive en celular, tablet y computador (F12 → modo dispositivo).
- [ ] HTML validado en https://validator.w3.org (errores corregidos).
- [ ] Lighthouse – Accesibilidad: `[puntaje]` (captura en `docs/lighthouse.png`).
- [ ] Regla 60-30-10, jerarquía tipográfica y heurísticas de Nielsen (visibilidad del estado, prevención de errores, consistencia).
- [ ] El enlace publicado abre desde un celular.

## 10. Créditos

- Ilustraciones SVG originales creadas para este proyecto (se pueden reemplazar por fotografías propias).
- Fuentes: Fraunces y Nunito Sans, Google Fonts (licencia SIL Open Font License).
- Datos de los destinos: ICANH (Parque Arqueológico de San Agustín) y fuentes turísticas públicas. Precios e itinerarios de los planes son de ejemplo.


