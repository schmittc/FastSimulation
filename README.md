# create docker image

docker build -f DockerImage/Dockerfile -t fastsim:latest DockerImage

# run docker container

docker run -it --rm -v $(pwd):/scratch fastsim:latest

# inside docker

cd /scratch
mg5_aMC -f madgraph_wz.script

ln -s /opt/delphes/MinBias.pileup .
DelphesPythia8 /opt/delphes/cards/delphes_card_ATLAS_PileUp.tcl pythia_card output.root
