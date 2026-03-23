# 1. Use Ubuntu as the base image
FROM ubuntu:22.04

# 2. Prevent interactive prompts during the build process
ENV DEBIAN_FRONTEND=noninteractive

# 3. Update repositories and install apache2, php, and net-tools
# We combine these to reduce layers and clean up the cache to save space
RUN apt-get update && apt-get install -y \
    apache2 \
    php \
    net-tools \
    && rm -rf /var/lib/apt/lists/*
# --- ADD THIS LINE HERE ---
RUN rm /var/www/html/index.html
# 4. Copy your file to the standard Ubuntu web root
COPY index.php /var/www/html/

# 5. Inform Docker that the container listens on port 80
EXPOSE 80

# 6. Start Apache in the foreground
# In Ubuntu, we use apache2ctl to handle the environment setup correctly
CMD ["apache2ctl", "-D", "FOREGROUND"]

