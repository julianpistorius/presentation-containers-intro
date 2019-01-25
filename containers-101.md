# Make your life (and analysis) easier with containers

<!-- .slide: data-timing="10" -->

--

## Audience

- Are you a biologist?  <!-- .element: class="fragment" data-fragment-index="1" -->
- Have you heard of Docker?  <!-- .element: class="fragment" data-fragment-index="2" -->
- Not sure where to start?  <!-- .element: class="fragment" data-fragment-index="3" -->

<!-- .slide: data-timing="20" -->

--

### You've come to the right place!

<!-- .slide: data-timing="10" -->

--

## Me

- Software Engineer  <!-- .element: class="fragment" data-fragment-index="1" -->
- Build software infrastructure for researchers  <!-- .element: class="fragment" data-fragment-index="2" -->
- Help researchers to use computational tools  <!-- .element: class="fragment" data-fragment-index="3" -->
- Was a 'container skeptic'  <!-- .element: class="fragment" data-fragment-index="4" -->

<!-- .slide: data-timing="20" -->

--

## CyVerse

Helps researchers:  <!-- .element: class="fragment" data-fragment-index="1" -->

1. Learn about, and  <!-- .element: class="fragment" data-fragment-index="2" --> 
2. Productively use  <!-- .element: class="fragment" data-fragment-index="3" -->

New tech like containers  <!-- .element: class="fragment" data-fragment-index="4" -->

<!-- .slide: data-timing="20" -->

---

## Analysis is getting complex

- Multiple software packages (R, Python, etc.)  <!-- .element: class="fragment" data-fragment-index="1" -->
- With specific versions  <!-- .element: class="fragment" data-fragment-index="2" -->
- Have to work together  <!-- .element: class="fragment" data-fragment-index="3" -->
- On different platforms  <!-- .element: class="fragment" data-fragment-index="4" -->

<!-- .slide: data-timing="30" -->

--

## The pain

- Hard to install one-by-one   <!-- .element: class="fragment" data-fragment-index="1" -->
- Wasted effort and time  <!-- .element: class="fragment" data-fragment-index="2" -->
- Fragile, hard-to-reproduce analyses  <!-- .element: class="fragment" data-fragment-index="3" -->

<!-- .slide: data-timing="30" -->

--

## Help! Make it stop!

How we we make it easy to install & use things consistently?  <!-- .element: class="fragment" data-fragment-index="1" -->

<!-- .slide: data-timing="10" -->

--

## <span>Containers!</span> <!-- .element: class="fragment" data-fragment-index="0" --> <sup>*</sup> <!-- .element: class="fragment" data-fragment-index="2" -->

New packages & apps are increasingly available as containers (BioContainers, etc.)  <!-- .element: class="fragment" data-fragment-index="3" -->

Note:
- "BioContainers is an open source and community-driven framework which provides system-agnostic executable environments for bioinformatics software. BioContainers framework allows software to be installed and executed under an isolated and controllable environment."
- There will be a webinar specifically on BioContainers in the near future

<!-- .slide: data-timing="30" -->

---

## Concepts & Terms

Note:
- These are broad strokes

<!-- .slide: data-timing="2" -->

--

## Image

A self-contained, read-only 'snapshot' of your applications and packages, with all their dependencies

<!-- .element: class="fragment" data-fragment-index="1" -->

<!-- .slide: data-timing="20" -->

--

## Dockerfile (or Singularity recipe)

Executable instructions (script) for:  <!-- .element: class="fragment" data-fragment-index="1" -->

- Creating an image  <!-- .element: class="fragment" data-fragment-index="2" -->
- Specifing the 'entry point' for the container  <!-- .element: class="fragment" data-fragment-index="3" -->

<!-- .slide: data-timing="20" -->

--

## Container

- A 'running image'
<!-- .element: class="fragment" data-fragment-index="1" -->

Note:
- The entry point is executed
- From Matt Rich's Singularity tutorial: The running container will have exactly the environment defined in the image.

<!-- .slide: data-timing="30" -->

--

## Docker

- A server (sometimes called a daemon): A program that runs in the background, and handles life cycle of images and containers  <!-- .element: class="fragment" data-fragment-index="1" -->
- A command-line client: You use it to tell the server what to do  <!-- .element: class="fragment" data-fragment-index="2" -->

<span>Download from: <https://www.docker.com/></span>  <!-- .element: class="fragment" data-fragment-index="3" -->

Note:
The reason they made a separate server and client is so that you can have the server program running on a different machine from the the client

<!-- .slide: data-timing="30" -->

--

## Singularity

A way to run containers on HPC  <!-- .element: class="fragment" data-fragment-index="1" -->

<span>Find out more: <https://www.sylabs.io/singularity/></span>  <!-- .element: class="fragment" data-fragment-index="2" -->

Note:
- Because of computer security reasons HPC folks usually don't allow Docker
- It is easy to create Singularity images from Docker images
- With Singularity there is no separate server and client

<!-- .slide: data-timing="20" -->

--

## What about my data?

Do not put your data in the image!  <!-- .element: class="fragment" data-fragment-index="1" -->

- Local data: 'Mount' it into a container when you start it  <!-- .element: class="fragment" data-fragment-index="2" -->
- Remote data: Pull into the container once it's running (e.g. CyVerse Data Store, S3, etc.)  <!-- .element: class="fragment" data-fragment-index="3" -->

Note:
- "Bind mounts" make the host's filesystem accessible inside the container.

<!-- .slide: data-timing="30" -->

--

## Compute resources

I need more!  <!-- .element: class="fragment" data-fragment-index="1" -->

Talk to us. There are a few options, and it depends on what you need.  <!-- .element: class="fragment" data-fragment-index="2" -->

<!-- .slide: data-timing="20" -->

--

## Sharing containers

Image registries  <!-- .element: class="fragment" data-fragment-index="1" -->

Note:
- Singularity Hub and Docker Hub

<!-- .slide: data-timing="20" -->

---

## Using Containers

Note:
- These are pre-recorded

<!-- .slide: data-timing="2" -->

--

## Demo: Command line app

```bash
mkdir -p ~/blast
cd ~/blast
docker pull biocontainers/blast:v2.2.31_cv2
docker run biocontainers/blast:v2.2.31_cv2 blastp -help
wget http://www.uniprot.org/uniprot/P04156.fasta
curl -O ftp://ftp.ncbi.nih.gov/\
refseq/D_rerio/mRNA_Prot/zebrafish.1.protein.faa.gz
gunzip zebrafish.1.protein.faa.gz
docker run -v $PWD:/data/ biocontainers/blast:v2.2.31_cv2 \
	makeblastdb -in zebrafish.1.protein.faa -dbtype prot
docker run -v $PWD:/data/ biocontainers/blast:v2.2.31_cv2 \
	blastp -query P04156.fasta -db zebrafish.1.protein.faa \
	-out results.txt
cat results.txt 
```

Note:
- See BioContainer Example: https://biocontainers.pro/docs/101/running-example/
- The above commands assumes that you have Docker installed

<!-- .slide: data-timing="300" -->

--

## Demo: Web app (Jupyter)

```bash
cd ~
git clone https://github.com/plyte/blastn-jupyter-docker.git
cd blastn-jupyter-docker/
docker build --tag blastn-jupyter-docker:local .
docker run -p 8888:8888 blastn-jupyter-docker:local
```

Note:
- See example: https://github.com/plyte/blastn-jupyter-docker
- Explain local IP & port

<!-- .slide: data-timing="300" -->

---

## CyVerse support for containers

1. Command line (Atmosphere)  <!-- .element: class="fragment" data-fragment-index="1" -->
2. Interactive apps (VICE)  <!-- .element: class="fragment" data-fragment-index="2" -->
3. HPC (XSEDE & OSG) <!-- .element: class="fragment" data-fragment-index="3" -->

Note:
- On Atmosphere run: `ezd` or `ezs`
- First will install Docker, the second Singularity

<!-- .slide: data-timing="60" -->

---

## Summary

- Package your analysis pipeline in a single container  <!-- .element: class="fragment" data-fragment-index="1" -->
- Everyone in your lab can have a consistent environment  <!-- .element: class="fragment" data-fragment-index="2" -->

<!-- .slide: data-timing="20" -->

--

## Next time

- How to build containers  <!-- .element: class="fragment" data-fragment-index="1" -->
- Running on different platforms  <!-- .element: class="fragment" data-fragment-index="2" -->
- Science applications  <!-- .element: class="fragment" data-fragment-index="3" -->

<!-- .slide: data-timing="20" -->

--

## Links & references

- [Docker](https://www.docker.com/)
- [Singularity](https://www.sylabs.io/singularity/)
- [Play with Docker Classroom](https://training.play-with-docker.com/)
- [Katacode - Learn Docker](https://www.katacoda.com/courses/docker/)
- [CyVerse Container Camp materials](https://cyverse-container-camp-workshop-2018.readthedocs-hosted.com/en/latest/)
- [Reproducible research with containers](http://typingducks.com/blog/reproducible_research_with_containers/)
- [Upendra's Cybercarpentry workshop notes](https://cyverse-cybercarpentry-container-workshop-2018.readthedocs-hosted.com/en/latest/)
- [Tyson Swetnam's Container Camp Presentation](https://gitpitch.com/tyson-swetnam/cc-camp)
- [Matthew Rich's Singularity workshop](https://nuitrcs.github.io/singularity-workshop/)
- [BioContainers](https://biocontainers.pro/)

<!-- .slide: data-timing="10" -->

--

## Thanks!

- Nirav Merchant
- Upendra Devisetty 
- Tyson Swetnam
- Blake Joyce
- Eric Lyons
- Ariella Gladstein
- Tina Lee
- Shelley Littin

<!-- .slide: data-timing="10" -->

--

![CyVerse Webinar](cyverse_webinar_end_slide.png "CyVerse Webinar")   <!-- .element height="100%" width="100%" style="border: 0; background: None; box-shadow: None" -->
