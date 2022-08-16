## 1. 需要学习slurm 作业管理系统常用指令
    sacct: 显示激活的或已完成作业或作业步的记账信息。
    sbatch：提交作业脚本使其运行。
    scancel：取消排队或运行中的作业或作业步。
    scontrol：显示或设定Slurm作业、队列、节点等状态。
    squeue：显示队列中的作业及作业步状态。
    srun：实时交互式运行并行作业，一般用于段时间测试，或者与sallcoc及sbatch结合。

## 2. fastqc质量检测
### 1. fastqc质量检测-参考指令
```shell
fastqc sample_A1_R1.fq.gz sample_A1_R2.fq.gz -o PATH_TO/01fastqc_out/ -t 4
fastqc sample_A2_R1.fq.gz sample_A2_R2.fq.gz -o PATH_TO/01fastqc_out/ -t 4
fastqc sample_A3_R1.fq.gz sample_A3_R2.fq.gz -o PATH_TO/01fastqc_out/ -t 4
fastqc sample_B1_R1.fq.gz sample_B1_R2.fq.gz -o PATH_TO/01fastqc_out/ -t 4
fastqc sample_B2_R1.fq.gz sample_B2_R2.fq.gz -o PATH_TO/01fastqc_out/ -t 4
fastqc sample_B3_R1.fq.gz sample_B3_R2.fq.gz -o PATH_TO/01fastqc_out/ -t 4
```

### 2. fastqc结果
结果有zip压缩包和html两个文件，html下载后直接打开可在网页界面查看结果，各分类说明可参考
1. 官方说明：[fastqc](https://www.bioinformatics.babraham.ac.uk/projects/fastqc/)
2. 网络解读：[简书](https://www.jianshu.com/p/fe6af418a8bc)；[知乎](https://zhuanlan.zhihu.com/p/88655260)

## 2. trimmomatic质量控制
### 1. trimmomatic质量控制-参考指令
```shell
java -jar trimmomatic-0.39.jar PE -threads 4 sample_A1_R1.fq.gz sample_A1_R2.fq.gz PATH_TO/02_trimmomatic_out/sample_A1_clean_R1.fq.gz PATH_TO/02_trimmomatic_out/sample_A1_unpaired_R1.fq.gz PATH_TO/02_trimmomatic_out/sample_A1_clean_R2.fq.gz PATH_TO/02_trimmomatic_out/sample_A1_unpaired_R2.fq.gz ILLUMINACLIP:PATH_TO_SOFTWARE/trimmomatic/TruSeq2-PE.fa:2:30:10 SLIDINGWINDOW:15:30 MINLEN:110 TRAILING:30 AVGQUAL:30
java -jar trimmomatic-0.39.jar PE -threads 4 sample_A2_R1.fq.gz sample_A2_R2.fq.gz PATH_TO/02_trimmomatic_out/sample_A2_clean_R1.fq.gz PATH_TO/02_trimmomatic_out/sample_A2_unpaired_R1.fq.gz PATH_TO/02_trimmomatic_out/sample_A2_clean_R2.fq.gz PATH_TO/02_trimmomatic_out/sample_A2_unpaired_R2.fq.gz ILLUMINACLIP:PATH_TO_SOFTWARE/trimmomatic/TruSeq2-PE.fa:2:30:10 SLIDINGWINDOW:15:30 MINLEN:110 TRAILING:30 AVGQUAL:30
java -jar trimmomatic-0.39.jar PE -threads 4 sample_A3_R1.fq.gz sample_A3_R2.fq.gz PATH_TO/02_trimmomatic_out/sample_A3_clean_R1.fq.gz PATH_TO/02_trimmomatic_out/sample_A3_unpaired_R1.fq.gz PATH_TO/02_trimmomatic_out/sample_A3_clean_R2.fq.gz PATH_TO/02_trimmomatic_out/sample_A3_unpaired_R2.fq.gz ILLUMINACLIP:PATH_TO_SOFTWARE/trimmomatic/TruSeq2-PE.fa:2:30:10 SLIDINGWINDOW:15:30 MINLEN:110 TRAILING:30 AVGQUAL:30
java -jar trimmomatic-0.39.jar PE -threads 4 sample_B1_R1.fq.gz sample_B1_R2.fq.gz PATH_TO/02_trimmomatic_out/sample_B1_clean_R1.fq.gz PATH_TO/02_trimmomatic_out/sample_B1_unpaired_R1.fq.gz PATH_TO/02_trimmomatic_out/sample_B1_clean_R2.fq.gz PATH_TO/02_trimmomatic_out/sample_B1_unpaired_R2.fq.gz ILLUMINACLIP:PATH_TO_SOFTWARE/trimmomatic/TruSeq2-PE.fa:2:30:10 SLIDINGWINDOW:15:30 MINLEN:110 TRAILING:30 AVGQUAL:30
java -jar trimmomatic-0.39.jar PE -threads 4 sample_B2_R1.fq.gz sample_B2_R2.fq.gz PATH_TO/02_trimmomatic_out/sample_B2_clean_R1.fq.gz PATH_TO/02_trimmomatic_out/sample_B2_unpaired_R1.fq.gz PATH_TO/02_trimmomatic_out/sample_B2_clean_R2.fq.gz PATH_TO/02_trimmomatic_out/sample_B2_unpaired_R2.fq.gz ILLUMINACLIP:PATH_TO_SOFTWARE/trimmomatic/TruSeq2-PE.fa:2:30:10 SLIDINGWINDOW:15:30 MINLEN:110 TRAILING:30 AVGQUAL:30
java -jar trimmomatic-0.39.jar PE -threads 4 sample_B3_R1.fq.gz sample_B3_R2.fq.gz PATH_TO/02_trimmomatic_out/sample_B3_clean_R1.fq.gz PATH_TO/02_trimmomatic_out/sample_B3_unpaired_R1.fq.gz PATH_TO/02_trimmomatic_out/sample_B3_clean_R2.fq.gz PATH_TO/02_trimmomatic_out/sample_B3_unpaired_R2.fq.gz ILLUMINACLIP:PATH_TO_SOFTWARE/trimmomatic/TruSeq2-PE.fa:2:30:10 SLIDINGWINDOW:15:30 MINLEN:110 TRAILING:30 AVGQUAL:30
```

### 2. trimmomatic结果
1. 输出文件*clean_R&.fq.gz 为质量控制后的文件
2. 出入文件*unpaired_R&.fq.gz 为质量控制中另一端被去除的单端数据（暂时不用于后续分析）

## 3. 需要手动写程序统计部分（可以通过fastqc结果也可以直接遍历gz文件）
1. 统计质量控制前后GC含量变化
2. 统计质量控制前后Q20占比
3. 统计质量控制前后Q30占比
4. 统计指控前后碱基数目，并统计占比
5. 统计指控前后reads数目，并统计占比
