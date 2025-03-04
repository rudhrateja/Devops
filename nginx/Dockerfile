# Use the official Nginx image as the base
FROM nginx:latest

# Install necessary tools
RUN apt-get update && apt-get install -y unzip curl tar

# Set the GitHub URL for your tar.zip file
ARG GITHUB_TAR_ZIP_URL="https://github.com/YOUR_USERNAME/YOUR_REPO/raw/YOUR_BRANCH/nginx.tar.zip"

# Set the working directory
WORKDIR /usr/share/nginx/html

# Download, extract, and clean up
RUN curl -L $GITHUB_TAR_ZIP_URL -o nginx.tar.zip \
    && unzip nginx.tar.zip -d /tmp/nginx_files \
    && tar -xf /tmp/nginx_files/nginx.tar -C /usr/share/nginx/html \
    && rm -rf /tmp/nginx_files nginx.tar.zip

# Expose Nginx default port
EXPOSE 80

# Start Nginx server
CMD ["nginx", "-g", "daemon off;"]
