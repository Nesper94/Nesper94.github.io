---
title: 'Introducción a las bases de datos biológicas'
date: 2023-10-02
date-modified: last-modified
author: Juan Camilo Arboleda Rivera
categories:
  - Bases de datos
  - Biología Computacional
  - Bioinformática
license: "CC BY-SA"
---

¿Qué son las bases de datos biológicas y cómo usarlas?

## Introducción

En la era de la información las bases datos son herramientas esenciales. Como 
su nombre lo indica, las bases de datos se encargan de almacenar de una
forma organizada montones de datos para que los usuarios de la base de datos
puedan hacer búsquedas y disponer de estos datos. En particular, las bases
de datos biológicas almacenan información biológica proveniente de
diferentes experimentos alrededor del mundo, así como literatura publicada y
análisis computacionales.

La disponibilidad de los datos procedentes de diferentes experimentos es
esencial para asegurar la transparencia en la ciencia, así como su
reproducibilidad. Además, estos datos pueden ser usados múltiples veces por
diferentes investigadores para realizar diferentes tipos de análisis que
permitan el avance de nuestro conocimiento sobre los seres vivos.

Cada base de datos se especializa en un tipo de información determinada, de
forma que existen algunas especializadas en almacenar secuencias biológicas,
otras en información taxonómica, otras en información estructural de
moléculas biológicas, otras en interacciones entre proteínas y muchas más.
Cada una de estas bases de datos maneja formatos de archivos diferentes según 
el tipo de información que maneje y sus diferentes necesidades. En esta 
práctica conoceremos algunos de los formatos más usados, como el formato 
`.fasta`, el `.gb`, el `.fastq` y el `.pdb`.

## Objetivos

1. Conocer las principales bases de datos usadas en bioinformática.
2. Conocer los principales formatos de archivos para almacenar información 
biológica.

## Bases de datos biológicas

* **NCBI**
    * **GenBank:** Base de datos primaria
    * **Sequence Read Archive (SRA):** Primaria
    * **Basic Local Alignment Search Tool (BLAST):** En realidad no es una base 
 de datos sino una herramienta de alineamiento de secuencias
    * **RefSeq:** Base de datos curada
    * **Expressed Sequence Tags (ESTs)**

* **Online Mendelian Inheritance in Man (OMIM)**
 
* **ENA**
* **Protein Data Bank (PDB)**
* **Uniprot/Swiss-Prot:** Curada
* **Protein families (Pfam)**

¡Hay muchísimas más bases de datos!

<img alt="Comic bases de datos biología" src="https://journals.plos.org/ploscompbiol/article/figure/image?size=large&id=10.1371/journal.pcbi.1005128.g001" width="600px">

## Mantenerse actualizado

Si quieren estar al día con las bases de datos biológicas, revisen la primera 
publicación de cada año de la revista [*Nucleic Acids Research*](https://academic.oup.com/nar), 
esta es dedicada a bases de datos.

## [GenBank](https://www.ncbi.nlm.nih.gov/genbank/)

Base de datos de secuencias públicas. Es una de las bases de datos más grandes 
por el hecho de ser **primaria**.

Busquemos el gen *Sonic hedgehog* en GenBank y descarguemos la información
en los formatos GenBank y FASTA y veamos la estructura interna de estos
archivos.

En [este enlace](https://www.ncbi.nlm.nih.gov/genbank/samplerecord/) puedes
encontrar la explicación detallada del formato GenBank, también conocido
como GBFF (GenBank File Format).

### El formato FASTA

Es el principal formato de archivo para almacenar secuencias biológicas
(principalmente nucleótidos y proteínas). Tiene la siguiente estructura:

```
> Mouse Pikachurin
MDLISTFSLHFLLLACSLPPGAVSLRTALRKSGKVGPPLDIKLGALNCTAFSIQWKTPKR
SGSSIIGYTVFYSEVGSDKSLRERSHNVPVGQDTLITEEVIGDLKPGTEYQVSVAAYSQT
GKGRLSFPRHVTTLSQDSCLPPAAPQQPHVLVVSDSEVALSWRPGENEGSAPIQSYSVEF
IRPDFDKSWTIIQERLQMDSMVIKGLDPDTNYQFAVKAMNAHGFSPRSWPSNTVRTLGPG
EAGSGHYGPGYITNPGVSEDDDGSEDELDLDVSFEEVKPLPATKVGNKKFSVESKKTSVS
NSVMGSRLAQPTSASLHETTVAIPPTPAQRKGKNSVAMMSRLFDMSCDETLCSADSFCVN
DYAWGGSRCHCNLGKGGEACSEDIFIQYPQFFGHSYVTFEPLKNSYQAFQVTLEFRAEAE
DGLLLYCGESEHGRGDFMSLALIRRSLHFRFNCGTGIAIIISETKIKLGAWHTVTLYRDG
LNGMLQLNNGTPVTGQSQGQYSKITFRTPLYLGGAPSAYWLVRATGTNRGFQGCVQSLSV
NGKKIDMRPWPLGKALNGADVGECSSGICDEASCIHGGTCAAIKADSYICLCPLGFRGRH
CEDAFALTIPQFRESLRSYAATPWPLEPQHYLSFTEFEITFRPDSGDGVLLYSYDTGSKD
FLSINMAAGHVEFRFDCGSGTGVLRSEAPLTLGQWHDLRVSRTAKNGILQVDKQKVVEGM
AEGGFTQIKCNTDIFIGGVPNYDDVKKNSGILHPFSGSIQKIILNDRTIHVKHDFTSGVN
VENAAHPCVGAPCAHGGSCRPRKEGYECDCPLGFEGLNCQKECGNHCLNTIIEAIEIPQF
IGRSYLTYDNPNILKRVSGSRSNAFMRFKTTAKDGLLLWRGDSPMRPNSDFISLGLRDGA
LIFSYNLGSGVASIMVNGSFSDGRWHRVKAVRDGQSGKITVDDYGARTGKSPGLMRQLNI
NGALYVGGMKEIALHTNRQYLRGLVGCISHFTLSTDYHISLVEDAVDGKNINTCGAK
```

## [SRA (Sequence Read Archive)](https://www.ncbi.nlm.nih.gov/sra)

Base de datos con secuencias en bruto.
Busquemos en esta base de datos el gen *Zelda* y descarguemos archivos en
formato FASTQ.

::: {.callout-tip}
Los archivos FASTQ pueden ser muy pesados, para evitar una descarga lenta,
podemos descargar archivos de ejemplo mucho más ligeros en [este
enlace](https://zenodo.org/records/3736457).
:::

### El formato FASTQ

El formato [FASTQ](https://en.wikipedia.org/wiki/FASTQ_format) (FASTA with 
Quality) es muy similar al FASTA pero incluye también información sobre la 
calidad de la secuencia:

[![Formato
FASTQ](https://upload.wikimedia.org/wikipedia/commons/c/cc/Formato-fastq.svg){title="Nesper94,
CC BY 4.0
&lt;https://creativecommons.org/licenses/by/4.0&gt;"}](https://commons.wikimedia.org/wiki/File:Formato-fastq.svg)

Utilizando la línea de comandos en Linux también es posible descargar
archivos FASTQ después de instalar la herramienta `SRA Toolkit`:

```bash
fastq-dump --stdout -X 2 SRR390728
```

También hay servidores que hacen sus datos disponibles mediante FTP, a ellos
podemos acceder mediante una interfaz web o también mediante una línea de 
comandos en Linux:

```bash
ftp ftp.1000genomes.ebi.ac.uk
```

## [ENA (European Nucleotide Archive)](https://www.ebi.ac.uk/ena/browser/home)

Este es un repositorio de datos similar al NCBI y que contiene información
de muchos tipos diferentes. Vayamos allí y busquemos una secuencia.

## [OMIM (Online Mendelian Inheritance in Man)](https://omim.org/)

OMIM como su nombre lo indica es una base de datos especializada en caracteres 
de **Herencia Mendeliana** en el ser humano.

## [Protein Data Bank](https://www.rcsb.org/)

Esta es una base de datos de estructuras de proteínas, muy útil en biología 
estructural y [dinámica molecular](https://youtu.be/xcMSHy3CqXA).

Vamos al [tutorial](http://pdb101.rcsb.org/learn/guide-to-understanding-pdb-data/biological-assemblies) 
y descarguemos algunos archivos.

Para visualizarlos vamos a usar el software [PyMOL](https://pymol.org/2/) que 
es Software Libre ;)

## [Uniprot](https://www.uniprot.org/)

Esta es una base de datos de proteínas, en donde se puede encontrar gran
cantidad de información asociada a ellas.

## [Interpro (Antes llamado Pfam)](https://www.ebi.ac.uk/interpro/)

Base de datos sobre análisis funcional de proteínas, su clasificación en
familias de proteínas y predicción de dominios funcionales y sitios
importantes. También se pueden encontrar alineamientos múltiples de
proteínas.

![alineamiento múltiple de proteínas](https://d3i71xaburhd42.cloudfront.net/a556ba6f4ae669b253de9a4a7cfa25f3d7b58742/4-Figure2-1.png)

Si quieres aprender más sobre bioinformática puedes seguir [este
tutorial](https://www.ebi.ac.uk/training/online/courses/bioinformatics-terrified/).
