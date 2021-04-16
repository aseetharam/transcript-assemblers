# Direct Evidence Pipeline Container

This image contains all the tools required to run the direct evidence pipeline. For the complete pipeline workflow, see this repo: Urmi's Snakemaker pipeline. 

## Getting Started

Pull the container:

```bash
singularity pull evidence.sif shub://aseetharam/transcript-assemblers
```

This will create a `evidence.sif` image, with the required programs pre-installed.



### Prerequisities

In order to run this container you'll need [Singularity](https://sylabs.io/guides/3.0/user-guide/installation.html) installed.

### Usage

BRAKER usage:

```
singularity run --no-home --home /opt/gm_key --cleanenv braker2.sif braker.pl --help
```

#### Environment Variables

  * `PATH` Location for all the installed tools
  * `AUGUSTUS_SCRIPTS_PATH` misc. scripts used by `augusutus`
  * `AUGUSTUS_BIN_PATH` `augustus` binaries
  * `GENEMARK_PATH` `GeneMark` scripts
  * `ALIGNMENT_TOOL_PATH` alignment programs that `braker` needs


### Example run

For running on your data:

```bash
readonly SINGULARITY_IMAGE=/path/to/braker2.sif
readonly BAM=/path/to/rnaseq.bam
readonly GENOME=/path/to/genome-masked.fasta
readonly PROT_SEQ=/path/to/mikado-proteins.faa
readonly SPECIES="unique-name"

# gffread adds `.` for strop codons, replace it with `*`
sed '/^[^>]/s/\./*/' ${PROT_SEQ} > ${PROT_SEQ##*/}.new

singularity pull braker2.sif shub://aseetharam/braker
singularity exec ${SINGULARITY_IMAGE} cp -R /usr/local/config augustus_config

env time -v singularity run \
    --no-home \
    --home /opt/gm_key \
    --cleanenv \
    --env AUGUSTUS_CONFIG_PATH=${PWD}/augustus_config \
    ${SINGULARITY_IMAGE} \
        --cores ${SLURM_JOB_CPUS_PER_NODE} \
        --species=${SPECIES} \
        --genome=${GENOME} \
        --bam=${BAM} \
        --prot_seq=${PROT_SEQ} \
        --prg=gth \
        --gth2traingenes \
        --gff3
```


## Authors

* **Nathan Weeks** - *Initial work* - [WebPage]()
* **Arun Seetharam** - *maintainer* - [WebPage]()

See also the list of [contributors](https://github.com/your/repository/contributors) who 
participated in this project.

