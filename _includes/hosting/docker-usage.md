## Using passbolt container

Passbolt requires a database backend to store the information. In this section we will be using a MariaDB database packaged as a docker container.
{% if page.passbolt_version == 'Pro' %}
  A subscription key file is also required to use Passbolt Pro. You can get the subscription key [here](https://www.passbolt.com/)
{% endif %}

### Manually run passbolt container and mariadb container

It is recommended to create a user defined network to ease the container name resolution. Using a user defined network will provide a method to access containers using their names instead ip addresses:
```bash
$ docker network create passbolt_network
```

First run the mariadb container:
```bash
$ docker run -d --name mariadb --net passbolt_network \
             -e MYSQL_ROOT_PASSWORD=<root_password> \
             -e MYSQL_DATABASE=<mariadb_database> \
             -e MYSQL_USER=<mariadb_user> \
             -e MYSQL_PASSWORD=<mariadb_password> \
             mariadb
```

Now we can run the passbolt container:
```bash
$ docker run --name passbolt{{page.docker_tag}} --net passbolt_network \
             {%- if page.passbolt_version == 'Pro' %}
             --mount type=bind,\
               source=<path_subscription>,\
               target=/var/www/passbolt/config/license \
             {% else %}
             {% endif -%}
             -p 443:443 \
             -p 80:80 \
             -e DATASOURCES_DEFAULT_HOST=mariadb \
             -e DATASOURCES_DEFAULT_PASSWORD=<mariadb_password> \
             -e DATASOURCES_DEFAULT_USERNAME=<mariadb_user> \
             -e DATASOURCES_DEFAULT_DATABASE=<mariadb_database> \
             -e APP_FULL_BASE_URL=https://mydomain.com \
             passbolt/passbolt:latest{{page.docker_tag}}
```

Note: strings between '<' and '>' are variables that the users should fill with their data.
