:construction: still in development :construction:

# Vcall

A variantcalling pipeline based on GATK 3.8.

### How to run it

1a. Use [Docker](https://www.docker.com/get-started). This is specially necessary if you want to rebuild the docker image, which basically contains a conda environment with all the necessary packages installed.

1b. Use [udocker](https://github.com/indigo-dc/udocker). This is what we're using in our servers, so this is what will be mentioned in the examples.

1c. Use [conda](https://docs.conda.io/en/latest/) directly. Create and activate a conda environment with the configuration file in vcall_conda.yml.

2a/b. Pull the docker image.
```
udocker pull jpmatos/vcall:0.2.2
udocker create --name=vcall jpmatos/vcall:0.2.2
```

2c. Create the conda environment.
```
conda env create -f vcall_conda.yml
conda activate vcall
```

3. Adjust the configuration file config.yaml by changing the appropriate variables:

5. In Command Prompt type:
```
udocker run -v </your_directory/>:/mnt/share vcall snakemake --snakefile /mnt/share/vcall-pipe.snake -p /mnt/share/repo/example_dataset/output/<analisis_to_make> --cores <n_of_avaliable_cores>
```

| Analysis_to_make:

> For comparation between Tumor and Normal reads:
```
/{your_read}.Normal_VS_Tumor_output.vcf 
```
> For Analisis of Copy-number variantes:
```
/{your_read}.my_reference.cnn
```
> For Annotation:
```
/{your_read}.exome_seq_final.vcf.gz
```
6. Then collect your output-file:
```
Output dir example:
/mnt/share/repo/example_dataset/output/T.vcf
```

Caution: you cannot use the same container several times simultaneously. 
If you're going to run several times the same image, you need to run each in their own separate container:
```
udocker run -v </your_directory/>:/mnt/share jpmatos/vcall:0.2.2 snakemake --snakefile /mnt/share/vcall-pipe.snake -p /mnt/share/repo/example_dataset/output/<analisis_to_make> --cores <n_of_avaliable_cores>
```


:warning: still in development :construction:

