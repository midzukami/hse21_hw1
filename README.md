# hse21_hw1
(я делал это дз на компьютере в корпусе НИУ ВШЭ, поэтому команды, коды и то что вышло я отправляю в виде текста или скрина, так-как делать отчет сам в корпусе было долго)
Хан Андрей группа 2

1)
ln -s /usr/share/data-minor-bioinf/assembly/oil_R1.fastq
ln -s /usr/share/data-minor-bioinf/assembly/oil_R2.fastq
ln -s /usr/share/data-minor-bioinf/assembly/oilMP_S4_L001_R1_001.fastq
ln -s /usr/share/data-minor-bioinf/assembly/oilMP_S4_L001_R2_001.fastq

2)
seqtk sample -s206 oil_R1.fastq 5000000 > subR1_pair.fq
seqtk sample -s206 oil_R2.fastq 5000000 > subR2_pair.fq
seqtk sample -s206 oilMP_S4_L001_R1_001.fastq 1500000 > subMP1.fq
seqtk sample -s206 oilMP_S4_L001_R2_001.fastq 1500000 > subMP2.fq

3)
$ rm *.fastq
$ ls -1 | xargs -tI{} fastqc {}
$ mkdir fastqc_raw
$ ls *.html -1 | xargs -tI{} mv -v {} fastqc_raw
$ ls *.zip -1 | xargs -tI{} mv -v {} fastqc_raw
$ multiqc fastqc_raw -o multiqc_raw

4)
![image](https://user-images.githubusercontent.com/43177979/139143243-23acd8fd-6589-4427-9aa2-04e70952bdda.png)

5)
![image](https://user-images.githubusercontent.com/43177979/139143299-6db67543-68a1-4187-ae57-2e20d2e465b2.png)
