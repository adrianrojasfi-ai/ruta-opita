# Prompt maestro – Ruta Opita

**Rol:**
Actúa como desarrollador frontend senior especializado en Tailwind CSS 4, diseño responsive mobile-first y accesibilidad web (WCAG 2.2 nivel AA).

**Contexto:**
Voy a crear la landing page de "Ruta Opita", una agencia de turismo (ficticia, para un trabajo universitario) con sede en Neiva, Huila, Colombia. Organiza planes guiados al Desierto de la Tatacoa (Villavieja), al Parque Arqueológico de San Agustín, al Estrecho del Magdalena y al Salto de Bordones. El público son viajeros nacionales y extranjeros de 20 a 40 años que planean su viaje desde el celular. El objetivo del sitio es mostrar los destinos y los planes, generar confianza y recibir solicitudes de reserva por medio de un formulario.

Datos reales que puedes usar en los textos: la Tatacoa es un bosque seco tropical de unos 330 km² con dos zonas, El Cusco (tierras rojas) y Los Hoyos (tierras grises, con piscina natural), y tiene observatorio astronómico; el Parque Arqueológico de San Agustín es Patrimonio de la Humanidad de la UNESCO desde 1995 y tiene esculturas en piedra de los siglos I a VIII; en el Estrecho del Magdalena el río pasa por un canal de roca de unos 2,20 metros de ancho; el Salto de Bordones es una cascada de cerca de 400 metros de altura.

**Tareas:**
Construye una sola página con estas secciones, en este orden:

1. Navbar fija con el logo en texto ("Ruta Opita"), enlaces a cada sección, botón "Reservar" y botón para cambiar entre modo claro y oscuro. En celular los enlaces se convierten en un menú hamburguesa que se abre y se cierra con JavaScript.
2. Hero con título principal, subtítulo, una ilustración de fondo del desierto con capa oscura y dos botones: "Ver destinos" y "Reservar mi viaje".
3. Sección "Destinos" con 4 tarjetas (Tatacoa, San Agustín, Estrecho del Magdalena, Salto de Bordones): imagen, nombre, municipio, descripción corta y efecto hover. Grid de 1 columna en celular, 2 en tablet y 4 en computador.
4. Sección "Planes" con 3 tarjetas de tours (nombre, duración, precio por persona en pesos colombianos, 3 elementos incluidos) y un botón "Ver detalles" que abre un modal con el itinerario de ese plan. El modal se cierra con un botón, con la tecla Esc y haciendo clic fuera.
5. Sección "Nosotros" con texto e imagen en dos columnas (una columna en celular) y tres cifras destacadas.
6. Galería de 6 imágenes en grid (2 columnas en celular, 3 en computador).
7. Preguntas frecuentes en acordeón (4 preguntas) que se abren y se cierran con JavaScript.
8. Formulario de contacto y reserva con nombre, correo, plan de interés (lista desplegable), fecha tentativa, número de personas (1 a 10) y mensaje. Valida con JavaScript que los campos obligatorios estén llenos y que el correo sea válido; muestra el error en rojo debajo de cada campo y, al enviar correctamente, un toast verde de confirmación que desaparece a los 4 segundos.
9. Pie de página con dirección en Neiva, horario de atención, redes sociales y derechos reservados.

**Restricciones:**
- Usa solo HTML, Tailwind CSS 4 mediante el Play CDN (https://cdn.jsdelivr.net/npm/@tailwindcss/browser@4) y JavaScript puro, sin otras librerías. No uses `tailwind.config.js`, ni las directivas `@tailwind`, ni el CDN de la versión 3.
- Define la paleta con `@theme` dentro de una etiqueta `<style type="text/tailwindcss">`, siguiendo la regla 60-30-10: fondo arena `#FBF6EE` (60 %), verde andino oscuro `#1F3B36` para texto, navbar y footer (30 %) y acento terracota `#B23A16` para botones y enlaces (10 %). Colores semánticos: éxito `#15803D`, error `#B91C1C` y advertencia `#A34A04`.
- Modo oscuro con la variante `dark:` activada por una clase `.dark` en `<html>` (usa `@custom-variant`), con fondo `#13201D`, texto `#F2EADF` y acento `#F0936D`. Guarda la preferencia en localStorage.
- Usa máximo dos fuentes de Google Fonts: Fraunces para títulos y Nunito Sans para textos.
- Diseña mobile-first y usa al menos los prefijos `sm:`, `md:` y `lg:`.
- Accesibilidad: textos alternativos descriptivos en todas las imágenes, `<label>` en todos los campos, contraste mínimo de 4.5:1, foco visible en botones y enlaces, `aria-expanded` en el menú y en el acordeón, `lang="es"`.
- Como imágenes, crea ilustraciones SVG sencillas y originales (paisajes con capas de colores de la paleta) y guárdalas en una carpeta `img/`; luego las reemplazaré por fotografías.

**Formato de salida:**
Entrega un archivo `index.html` con el JavaScript al final del `<body>`, el código indentado y comentarios en español que separen cada sección, más los archivos SVG de la carpeta `img/`. Al final, explica en una lista corta cómo abrir el sitio y qué partes debería personalizar.
