# Práctica «Ahora lo hacemos tú y yo»
Taller **LaTeX con IA** · Grupo Universitario de Informática (UVa)

Partimos de la **plantilla de entregables de la UVa** (`Template.tex`) y la
convertimos en un proyecto modular, con estilo propio y bibliografía en `.bib`.

## Contenido del paquete

```text
taller_latex_gui/
├─ README.md            ← este guion
├─ scholar_guia.md      ← de Google Scholar a refs.bib (+ lista de comprobación)
├─ inkscape_guia.md     ← vectorizar con Inkscape e incluirlo en LaTeX
├─ glosario.md          ← qué hace cada comando que aparece en la práctica
├─ prompts_ia.md        ← prompts de cada paso
├─ presentacion/        ← diapositivas (index.html) + Recursos/
├─ 00_inicio/
│  ├─ monolito.tex      ← la plantilla UVa con contenido y 8 «problemas»
│  └─ Recursos/         ← logo UVa + hdt_esquema.png (para vectorizar)
└─ 01_solucion/
   ├─ main.tex          ← solo ensambla y rellena los datos del documento
   ├─ styles/mistilo.sty← diseño: paleta, títulos, cabeceras, enlaces, cajas, portada
   ├─ capitulos/        ← 01_intro.tex, 02_datos.tex (solo contenido)
   ├─ bib/refs.bib      ← 2 referencias reales de la UVa
   └─ Recursos/         ← logo UVa + hdt_esquema.svg/.pdf (figura vectorial)
```

## Qué hemos hecho con la plantilla

| En la plantilla original | En la solución |
|---|---|
| Preámbulo mezclado con el cuerpo | Todo el diseño en `styles/mistilo.sty` |
| Portada escrita a mano en el cuerpo | Comando `\makeportada` + `\titulodoc`, `\autordoc`, `\titulacion`, `\mencion` en `main.tex` |
| Logo con ruta escrita a mano | `\graphicspath{{Recursos/}}` y `\includegraphics{UVA-3881270087.pdf}` |
| `graphics` y `listings` cargados de más | Una sola carga de cada paquete |
| `hidelinks` + enlaces azul/magenta/cyan | Una política: enlaces en el color de acento |
| Cabecera vacía, pie con número | Cabecera con título corto y sección actual, filete suave |
| Títulos sin color | `titlesec` con paleta (`tinta`, `acento`) |
| `\fcolorbox` copiado a mano | Entorno `aviso` (`tcolorbox`) |
| `\title{\textbf{...}` sin cerrar | Corregido (la plantilla original no compilaba) |
| Bibliografía manual | `biblatex` + `bib/refs.bib` |

## Para quien empieza a modificar los ejemplos

Todos los ficheros `.tex`, `.sty` y `.bib` están **comentados línea a línea**: los
comentarios empiezan por `%` y explican qué hace cada bloque y **qué puedes
cambiar sin romper nada**. Orden de lectura recomendado:

1. `00_inicio/monolito.tex`: guía de lectura y comentarios en cada bloque.
2. `01_solucion/main.tex`: cómo se ensambla y se compila.
3. `01_solucion/capitulos/`: cómo escribir secciones, figuras, tablas y citas.
4. `01_solucion/bib/refs.bib`: anatomía de una entrada y cómo añadir otra.
5. `01_solucion/styles/mistilo.sty`: dónde cambiar colores, títulos y cabeceras.
6. `glosario.md`: consulta rápida de comandos.

Consejo: cambia **una cosa cada vez** (un color, un título, una clave) y compila.

## Preparación (antes del taller)

- **Overleaf (recomendado):** sube `00_inicio/` y `01_solucion/` como dos
  proyectos. Usa `biber` sin configuración.
- **Local:** TeX Live con `biblatex`, `biber`, `tcolorbox`, `titlesec`,
  `fancyhdr`, `listings` y `babel-spanish`. Compila con `latexmk -pdf main.tex`.
- Que cada asistente tenga una IA y Google Scholar a mano.
- El logo se carga desde `Recursos/`: respeta ese nombre de carpeta.

> Nota: el monolito y el conjunto estilo + secciones + portada compilan en mi
> entorno. La parte con `biblatex`/`biber` no se pudo ejecutar allí: haz una
> compilación de prueba tú antes del taller.

## Guion sugerido (≈ 58 min, ajustable)

| Min | Fase | Qué ocurre |
|---|---|---|
| 0–5 | Diagnóstico | Compilar el monolito. Recorrer los `[PROBLEMA 1-8]`. |
| 5–20 | **Paso 1** · Modularizar | Mover diseño al `.sty`, secciones a `capitulos/`, portada a comando. |
| 20–35 | **Paso 2** · Bibliografía | Demo con *Trasgo*; equipos con HDT y el reto de Fresno. |
| 35–47 | **Paso 3** · Profesionalizar | Cabeceras, títulos, enlaces, `aviso`, tabla `booktabs`; usar la IA. |
| 47–55 | **Paso 4** · Figuras | Vectorizar `hdt_esquema.png` con Inkscape, exportar a PDF y sustituirlo (`inkscape_guia.md`). |
| 55–58 | Cierre | Cambiar `style=ieee` por `apa` y el color `acento`: todo se actualiza. |

## Comentarios para el ponente

**Paso 1**
- Empieza por **leer el error** del monolito: falta una `}` en `\title` en la
  plantilla original. Buen ejemplo de que la IA ayuda, pero hay que saber leer el log.
- Que muevan a mano un bloque al `.sty` antes de pedir el resto a la IA.
- Pregunta: «¿qué debería haber dentro de una sección?» → solo contenido.
- La clase es `article` (usa `\section`). Para un TFG largo, cambia a `report`
  y usa `\chapter`; la modularización es idéntica.

**Paso 2**
- Gran ocasión para hablar de **alucinaciones en referencias**: la IA puede dar
  BibTeX verosímil pero falso. Verificamos con DOI y fuentes de la UVa.
- *Trasgo* se desarrolló en la UVa y *HDT* encaja con la idea del taller (dividir en módulos).

**Paso 4**
- Instalar Inkscape antes del taller (versión 1.x). Si alguien no puede,
  entrega el SVG ya trazado en `01_solucion/Recursos/`.
- Muestra primero el fallo: ampliar el PNG en el PDF (borroso) y luego el PDF vectorial (nítido).
- Insiste en borrar el mapa de bits tras trazar: si no, el PDF «vectorial» lleva el PNG dentro.
- Avisa: fotos y capturas no se vectorizan.
- La figura vectorial de la solución (`hdt_esquema.pdf`) se generó con una
  herramienta de conversión de SVG a PDF, no con Inkscape; el procedimiento con
  Inkscape de la guía no se ha podido ejecutar en mi entorno, así que pruébalo antes.

**Paso 3**
- Cambia `acento` en `mistilo.sty` y enseña cómo se recolorean portada,
  títulos, enlaces, cabecera y cajas.
- Compara un prompt vago con uno preciso: el vago suele tocar de más.
- Para ir más allá: convertir `mistilo.sty` en `miclase.cls` (ver `prompts_ia.md`).

## Errores típicos

| Síntoma | Causa probable |
|---|---|
| Citas como `[?]` | Falta ejecutar `biber`, o clave mal escrita. |
| `File 'styles/mistilo.sty' not found` | Compilas desde fuera de `01_solucion/`. |
| `File 'UVA-3881270087.pdf' not found` | La carpeta no se llama exactamente `Recursos`. |
| La figura sale borrosa | Se incluyó el `.png`; usa el PDF exportado desde Inkscape. |
| `Undefined control sequence \begin{aviso}` | El `.sty` no se carga o falta `tcolorbox`. |
| Cabecera vacía en la 1.ª página de sección | Normal en `article`: la portada usa `\thispagestyle{empty}`. |

## Checklist final

- [ ] `main.tex` solo ensambla y rellena datos.
- [ ] Las secciones no tienen `\usepackage`.
- [ ] La portada sale de `\makeportada`.
- [ ] No queda `\fcolorbox` ni `thebibliography`.
- [ ] Imágenes solo en `Recursos/`, las figuras de dibujo en PDF vectorial.
- [ ] Referencias nuevas contrastadas con su DOI.
