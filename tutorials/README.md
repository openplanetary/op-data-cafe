### Using Git for processing pipelines of planetary data

Github repo: https://github.com/afrigeri/mdis_data_pipeline
Abstract: [Using Git in Planetary Research](https://meetingorganizer.copernicus.org/EPSC2018/EPSC2018-1058-2.pdf)


# Docker with Mario at OpenPlanetaryDataCafe - EPSC2018

what is Docker?

Different from VirtualBox - it's more app-oriented.

Example: docker with python + jupyter

Docker works differently in GNU/Linux vs Win|Max

User interface: docker [option]

you start a virtual machine with a root account

Basic commants:
docker ps -> see current processes


Process:

  1. - you install docker
  2. - you search the docker images
  3. - there are official images - like ubuntu.  Using the official ones is safer for a newbie.
  4. - Search by tags facilitates
  5. - we docker pull debian
  6. - what images do I have locally?: docker.exe images
  7. - docker.exe run -i debian

If we want to build our image.  We have to prepare a configuration file.

Experiment:
Docker debian on MS Windows 10 machine
