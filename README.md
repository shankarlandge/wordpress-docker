# WordPress + MySQL Docker Setup (No Dockerfile, No YAML) .

## 💡 Docker Commands

### Run MySQL Container
docker run -d \
  --name mysql-container \
  -e MYSQL_ROOT_PASSWORD=rootpass \
  -e MYSQL_DATABASE=wpdb \
  -e MYSQL_USER=wpuser \
  -e MYSQL_PASSWORD=wppassword \
  mysql:5.7

### Run WordPress Container
docker run -d \
  --name wordpress-container \
  -e WORDPRESS_DB_HOST=mysql-container:3306 \
  -e WORDPRESS_DB_NAME=wpdb \
  -e WORDPRESS_DB_USER=wpuser \
  -e WORDPRESS_DB_PASSWORD=wppassword \
  -p 80:80 \
  --link mysql-container:mysql \
  wordpress:latest

## 🌐 Access Site
http://<your-ec2-public-ip>  
