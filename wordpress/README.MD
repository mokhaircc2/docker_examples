WordPress is a free and open-source Content Management System (CMS) built on a MySQL database with PHP processing. Thanks to its extensible plugin architecture and templating system, most of its administration can be done through the web interface. This is a reason why WordPress is a popular choice when creating different types of websites, from blogs to product pages to eCommerce sites.

Running WordPress typically involves installing a LAMP (Linux, Apache, MySQL, and PHP) or LEMP (Linux, Nginx, MySQL, and PHP) stack, which can be time-consuming. However, by using tools like Docker and Docker Compose, you can streamline the process of setting up your preferred stack and installing WordPress. Instead of installing individual components by hand, you can use images, which standardize things like libraries, configuration files, and environment variables. Then, run these images in containers, isolated processes that run on a shared operating system. Additionally, by using Compose, you can coordinate multiple containers — for example, an application and database — to communicate with one another.

Once you install Docker Engine and Compose, you can get started on your first WordPress development project. You’ll need to create a new empty project directory using the ‘make directory’ command:

**mkdir wordpress/**

Next, you can move over to your new directory using the following command: 

**cd wordpress/**

You’ll now be in your new project directory.

Now create **docker-compose.yml** file by typing the command: touch docker-compose.yml. In here you will write your code which will create two services, WordPress installation and MySQL database, including necessary ports, hostnames, and passwords.

Now that you’ve configured the YAML file, you’ll need to execute the command that will pull in all the required images and set up your WordPress project. From within your project directory on the terminal using Visual Studio Code, run the following command: 

**docker-compose up -d**

You should now see that Docker is ‘pulling’ in the MySQL and WordPress images. 

To access the wordpress installation:</b>

Since we want wordpress to be accessible outside of the container, we open port-mapping from 8080 on our host to port 80 of the container by defining it in ports field.
Because you’re installing this site locally, you’ll need to use the port indicated in your YAML file rather than the typical WordPress /install.php script. Use https://localhost:8080. You can access WordPress in a browser to complete the standard installation steps.

Access your wordpress installation with **http://localhost:8080/wp-admin/install.php**

It’s recommended that you ‘shut down and clean up’ once you’ve completed the installation as well. To do this use the followng command:

**docker compose down** 

This will stop and remove the containers, but preserves the WordPress database.
