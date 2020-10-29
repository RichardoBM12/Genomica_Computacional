# Comandos de la Práctica 01
## Ricardo Badillo Macias

#Parte I.
**Respuesta 1:**
echo $0
bash
echo $SHELL
/bin/bash

**Respuesta 2:**
mkdir data filtered raw_data meta scripts figures archive

**Respuesta 3:**
mv filtered data/ && mv raw_data data/

**Respuesta 4:**
Se debe para tener un mejor control de todos los datos, scripts, información del proyecto bioinformático. Y tener en claro lo que se tiene en cada paso.

data : Contiene los datos, dependiendo al tipo de dato puede tener otros nombres, como genetic y spatial. Los datos geneticos pueden dividirse a su vez en mas subdirectorios como raw,filtered, genotypes,data_in,data_out de modo que los datos crudos estén en un directorio y los modificados por análisis subsecuentes en otros directorios.

meta : Es donde se puede guardar todos los metadatos, como un archivo cvs, detallando la información de cada una de las muestras.  Es posible guardar cualquier otro documento necesario para procesar los datos.

scripts: Es donde se guarda todos los scripts necesarios para correr el analisis de principio a fin. Este directorio es obligatorio. Es la carpeta más dificil de documentar.

figures: Opcionalmente, es donde puedes poner el codigo que se utilice solo para hacer figuras de una publicación dada. Es como un extracto de bin dedicado a esto.

archive: Este archivo NO se encuentra en el repositorio. Es para guardar los scripts y resultados que no se necesite más pero que es bueno no borrar por completo.

#Parte II.
**Respuesta 1:**
ls -1
-rw-r--r-- 1 ricardo ricardo 90 oct 28 17:08 delay.sh
chmod a+x delay.sh

**Respuesta 2:**
ls -1
-rwxr--r-- 1 ricardo ricardo 90 oct 28 17:08 delay.sh
./delay.sh
Despues de la Parte I. necesito un descanso de exactamente 30 segundos.

**Respuesta 3:**
El comando en delay.sh -> sleep 30
./delay.sh

**Respuesta 4:**
El comando en delay.sh -> sleep 300
./delay.sh &
htop
3742 pts/0    00:00:00 sleep
kill 3742

./delay.sh: línea 2:  3742 Terminado               sleep 300
Ya puedo continuar!
[1]+  Hecho                   ./delay.sh

#Parte III.
**Respuesta 1:**
touch meta/SarsCov-2.txt
subl meta/SarsCov-2.txt

**Respuesta 2:**
cd
cd Descargas
mv sequence.fasta sarscov2_genome.fasta
mv sequence.gff3 sarscov2_genome.gff3
mv sequence.fasta splike_c.faa
mv sequence\(1\).fasta splike_b.faa
mv sequence\(2\).fasta splike_a.faa
cd
touch Escritorio/GenomicaComputacional/rbadillo_p01/meta/SarsCov-2_Spike.txt
subl Escritorio/GenomicaComputacional/rbadillo_p01/meta/SarsCov-2_Spike.txt
mv Descargas/SRR10971381_R1.fastq.gz Descargas/SRR10971381_R2.fastq.gz Descargas/sarscov2_assembly.fasta.gz Descargas/splike_a.faa Descargas/splike_b.faa Descargas/splike_c.faa Descargas/sarscov2_genome.fasta Descargas/sarscov2_genome.gff3 Escritorio/GenomicaComputacional/rbadillo_p01/data/raw_data

#Parte IV:
**Respuesta 1:**
cd Escritorio/GenomicaComputacional/rbadillo_p01/data/filtered
ln -s /home/ricardo/Escritorio/GenomicaComputacional/rbadillo_p01/data/raw_data/splike_c.faa
ln -s /home/ricardo/Escritorio/GenomicaComputacional/rbadillo_p01/data/raw_data/splike_b.faa
ln -s /home/ricardo/Escritorio/GenomicaComputacional/rbadillo_p01/data/raw_data/splike_a.faa

**Repuesta 2:**
touch glycoproteins.faa

**Respuesta 3:**
head -1 splike_c.faa 
>pdb|6VXX|C Chain C, SARS-CoV-2 spike glycoprotein
head -1 splike_b.faa 
>pdb|6VXX|B Chain B, SARS-CoV-2 spike glycoprotein
head -1 splike_a.faa 
>pdb|6VXX|A Chain A, SARS-CoV-2 spike glycoprotein

**Respuesta 4:**
cat splike_a.faa > glycoproteins.faa  && cat splike_b.faa >> glycoproteins.faa  && cat splike_c.faa >> glycoproteins.faa

**Respuesta 5:**
mv data/raw_data/splike_c.faa data/raw_data/splike_b.faa data/raw_data/splike_a.faa archive/
Se rompieron las ligas simbolicas suaves
zless sarscov2_assembly.fasta.gz
zless SRR10971381_R1.fastq.gz
zless SRR10971381_R2.fastq.gz

**Respuesta 6:**
cat sarscov2_genome.fasta
zcat sarscov2_assembly.fasta.gz

head -3  sarscov2_genome.fasta 
>NC_045512.2 Severe acute respiratory syndrome coronavirus 2 isolate Wuhan-Hu-1, complete genome
ATTAAAGGTTTATACCTTCCCAGGTAACAAACCAACCAACTTTCGATCTCTTGTAGATCTGTTCTCTAAA
CGAACTTTAAAATCTGTGTGGCTGTCACTCGGCTGCATGCTTAGTGCACTCACGCAGTATAATTAATAAC
zcat sarscov2_assembly.fasta.gz | head -3

>NODE_1_length_264_cov_161.042781
CACAAATCTTAACACTCTTCCCTACACGACGCTCTTCCGATCTACGCCGGGCCATTCGTA
CGAACCGATACCTGTGGTAAAGGGTCCTACTGTATGGTGGTACACGAGTAGTAGCAAATG

Por mientras el archivo sarscov2_genome.fasta describe el genoma del virus, el sarsvoc2_assembly.fasta.gaz describe el genoma del virus.

**Respuesta 7:**
grep -o \> sarscov2_genome.fasta | wc -l 
1
zcat sarscov2_assembly.fasta.gz | grep -o \> | wc -l 
35

**Respuesta 8:**
zcat SRR10971381_R2.fastq.gz  | head -12
@SRR10971381.512_2
CGTGGAGTATGGCTACATACTACTTATTTGATGAGTCTGGTGAGTTTAAAGTGGCTTCACATATGTATTGTTCTTTCTACCCTCCAGATGAGGATGAAGAAGAAGGTGATTGTGAAGAAGAAGAGTTTGAGCCATCAACTCAATATGAGT
+
/FFFA/A/FFFF66FFFFFF/FF/FFFFFFFFFFFFF/AFFF6FFFA6FFFFF/FFFFFFFFFFFFFFFFFF/FF/FFFFFA/FFF/FFF/A/AFA/FFFFF/=F/F/F/AFAFF//A/AFF//FFAF/FFF=FFAFFFA/A/6=///==
@SRR10971381.556_2
TTTGTAAAAATAAAATAAAAAAAATAAAAATAATATATTAAAAAAAGATAAATAAAAAAATGAACAATTAATAAAAAAAAAAAAAAAAAAAAATTAAAAAAAAAAAAAAAAAAAATAAAAAAAAAAAAAAATAAAAAAAAAATTATAAAA
+
6AFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFFF/FFFAFFFFFF/FFA/FF=F//=FF/FFFFFFFFFFFFFA/FFFF/FF/FA//F/FFFFFFA/=FFFFF/FFFF/F=FFFAFF///FFFFA/FF/6//////=/
@SRR10971381.1428_2
AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA
+
FFFFFFFFFFFFAFFFAFFFFFF6A//F//FFF

El caracter que me puede ayudar a obtener el conteo de secuencias es @.

zless SRR10971381_R2.fastq.gz | grep @ | wc -l

130022

**Respuesta 9:**
Tanto los archivos .faa como los .fasta contienen cadenas/secuencias que hacen referencia a nucleótidos, mientras que los .faa contienen cadenas/secuencias que hacen referencia a aminoácidos. Por otro lado, los archivos .fastq hacen referencia a cadenas de nucleótidos y sus puntuaciones de calidad correspondientes (por cada cadena de nucleótidos).

Los archivos .fasta contiene secuencias que hacen referencia a nucleotidos, los .faa contiene secuencias que hacen referencia a aminoácidos. Los archivos .fastq hacen referencia a secuencias de nucleotidos y a puntuaciones de calidad.

**Respuesta 10**

less presenta la información bastante caotica, provocando que la información sea bastante complicado de entender, y dificil moverse por la misma. Debido a que muestra a linea entera y cuando sobrepasa aparece en la linea aparte.

less -S agrupa la información de forma ordenada, provocando que sea facil entender la información de la msima y facil moverse por la misma. Debido  a que permite la capacidad de navegar sin mostrar la información a parte.

**Respuesta 11**
cut -f 3 sarscov2_genome.gff3 | grep gene | wc -l
11

El campo 3 corresponde al tipo de caracteristica.

CDS es una secuencia de codificación de proteinas.
gene es una secuencia de codificaci´on del simbolo del gen primario.

