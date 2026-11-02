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

| Componente | Estados | Cómo se resuelve cada estado en CSS |
| --- | --- | --- |
| Botón | normal, hover, foco, desactivado, secundario | |
| Turno | disponible, seleccionado, ocupado, foco | |
| Contador de invitados | | |
| Aviso de pago | | |

## 5. Comparativa de tecnologías (RA1 · CE e · RA2 · CE i)

| Criterio | Figma | Penpot | Diseño en código |
| --- | --- | --- | --- |
| Coste / licencia | | | |
| Traslado a código (handoff) | | | |
| Mantenimiento del sistema | | | |

| Criterio | Sass + CSS propio | CSS nativo sin preprocesador | Bootstrap / Tailwind |
| --- | --- | --- | --- |
| Tokens y temas | | | |
| Peso del CSS final | | | |
| Control de la cascada | | | |

**Decisión y motivo:**
