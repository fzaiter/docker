<a id="readme-top"></a>
<!-- PROJECT LOGO -->
<br />
<div align="center">
  <a href="https://github.com/fzaiter/docker">
    <img src="https://upload.wikimedia.org/wikipedia/commons/thumb/4/4e/Docker_%28container_engine%29_logo.svg/610px-Docker_%28container_engine%29_logo.svg.png" alt="Logo" width="30%" height="30%">
  </a>

  <h3 align="center">🏠 Docker Compose Collection for Homelab</h3>

  <p align="center">
    A collection of Docker Compose files designed for deploying various services in a homelab environment.
    Customize each configuration to suit your needs and start deploying!
  </p>
</div>

---

## 🔃 Port Mapping

Docker Compose enables you to map container ports to host ports, allowing services to be accessed from your host system. The format is `host_port:container_port`, where:

- The **left side** specifies the port on your host.
- The **right side** specifies the internal port within the container.

For example, to map port `80` of a container to port `8000` on your host machine:

```yaml
    ports:
      - "8000:80"
```
In this example:
> 8000: The host port through which external applications or users access the service. 
>
> 80: The container's internal port that the service listens on. 

> [!NOTE]  
> In the files where port variables are used, you can customize this by simply replacing the host port with an available port on your host system and keeping the one to the right side as it comes.

<p align="right">(<a href="#readme-top">back to top</a>)</p>

## 🔄 Volume Mapping

Docker Compose also allows you to map volumes from your host system to containers. The format is `source_path:destination_path`, where:

- The **left side** specifies the path on your host.
- The **right side** specifies the folder the container is expecting at that location.

For example, to map a local directory located at `/volume/docker/containername/data` to a container directory `/data`:

```yaml
    volumes:
      - /volume/docker/containername/data:/data
```
In this example:

> /volume/docker/containername/data: The host directory that you want to share with the container.
>
> /data: The directory the container will expect.

> [!NOTE]  
> In the files where volume variables are used, you can customize this by replacing the source path with a desired directory on your host system and keeping the other one as it comes.


## ⏰ Setting Time Zone

To set the time zone of a Docker container, use the TZ environment variable. For example:
```yaml
    environment:
      - TZ=America/Los_Angeles
```
> [!NOTE]  
> In the files where TZ variables are used, replace "America/Los_Angeles" with the time zone you want. Check your time zone using this [time zone finder by Marius Bogdan Lizandru](https://timezone.mariushosting.com/).

<p align="right">(<a href="#readme-top">back to top</a>)</p>

## 🔒 Managing Sensitive Information

For security best practices, avoid including sensitive information directly in Compose files. Instead, use environment variables or a separate .env file.
Option 1: Defining Variables in environment

Define sensitive variables directly in the docker-compose.yml file under the environment section:

>docker-compose.yml:
>```yaml
>    environment:
>      - TZ=America/Los_Angeles
>      - PUID=1000
>      - PGID=1000
>```
Option 2: Using a .env File

Alternatively, include sensitive information in a separate .env file and reference it in your docker-compose.yml:

>docker-compose.yml:
>```yaml
>env_file: stack.env
>```
>stack.env:
>```yaml
>    TZ=America/Los_Angeles
>    PUID=1000
>    PGID=1000
>```

> [!NOTE]  
> Note: When sensitive values are required, stack.env will use placeholder values like {VALUE} for you to replace with actual information. Make sure to save this .env file in the same directory as the docker-compose.yml file.

<p align="right">(<a href="#readme-top">back to top</a>)</p>

## 🙏 Acknowledgments

Usually most of these files have been taken from other sites and modified slightly to work in my own environment. These sites can be varied although I would particularly like to thank [Marius Hosting](https://mariushosting.com/), a website where Marius Bogdan Lizandru shares many stacks to implement directly via portainer.

<p align="right">(<a href="#readme-top">back to top</a>)</p>
