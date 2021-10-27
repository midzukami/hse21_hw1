# hse21_hw1
(я делал это дз на компьютере в корпусе НИУ ВШЭ, поэтому команды, коды и то что вышло я отправляю в виде текста или скрина, так-как делать отчет сам в корпусе было долго, поэтому вышло все плохо и некрасиво, прошу прощения)
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
mkdir fastqc
fastqc sub1.fq sub2.fq submp1.fq submp2.fq -o fastqc
mkdir multiqc
multiqc fastqc -o multiqc

4)
platanus_trim sub1.fq sub2.fq
platanus_internal_trim submp1.fq submp2.fq

rm sub*.fq

5)
mkdir fastqc_trim
ls | grep 'trimmed' | xargs -tI{} fastqc -o fastqc_trim {}
multiqc fastqc_trim/ -o multiqc_trim/

6)
platanus assemble -f sub1.fq.trimmed sub2.fq.trimmed
platanus scaffold -c out_contig.fa -IP1 sub*.fq.trimmed -OP2 submp*.fq.int_trimmed
platanus gap_close -c out_scaffold.fa -IP1 sub*.fq.trimmed -OP2 submp*.fq.int_trimmed 

rm *trimmed

7)
![image](https://user-images.githubusercontent.com/43177979/139144392-021d026b-443e-48d2-a92e-ee183cfcf44c.png)

8)
![image](https://user-images.githubusercontent.com/43177979/139144497-dcd91a21-80d8-43d3-a6d6-b64d1541cd7a.png)

9)
![image](https://user-images.githubusercontent.com/43177979/139144561-e9457d91-7ccf-4f12-972f-70605f86b546.png)

10)
![image](https://user-images.githubusercontent.com/43177979/139144949-13f37db3-bfcf-4a18-88be-6eed52656fba.png)

