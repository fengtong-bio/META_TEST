```shell
mamba create -n drep_tmp -y -c conda-forge -c bioconda python=3.10 mamba drep=3.4.3 fastani

conda activate PATHTO/drep
pip install  drep -i https://pypi.tuna.tsinghua.edu.cn/simple
mamba install hmmer pplacer -y
pip3 install checkm-genome  -i https://pypi.tuna.tsinghua.edu.cn/simple

cd PATHTO/checkm_database
wget -c https://data.ace.uq.edu.au/public/CheckM_databases/checkm_data_2015_01_16.tar.gz
tar -xvf *.tar.gz
checkm data setRoot PATHTO/checkm_database
dRep check_dependencies
```
################################################################################################################################
```shell
export PATH=PATHTO/drep_tmp/bin:$PATH
cd PATHTO/06drep
rm -rf bin_fa
checkm lineage_wf -t 128 -x fa --tab_table -f bins_qa.txt PATHTO/06drep/XXX_all_bin checkm_out
cp bins_qa.txt bins_qa_copy.txt
sed -i 's/ /_/g' bins_qa_copy.txt
rm -rf XXX_checkm_bin_fa
mkdir XXX_checkm_bin_fa
awk '{if ($12 >= 80 && $13 <= 10) print "cp PATHTO/06drep/XXX_all_bin/" $1 ".fa XXX_checkm_bin_fa/"}' bins_qa_copy.txt |bash

dRep dereplicate --ignoreGenomeQuality XXX_drep_out_99 -g XXX_checkm_bin_fa/*fa -sa 0.99 -p 128
dRep dereplicate --ignoreGenomeQuality XXX_drep_out_95 -g XXX_checkm_bin_fa/*fa -sa 0.95 -p 128
```
