# Install FastqPuri

https://github.com/jengelmann/FastqPuri

1. Build docker image from latest GH
2. Build apptainer image from docker image
  - Use multi-exec format for executables in `/usr/local/bin`

## Build docker image
```
curl -Lo jengelmann-fastqpuri-bf88549.zip https://github.com/jengelmann/FastqPuri/archive/bf88549580ead8e8b0e620331f840e9119586a77.zip
unzip jengelmann-fastqpuri-bf88549.zip
cd FastqPuri-bf88549580ead8e8b0e620331f840e9119586a77
docker build -t fastqpuri:bf88549 .
```

## Build Apptainer image
Using the [definition file](Apptainer.def).
```
sudo -E apptainer build fastqpuri.sif Apptainer.bf88549
```

## make symlinks for executables
```
apptainer exec fastqpuri.sif ls /usr/local/bin | xargs -L1 ln -s fastqpuri.sif
```

