---
layout: page
title: Administrator Guide
permalink: /admin/quickstart/
---

# Installing and Configuring Your ownCloud Server

This quickstart guide provides an overview of how to get your ownCloud server
up and running with Docker. See [Manual Installation on Linux](https://doc.owncloud.com/server/admin_manual/installation/manual_installation.html) to learn how to install ownCloud manually. This
quickstart guide covers these topics:

- [Installing an ownCloud Server](#installing-the-owncloud-server)
- [Configuring an ownCloud Server](#configuring-the-owncloud-server)
  - [Enabling Localhost Connections](#enabling-localhost-connections-to-the-owncloud-server)
- [Adding a User Account](#creating-new-user-accounts)

Before getting started, we recommend these system requirements:

| Platform | Options |
| --- | --- |
| Operating System | Ubuntu 18.04 LTS |
| Database | MariaDB 10+ |
| Web server | Apache 2.4 with prefork and mod_php |
| PHP Runtime | 7.3 |

See [Software Requirements](https://doc.owncloud.com/server/admin_manual/installation/system_requirements.html)
for a full list of the supported environments.

## Installing the ownCloud Server

First you must install the ownCloud server. You can use your preferred Docker
CLI tools. The steps below use [Docker Compose](https://docs.docker.com/compose/):

1.  Create a new project directory and navigate to it:

    ```bash
    mkdir owncloud-docker-server
    ```

    ```bash
    cd owncloud-docker-server
    ```

2.  Copy `docker-compose.yml` from the GitHub repository:

    ```bash
    wget https://raw.githubusercontent.com/owncloud/docs/master/modules/admin_manual/examples/installation/docker/docker-compose.yml
    ```

3.  Create the environment configuration file:

    ```bash
    cat << EOF > .env
    OWNCLOUD_VERSION=10.3
    OWNCLOUD_DOMAIN=localhost
    ADMIN_USERNAME=admin
    ADMIN_PASSWORD=admin
    HTTP_PORT=8080
    EOF
    ```

4.  Build and start the container:

    ```bash
    docker-compose up -d
    ```

You can verify that the containers are running with the `docker-compose ps`
command. The output should look similar to the one below:

    Name                Command                       State             Ports
    __________________________________________________________________________________________
    server_db_1         /usr/bin/entrypoint/bin/s …   Up                3306/tcp
    server_owncloud_1   /usr/local/bin/entrypoint …   Up                0.0.0.0:8080->8080/tcp
    server_redis_1      /bin/s6-svscan /etc/s6        Up                6379/tcp
    -----------------------------------------------

>**Note:** It takes a few minutes for ownCloud to be fully functional.

Once the server is installed, you can configure it next.

## Configuring the ownCloud Server

ownCloud provides an automatic configuration feature to save you time.
Follow these steps:

1.  Create the database and a database user with the command below:

    ```bash
    mysql -uroot -p
    ```

2.  Enter these lines in the `MariaDB[root]>` prompt that appears:

    ```bash
    CREATE DATABASE IF NOT EXISTS owncloud;
    GRANT ALL PRIVILEGES ON owncloud.* TO 'username'@'localhost' IDENTIFIED BY 'password';
    ```

3.  Create a configuration file called `config/autoconfig.php` in your project's
    root folder and add these parameters to it:

    ```php
    <?php
    $AUTOCONFIG = [
      "dbtype"        => "mysql",
      "dbname"        => "owncloud",
      "dbuser"        => "username",
      "dbpass"        => "password",
      "dbhost"        => "localhost",
      "dbtableprefix" => "",
      "adminlogin"    => "root",
      "adminpass"     => "root-password",
      "directory"     => "/www/htdocs/owncloud/data",
    ];
    ```

>**Note:** The `autoconfig.php` file is automatically removed after the initial
configuration is applied.

### Enabling Localhost Connections to the ownCloud Server

By default, the ownCloud server is accessible under the route `/owncloud`
(e.g. https://example.com/owncloud). Follow these steps to make your ownCloud
server available on localhost as well:

1.  Edit the Alias directive in `/etc/apache2/sites-enabled/owncloud.conf` to
    alias your ownCloud directory to the Web server root:

    ```properties
    Alias / "/var/www/owncloud/"
    ```

2.  Edit the `overwrite.cli.url` parameter in
    `/var/www/owncloud/config/config.php`:

    ```php
    'overwrite.cli.url' => 'http://localhost/',
    ```

Now your users can access the ownCloud server at the server's IP address and
port `8080` on their local host machine.

Next, you can create your users' accounts so they can log in and access the
ownCloud server.

## Creating New User Accounts

To Create a new User account, follow these steps:

1.  Open your browser and point it to the ownCloud server's IP address.

2.  Go to the User's Page.

3.  Enter the new user's **Login Name** and their **E-Mail** address in the
    input fields at the top of the page and click the **[Create]** button to
    create a new user.

Once your User accounts are created, your users can access the ownCloud server
through these methods:

- [Web interface](https://doc.owncloud.com/server/user_manual/files/webgui/overview.html)
- [Desktop Client](/user/quickstart/#Connecting with the Desktop Client)
- [Android App](/user/quickstart/#connecting-to-owncloud-on-android)
- [iOS App](/user/quickstart/#connecting-to-owncloud-on-ios)

Great! Now you know how to install an ownCloud server and configure it for your
users. See the [ownCloud Documentation](https://doc.owncloud.com/server/) for
more detailed information, including how to customize your ownCloud server.
