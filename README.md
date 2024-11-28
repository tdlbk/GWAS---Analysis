Gwas/缺失质控
 #Git plink数据格式转化
 plink --bfile HapMap_3_r3_1 --recode --out test
 plink --file test --missing #结果生成两个文件，分别是一个个体ID上SNP缺失的信息，另一个是每个SNP在个体ID中缺失的信息。

#R.studio：读取这两个文件，然后用频率的那一列作图，将图保存为pdf输出。
indmiss<-read.table(file="plink.imiss", header=TRUE)
snpmiss<-read.table(file="plink.lmiss", header=TRUE)

pdf("histimiss.pdf") #indicates pdf format and gives title to file
hist(indmiss[,6],main="Histogram individual missingness") #selects column 6, names header of file

pdf("histlmiss.pdf")
hist(snpmiss[,5],main="Histogram SNP missingness")
dev.off() # shuts down the current device
