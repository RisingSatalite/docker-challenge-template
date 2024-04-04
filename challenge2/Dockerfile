#build command, dot is needed to tell docker, the image is in same directory
#the period at the end it needed for path
#docker build -t assignment2image .

# Import node
FROM node:latest AS build

# Create a directory to work in
WORKDIR /app

# Copy the package.json and package-lock.json file
COPY package*.json ./

# Install dependencies
RUN npm install

# So install nginx here to display the html file
FROM nginx:latest

# A common place to put the html files
COPY server.js /usr/share/nginx/html

# Build the application
RUN npm run build

# Make port 8080 availble to be used
EXPOSE 8080

# Other setting needed to make port 8080 work
RUN sed -i 's/80/8080/g' /etc/nginx/conf.d/default.conf
CMD ["nginx", "-g", "daemon off;"]