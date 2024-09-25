# GeoServer & PostgreSQL Docker Setup

This guide will help you set up GeoServer with PostgreSQL using Docker.

---

## Quick Start

### Running GeoServer

To launch GeoServer with Docker:

```bash
docker-compose up -d
```

Alternatively, you can run GeoServer manually with:

```bash
docker run -it -p5050:8080 docker.osgeo.org/geoserver:2.25.x
```

- **GeoServer URL**: [http://localhost:5050/geoserver](http://localhost:5050/geoserver)
- **User**: `admin`
- **Password**: `geoserver`

---

## Connecting GeoServer to PostgreSQL

Follow these steps to connect GeoServer with a PostgreSQL database.

### Step 1: Install and Set Up PostgreSQL

1. **Install PostgreSQL** on a server or machine that GeoServer can access.
2. **Create a PostgreSQL database** for GeoServer to use.
3. **Create a PostgreSQL user** with the necessary privileges for the database.

### Step 2: Install and Set Up GeoServer

1. Download and install GeoServer or run it in Docker (as shown above).
2. Start GeoServer and access the web interface at `http://localhost:5050/geoserver`.

### Step 3: Configure Data Store in GeoServer

1. **Log in** to the GeoServer web interface using the credentials above.
2. Navigate to **Data > Stores** from the left-hand menu.
3. Click **Add a new Store** and select **PostGIS** as the data store type (depending on your PostgreSQL version).
4. Fill in the connection details:
   - **Database**: Name of your PostgreSQL database.
   - **Host**: PostgreSQL server hostname.
   - **Port**: PostgreSQL port (usually `5432`).
   - **User**: PostgreSQL username.
   - **Password**: PostgreSQL password.
5. Click **Save** to store the connection.

### Step 4: Create a Workspace and Publish Layers

1. Navigate to **Data > Workspaces** from the left-hand menu.
2. Click **Create a new Workspace** and give it a name.
3. Go back to **Data > Stores**, select your PostgreSQL data store, and add layers to the workspace.
4. Publish the layers.

### Step 5: Test the Connection

1. Navigate to **Layer Preview** from the GeoServer web interface.
2. Select one of your layers and click **OpenLayers** (or any other preview option) to ensure the data is being served from PostgreSQL through GeoServer.

---

## Example PostGIS Configuration

Here’s an example configuration for a PostGIS data store in GeoServer:

- **Workspace**: `myworkspace`
- **Data Store**: `mypostgis`
- **Connection Parameters**:
  - **Database**: `your_database_name`
  - **Host**: `your_postgresql_host`
  - **Port**: `your_postgresql_port`
  - **User**: `your_postgresql_user`
  - **Password**: `your_postgresql_password`

---

## Best Practices

- **Security**: Always handle database connections securely. Use strong passwords and authentication mechanisms.
- **Monitoring & Backups**: Regularly monitor your database and GeoServer setup and ensure backups are in place.
- **Version Compatibility**: Ensure that the versions of PostgreSQL, PostGIS, and GeoServer you are using are compatible.

For more detailed instructions, refer to the [official GeoServer documentation](https://docs.geoserver.org/main/en/user/installation/docker.html).

---

This README provides a clear and structured guide for setting up GeoServer with PostgreSQL in a Docker environment, while also emphasizing important security and maintenance practices.
