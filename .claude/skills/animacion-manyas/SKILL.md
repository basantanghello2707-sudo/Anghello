---
name: animacion-manyas
description: Crea una animación de intro para Manyas en Remotion a partir de los assets en public/ y un concepto en una línea. Úsala cuando se pida una animación de logo, intro o pieza de marca Manyas.
argument-hint:
- concepto en una frase
---

# Animación de marca — Manyas

Manyas es una varieté de conversación y humor absurdo. El tono visual manda:
**irreverencia primero, familiaridad al final.** El caos resuelve en hogar.

Concepto de esta pieza: $ARGUMENTS

Si no se pasó ningún concepto, pregunta cuál es antes de empezar.

## Antes de escribir código

1. Lista los archivos de `public/`. No inventes nombres: usa los que existen.
2. Si faltan las letras individuales del logo como SVG separados, dilo y detente.
   La mecánica de recolección las necesita.
3. Confirma en una línea qué entendiste del concepto y qué vas a construir.
   Luego sigue sin esperar aprobación.

## Convenciones no negociables

- Assets: solo desde `public/`, con `staticFile()`. Nunca rutas absolutas.
- Imágenes: componente `<Img>` de Remotion, nunca la etiqueta `<img>`.
- Las letras conservan su proporción original. Prohibido estirar, aplastar
  o deformar al aterrizar. Solo rebote suave y breve.
- 30 fps. En los comentarios del código anota los tiempos en segundos además
  de en frames.
- Una escena por archivo, en `src/scenes/`. Nada de un archivo gigante.
- Nada se mueve a velocidad constante: todo acelera y desacelera.
- Las acciones se superponen; no esperan a que la anterior termine.

## Fases

Ejecútalas en orden. Haz commit al terminar cada una, con un mensaje que
describa el estado alcanzado.

**1. Base.** Configura dimensiones, fps y duración en `Root.tsx`. Muestra el
logo centrado y quieto sobre fondo plano. Verifica que los assets cargan.

**2. Recorrido.** Un lienzo ancho de seis zonas por el que la cámara se
desplaza lateralmente. Pausas perceptibles en cada zona. Rectángulos de color
plano como marcador de posición.

**3. Mecánica.** Una sola letra, en la primera zona: aparece, viaja al centro,
se coloca con rebote suave, y queda fija respecto a la pantalla mientras el
fondo sigue pasando detrás. Esta fase es la crítica; si no funciona bien,
no avances.

**4. Las seis letras.** M, A, N, Y, A, S en orden de lectura, una por zona.
Cada una se descubre de una forma distinta: cae, gira, se desliza, crece,
se revela. Ninguna repite el modo de otra.

**5. Personalidad.** Reemplaza los marcadores por escenas con carácter. Cada
zona es un mundo que no tiene que ver con el anterior. Formas, patrones y
color; nada de imágenes externas. Usa los fondos oficiales de `public/` como
paleta de referencia.

**6. Cierre.** Con la última letra, la palabra está completa en el centro.
Cambia el tono: el fondo se simplifica, el movimiento se detiene, MANYAS
queda quieto los últimos segundos.

**7. Pulido.** Revisa easing en todo. Difumina los límites entre zonas:
elementos que invaden la siguiente, degradados entre fondos contiguos,
desenfoque proporcional a la velocidad de cámara. Y rompe el ritmo a
propósito en dos momentos — un corte brusco o una pausa más larga de lo
esperado — para que lo absurdo no quede demasiado prolijo.

## Autorrevisión visual

Al terminar las fases 4, 6 y 7, mira el resultado antes de seguir:

```
npx remotion render <Composicion> out/check --frames=0,45,90,150,240,330 --image-format=png
```

Abre esas imágenes con la herramienta de lectura y revisa:

- ¿Hay letras superpuestas o tapadas?
- ¿Algo se sale del encuadre?
- ¿Las letras se leen contra el fondo, o el contraste es insuficiente?
- ¿Alguna letra está deformada respecto a su proporción original?
- ¿Algún frame está vacío o en negro por un asset que no cargó?

Arregla lo que encuentres y vuelve a revisar. Repite hasta dos veces; si algo
persiste, descríbelo y pregunta en vez de seguir intentando.

Esta revisión detecta errores objetivos. No juzga si la animación es buena:
eso lo decide la persona.

## Cuándo detenerte y preguntar

- Faltan assets, o los nombres no coinciden con lo esperado.
- El concepto pide algo que contradice estas convenciones.
- Dos revisiones seguidas no resuelven el mismo problema visual.

## Al terminar

Resume en pocas líneas: qué construiste, qué decisiones tomaste por tu cuenta,
y qué conviene que la persona revise con sus propios ojos — ritmo, timing de
los chistes, y si el conjunto se siente Manyas.
