# Use Nginx to serve static files
FROM nginx:latest

# Copy the site into the web root
# (destination path per instructions)
COPY ./softy-pinko-front-end /var/www/html/softy-pinko-front-end

# Copy our nginx server config to replace the default site config
COPY ./softy-pinko-front-end.conf /etc/nginx/conf.d/default.conf

# (Optional/documentation) expose 9000 inside the container
EXPOSE 9000

# Nginx image already has the correct CMD/ENTRYPOINT
