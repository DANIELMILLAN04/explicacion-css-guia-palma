¡Claro! Te explico el archivo `diseño.css` en el mismo orden. En CSS, cada bloque tiene un **selector** —indica a qué elementos HTML se aplica— y, entre llaves `{ }`, una lista de **propiedades** con sus valores.

Por ejemplo:

```css
body {
  color: navy;
}
```

`body` es el selector; `color` es la propiedad y `navy` su valor. Cada declaración termina con `;`.

## 1. Variables de color y estilo general

```css
:root {
  color-scheme: light;
  --color-fondo: #f7f4ed;
  --color-superficie: #fffdf8;
  --color-texto: #24343a;
  --color-secundario: #58696d;
  --color-mar: #176b72;
  --color-mar-oscuro: #104e56;
  --color-acento: #c66b45;
  --sombra: 0 12px 30px rgba(36, 52, 58, 0.09);
}
```

- `:root` representa el elemento principal de la página, es decir, el documento HTML. Se usa para guardar valores disponibles en todo el CSS.
- `color-scheme: light` indica que la página está diseñada para un esquema claro.
- Las propiedades que comienzan por `--` son **variables CSS**. Sirven para reutilizar valores y cambiarlos desde un solo sitio.
  - `--color-fondo`: color crema del fondo de la página.
  - `--color-superficie`: color casi blanco de las secciones.
  - `--color-texto`: color principal del texto.
  - `--color-secundario`: color de textos secundarios, como el pie de página.
  - `--color-mar`: tono turquesa utilizado en enlaces y otros detalles.
  - `--color-mar-oscuro`: versión más oscura para los títulos.
  - `--color-acento`: color naranja usado para destacar el foco del teclado.
  - `--sombra`: sombra que se reutiliza en algunas tarjetas.
- Los colores que empiezan con `#` están escritos en hexadecimal. En `rgba(36, 52, 58, 0.09)`, los tres primeros números indican el color y `0.09` su transparencia.

La llave `}` cierra el bloque de variables.

## 2. Ajuste general de las cajas

```css
* {
  box-sizing: border-box;
}
```

- `*` es el selector universal: se aplica a todos los elementos.
- `box-sizing: border-box` hace que el ancho y alto que indiquemos incluyan también el relleno (`padding`) y el borde. Así es más sencillo controlar el tamaño de las cajas.

## 3. Desplazamiento de la página

```css
html {
  scroll-behavior: smooth;
}
```

- `html` selecciona el documento completo.
- `scroll-behavior: smooth` hace que los desplazamientos dentro de la página sean suaves, en lugar de instantáneos.

## 4. Estilo básico de toda la página

```css
body {
  margin: 0;
  background: var(--color-fondo);
  color: var(--color-texto);
  font-family: "Segoe UI", Tahoma, Geneva, Verdana, sans-serif;
  font-size: 1rem;
  line-height: 1.7;
}
```

- `body` selecciona el contenido visible de la página.
- `margin: 0` quita el margen que el navegador añade automáticamente alrededor de la página.
- `background` establece el color de fondo. `var(--color-fondo)` significa «usa el valor guardado en esa variable».
- `color` define el color predeterminado del texto.
- `font-family` establece la tipografía. El navegador prueba las fuentes en orden: primero `"Segoe UI"`; si no está disponible, prueba `Tahoma`, y así sucesivamente. `sans-serif` es la alternativa genérica.
- `font-size: 1rem` establece el tamaño base de letra. Normalmente `1rem` equivale al tamaño predeterminado del navegador, que suele ser 16 píxeles.
- `line-height: 1.7` da espacio entre líneas para que los párrafos sean más fáciles de leer. Es 1,7 veces el tamaño de letra.

## 5. Cabecera

```css
header {
  padding: clamp(2.5rem, 7vw, 5rem) 1.25rem;
  background: linear-gradient(135deg, #104e56, #24838a);
  color: #fffdf8;
  text-align: center;
}
```

- `header` selecciona las cabeceras de las páginas.
- `padding` añade espacio **dentro** de la cabecera:
  - `clamp(2.5rem, 7vw, 5rem)` establece el espacio vertical mínimo, preferido y máximo. Se adapta al tamaño de la pantalla.
  - `1.25rem` es el espacio horizontal a cada lado.
- `background: linear-gradient(...)` crea un fondo degradado. `135deg` marca la dirección del degradado y los dos códigos hexadecimales son sus colores.
- `color` pone el texto de la cabecera en un tono claro para que contraste con el fondo.
- `text-align: center` centra el texto.

### Título principal

```css
header h1 {
  margin: 0 0 0.5rem;
  font-size: clamp(2.25rem, 6vw, 4rem);
  line-height: 1.1;
}
```

`header h1` selecciona los títulos `<h1>` que están dentro de una cabecera.

- `margin: 0 0 0.5rem` quita el margen de arriba y de los lados, y deja `0.5rem` debajo. Con tres valores, el orden es: arriba, lados, abajo.
- `font-size: clamp(...)` adapta el tamaño del título a la pantalla: nunca será menor que `2.25rem` ni mayor que `4rem`; `6vw` es el valor que intenta usar, según el ancho de la ventana.
- `line-height: 1.1` ajusta la distancia entre líneas del título.

### Párrafos de la cabecera

```css
header p {
  max-width: 52rem;
  margin: 0.75rem auto 0;
  color: rgba(255, 253, 248, 0.92);
}
```

- `header p` selecciona los párrafos dentro de la cabecera.
- `max-width: 52rem` limita su anchura para que las líneas no se hagan demasiado largas.
- `margin: 0.75rem auto 0` añade margen arriba, centra horizontalmente con `auto` y no añade margen abajo.
- `color: rgba(...)` establece un color claro con un poco de transparencia.

### Imagen de la cabecera

```css
header img {
  display: block;
  width: min(100%, 40rem);
  height: auto;
  max-height: 25rem;
  margin: 1.5rem auto;
  border: 5px solid rgba(255, 255, 255, 0.75);
  border-radius: 1.25rem;
  box-shadow: 0 16px 36px rgba(0, 0, 0, 0.2);
  object-fit: cover;
}
```

`header img` selecciona las imágenes que están dentro de la cabecera.

- `display: block` convierte la imagen en un bloque, lo que permite centrarla con márgenes automáticos.
- `width: min(100%, 40rem)` usa el menor valor entre el ancho disponible y `40rem`. Así no se sale de la pantalla ni crece demasiado.
- `height: auto` conserva las proporciones originales de la imagen.
- `max-height: 25rem` limita su altura máxima.
- `margin: 1.5rem auto` añade espacio arriba y abajo, y la centra horizontalmente.
- `border` dibuja un borde blanco de 5 píxeles.
- `border-radius` redondea las esquinas.
- `box-shadow` añade una sombra: los valores representan desplazamiento horizontal, vertical, desenfoque y color.
- `object-fit: cover` hace que la imagen cubra el espacio asignado. Si sus proporciones no coinciden, recorta una parte para evitar que se deforme.

## 6. Contenido principal

```css
main {
  width: min(100% - 2rem, 68rem);
  margin: 2.5rem auto;
}
```

- `main` selecciona el contenido principal de cada página.
- `width: min(...)` calcula el ancho menor entre el disponible —restando `2rem` para dejar espacio en los lados— y `68rem`, que es el ancho máximo.
- `margin: 2.5rem auto` añade espacio arriba y abajo, y centra el contenido horizontalmente.

## 7. Secciones como tarjetas

```css
section {
  margin: 0 0 1.5rem;
  padding: clamp(1.25rem, 4vw, 2.25rem);
  overflow: hidden;
  background: var(--color-superficie);
  border: 1px solid rgba(36, 52, 58, 0.07);
  border-radius: 1.25rem;
  box-shadow: var(--sombra);
}
```

- `section` selecciona cada sección de contenido.
- `margin: 0 0 1.5rem` deja espacio debajo de cada sección.
- `padding` añade espacio interior adaptable al tamaño de pantalla.
- `overflow: hidden` oculta lo que sobresalga de los bordes de la sección.
- `background` aplica el color claro guardado en `--color-superficie`.
- `border` añade un borde fino y ligeramente transparente.
- `border-radius` redondea las esquinas.
- `box-shadow` aplica la sombra guardada en `--sombra`.

### Títulos de las secciones

```css
section h2 {
  margin: 0 0 1rem;
  color: var(--color-mar-oscuro);
  font-size: clamp(1.4rem, 3vw, 2rem);
  line-height: 1.25;
}
```

Este selector afecta solo a los `<h2>` que están dentro de una sección.

- `margin` quita el margen superior y deja espacio debajo del título.
- `color` usa el tono de mar oscuro definido como variable.
- `font-size` adapta el tamaño del título según la pantalla, respetando un mínimo y un máximo.
- `line-height` da algo de espacio entre las líneas del título.

### Último párrafo de cada sección

```css
section p:last-child {
  margin-bottom: 0;
}
```

- `section p:last-child` selecciona un párrafo `<p>` que sea el último elemento de su sección.
- `margin-bottom: 0` elimina el espacio sobrante debajo de ese último párrafo.

## 8. Imágenes del contenido

```css
main img {
  display: inline-block;
  width: min(100%, 18rem);
  height: 13rem;
  margin: 0.4rem;
  border-radius: 0.85rem;
  box-shadow: 0 5px 16px rgba(36, 52, 58, 0.14);
  object-fit: cover;
  vertical-align: middle;
  transition: transform 180ms ease, box-shadow 180ms ease;
}
```

`main img` selecciona las imágenes que están dentro del contenido principal.

- `display: inline-block` permite que varias imágenes aparezcan una al lado de otra, pero conservando propiedades de tamaño.
- `width: min(100%, 18rem)` impide que la imagen sea más ancha que el espacio disponible o que `18rem`.
- `height: 13rem` fija su altura en pantallas grandes.
- `margin: 0.4rem` deja un pequeño espacio alrededor de cada imagen.
- `border-radius` redondea las esquinas.
- `box-shadow` añade una sombra suave.
- `object-fit: cover` llena el espacio recortando lo necesario, sin estirar la imagen.
- `vertical-align: middle` alinea las imágenes con el centro del contenido que tengan al lado.
- `transition` suaviza los cambios de `transform` y `box-shadow` durante `180ms`. `ease` hace que la animación empiece y termine suavemente.

### Al pasar el ratón por una imagen

```css
main img:hover {
  transform: translateY(-3px);
  box-shadow: 0 10px 22px rgba(36, 52, 58, 0.2);
}
```

- `:hover` se activa cuando pasas el cursor por encima de la imagen.
- `translateY(-3px)` la desplaza 3 píxeles hacia arriba.
- `box-shadow` aumenta la sombra para dar sensación de profundidad.

## 9. Lista de enlaces de inicio

```css
ul {
  display: grid;
  gap: 0.75rem;
  margin: 1.25rem 0 0;
  padding: 0;
  list-style: none;
}
```

- `ul` selecciona las listas no ordenadas, como la lista de enlaces de la página de inicio.
- `display: grid` organiza sus elementos mediante CSS Grid. Como no se han definido columnas, los elementos se colocan uno debajo de otro.
- `gap` establece la distancia entre elementos.
- `margin` deja espacio encima de la lista y elimina el margen inferior.
- `padding: 0` elimina la sangría que los navegadores suelen poner a las listas.
- `list-style: none` quita las viñetas.

## 10. Enlaces

```css
a {
  color: var(--color-mar);
  font-weight: 650;
  text-decoration-thickness: 1px;
  text-underline-offset: 0.2em;
}
```

- `a` selecciona todos los enlaces.
- `color` usa el color turquesa definido en `--color-mar`.
- `font-weight: 650` hace que el texto sea más grueso que el normal.
- `text-decoration-thickness` ajusta el grosor del subrayado.
- `text-underline-offset` separa un poco el subrayado de las letras.

### Enlaces de la lista y del pie de página

```css
section li a,
footer a {
  display: inline-block;
  padding: 0.7rem 1rem;
  border-radius: 0.7rem;
  transition: background-color 180ms ease, color 180ms ease;
}
```

- `section li a` selecciona enlaces dentro de elementos de lista dentro de una sección.
- `footer a` selecciona enlaces del pie de página.
- La coma `,` significa que las mismas reglas se aplican a ambos selectores.
- `display: inline-block` permite darles tamaño y relleno sin que ocupen toda la línea.
- `padding` añade espacio dentro del enlace: `0.7rem` arriba y abajo, `1rem` a los lados.
- `border-radius` redondea sus esquinas.
- `transition` suaviza los cambios de color al pasar el cursor.

### Apariencia de los enlaces de la lista

```css
section li a {
  background: #e8f2ef;
  text-decoration: none;
}
```

- `background` pone un fondo verde claro detrás del enlace.
- `text-decoration: none` quita el subrayado.

### Estado al pasar el cursor

```css
section li a:hover,
footer a:hover {
  background: var(--color-mar);
  color: #fff;
  text-decoration: none;
}
```

- `:hover` aplica estas reglas cuando pasas el cursor por encima.
- Los dos tipos de enlace cambian al fondo turquesa y al texto blanco.
- `text-decoration: none` mantiene el texto sin subrayado.

### Foco del teclado

```css
a:focus-visible {
  outline: 3px solid var(--color-acento);
  outline-offset: 3px;
}
```

- `:focus-visible` selecciona un enlace cuando recibe el foco de forma visible, por ejemplo, al llegar a él usando la tecla `Tab`.
- `outline` dibuja un contorno naranja de 3 píxeles.
- `outline-offset` separa el contorno unos píxeles del enlace. Esto ayuda a quienes navegan con teclado a saber qué elemento está seleccionado.

## 11. Pie de página

```css
footer {
  padding: 1.5rem 1rem;
  background: #e9e4d9;
  color: var(--color-secundario);
  text-align: center;
}
```

- `footer` selecciona el pie de página.
- `padding` añade espacio interior: `1.5rem` arriba y abajo, y `1rem` a los lados.
- `background` pone un fondo beige.
- `color` aplica el color secundario al texto.
- `text-align: center` centra su contenido.

```css
footer p {
  margin: 0;
}
```

- Selecciona los párrafos del pie de página.
- `margin: 0` quita el margen automático del párrafo.

## 12. Adaptación a pantallas pequeñas

```css
@media (max-width: 600px) {
  ...
}
```

`@media` permite aplicar reglas solo cuando se cumple una condición. Aquí se aplican cuando la pantalla mide **600 píxeles de ancho o menos**, como en muchos móviles.

```css
main {
  width: min(100% - 1.25rem, 68rem);
  margin: 1.25rem auto;
}
```

Dentro de la media query, estas reglas reducen los márgenes del contenido principal para aprovechar mejor el espacio del móvil.

```css
section {
  border-radius: 1rem;
}
```

En pantallas pequeñas, las esquinas de las secciones se redondean un poco menos.

```css
main img {
  width: calc(100% - 0.8rem);
  height: auto;
  max-height: 18rem;
  aspect-ratio: 4 / 3;
}
```

- `width: calc(100% - 0.8rem)` calcula el ancho disponible menos un pequeño espacio.
- `height: auto` permite que la altura se adapte al ancho.
- `max-height: 18rem` impide que la imagen crezca demasiado.
- `aspect-ratio: 4 / 3` indica una proporción de cuatro partes de ancho por tres de alto.

## 13. Respeto a quienes prefieren menos movimiento

```css
@media (prefers-reduced-motion: reduce) {
  ...
}
```

Esta condición se activa si el dispositivo indica que su usuario prefiere reducir las animaciones.

```css
html {
  scroll-behavior: auto;
}
```

En ese caso, el desplazamiento deja de ser suave y pasa a ser normal e inmediato.

```css
*,
*::before,
*::after {
  transition-duration: 0.01ms !important;
}
```

- `*` selecciona todos los elementos.
- `*::before` y `*::after` seleccionan también los elementos decorativos que CSS puede crear antes o después del contenido.
- `transition-duration: 0.01ms` deja las transiciones prácticamente instantáneas.
- `!important` hace que esta regla tenga prioridad frente a otras duraciones de transición, para respetar la preferencia de reducir el movimiento.

La última llave `}` cierra la condición `@media`, y la anterior cierra la regla del selector universal. Las llaves sirven para delimitar cada bloque de reglas.
