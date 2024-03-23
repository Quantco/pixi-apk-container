# pixi-apko-container

A container image for Pixi, built with [Apko](https://github.com/chainguard-dev/apko). Using Apko brings many benefits:

- Fully reproducible by default. Run apko twice and you will get exactly the same binary.
- Fast. apko aims to build images in ms.
- Small. apko generated images only contain what's needed by the application, in the style of distroless.
- SBOM Support. apko produces a Software Bill of Materials (SBOM) for images, detailing all the packages inside.

## Getting Started

1. Install Apko (see documentation [here](https://github.com/chainguard-dev/apko?tab=readme-ov-file#installation)).
1. Build the tarball: `apko build pixi.yaml pixi:latest pixi.tar`
1. Check the size of the tarball: `ls -lh pixi.tar`
1. Check the checksum of the tarball: `shasum -a 256 pixi.tar`
1. Load the tarball into your container runtime: `docker load < pixi.tar`
1. Test the container: `docker run pixi:latest-"$(arch)" -c 'pixi --version'`
