# Guía: vectorizar con Inkscape e incluirlo en LaTeX

Para el PASO 4 de la práctica. Escrita para **Inkscape 1.x**; los menús pueden
variar ligeramente entre versiones.

## 0. ¿Cuándo vectorizar?

| Material | ¿Vectorizar? | Formato recomendado en LaTeX |
|---|---|---|
| Logos, esquemas, diagramas, dibujos de línea | Sí | PDF vectorial |
| Boceto o escaneo de un dibujo propio | Sí (trazado) | PDF vectorial |
| Gráficas generadas con código (matplotlib, gnuplot...) | No hace falta | Exportar directamente a PDF |
| Fotografías y capturas de pantalla | No | PNG/JPG a buena resolución |

Una foto «vectorizada» pesa mucho y se ve peor. Trazar sirve para figuras de
formas y colores planos.

## 1. Vectorizar un mapa de bits (trazado)

Práctica: `00_inicio/Recursos/hdt_esquema.png` (PNG de baja resolución).

1. **Archivo → Importar** (`Ctrl+I`) y elige el PNG. Opción *Incrustar*.
2. Selecciona la imagen y abre **Camino → Vectorizar mapa de bits**
   (`Mayús+Alt+B`). En inglés: *Path → Trace Bitmap*.
3. Elige el modo según la imagen:
   - **Corte de brillo** (*Brightness cutoff*): una pasada en blanco y negro.
     Ideal para dibujos de línea y logos monocromos.
   - **Detección de bordes** (*Edge detection*): contornos finos.
   - **Cuantización de color / Múltiples pasadas** (*Color quantization / Multiple scans*):
     imágenes con pocos colores planos, como nuestro esquema.
4. Marca *Vista previa* y ajusta el umbral o el número de colores hasta que
   el resultado sea fiel. Pulsa **Aplicar**.
5. El resultado queda **encima** de la imagen original: muévelo y borra el
   mapa de bits (si no, el PDF seguirá llevando el PNG dentro).
6. **Camino → Simplificar** (`Ctrl+L`) reduce nodos; revisa con la herramienta
   de nodos (`N`).
7. **El texto no se traza bien:** escríbelo de nuevo con la herramienta de
   texto (`T`) y borra las curvas del texto trazado.
8. **Editar → Redimensionar página al contenido** (`Mayús+Ctrl+R`): elimina
   márgenes blancos y evita que la figura salga con espacio de más.

## 2. Exportar a PDF

**Archivo → Guardar una copia** (`Mayús+Ctrl+Alt+S`) → tipo **PDF**. Guarda en
`Recursos/` sin espacios en el nombre: `hdt_esquema.pdf`.

Hay dos formas de tratar el texto del dibujo:

| Opción del diálogo | Resultado |
|---|---|
| *Incrustar fuentes* o *Convertir texto en trazos* | PDF autocontenido. Se incluye con `\includegraphics`. |
| *Omitir texto en el PDF y crear archivo LaTeX* | Genera `fig.pdf` y `fig.pdf_tex`: el texto lo compone LaTeX con la fuente del documento. |

### Opción A: PDF autocontenido (la más sencilla)

```latex
\begin{figure}[H]
  \centering
  \includegraphics[width=0.85\linewidth]{hdt_esquema.pdf}
  \caption{Esquema de HDT.}
  \label{fig:hdt}
\end{figure}
```

En nuestra plantilla `\graphicspath{{Recursos/}}` está en `mistilo.sty`, así que
basta con el nombre del fichero.

### Opción B: PDF + `.pdf_tex` (texto con la fuente del documento)

```latex
\begin{figure}[H]
  \centering
  \def\svgwidth{0.85\linewidth}
  \input{Recursos/hdt_esquema.pdf_tex}
  \caption{Esquema de HDT.}
\end{figure}
```

Necesita `graphicx` y `xcolor` (ya cargados en el estilo). El `.pdf` y el
`.pdf_tex` deben estar juntos en `Recursos/`. Ventaja: las etiquetas usan la
misma tipografía que el texto y pueden contener fórmulas.

### Opción C: paquete `svg` (incluir el `.svg` directamente)

```latex
\usepackage{svg}
\includesvg[width=0.85\linewidth]{Recursos/hdt_esquema}
```

Requiere Inkscape instalado en el equipo de compilación y compilar con
`-shell-escape` (`latexmk -pdf -shell-escape main.tex`). En entornos online
suele ser más fiable exportar el PDF a mano (opciones A o B).

## 3. Exportar desde la terminal (útil para automatizar)

```bash
# PDF autocontenido
inkscape Recursos/hdt_esquema.svg --export-type=pdf \
         --export-filename=Recursos/hdt_esquema.pdf

# PDF + .pdf_tex
inkscape Recursos/hdt_esquema.svg --export-type=pdf \
         --export-filename=Recursos/hdt_esquema.pdf --export-latex
```

(En Inkscape 0.92 las opciones eran distintas: `-A` para PDF.)

## 4. Lista de comprobación

- [ ] Hay trazos reales: al ampliar al 800 % en el visor de PDF no se ven píxeles.
- [ ] Se borró el mapa de bits original antes de exportar.
- [ ] El tamaño de página se ajustó al dibujo (sin márgenes blancos).
- [ ] El texto está escrito de nuevo o incrustado como fuente.
- [ ] Nombre del fichero sin espacios ni acentos, y dentro de `Recursos/`.
- [ ] El `.svg` fuente se conserva junto al PDF para poder editarlo.

## 5. Con ayuda de la IA

- Pídele un **script de exportación por lotes** que recorra `Recursos/*.svg`.
- Pídele que **dibuje el esquema directamente en SVG o TikZ** y retócalo en
  Inkscape: es un buen punto de partida, pero revisa textos y proporciones.
- Si el trazado sale sucio, descríbele el defecto y los ajustes que has usado;
  te sugerirá modo y umbral. No puede ver tu pantalla: pega los valores reales.
