# Docker

A Collection of cocker compose files to deploy different services in a homelab environment.

Simply tweak to your environment and deploy!

## 🔒 Sensitive Information

To apply best practices, the files do not include any information that may be considered sensitive, in order to prevent it from being leaked. While we can include these variables as part of the `environment` section of our files, a common strategy is to include them in a separate `.env` file.

- **Including variables as part of the `environment` section:**


    >docker-compose.yml
    >```docker
    >environment:
    >  - TZ=America/Los_Angeles
    >  - PUID=1000
    >  - PGID=1000
    >```

- **Including them in a separate `.env` file and referencing it from the `docker-compose` file:**

    >docker-compose.yml
    >```docker
    >env_file: stack.env
    >```

    >stack.env
    >```docker
    >TZ=America/Los_Angeles
    >PUID=1000
    >PGID=1000
    >```
    > Just remember to save this file in the same place as the `docker-compose.yml` file.

When some dockers include sensitive variables, these will be listed in a comment at the end of each `docker-compose` and should be included in one of the two approaches indicated above.

## Setting Time Zone

To set the time zone of a Docker container, we can use the `TZ` environment variable as:
`TZ=America/Los_Angeles`

Just replace “America/Los_Angeles” with the time zone you want to use. You can check your time zone using this [website created by Marius Bodgan](https://timezone.mariushosting.com/).
