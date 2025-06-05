FROM mysql:8.0.33

# Use ARGs for sensitive values so they can be passed during build or runtime more securely
ARG MYSQL_ROOT_PASSWORD=vprodbpass
ARG MYSQL_DATABASE=accounts

# Set environment variables for MySQL
ENV MYSQL_ROOT_PASSWORD=${MYSQL_ROOT_PASSWORD}
ENV MYSQL_DATABASE=${MYSQL_DATABASE}

# Copy DB initialization script to proper location
COPY db_backup.sql /docker-entrypoint-initdb.d/

# Expose default MySQL port
EXPOSE 3306
