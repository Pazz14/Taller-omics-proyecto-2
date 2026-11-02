Recreación del Análisis GWAS y Genética Cuantitativa (Ando et al., 2018)

Este repositorio contiene el código en R y la documentación correspondiente a la reproducción bioinformática del estudio de asociación de genoma completo (GWAS) publicado por Ando et al. (2018) ("Genome-wide associations for multiple pest resistances in a Northwestern United States elite spring wheat panel").

Resumen del Proyecto

El objetivo principal fue validar y reevaluar la arquitectura genética de la resistencia a tres patógenos/plagas clave en el panel de trigo de primavera del Pacífico Noroeste de EE. UU. (PNW Wheat Panel):

Mosca de Hessian (Mayetiola destructor)

Roya amarilla (Puccinia striiformis f. sp. tritici)

Mancha foliar por Septoria (Zymoseptoria tritici)

Metodología y Workflow

El análisis se estructuró en cuatro etapas clave dentro del entorno R:

1. Control de Calidad Genotípico y Fenotípico

Matriz Genotípica: 395 líneas de trigo recodificadas a formato aditivo numérico ($0, 1, 2$).

Filtros Aplicados:

Frecuencia del Alelo Menor ($\text{MAF} \ge 10\%$).

Loci/Individuos con faltantes ($\text{Missingness} \le 10\%$). Imputación de datos faltantes por la moda.

Eliminación de marcadores monomórficos.

Genotipos finales retained: 5,460 SNPs de alta calidad.

Fenotipos: Limpieza y reconstrucción de 23 rasgos fenotípicos evaluados en campo y viveros de infección.

2. Estructura Poblacional y Decaimiento del LD

PCA (Componentes Principales): Evaluación de la estratificación genética de la población (PC1 = 10.47%, PC2 = 6.41%).

LD Decay: Estimación del desequilibrio de ligamiento intracromosómico mediante suavizado LOESS ($r^2$ crítico = 0.28). Se estableció una ventana de asociación de QTLs de $\approx 5\text{ cM}$.

3. Mapeo por Asociación (GWAS)

Modelo: Modelo Lineal Mixto (LMM) incorporando la matriz de parentesco genético (Kinship) de VanRaden.

Paz Echeverría

Escuela de Ingeniería Civil en Bioinformática, Facultad de Ingeniería

Universidad de Talca — Módulo: Taller Omics (2026)

Paquete Utilizado: statgenGWAS en R.

Ajuste: Corrección por multiplicidad mediante umbral de Bonferroni ($\alpha = 0.05$).
