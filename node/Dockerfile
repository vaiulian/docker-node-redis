# Set the base image to Ubuntu
FROM ubuntu:trusty

# Install Node.js and other dependencies
RUN apt-get update && \
    apt-get -y install curl && \
    curl -sL https://deb.nodesource.com/setup_4.x | sudo bash - && \
    apt-get -y install python build-essential nodejs

# Install nodemon
RUN npm install -g nodemon

# Create App directory & copy package.json to it
RUN mkdir -p /src
ADD package.json /src

# Define working directory
WORKDIR /src

# Install dependencies
RUN npm install

# Expose port
EXPOSE  8080

# Run app using nodemon
CMD ["nodemon", "-L", "/src/index.js"]