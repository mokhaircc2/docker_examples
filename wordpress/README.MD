Running WordPress websites can involve using a wide number of configurations and software dependencies to produce high-quality products.  Docker is a product that offers a solution for a quicker and smoother WordPress setup locally without running so many different software packages on your own machine.

Once you install Docker Engine and Compose installed, you can get started on your first WordPress development project. You’ll need to create a new, empty project directory using the ‘make directory’ command:

**mkdir wordpress/**

Next, you can move over to your new directory using the following command: 

cd wordpress/

You’ll now be in your new project directory.

Now use the docker-compose.yaml file. This will create your new WordPress installation and the necessary MySQL database. Your file will contain all of the information for both WordPress and your database, including necessary ports, databases, hostnames, and passwords.

Now that you’ve configured the YAML file, you’ll need to execute the command that will pull in all the required images and set up your WordPress project. From within your project directory, you’ll run the following command: 

docker-compose up -d

You should now see that Docker is ‘pulling’ in the MySQL and WordPress images. 

To access the wordpress installation:

Because you’re installing this site locally, you’ll need to use the port indicated in your YAML file rather than the typical WordPress /install.php script. Since we’re using Docker Desktop for Mac in our example, we’ll use https://localhost as the IP address and open port https://localhost:8080. This was the port designated in the YAML file. You can access WordPress in a browser to complete the standard installation steps.

It’s recommended that you ‘shut down and clean up’ once you’ve completed the installation as well. To do this, you can use the Docker ‘down’ command. This will stop and remove the containers, but preserves the WordPress database.


Using WordPress and Docker for Streamlined Deployment to Production:

It’s important to note here that sites hosted on WP Engine servers do not have the root access that is necessary to setup a new docker image. However, if your site is on a production server you can follow the steps below to ship your image.

Now that you’ve created a WordPress image locally, you might be wondering how you can use the same image on a production server. Some of the steps you just completed will be the same, but you’ll need to create a private repository on Docker Hub first. 

To take your WordPress Docker container to production, you’ll need to use your Docker account and push the image to a private repository. From there, you can follow the same steps we previously went over, but you’ll pull the image from your repository directly to your production server by changing the port information in your YAML file. 
