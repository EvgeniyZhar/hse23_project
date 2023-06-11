# hse23_project
DNMT3A (DNA (cytosine-5)-methyltransferase 3A) - ДНК-метилтрансфераза, устанавливающая паттерны метилирования ДНК на ранних стадиях развития, [метилирует сайты CpG](https://www.sciencedirect.com/science/article/pii/S153561081400316X) в кодирующих областях генов, где такое метилирование может увеличить транскрипцию генов. Является основным [геном-кандидатом](https://pubmed.ncbi.nlm.nih.gov/32018205/) в качестве посредника между пренатальными воздействиями и исходами родов. Изучение данной метилтрансферазы [актуально](https://pubmed.ncbi.nlm.nih.gov/28003281/) также в связи с частотой ее мутаций в большом количестве незрелых и зрелых гематологических новообразований. Домены: PWWP_DNMT3A, ADDz_Dnmt3a

[Экспрессируется](https://www.ncbi.nlm.nih.gov/gene/1788#gene-expression) в плаценте, яичниках, селезенке и др.:
![Снимок экрана (1815)](https://github.com/EvgeniyZhar/hse23_project/assets/75982317/55dcc9eb-e358-4efd-adc8-bdbda7267d14)

Множественное белковое выравнивание каждого из 4-х гистонов (для каждого приложен один скриншот из MEGA-X, выравнивание произведено программой ClustalW):

H2A
![Снимок экрана (1816)](https://github.com/EvgeniyZhar/hse23_project/assets/75982317/2aba70c3-eb0d-42cd-a9e2-c0ae5b13b01e)

H2B
![Снимок экрана (1818)](https://github.com/EvgeniyZhar/hse23_project/assets/75982317/ebd359ff-00d4-4a27-b50f-5ec22b07ccb3)

В обоих случаях присутсвует весомое кол-во различий, но структура схожа, что говорить о схожести выполняемой функции и полиморфизме/мутациях, как причинах расхождения.

H3
![Снимок экрана (1819)](https://github.com/EvgeniyZhar/hse23_project/assets/75982317/6ad15089-1974-4957-872e-1c1995870075)

H4
![Снимок экрана (1820)](https://github.com/EvgeniyZhar/hse23_project/assets/75982317/d1e12249-9892-42d2-ae2c-b7ef580248bd)

В обоих случаях различий практически нет, так что скорее всего это один и тот же ген с немногочисленными мутациями.

Код выравнивания:
```
!blastp  -query DNMT3A.fasta  -db /mnt/storage/project_2023/proteomes/c.elegans.faa  -out AAc.elegans.blast  -outfmt 7
!blastp  -query DNMT3A.fasta  -db /mnt/storage/project_2023/proteomes/ciliate.faa  -out AAciliate.blast  -outfmt 7
!blastp  -query DNMT3A.fasta  -db /mnt/storage/project_2023/proteomes/drosophila.faa  -out AAdrosophila.blast  -outfmt 7
!blastp  -query DNMT3A.fasta  -db /mnt/storage/project_2023/proteomes/e.coli.faa  -out AAe.coli.blast  -outfmt 7
!blastp  -query DNMT3A.fasta  -db /mnt/storage/project_2023/proteomes/human.faa  -out AAhuman.blast  -outfmt 7
!blastp  -query DNMT3A.fasta  -db /mnt/storage/project_2023/proteomes/methanocaldococcus.faa  -out AAmethanocaldococcus.blast  -outfmt 7
!blastp  -query DNMT3A.fasta  -db /mnt/storage/project_2023/proteomes/mouse.faa  -out AAmouse.blast  -outfmt 7
!blastp  -query DNMT3A.fasta  -db /mnt/storage/project_2023/proteomes/thermococcus.faa  -out AAthermococcus.blast  -outfmt 7
!blastp  -query DNMT3A.fasta  -db /mnt/storage/project_2023/proteomes/tuberculosis.faa  -out AAtuberculosis.blast  -outfmt 7
!blastp  -query DNMT3A.fasta  -db /mnt/storage/project_2023/proteomes/yeast.faa  -out AAyeast.blast  -outfmt 7
!blastp  -query DNMT3A.fasta  -db /mnt/storage/project_2023/proteomes/zebrafish.faa  -out AAzebrafish.blast  -outfmt 7

!makeblastdb  -dbtype prot  -in /mnt/storage/project_2023/proteomes/zebrafish.faa  -out zebrafish.proteins
!makeblastdb  -dbtype prot  -in /mnt/storage/project_2023/proteomes/c.elegans.faa  -out c.elegans.proteins
!makeblastdb  -dbtype prot  -in /mnt/storage/project_2023/proteomes/ciliate.faa  -out ciliate.proteins
!makeblastdb  -dbtype prot  -in /mnt/storage/project_2023/proteomes/drosophila.faa  -out drosophila.proteins
!makeblastdb  -dbtype prot  -in /mnt/storage/project_2023/proteomes/e.coli.faa  -out e.coli.proteins
!makeblastdb  -dbtype prot  -in /mnt/storage/project_2023/proteomes/human.faa  -out human.proteins
!makeblastdb  -dbtype prot  -in /mnt/storage/project_2023/proteomes/methanocaldococcus.faa  -out methanocaldococcus.proteins
!makeblastdb  -dbtype prot  -in /mnt/storage/project_2023/proteomes/mouse.faa  -out mouse.proteins
!makeblastdb  -dbtype prot  -in /mnt/storage/project_2023/proteomes/thermococcus.faa  -out thermococcus.proteins
!makeblastdb  -dbtype prot  -in /mnt/storage/project_2023/proteomes/tuberculosis.faa  -out tuberculosis.proteins
!makeblastdb  -dbtype prot  -in /mnt/storage/project_2023/proteomes/yeast.faa  -out yeast.proteins

!blastp  -query H2A.fasta  -db zebrafish.proteins   -outfmt 7  >  gene_H2A_zebrafish.txt
!blastp  -query H2A.fasta  -db c.elegans.proteins   -outfmt 7  >  gene_H2A_c.elegans.txt
!blastp  -query H2A.fasta  -db ciliate.proteins   -outfmt 7  >  gene_H2A_ciliate.txt
!blastp  -query H2A.fasta  -db drosophila.proteins  -outfmt 7  >  gene_H2A_drosophila.txt
!blastp  -query H2A.fasta  -db e.coli.proteins  -outfmt 7  >  gene_H2A_e.coli.txt
!blastp  -query H2A.fasta  -db human.proteins  -outfmt 7  >  gene_H2A_human.txt
!blastp  -query H2A.fasta  -db methanocaldococcus.proteins  -outfmt 7  >  gene_H2A_methanocaldococcus.txt
!blastp  -query H2A.fasta  -db mouse.proteins  -outfmt 7  >  gene_H2A_mouse.txt
!blastp  -query H2A.fasta  -db thermococcus.proteins  -outfmt 7  >  gene_H2A_thermococcus.txt
!blastp  -query H2A.fasta  -db tuberculosis.proteins  -outfmt 7  >  gene_H2A_tuberculosis.txt
!blastp  -query H2A.fasta  -db yeast.proteins  -outfmt 7  >  gene_H2A_yeast.txt
#И для остальных с заменой названия гистона
```
![image](https://github.com/EvgeniyZhar/hse23_project/assets/75982317/83f63b52-8048-4aba-9344-28a3e620c2d0)

Тепловая карта ([ссылка](https://colab.research.google.com/drive/1MzX-WwzVnPiWVsPv5YIe-j88bysXC701?usp=sharing)):
![map](https://github.com/EvgeniyZhar/hse23_project/assets/75982317/7b4de08b-8907-4bab-9597-79a16520c3d2)

На основе полученной карты можно сделать вывод, что данный белок представлен только у позвоночных, что может указывать на их специфическую роль в эпигенетическом регулировании у более сложных организмов. В то же время при поиске дальнего гомолога для групповой части проекта выяснилось, что у более примитивных организмов есть схожие по функциям белки, имеющие подобные домены (например, pwwp), которые, однако, либо гомологичны иным белкам человека, либо исцезают по мере усложнения организмов.

[Групповой проект](https://github.com/missaline/hse23_group_project)
