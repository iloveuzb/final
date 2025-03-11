# Use official CentOS image as base image
FROM centos:7

# Install required packages (httpd, php, mysql, php-mysql)
RUN yum -y install httpd php mysql php-mysql tar bind-utils man man-pages mlocate sysstat && \
    yum clean all

# Enable and start httpd service
RUN systemctl enable httpd

# Create the working directory
WORKDIR /var/www/html

# Download and untar the app archive from the given URL
RUN curl -L https://aws-tc-largeobjects.s3-us-west-2.amazonaws.com/CUR-TF-200-ACACAD/studentdownload/lab-app.tgz -o lab-app.tgz && \
    tar -xzvf lab-app.tgz && \
    rm lab-app.tgz

# Change ownership of the directory to apache user
RUN chown apache:root /var/www/html/rds.conf.php

# Expose HTTP port 80
EXPOSE 80

# Start Apache when the container runs
CMD ["httpd", "-D", "FOREGROUND"]

