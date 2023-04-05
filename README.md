# Dnd41
## Часть 1

Клеточная линия, рассматриваемая в ДЗ2 (H2), имеет недостаточное количество ChIP-seq экспериментов в рассматриваемых гистоновых метках, поэтому для этого дз будет рассматриваться Dnd41.

### Список гистоновых меток

| Гистоновая метка | Ссылка |
|------------------|--------|
|   H3K27ac          |    http://hgdownload.cse.ucsc.edu/goldenPath/hg19/encodeDCC/wgEncodeBroadHistone/wgEncodeBroadHistoneHepg2H2azStdAlnRep1.bam    |
|   H4K20me1        |    http://hgdownload.cse.ucsc.edu/goldenPath/hg19/encodeDCC/wgEncodeBroadHistone/wgEncodeBroadHistoneHepg2H3k04me1StdAlnRep1.bam    |
|   EZH2        |    http://hgdownload.cse.ucsc.edu/goldenPath/hg19/encodeDCC/wgEncodeBroadHistone/wgEncodeBroadHistoneHepg2H3k09me3AlnRep1.bam    |
|   H3K79me2        |    http://hgdownload.cse.ucsc.edu/goldenPath/hg19/encodeDCC/wgEncodeBroadHistone/wgEncodeBroadHistoneHepg2H3k4me2StdAlnRep1.bam    |
|   H3K4me3         |    http://hgdownload.cse.ucsc.edu/goldenPath/hg19/encodeDCC/wgEncodeBroadHistone/wgEncodeBroadHistoneHepg2H3k9acStdAlnRep1.bam    |
|   H3K9ac        |    http://hgdownload.cse.ucsc.edu/goldenPath/hg19/encodeDCC/wgEncodeBroadHistone/wgEncodeBroadHistoneHepg2H3k27acStdAlnRep1.bam    |
|   CTCF       |    http://hgdownload.cse.ucsc.edu/goldenPath/hg19/encodeDCC/wgEncodeBroadHistone/wgEncodeBroadHistoneHepg2H3k36me3StdAlnRep1.bam    |
|   H3K27me3       |    http://hgdownload.cse.ucsc.edu/goldenPath/hg19/encodeDCC/wgEncodeBroadHistone/wgEncodeBroadHistoneHepg2H3k79me2StdAlnRep1.bam    |
|   H3K9me3       |    http://hgdownload.cse.ucsc.edu/goldenPath/hg19/encodeDCC/wgEncodeBroadHistone/wgEncodeBroadHistoneHepg2H4k20me1StdAlnRep1.bam    |

### cellmarkfiletable.txt
[Файл](./cellmarkfiletable.txt)
Результаты
![результаты](https://drive.google.com/uc?export=view&id=1WlPH_zyFcgjpveb5BkcgiwYwG0cqvhNC)
### ChromHMM
[Папка с выдачей](./data/)
### Эпигетические типы

| Состояние | Эпигенетический тип |Встречаемость в гистоновых модификациях| Описание | 
|-----------|----------|------|----------|
|     1     |  Promoter  | Во всех, но больше всего в H3K4me3, H3K9ac, H2AFZ |Ассоциирован с TSS и CpG островками 
|     2     |  Promoter |Практически во всех, но больше всего в H3K4me3, H3K9ac, H3K27ac, H2AFZ   |  Ассоциирован с TSS, exon и CpG островками
|     3     |  Promoter | Практически во всех, но больше всего в H3K4me3, H3K9ac, H3K27ac   |  Ассоциирован с TSS2kb, exon и CpG островками 
|     4     |  Transcriptional transition |  Практически во всех, но больше всего в H3K79me2, H3K4me3 |   Располагается в гене + связан с экзонами и TES 
|     5     |  Transcribed | Практически во всех, но больше всего в H3K79me2, H3K20me1    | Располагается в гене 
|     6     |  Transcriptional transition  | Практически во всех, но слабо | Располагается в гене + связан с экзонами и TES 
|     7     |  Transcribed |   H3K79me2 |Располагается в гене |
|     8     |  Enchanser | Практически во всех, но больше всего в H3K79me2, H3K27ac   | Находится в геноме и связан с ядерной ламиной  
|     9     |  Heterochromatine |  H3K27ac   | Связан с ядерной ламиной
|    10     |   Heterochromatine |   Практически нет нигде  | Связан с ядерной ламиной     
|11 |  Heterochromatine |  -   | Связан с ядерной ламиной  и высокий процент нахождения в геноме   
|12|  Heterochromatine |   EZH2  | Связан с ядерной ламиной     
|13|  Active enhancer |   H3K27me3  | Связан с ядерной ламиной и TES    
|14|  Transcribed |   CTCF  | Связан с ядерной ламиной  и TES    
|15|  Heterochromatine |   H3K9me3  | Связан с ядерной ламиной|
 ### Пример:
   ![результаты](https://drive.google.com/uc?export=view&id=1wPTs0XbDrGHVk3S33fBs3vBNamXdwgfk)
   
### Список всех запущенных команд
```
!curl -O https://raw.githubusercontent.com/deepjavalibrary/d2l-java/master/tools/fix-colab-gpu.sh && bash fix-colab-gpu.sh
!curl -O https://raw.githubusercontent.com/deepjavalibrary/d2l-java/master/tools/colab_build.sh && bash colab_build.sh
!java --list-modules | grep "jdk.jshell"
!wget http://compbio.mit.edu/ChromHMM/ChromHMM.zip
!unzip /content/ChromHMM.zip

!wget http://hgdownload.cse.ucsc.edu/goldenPath/hg19/encodeDCC/wgEncodeBroadHistone/wgEncodeBroadHistoneDnd41H2azAlnRep1.bam -O H2AFZ.bam
!wget http://hgdownload.cse.ucsc.edu/goldenPath/hg19/encodeDCC/wgEncodeBroadHistone/wgEncodeBroadHistoneDnd41H3k27acAlnRep1.bam -O H3K27ac.bam
!wget http://hgdownload.cse.ucsc.edu/goldenPath/hg19/encodeDCC/wgEncodeBroadHistone/wgEncodeBroadHistoneDnd41H3k27me3AlnRep1.bam -O H3K27me3.bam
!wget http://hgdownload.cse.ucsc.edu/goldenPath/hg19/encodeDCC/wgEncodeBroadHistone/wgEncodeBroadHistoneDnd41H3k04me3AlnRep1.bam -O H3K4me3.bam
!wget http://hgdownload.cse.ucsc.edu/goldenPath/hg19/encodeDCC/wgEncodeBroadHistone/wgEncodeBroadHistoneDnd41H3k79me2AlnRep1.bam -O H3K79me2.bam
!wget http://hgdownload.cse.ucsc.edu/goldenPath/hg19/encodeDCC/wgEncodeBroadHistone/wgEncodeBroadHistoneDnd41H3k09acAlnRep1.bam -O H3K9ac.bam
!wget http://hgdownload.cse.ucsc.edu/goldenPath/hg19/encodeDCC/wgEncodeBroadHistone/wgEncodeBroadHistoneDnd41H3k09me3AlnRep1.bam -O H3K9me3.bam
!wget http://hgdownload.cse.ucsc.edu/goldenPath/hg19/encodeDCC/wgEncodeBroadHistone/wgEncodeBroadHistoneDnd41H4k20me1AlnRep1.bam -O H4K20me1.bam
!wget http://hgdownload.cse.ucsc.edu/goldenPath/hg19/encodeDCC/wgEncodeBroadHistone/wgEncodeBroadHistoneDnd41CtcfAlnRep1.bam -O CTCF.bam
!wget http://hgdownload.cse.ucsc.edu/goldenPath/hg19/encodeDCC/wgEncodeBroadHistone/wgEncodeBroadHistoneDnd41Ezh239875AlnRep1.bam -O EZH2.bam


!java -mx5000M -jar /content/ChromHMM/ChromHMM.jar BinarizeBam -b 200  /content/ChromHMM/CHROMSIZES/hg19.txt /content/ cellmarkfiletable.txt   binarizedData

!java -mx5000M -jar /content/ChromHMM/ChromHMM.jar LearnModel /content/binarizedData /content/data 15 hg19

!zip -r data.zip data

from google.colab import files
files.download("data.zip")
```
##  Часть 2
### Код
```

skipped = 0
new_names = {'1' : 'Promoter', '2' : 'Promoter', '3' : 'Promoter', '4' : 'Transcriptional_transition', 
             '5' : 'Transcribed', '6' : 'Transcriptional_transition', '7' : 'Transcribed', '8' : 'Enchanser', 
             '9' : 'Heterochromatine', '10' : 'Heterochromatine', '11' : 'Heterochromatine', '12' : 'Active_enhancer',
             '13' : 'Transcribed', '14' : 'Heterochromatine', '15' : 'Heterochromatine'}

with open('Dnd41_15_dense.bed') as file:
  with open('Dnd41_15_modified_dense.bed','w') as f:
    for line in file:
      if skipped == 0:
        f.write(line)
        skipped = 1
      else:
        data = line
        data = data.split('\t')
        data[3] = new_names[data[3]]
        f.write('\t'.join(data))
        
!head Dnd41_15_modified_dense.bed
```
### Результаты выполнения
![результаты](https://drive.google.com/uc?export=view&id=10_ZdQwX_uSxk3q5zQzthV30Rf5s7twgP)
Геномный браузер:
![результаты](https://drive.google.com/uc?export=view&id=1zUc708VhzTZsBEwqpEc-RUVoZYIcjWJW)