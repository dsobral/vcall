# Vcall
A variantcalling pipeline.

# How to run it
.Have [Docker](https://www.docker.com/get-started) installed
.Open Command Prompt
.In Command Prompt type: docker pull jpmatos/vcall:0.1.1 (or other tag)
.Config the config_docker.yaml by changing 'Dir_settings:' and 'Settings:'
.In Command Prompt write: docker run -v </your_directory/>:/mnt/share jpmatos/vcall:0.1.1 snakemake --snakefile /mnt/share/vcall-pipe.snake -p /mnt/share/repo/example_dataset/output/<your_read>.Normal_VS_Tumor_output.vcf --cores <n_of_avaliable_cores>

#Some suggestions:
If your docker is slow, try this:
.Open docker container: docker run -v </your_directory/docker_folder>:/mnt/share/ jpmatos/vcall:0.1.1
.Then type: snakemake --snakefile /mnt/share/vcall-pipe.snake -p /mnt/share/repo/example_dataset/output/<your_read>.Normal_VS_Tumor_output.vcf --cores <n_of_avaliable_cores>
This time the container will not close after the pipeline run.


still in development...