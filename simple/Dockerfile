FROM nginx:alpine

MAINTAINER Joe Bowman "joebowman86@gmail.com"

# Update package manager
RUN apk update

# Install software 
RUN apk add git python py-pip openssh-client

# Install mkdocs packages
RUN pip install mkdocs mkdocs-bootstrap mkdocs-bootswatch

# Make ssh dir
RUN mkdir ~/.ssh/

# Create known_hosts
RUN ssh-keyscan -H github.com > ~/.ssh/known_hosts

# Clone the mkdocs repo into the docker container
RUN git clone https://github.com/joe-bowman/jbio-cv jbio-cv

# Build mkdocs into HTML
WORKDIR jbio-cv
RUN mkdocs build

# Copy build mkdocs files into nginx document root
RUN mv -f site/* /usr/share/nginx/html/


