

# WordPress Docker Setup

This repository contains a Dockerized setup for running WordPress with a MySQL database using Docker Compose. The configuration allows you to easily deploy a local instance of WordPress for development or testing.

## Features
- **WordPress**: Latest version of WordPress running on PHP.
- **MySQL Database**: MySQL 5.7 database to store WordPress data.
- **Docker Compose**: Simplifies the process of setting up and linking WordPress and MySQL services.
- **Data Persistence**: Both WordPress and MySQL data are persisted through Docker volumes (`wp_data` and `db_data`).

## Prerequisites
- [Docker](https://docs.docker.com/get-docker/) installed on your machine.
- [Docker Compose](https://docs.docker.com/compose/install/) installed.

## How to Run the Project

1. **Clone the Repository**:
   Clone this repository to your local machine.
   ```bash
   git clone https://github.com/Muhammad-AbdulRehman-Aamer/wordpress-docker.git
   cd wordpress-docker
   ```

2. **Start the Containers**:
   Use Docker Compose to bring up the WordPress and MySQL containers.
   ```bash
   docker-compose up -d
   ```

   This command will:
   - Pull the necessary Docker images (`wordpress:latest` and `mysql:5.7`).
   - Create two containers: one for WordPress and one for MySQL.
   - Expose WordPress on port `8000`.

3. **Access WordPress**:
   Once the containers are running, open your web browser and go to:
   ```
   http://localhost:8000
   ```
   You'll be greeted by the WordPress setup wizard.

4. **Configure WordPress**:
   Follow the on-screen instructions to configure your WordPress site:
   - Database Name: `wordpress`
   - Username: `root`
   - Password: `password`
   - Database Host: `db`

   These values are set in the `docker-compose.yml` file and will allow WordPress to connect to the MySQL container.

5. **Stop the Containers**:
   When you're done, you can stop the containers with:
   ```bash
   docker-compose down
   ```

## Environment Variables

The `docker-compose.yml` file sets up environment variables for WordPress and MySQL containers:

- **WordPress Container**:
  - `WORDPRESS_DB_HOST`: Database host (`db:3306`).
  - `WORDPRESS_DB_USER`: MySQL root user (`root`).
  - `WORDPRESS_DB_PASSWORD`: MySQL root password (`password`).
  - `WORDPRESS_DB_NAME`: Database name (`wordpress`).

- **MySQL Container**:
  - `MYSQL_ROOT_PASSWORD`: MySQL root password (`password`).
  - `MYSQL_DATABASE`: Default database name (`wordpress`).

## Volumes

The project uses Docker volumes to persist data:

- **WordPress Data**: Stored in `./wp_data`, mapped to `/var/www/html` inside the container.
- **MySQL Data**: Stored in `./db_data`, mapped to `/var/lib/mysql` inside the container.

These volumes ensure that your WordPress content and database data persist across container restarts.

## Troubleshooting

- **Permission Issues**: If you encounter permission errors, ensure that Docker has the necessary permissions to create and access the `wp_data` and `db_data` directories.
- **MySQL Connection Error**: Double-check the database settings in the WordPress setup wizard and ensure they match the `docker-compose.yml` file.



---


