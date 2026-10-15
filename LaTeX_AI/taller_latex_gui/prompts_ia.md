# Prompts para la práctica

Fórmula de un buen prompt: **rol + fichero + cambio exacto + qué NO tocar + formato de salida**.
Pega siempre el fragmento real; no se lo describas de memoria.

---

## PASO 1 · Modularizar

**Prompt**

```text
Actúa como experto en LaTeX. Te paso un documento monolítico [PEGAR monolito.tex].
Es la plantilla de entregables de la UVa. Quiero dividirla así:
- styles/mistilo.sty: todo el preámbulo que sea diseño (paquetes, márgenes, colores).
- capitulos/01_intro.tex y capitulos/02_datos.tex: solo el contenido de cada sección.
- Un comando \makeportada en el .sty, con \titulodoc, \autordoc, \titulacion
  y \mencion para rellenar los datos desde main.tex.
- Las imágenes en la carpeta Recursos/ usando \graphicspath.
- main.tex: documentclass, idioma, datos del documento e \include de las secciones.
Dame cada fichero por separado, indicando su ruta. No cambies el texto de los
capítulos ni inventes paquetes.
```

**Qué revisar**
- ¿Las secciones contienen `\usepackage`? No deberían.
- ¿Aparece `\documentclass` fuera de `main.tex`? Error.
- ¿Compila? Si no, pasa al prompt de depuración (abajo).

---

## PASO 2 · Bibliografía

**Prompt A: convertir la bibliografía manual**

```text
Convierte esta bibliografía escrita con thebibliography en un fichero .bib
válido para biblatex [PEGAR bloque thebibliography]. Conserva las claves
exactas de \bibitem. Si te falta un dato (DOI, número), déjalo fuera y
dímelo en una lista aparte. No inventes ningún campo.
```

**Prompt B: limpiar una entrada de Google Scholar** (para el reto)

```text
Esta entrada BibTeX viene de Google Scholar [PEGAR]. Revísala para biblatex:
protege con llaves las siglas del título, usa la clave autorAño+palabra y
dime qué campos faltan. NO completes datos que no estén en la entrada:
márcalos como «por verificar».
```

**Qué revisar**
- Comprueba cada referencia con su **DOI** o la página del editor.
- Las IA pueden inventar referencias verosímiles. La verificación es tuya.
- Cambia `style=ieee` por `style=apa` en `main.tex` y observa que el texto no se toca.

---

## PASO 3 · Estilos y templates

**Prompt A: sustituir las cajas a mano**

```text
Tengo este estilo [PEGAR mistilo.sty] y este capítulo [PEGAR 01_intro.tex].
Cambia únicamente el entorno "aviso" para que el borde izquierdo sea de 4 pt
en azul marino y el título esté en versalitas. Mantén compatibilidad con los
usos actuales \begin{aviso}...\end{aviso}. No modifiques nada más.
Devuélveme solo el bloque \newtcolorbox modificado.
```

**Prompt B: convertir el estilo en plantilla**

```text
Convierte este preámbulo [PEGAR] en una clase miclase.cls basada en report,
con portada, cabeceras y el color de acento como opción de clase
(\documentclass[acento=verde]{miclase}). Explícame qué opciones expone.
```

**Prompt B2: cabeceras y títulos profesionales**

```text
Este es mi mistilo.sty [PEGAR]. Mejora SOLO la parte de cabeceras y títulos:
cabecera con el título corto a la izquierda y la sección actual a la derecha,
filete fino en color acento y títulos de sección con filete inferior.
Usa fancyhdr y titlesec. No cambies la paleta ni el resto de paquetes.
```

**Prompt C: tabla**

```text
Pasa esta tabla [PEGAR] de \hline a booktabs, con cabecera de fondo
acento!10, sin líneas verticales y espaciado cómodo.
Indica qué paquetes extra necesita.
```

---

## PASO 4 · Figuras vectoriales

```text
Tengo un fichero Recursos/hdt_esquema.svg. Dame un script bash que exporte
todos los .svg de Recursos/ a PDF con Inkscape 1.x (--export-type=pdf) y
explícame cómo incluirlos en LaTeX con \includegraphics. No uses opciones
que no existan en Inkscape 1.x.
```

Revisa: que la IA no mezcle opciones de Inkscape 0.92 y 1.x, y que el PDF
resultante sea vectorial (zoom al 800 %).

---

## Depuración (cuando algo no compila)

```text
Error de compilación: [PEGAR la primera línea que empieza por «!»]
Fragmento del fichero [NOMBRE]: [PEGAR ~20 líneas alrededor]
Dame la causa raíz y solo la corrección puntual. No reescribas el fichero.
```

---

## Reglas para la sala

1. Un cambio por prompt; compila después de cada uno.
2. Pega el código real, no lo describas.
3. Si la IA propone un paquete que no conoces, búscalo en CTAN antes de usarlo.
4. Si la IA toca ficheros que no pediste, rechaza el cambio.
