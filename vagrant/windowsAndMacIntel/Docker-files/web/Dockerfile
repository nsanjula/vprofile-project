# Here by default we are using latest image
FROM nginx
LABEL "Project"="vprofile"
LABEL "Author"="Nisal"

# Removing the default nginx configuration files
RUN rm -rf /etc/nginx/conf.d/default.conf

# Copying our configuration into the nginx configuration directory.
COPY nginvproapp.conf /etc/nginx/conf.d/vproapp.conf