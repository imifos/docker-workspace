# ftkimager-3.1.1-docker

AccessData FTK Imager v3.1.1 CLI (Aug 24 2012) in Docker

Download the ftkimager tar.gz file into Dockerfile directory. (Source: https://accessdata.com/product-download/debian-and-ubuntu-x64-3-1-1)

Build:
  * ```docker build -t ftkimager .```

Test and Help:
  * ```docker run --rm ftkimager```

Convert RAW to EWF/E01
  * Input and output files must be in current directory
  * ```docker run -ti --rm -v `pwd`:`pwd` -w `pwd` ftkimager inimage.raw outimage --e01 --compress 9```
