Running WordPress websites can involve using a wide number of configurations and software dependencies to produce high-quality products.  Docker is a tool that offers a solution for a quicker and smoother WordPress setup locally without running so many different software packages on your own machine.

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

Because you’re installing this site locally, you’ll need to use the port indicated in your YAML file rather than the typical WordPress /install.php script. Since we’re using Docker Desktop for Mac in our example, we’ll use https://localhost as the IP address and open port https://localhost:8080. This was the port designated in the YAML file. You can access WordPress in a browser to complete the standard installation steps.

Access your wordpress installation with **http://localhost:8080/wp-admin/install.php**

It’s recommended that you ‘shut down and clean up’ once you’ve completed the installation as well. To do this use the followng command:

**docker compose down** 

This will stop and remove the containers, but preserves the WordPress database.
