# Glosario rápido de la práctica

Para quien empieza a modificar los ejemplos. Los comandos aparecen en
`monolito.tex` y en `01_solucion/`.

## Estructura del documento

| Comando | Qué hace |
|---|---|
| `\documentclass{...}` | Elige el tipo de documento (`article`, `report`...). |
| `\usepackage{...}` | Carga un paquete que añade funciones. |
| `\begin{document}` / `\end{document}` | Delimitan lo que se imprime. |
| `\include{fichero}` | Inserta otro `.tex` en página nueva (sin escribir `.tex`). |
| `\input{fichero}` | Inserta otro `.tex` tal cual, sin salto de página. |

## Texto y secciones

| Comando | Qué hace |
|---|---|
| `\section{..}`, `\subsection{..}` | Crean secciones y subsecciones numeradas. |
| `\emph{..}`, `\textbf{..}` | Cursiva de énfasis y negrita. |
| `~` | Espacio que no permite salto de línea (`sección~2`). |
| `%` | Comentario: LaTeX ignora el resto de la línea. |

## Referencias cruzadas y citas

| Comando | Qué hace |
|---|---|
| `\label{etiqueta}` | Pone un nombre a una sección, figura o tabla. |
| `\ref{etiqueta}` | Escribe el número de lo etiquetado. |
| `\cite{clave}` | Inserta una cita; la clave está en `refs.bib`. |
| `\printbibliography` | Imprime la lista de referencias citadas. |

## Figuras, tablas y cajas

| Comando | Qué hace |
|---|---|
| `\begin{figure}[H]` | Figura numerada colocada justo aquí. |
| `\includegraphics[width=..]{f}` | Inserta la imagen `f` (busca en `Recursos/`). |
| `\caption{..}` | Pie de figura o de tabla. |
| `\begin{tabular}{lll}` | Tabla de tres columnas; `&` separa, `\\` termina fila. |
| `\toprule` `\midrule` `\bottomrule` | Líneas horizontales de `booktabs`. |
| `\begin{aviso}...\end{aviso}` | Caja de aviso definida en `mistilo.sty`. |

## Del estilo (`mistilo.sty`)

| Comando | Qué hace |
|---|---|
| `\definecolor{nombre}{HTML}{RRGGBB}` | Crea un color con nombre. |
| `\color{nombre}` | Aplica ese color al texto que sigue. |
| `\titulodoc`, `\autordoc`, `\titulacion`, `\mencion` | Rellenan los datos de la portada. |
| `\makeportada` | Dibuja la portada con esos datos. |

## Para tu bibliografía

| Término | Significado |
|---|---|
| Clave | Nombre corto de la referencia; lo que va dentro de `\cite{}`. |
| Campo | Dato de la entrada (`author`, `title`, `year`, `doi`...). |
| `and` | Separa autores en el campo `author`. |
| `{RDF}` | Las llaves protegen las mayúsculas del título. |
| `biber` | Programa que procesa el `.bib` (se ejecuta entre dos pasadas). |
