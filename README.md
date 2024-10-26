# WordPress and MySQL Docker Compose Setup

This Docker Compose configuration sets up a WordPress application with a MySQL database. The configuration creates two services:

- **onu-2**: Runs the WordPress application.
- **onu-3**: Runs the MySQL database required by WordPress.

## Requirements

- Docker Engine 20.10 or later
- Docker Compose 1.29 or later

## Configuration Details

### Services

1. **WordPress (onu-2)**
   - **Image**: `wordpress`
   - **Ports**: Exposes WordPress on `8081`.
   - **Environment Variables**:
     - `WORDPRESS_DB_HOST`: Hostname of the MySQL container (`onu-3`).
     - `WORDPRESS_DB_USER`: MySQL username for WordPress (set to `root`).
     - `WORDPRESS_DB_PASSWORD`: MySQL root password (set to `onuora`).
     - `WORDPRESS_DB_NAME`: Name of the database for WordPress (`wordpress`).

2. **MySQL (onu-3)**
   - **Image**: `mysql:5.7`
   - **Environment Variables**:
     - `MYSQL_DATABASE`: Database name for WordPress (`wordpress`).
     - `MYSQL_ROOT_PASSWORD`: Root password for MySQL (set to `onuora`).
   - **Volumes**:
     - `./mysql:/var/lib/mysql`: Persists MySQL data on the host machine within the `./mysql` directory.

## Usage

### Starting the Services

To start the WordPress and MySQL services, run:

```bash
docker-compose up -d
