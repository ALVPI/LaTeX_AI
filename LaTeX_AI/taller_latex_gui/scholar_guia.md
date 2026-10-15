# Guía: de Google Scholar a `refs.bib`

Guía para el PASO 2 de la práctica. Usamos artículos reales de profesorado e
investigadores de la Universidad de Valladolid.

## 1. Referencias de partida (ya verificadas)

| Clave | Referencia | Dónde comprobarla |
|---|---|---|
| `gonzalez2011trasgo` | A. González-Escribano y D. R. Llanos, «Trasgo: a nested-parallel programming system», *The Journal of Supercomputing*, 58(2), pp. 226–234, 2011. DOI `10.1007/s11227-009-0367-5` | https://uvadoc.uva.es/handle/10324/70438 (acceso abierto) |
| `fernandez2013hdt` | J. D. Fernández, M. A. Martínez-Prieto, C. Gutiérrez, A. Polleres y M. Arias, «Binary RDF representation for publication and exchange (HDT)», *Journal of Web Semantics*, 19, pp. 22–41, 2013. DOI `10.1016/j.websem.2013.01.002` | https://portaldelaciencia.uva.es/documentos/61a1fe60bd93e62bb60215bd |

Para saber más del profesorado: grupo de investigación Trasgo
(https://trasgo.infor.uva.es/), fundado por Arturo González-Escribano y
Diego R. Llanos, del Departamento de Informática de la UVa.

## 2. Procedimiento con Google Scholar (demostración)

1. Entra en https://scholar.google.com y busca el título **entre comillas**:
   `"Trasgo: a nested-parallel programming system"`.
2. Debajo del resultado correcto pulsa **Citar** (icono de comillas).
3. En la ventana, al final, pulsa **BibTeX**. Se abre texto plano.
4. Copia el contenido en `bib/refs.bib`.
5. **Revísalo antes de usarlo** (siguiente apartado). Scholar es cómodo, pero
   no es una fuente fiable de metadatos.

## 3. Lista de comprobación: lo que Scholar suele hacer mal

| Problema habitual | Qué hacer |
|---|---|
| Falta el campo `doi` | Añádelo desde la página del editor o de UVaDOC. |
| Mayúsculas perdidas en el título (`rdf`, `hdt`) | Protégelas con llaves: `{RDF}`, `{HDT}`. |
| Tipo de entrada incorrecto (`@article` vs `@inproceedings`) | Compáralo con la página del editor. |
| Faltan `volume`, `number` o `pages` | Complétalos con la fuente oficial. |
| Clave poco descriptiva o duplicada | Renómbrala: `primerAutor + año + palabra`. |
| Varias versiones del mismo trabajo (preprint, congreso, revista) | Cita la versión publicada que realmente uses. |
| Autores abreviados o con `others` | Sustituye por la lista completa si la conoces. |

Regla de oro: **todo dato que no puedas contrastar con el DOI o con la página
del editor, se marca y se revisa**.

## 4. Reto (para los equipos que vayan rápido)

Obtén desde Scholar la entrada BibTeX del artículo de Fresno, González-Escribano
y Llanos *«Blending Extensibility and Performance in Dense and Sparse Parallel
Data Management»* (*IEEE Transactions on Parallel and Distributed Systems*),
listado en la web de publicaciones de Javier Fresno
(https://www.infor.uva.es/~jfresno/publications.php).

Esta entrada **no está contrastada en el material**: año, volumen y páginas
hay que sacarlos de Scholar y comprobarlos con el DOI. Es justo el ejercicio.

Después, pide a la IA que te la limpie con el prompt de `prompts_ia.md`
(sección «Referencias») y compara el resultado con tu revisión manual.
