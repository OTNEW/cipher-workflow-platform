Bootstrap: docker
From: bioconductor/release_core2

%labels
Maintainer cag104@ucsd.edu
Version 1.0

%environment
export PATH="/opt/anaconda2/bin:$PATH"

%post

	apt-get update

	apt-get install -y wget
	
	R --slave -e "source('https://bioconductor.org/biocLite.R'); \
		      biocLite('ChIPQC')"

	R --slave -e "source('https://bioconductor.org/biocLite.R'); \
                      biocLite('groHMM')"

	R --slave -e "source('https://bioconductor.org/biocLite.R'); \
                      biocLite('RUVSeq')"

	R --slave -e "source('https://bioconductor.org/biocLite.R'); \
                      biocLite('edgeR')"

	R --slave -e "source('https://bioconductor.org/biocLite.R'); \
                      biocLite('DESeq2')"

	R --slave -e "source('https://bioconductor.org/biocLite.R'); \
                      biocLite('ChIPseeker')"

	R --slave -e 'install.packages(c("ggplot2", "data.table", "RColorBrewer"), repos="https://cloud.r-project.org/")'

	R --slave -e 'install.packages("http://hartleys.github.io/QoRTs/QoRTs_LATEST.tar.gz", repos=NULL, type="source")'

	wget https://repo.continuum.io/archive/Anaconda2-4.4.0-Linux-x86_64.sh
	bash Anaconda2-4.4.0-Linux-x86_64.sh -b -p /opt/anaconda2

	/opt/anaconda2/bin/conda install -c bioconda --yes bbmap samtools epic sambamba deeptools macs2 bedtools bedops multiqc subread stringtie nextflow bowtie2 bwa hisat2 star fastqc gimmemotifs preseq