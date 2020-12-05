<p align="center">
    <h1 align="center">The GodBox!</h1>
</p>


The Godbox is a devilbox inspired project fosed on advanced Laravel developer.
The Godbox is a modern and highly customisable **dockerized PHP stack** supporting full **LAMP**
and **MEAN** and running on all major platforms.  The main goal is to easily switch and combine
any version required for local development. It supports an **unlimited number of projects** for
which **vhosts**, **SSL certificates** and **DNS records** are created automatically.
**Reverse proxies** per project are supported to ensure listening server such as NodeJS can also be reached.
Email catch-all and popular development tools will be at your service as well. Configuration is not necessary, as everything is already pre-setup.

Furthermore, the Godbox provides an **identical** and **reproducible development environment** for different host operating systems.

**Requirements**

![Linux](https://raw.githubusercontent.com/cytopia/icons/master/64x64/linux.png)
![OSX](https://raw.githubusercontent.com/cytopia/icons/master/64x64/osx.png)
![Windows](https://raw.githubusercontent.com/cytopia/icons/master/64x64/windows.png)
![Plus](https://raw.githubusercontent.com/cytopia/icons/master/64x64/plus.png)
![Docker](https://raw.githubusercontent.com/cytopia/icons/master/64x64/docker.png)

* [Docker Engine 17.06.0+](https://docs.docker.com/compose/compose-file/compose-versioning/#version-23)
* [Docker Compose 1.16.0+](https://docs.docker.com/compose/compose-file/compose-versioning/#version-23)

## Architecture

#### Available Stacks

The Godbox aims to be a swiss army knife for local development by providing you all the services
you would ever need. To get an idea about the architecture behind it and to also see what's available
have a look at the following diagrams and tables.

#### Available Container

The following table lists all integrated and pre-configured Docker container shipped by the Godbox.
Only the webserver and PHP container are mandatory, all others are optional and don't need to be started.

Each of them is also available in multiple different versions in order to reflect your exact desired environment.

| Accel   | Web        | App            | SQL        | NoSQL     | Queue / Search | ELK           | Utils     |
|---------|------------|----------------|------------|-----------|----------------|---------------|-----------|
| HAProxy | Apache     | PHP            | MariaDB    | Memcached | RabbitMQ       | ElasticSearch | Bind      |
| Varnish | Nginx      | Python (Flask) | MySQL      | MongoDB   | Solr           | Logstash      | Blackfire |
|         |            |                | PerconaDB  | Redis     |                | Kibana        | MailHog   |
|         |            |                | PostgreSQL |           |                |               | Ngrok     |
|         |            |                |            |           |                |               | Jenkins     |


## Usage

#### Quick start

<table width="100%" style="width:100%; display:table;">
 <thead>
  <tr>
   <th width="50%" style="width:50%;">Linux and MacOS</th>
   <th width="50%" style="width:50%;">Windows</th>
  </tr>
 </thead>
 <tbody style="vertical-align: bottom;">
  <tr>
   <td>
<div class="highlight highlight-source-shell"><pre># Get the Godbox
git clone https://github.com/icarojobs/godbox devilbox</pre></div>
<div class="highlight highlight-source-shell"><pre># Create docker-compose environment file
cd devilbox
mkdir jenkins
mkdir dumps
cp env-example .env</pre></div>
<div class="highlight highlight-source-shell"><pre># Edit your configuration
vim .env</pre></div>
<div class="highlight highlight-source-shell"><pre># Start all container
docker-compose up</pre></div>
   </td>
   <td>
    1. Clone <code>https://github.com/icarojobs/godbox</code> to <code>C:\godbox</code> with <a href="https://git-scm.com/downloads">Git for Windows</a><br/><br/>
    2. Copy <code>C:\godbox\env-example</code> to <code>C:\godbox\.env</code><br/><br/>
    3. Edit <code>C:\godbox\.env</code><br/><br/>
    4. <a href="https://godbox.readthedocs.io/en/latest/howto/terminal/open-terminal-on-win.html">Open a terminal on Windows</a> and type:<br/><br/><br/>
    <pre># Start all container
C:\godbox> docker-compose up</pre></div>
   </td>
  </tr>
 </tbody>
</table>

#### Selective start

The above will start all containers, you can however also just start the containers you actually need. This is achieved by simply specifying them in the docker-compose command.

```bash
docker-compose up httpd php mysql redis
```

#### Run different versions

Every single attachable container comes with many different versions. In order to select the desired version for a container, simply edit the `.env` file and uncomment the version of choice. Any combination is possible.

<table>
  <thead>
    <tr>
      <th>Apache</th>
      <th>Nginx</th>
      <th>PHP</th>
      <th>MySQL</th>
      <th>MariaDB</th>
      <th>Percona</th>
      <th>PgSQL</th>
      <th>Redis</th>
      <th>Memcached</th>
      <th>MongoDB</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td><a target="_blank" title="Apache 2.2"       href="https://github.com/godbox/docker-apache-2.2">2.2</a></td>
      <td><a target="_blank" title="Nginx stable"     href="https://github.com/godbox/docker-nginx-stable">stable</a></td>
      <td><a target="_blank" title="PHP 5.2"          href="https://github.com/godbox/docker-php-fpm">5.2</a><sup>[1]</sup></td>
      <td><a target="_blank" title="MySQL 5.5"        href="https://github.com/godbox/docker-mysql">5.5</a></td>
      <td><a target="_blank" title="MariaDB 5.5"      href="https://github.com/godbox/docker-mysql">5.5</a></td>
      <td><a target="_blank" title="PerconaDB 5.5"    href="https://github.com/godbox/docker-mysql">5.5</a></td>
      <td><a target="_blank" title="PgSQL 9.0"        href="https://github.com/docker-library/postgres">9.0</a></td>
      <td><a target="_blank" title="Redis 2.8"        href="https://github.com/docker-library/redis">2.8</a></td>
      <td><a target="_blank" title="Memcached 1.4"    href="https://github.com/docker-library/memcached">1.4</a></td>
      <td><a target="_blank" title="MongoDB 2.8"      href="https://github.com/docker-library/mongo">2.8</a></td>
    </tr>
    <tr>
      <td><a target="_blank" title="Apache 2.4"       href="https://github.com/godbox/docker-apache-2.4">2.4</a></td>
      <td><a target="_blank" title="Nginx mainline"   href="https://github.com/godbox/docker-nginx-mainline">mainline</a></td>
      <td><a target="_blank" title="PHP 5.3"          href="https://github.com/godbox/docker-php-fpm">5.3</a></td>
      <td><a target="_blank" title="MySQL 5.6"        href="https://github.com/godbox/docker-mysql">5.6</a></td>
      <td><a target="_blank" title="MariaDB 10.0"     href="https://github.com/godbox/docker-mysql">10.0</a></td>
      <td><a target="_blank" title="PerconaDB 5.6"    href="https://github.com/godbox/docker-mysql">5.6</a></td>
      <td><a target="_blank" title="PgSQL 9.1"        href="https://github.com/docker-library/postgres">9.1</a></td>
      <td><a target="_blank" title="Redis 3.0"        href="https://github.com/docker-library/redis">3.0</a></td>
      <td><a target="_blank" title="Memcached 1.5"    href="https://github.com/docker-library/memcached">1.5</a></td>
      <td><a target="_blank" title="MongoDB 3.0"      href="https://github.com/docker-library/mongo">3.0</a></td>
    </tr>
    <tr>
      <td></td>
      <td></td>
      <td><a target="_blank" title="PHP 5.4"          href="https://github.com/godbox/docker-php-fpm">5.4</a></td>
      <td><a target="_blank" title="MySQL 5.7"        href="https://github.com/godbox/docker-mysql">5.7</a></td>
      <td><a target="_blank" title="MariaDB 10.1"     href="https://github.com/godbox/docker-mysql">10.1</a></td>
      <td><a target="_blank" title="PerconaDB 5.7"    href="https://github.com/godbox/docker-mysql">5.7</a></td>
      <td><a target="_blank" title="PgSQL 9.2"        href="https://github.com/docker-library/postgres">9.2</a></td>
      <td><a target="_blank" title="Redis 3.2"        href="https://github.com/docker-library/redis">3.2</a></td>
      <td><a target="_blank" title="Memcached 1.6"    href="https://github.com/docker-library/memcached">1.6</a></td>
      <td><a target="_blank" title="MongoDB 3.2"      href="https://github.com/docker-library/mongo">3.2</a></td>
    </tr>
    <tr>
      <td></td>
      <td></td>
      <td><a target="_blank" title="PHP 5.5"          href="https://github.com/godbox/docker-php-fpm">5.5</a></td>
      <td><a target="_blank" title="MySQL 8.0"        href="https://github.com/godbox/docker-mysql">8.0</a></td>
      <td><a target="_blank" title="MariaDB 10.2"     href="https://github.com/godbox/docker-mysql">10.2</a></td>
      <td><a target="_blank" title="PerconaDB 8.0"    href="https://github.com/godbox/docker-mysql">8.0</a></td>
      <td><a target="_blank" title="PgSQL 9.3"        href="https://github.com/docker-library/postgres">9.3</a></td>
      <td><a target="_blank" title="Redis 4.0"        href="https://github.com/docker-library/redis">4.0</a></td>
      <td><a target="_blank" title="Memcached latest" href="https://github.com/docker-library/memcached">latest</a></td>
      <td><a target="_blank" title="MongoDB 3.4"      href="https://github.com/docker-library/mongo">3.4</a></td>
    </tr>
    <tr>
      <td></td>
      <td></td>
      <td><a target="_blank" title="PHP 5.6"          href="https://github.com/godbox/docker-php-fpm">5.6</a></td>
      <td></td>
      <td><a target="_blank" title="MariaDB 10.3"     href="https://github.com/godbox/docker-mysql">10.3</a></td>
      <td></td>
      <td><a target="_blank" title="PgSQL 9.4"        href="https://github.com/docker-library/postgres">9.4</a></td>
      <td><a target="_blank" title="Redis 5.0"        href="https://github.com/docker-library/redis">5.0</a></td>
      <td></td>
      <td><a target="_blank" title="MongoDB 3.6"      href="https://github.com/docker-library/mongo">3.6</a></td>
    </tr>
    <tr>
      <td></td>
      <td></td>
      <td><a target="_blank" title="PHP 7.0"          href="https://github.com/godbox/docker-php-fpm">7.0</a></td>
      <td></td>
      <td><a target="_blank" title="MariaDB 10.4"     href="https://github.com/godbox/docker-mysql">10.4</a></td>
      <td></td>
      <td><a target="_blank" title="PgSQL 9.5"        href="https://github.com/docker-library/postgres">9.5</a></td>
      <td><a target="_blank" title="Redis 6.0"        href="https://github.com/docker-library/redis">6.0</a></td>
      <td></td>
      <td><a target="_blank" title="MongoDB 4.0"      href="https://github.com/docker-library/mongo">4.0</a></td>
    </tr>
    <tr>
      <td></td>
      <td></td>
      <td><a target="_blank" title="PHP 7.1"          href="https://github.com/godbox/docker-php-fpm">7.1</a></td>
      <td></td>
      <td><a target="_blank" title="MariaDB 10.5"     href="https://github.com/godbox/docker-mysql">10.5</a></td>
      <td></td>
      <td><a target="_blank" title="PgSQL 9.6"        href="https://github.com/docker-library/postgres">9.6</a></td>
      <td><a target="_blank" title="Redis latest"     href="https://github.com/docker-library/redis">latest</a></td>
      <td></td>
      <td><a target="_blank" title="MongoDB 4.2"      href="https://github.com/docker-library/mongo">4.2</a></td>
    </tr>
    <tr>
      <td></td>
      <td></td>
      <td><a target="_blank" title="PHP 7.2"          href="https://github.com/godbox/docker-php-fpm">7.2</a></td>
      <td></td>
      <td></td>
      <td></td>
      <td>...</td>
      <td></td>
      <td></td>
      <td><a target="_blank" title="MongoDB 4.4"     href="https://github.com/docker-library/mongo">4.4</a></td>
    </tr>
    <tr>
      <td></td>
      <td></td>
      <td><a target="_blank" title="PHP 7.3"          href="https://github.com/godbox/docker-php-fpm">7.3</a></td>
      <td></td>
      <td></td>
      <td></td>
      <td><a target="_blank" title="PgSQL 12.3"       href="https://github.com/docker-library/postgres">12.3</a></td>
      <td></td>
      <td></td>
      <td><a target="_blank" title="MongoDB latest"   href="https://github.com/docker-library/mongo">latest</a></td>
    </tr>
    <tr>
      <td></td>
      <td></td>
      <td><a target="_blank" title="PHP 7.4"          href="https://github.com/godbox/docker-php-fpm">7.4</a></td>
      <td></td>
      <td></td>
      <td></td>
      <td><a target="_blank" title="PgSQL 12.4"       href="https://github.com/docker-library/postgres">12.4</a></td>
      <td></td>
      <td></td>
      <td></td>
    </tr>
    <tr>
      <td></td>
      <td></td>
      <td><a target="_blank" title="PHP 8.0"          href="https://github.com/godbox/docker-php-fpm">8.0</a><sup>[2]</sup></td>
      <td></td>
      <td></td>
      <td></td>
      <td><a target="_blank" title="PgSQL 13.0"       href="https://github.com/docker-library/postgres">13.0</a></td>
      <td></td>
      <td></td>
      <td></td>
    </tr>
    <tr>
      <td></td>
      <td></td>
      <td><a target="_blank" title="PHP 8.1"          href="https://github.com/godbox/docker-php-fpm">8.1</a><sup>[2]</sup></td>
      <td></td>
      <td></td>
      <td></td>
      <td><a target="_blank" title="PgSQL latest"     href="https://github.com/docker-library/postgres">latest</a></td>
      <td></td>
      <td></td>
      <td></td>
    </tr>
  </tbody>
</table>

<small><strong><sup>[1]</sup></strong> <strong>PHP 5.2</strong> is available to use, but it is not officially supported. The Godbox intranet does not work with this version as PHP 5.2 does not support namespaces. Furthermore PHP 5.2 does only work with Apache 2.4, Nginx stable and Nginx mainline. It does not work with Apache 2.2. Use at your own risk.</small>

<small><strong><sup>[2]</sup></strong> <strong>PHP 8.0 / PHP 8.1</strong> are upcoming unreleased versions of PHP, which are directly built out of their [official git branches](https://github.com/php/php-src/) every night to assure you will leverage their latest features.</small>

#### Additional services

Additionally to the default stack, there are a variety of other services that can be easily enabled and started.

<table>
 <thead>
  <tr>
   <th>Python (Flask)</th>
   <th>Blackfire</th>
   <th>ELK</th>
   <th>MailHog</th>
   <th>Ngrok</th>
   <th>RabbitMQ</th>
   <th>Solr</th>
   <th>HAProxy</th>
   <th>Varnish</th>
  </tr>
 </thead>
 <tbody>
  <tr>
   <td><a target="_blank" title="Python 2.7   "    href="https://github.com/godbox/docker-python-flask">2.7</a></td>
   <td><a target="_blank" title="Blackfire 1.8"    href="https://github.com/blackfireio/docker">1.8</a></td>
   <td><a target="_blank" title="ELK stack"        href="https://www.docker.elastic.co">5.x.y</a></td>
   <td><a target="_blank" title="MailHog v1.0.0"   href="https://github.com/mailhog/MailHog">v1.0.0</a></td>
   <td><a target="_blank" title="Ngrok 2.x"        href="https://github.com/godbox/docker-ngrok">2.x</a></td>
   <td><a target="_blank" title="RabbitMQ 3.6"     href="https://github.com/rabbitmq/rabbitmq-server">3.6</a></td>
   <td><a target="_blank" title="Solr 5"           href="https://github.com/apache/lucene-solr">5</a></td>
   <td><a target="_blank" title="HAProxy 1.x"      href="https://github.com/godbox/docker-haproxy">1.x</a></td>
   <td><a target="_blank" title="Varnish 4"        href="https://github.com/godbox/docker-varnish">4</a></td>
  </tr>
  <tr>
   <td>...</td>
   <td>...</td>
   <td><a target="_blank" title="ELK stack"        href="https://www.docker.elastic.co">6.x.y</a></td>
   <td><a target="_blank" title="MailHog latest"   href="https://github.com/mailhog/MailHog">latest</a></td>
   <td></td>
   <td><a target="_blank" title="RabbitMQ 3.7"     href="https://github.com/rabbitmq/rabbitmq-server">3.7</a></td>
   <td><a target="_blank" title="Solr 6"           href="https://github.com/apache/lucene-solr">6</a></td>
   <td></td>
   <td><a target="_blank" title="Varnish 5"        href="https://github.com/godbox/docker-varnish">5</a></td>
  </tr>
  <tr>
   <td><a target="_blank" title="Python 3.7   "    href="https://github.com/godbox/docker-python-flask">3.7</a></td>
   <td><a target="_blank" title="Blackfire 1.18.0" href="https://github.com/blackfireio/docker">1.18.0</a></td>
   <td><a target="_blank" title="ELK stack"        href="https://www.docker.elastic.co">7.x.y</a></td>
   <td></td>
   <td></td>
   <td><a target="_blank" title="RabbitMQ latest"  href="https://github.com/rabbitmq/rabbitmq-server">latest</a></td>
   <td><a target="_blank" title="Solr 7"           href="https://github.com/apache/lucene-solr">7</a></td>
   <td></td>
   <td><a target="_blank" title="Varnish 6"        href="https://github.com/godbox/docker-varnish">6</a></td>
  </tr>
  <tr>
   <td><a target="_blank" title="Python 3.8   "    href="https://github.com/godbox/docker-python-flask">3.8</a></td>
   <td><a target="_blank" title="Blackfire latest" href="https://github.com/blackfireio/docker">latest</a></td>
   <td></td>
   <td></td>
   <td></td>
   <td></td>
   <td><a target="_blank" title="Solr latest"      href="https://github.com/apache/lucene-solr">latest</a></td>
   <td></td>
   <td><a target="_blank" title="Varnish latest"   href="https://github.com/godbox/docker-varnish">latest</a></td>
  </tr>
 </tbody>
</table>


#### Enter the container

You can also work directly inside the php container. Simply use the bundled scripts `shell.sh` (or `shell.bat` for Windows).
The `PS1` will automatically be populated with current chosen php version.
Navigate the the Godbox directory and type the below listed command:

<table width="100%" style="width:100%; display:table;">
 <thead>
  <tr>
   <th width="50%" style="width:33%;">Linux and MacOS</th>
   <th width="50%" style="width:33%;">Windows</th>
  </tr>
 </thead>
 <tbody style="vertical-align: bottom;">
  <tr>
   <td>
<div class="highlight highlight-source-shell"><pre>host> ./shell.sh
godbox@php-7.0.19 in /shared/httpd $</pre></div>
   </td>
   <td>
<div class="highlight highlight-source-shell"><pre>C:\godbox> shell.bat
godbox@php-7.0.19 in /shared/httpd $</pre></div>
   </td>
  </tr>
 </tbody>
</table>

Your projects can be found in `/shared/httpd`. DNS records are automatically available inside the php container. Also every other service will be available on `127.0.0.1` inside the php container (tricky socat port-forwarding).

## License

**[MIT License](LICENSE.md)**

Copyright (c) 2016 **[icarojobs](https://github.com/icarojobs)**
