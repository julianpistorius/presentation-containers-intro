# Make your life (and analysis) easier with containers

Note:
Introduction

<!-- .slide: data-timing="10" -->

--

## Audience

- Are you a biologist?  <!-- .element: class="fragment" data-fragment-index="1" -->
- Have you heard of Docker?  <!-- .element: class="fragment" data-fragment-index="2" -->
- Not sure where to start?  <!-- .element: class="fragment" data-fragment-index="3" -->

<!-- .slide: data-timing="10" -->

--

### You've come to the right place!

<!-- .slide: data-timing="10" -->

--

## Me

- Software Engineer  <!-- .element: class="fragment" data-fragment-index="1" -->
- Build software infrastructure for researchers  <!-- .element: class="fragment" data-fragment-index="2" -->
- Help researchers to use computational tools  <!-- .element: class="fragment" data-fragment-index="3" -->
- Was a 'container skeptic'  <!-- .element: class="fragment" data-fragment-index="4" -->

<!-- .slide: data-timing="10" -->

--

## CyVerse

Helps researchers:  <!-- .element: class="fragment" data-fragment-index="1" -->

1. Learn about, and  <!-- .element: class="fragment" data-fragment-index="2" --> 
2. Productively use  <!-- .element: class="fragment" data-fragment-index="3" -->

New tech like containers  <!-- .element: class="fragment" data-fragment-index="4" -->

<!-- .slide: data-timing="10" -->

---

## Analysis is getting complex

- Multiple software packages (R, Python, etc.)  <!-- .element: class="fragment" data-fragment-index="1" -->
- With specific versions  <!-- .element: class="fragment" data-fragment-index="2" -->
- Have to work together  <!-- .element: class="fragment" data-fragment-index="3" -->
- On different platforms  <!-- .element: class="fragment" data-fragment-index="4" -->

<!-- .slide: data-timing="10" -->

--

## The pain

- Hard to install one-by-one   <!-- .element: class="fragment" data-fragment-index="1" -->
- Wasted effort and time  <!-- .element: class="fragment" data-fragment-index="2" -->
- Fragile, hard-to-reproduce analyses  <!-- .element: class="fragment" data-fragment-index="3" -->

<!-- .slide: data-timing="10" -->

--

## Help! Make it stop!

How we we make it easy to install & use things consistently?  <!-- .element: class="fragment" data-fragment-index="1" -->

<!-- .slide: data-timing="10" -->

--

## <span>Containers!</span> <!-- .element: class="fragment" data-fragment-index="0" --> <sup>*</sup> <!-- .element: class="fragment" data-fragment-index="2" -->

New packages & apps are increasingly available as containers (biocontainers, etc.)  <!-- .element: class="fragment" data-fragment-index="3" -->

<!-- .slide: data-timing="10" -->

---

## Concepts & Terms

Note:
- These are broad strokes

<!-- .slide: data-timing="2" -->

--

## Image

A self-contained, read-only 'snapshot' of your applications and packages, with all their dependencies

<!-- .element: class="fragment" data-fragment-index="1" -->

<!-- .slide: data-timing="10" -->

--

## Dockerfile (or Singularity recipe)

Executable instructions (script) for:  <!-- .element: class="fragment" data-fragment-index="1" -->

- Creating an image  <!-- .element: class="fragment" data-fragment-index="2" -->
- Specifing the 'entry point' for the container  <!-- .element: class="fragment" data-fragment-index="3" -->

<!-- .slide: data-timing="10" -->

--

## Container

- A 'running image'
<!-- .element: class="fragment" data-fragment-index="1" -->

Note:
The entry point is executed

<!-- .slide: data-timing="10" -->

--

## Docker

- A server (daemon): Handles life cycle of images and containers  <!-- .element: class="fragment" data-fragment-index="1" -->
- A command-line client: To tell the server what to do  <!-- .element: class="fragment" data-fragment-index="2" -->

<span>Download from: <https://www.docker.com/></span>  <!-- .element: class="fragment" data-fragment-index="3" -->

<!-- .slide: data-timing="10" -->

--

## Singularity

A way to run containers on HPC  <!-- .element: class="fragment" data-fragment-index="1" -->

Note:
- Because of computer security reasons HPC folks usually don't allow Docker
- It is easy to create Singularity images from Docker images

<!-- .slide: data-timing="10" -->

--

## What about my data?

Do not put your data in the image!  <!-- .element: class="fragment" data-fragment-index="1" -->

- Local data: 'Mount' it into a container when you start it  <!-- .element: class="fragment" data-fragment-index="2" -->
- Remote data: Pull into the container once it's running (e.g. CyVerse Data Store, S3, etc.)  <!-- .element: class="fragment" data-fragment-index="3" -->

<!-- .slide: data-timing="10" -->

--

## Compute resources

I need more!  <!-- .element: class="fragment" data-fragment-index="1" -->

Talk to us. There are a few options, and it depends on what you need.  <!-- .element: class="fragment" data-fragment-index="2" -->

<!-- .slide: data-timing="10" -->

--

## Sharing containers

Image registries  <!-- .element: class="fragment" data-fragment-index="1" -->

Note:
- Singularity Hub and Docker Hub

<!-- .slide: data-timing="10" -->

---

## Using Containers

Note:
- These are pre-recorded

<!-- .slide: data-timing="2" -->

--

## Command line app

TODO

1. Get image  <!-- .element: class="fragment" data-fragment-index="1" -->
2. Locate data  <!-- .element: class="fragment" data-fragment-index="2" -->
3. Run  <!-- .element: class="fragment" data-fragment-index="3" -->

Note:
- FastQC?

<!-- .slide: data-timing="10" -->

--

## Web app

TODO

1. Get image  <!-- .element: class="fragment" data-fragment-index="1" -->
2. Locate data  <!-- .element: class="fragment" data-fragment-index="2" -->
3. Run  <!-- .element: class="fragment" data-fragment-index="3" -->

Note:
- RStudio?
- Use output data from command line app?
- Explain local IP & port

<!-- .slide: data-timing="10" -->

--

## CyVerse support for containers

1. Command line (Atmosphere)  <!-- .element: class="fragment" data-fragment-index="1" -->
2. Interactive apps (VICE)  <!-- .element: class="fragment" data-fragment-index="2" -->
3. HPC (XSEDE & OSG) <!-- .element: class="fragment" data-fragment-index="3" -->

Note:
- ezd/ezs

<!-- .slide: data-timing="10" -->

---

## Summary

- Package your analysis pipeline in a single container  <!-- .element: class="fragment" data-fragment-index="1" -->
- Everyone in your lab can have a consistent environment  <!-- .element: class="fragment" data-fragment-index="2" -->

<!-- .slide: data-timing="10" -->

--

## Next time

- How to build containers  <!-- .element: class="fragment" data-fragment-index="1" -->
- Running on different platforms  <!-- .element: class="fragment" data-fragment-index="2" -->
- Science applications  <!-- .element: class="fragment" data-fragment-index="3" -->

<!-- .slide: data-timing="10" -->

--

## Links & references

TODO

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
- Mary Margaret Sprinkles

<!-- .slide: data-timing="10" -->

--

