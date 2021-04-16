# Direct Evidence Pipeline Container [![https://www.singularity-hub.org/static/img/hosted-singularity--hub-%23e32929.svg](https://www.singularity-hub.org/static/img/hosted-singularity--hub-%23e32929.svg)](https://singularity-hub.org/collections/4893)

This image contains all the tools required to run the direct evidence pipeline. For the complete pipeline workflow, see this [paste some link here](). 

## Getting Started

To get the container:

```bash
singularity pull evidence.sif shub://aseetharam/transcript-assemblers
```

This will create a `evidence.sif` image, with the required programs pre-installed. All the programs required for evidence-based gene prediction are installed in this image and you can either run the pipeline by hand or use the Snakemake/Nextflow workflows to run them.


### Prerequisities

In order to run this container you'll need [Singularity](https://sylabs.io/guides/3.0/user-guide/installation.html) installed.

### Usage

Each tool has their own usage, so please check individual tools and their requirements if you are running them by hand.

```
# Transcript assemblers:
singularity run --cleanenv evidence.sif Trinity
singularity run --cleanenv evidence.sif class
singularity run --cleanenv evidence.sif strawberry
singularity run --cleanenv evidence.sif stringtie
singularity run --cleanenv evidence.sif cufflinks

# ORF predictor
singularity run --cleanenv evidence.sif TransDecoder.LongOrfs
singularity run --cleanenv evidence.sif orfipy

# Mikado-related
singularity run --cleanenv evidence.sif mikado
singularity run --cleanenv evidence.sif diamond
singularity run --cleanenv evidence.sif portcullis
singularity run --cleanenv evidence.sif samtools
singularity run --cleanenv evidence.sif prodigal
```

### Environment Variables

  * `PATH` Location for all the installed tools
  * `PYTHONDONTWRITEBYTECODE`  set to true
  * `TRINITY_HOME` to utlilites to work

## Example run

For running on your data:

```bash
will update this section later
```


## Authors

* **Arun Seetharam** - *author & maintainer* - [WebPage]()

See also the list of [contributors](https://github.com/your/repository/contributors) who 
participated in this project.

