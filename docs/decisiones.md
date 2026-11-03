# Documento de decisiones de diseño

> Cada decisión: **qué** elegiste, **por qué**, y **qué alternativa descartaste**.
> Se evalúa la justificación, no la longitud. Máximo 2 páginas en la Fase 1.

## Ruta de trabajo

- [ ] Ruta A · Figma
- [x] Ruta B · VS Code

He elegido trabajar en VS Code porque puedo cambiar los estilos y ver
el resultado directamente en el navegador. Así no tengo que actualizar
también el diseño en Figma.

## 1. Color (RA1 · CE b)

He usado el tono 322° que corresponde al caso de Las Dunas.
La escala mantiene ese tono y un croma de 0.04, cambiando la luminosidad
para obtener morados claros y oscuros.

En el tema claro uso el acento-700 y en el oscuro el acento-400,
para que destaquen sobre el fondo. No he mantenido el turquesa
porque no era el color asignado a mi caso.

El contraste del acento sobre la superficie es de 7,24:1 en claro
y 6,71:1 en oscuro. Los dos superan el mínimo de 4,5:1.

De momento no he añadido tokens ni pares de contraste nuevos.
He ejecutado npm run check y no ha dado errores.

## 2. Tipografía (RA1 · CE b)

He mantenido system-ui porque se lee bien y no necesita descargar
fuentes externas. He descartado una fuente decorativa porque la web
se centra en consultar horarios y hacer reservas.

El tamaño base es de 16 px en móvil y 18 px en escritorio.
La escala aumenta con una razón de 1.2 en móvil y 1.25 en escritorio.
Así se diferencian los títulos del texto sin que en móvil sean
demasiado grandes.

He limitado los párrafos a 65ch para que las líneas no sean demasiado
largas en pantallas grandes. He descartado que ocupen todo el ancho
porque cuesta más seguir la lectura.

## 3. Espaciado y forma

He mantenido los espacios de la plantilla, basados en múltiplos de
4 px, para que la separación entre elementos sea consistente.

Los campos usan un radio de 8 px y las tarjetas de 12 px.
He descartado poner medidas distintas en cada elemento porque
sería más difícil mantener el mismo estilo en toda la web.

## 4. Componentes (RA1 · CE f)

| Componente | Estados | Cómo se resuelve en CSS |
| --- | --- | --- |
| Botón | Normal, hover, foco, desactivado y secundario | Usa tokens, `:hover`, `:focus-visible`, `:disabled` y la clase `.boton--secundario`. |
| Turno | Disponible, seleccionado, ocupado y foco | Uso Grid para colocar el radio y los textos. Con `:has()` cambia la tarjeta según el estado del radio. El ocupado lleva borde discontinuo y el texto «Ocupado». |
| Contador de invitados | Opción marcada y foco | Cuatro radios del 0 al 3, colocados en fila con Flexbox. Uso `:has(:checked)` para la selección y `:has(:focus-visible)` para el foco. |
| Aviso de pago | Normal | Borde de acento, fondo tenue y concepto con fuente monoespaciada. Incluye importe, teléfono y concepto. |

He mantenido los radios visibles para reconocer la opción seleccionada
sin depender solo del color. He descartado usar botones con JavaScript
porque los radios ya permiten elegir una única opción y usar el teclado.

El aviso muestra un ejemplo fijo de 2 invitados a 2 € cada uno.
En esta fase solo se pide diseñar el componente.

## 5. Comparativa de tecnologías (RA1 · CE e · RA2 · CE i)

| Criterio | Figma | Penpot | Diseño en código |
| --- | --- | --- | --- |
| Coste / licencia | Herramienta propietaria, con plan gratuito limitado y planes de pago. | Código abierto, con posibilidad de alojarlo en un servidor propio. | HTML y CSS no requieren pagar licencias; puedo trabajar con VS Code. |
| Traslado a código | Permite consultar el diseño para implementarlo después. | Permite inspeccionar medidas y obtener referencias de CSS y HTML. | El diseño ya está implementado y se prueba en el navegador. |
| Mantenimiento | Hay que mantener el diseño y su implementación coordinados. | También requiere coordinar el archivo de diseño con el código. | Los componentes y la guía usan los mismos tokens. |

| Criterio | Sass + CSS propio | CSS nativo sin preprocesador | Bootstrap / Tailwind |
| --- | --- | --- | --- |
| Tokens y temas | Mapas y funciones Sass generan las variables CSS de los temas. | Puede usar variables CSS y temas sin compilar Sass. | Ofrecen sus propios sistemas de personalización. |
| Peso del CSS final | Depende de las reglas que escriba y genere al compilar. | Depende de las reglas que escriba. | Bootstrap completo incluye estilos que quizá no use; Tailwind genera estilos según las clases detectadas. |
| Control de la cascada | Organizo los estilos con módulos, BEM y `@layer`. | También permite BEM y `@layer`, pero sin los módulos de Sass. | Hay que adaptarse a las clases y organización del framework. |

**Decisión y motivo:**

He elegido VS Code y Sass con CSS propio porque puedo ver el resultado
directamente en el navegador y aprovechar los mapas, funciones y mixins
de la plantilla. Sass también comprueba los contrastes al compilar.

He descartado Figma y Penpot para no mantener otro diseño aparte.
CSS nativo permitiría hacer la interfaz, pero no aprovecharía las
herramientas Sass de la plantilla. No uso Bootstrap ni Tailwind porque
la práctica pide trabajar sin frameworks y crear nuestros componentes.