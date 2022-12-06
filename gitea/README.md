# Docker-Compose-Gitea

A Docker Compose file for Gitea - Git with a cup of tea ([gitea.io](https://gitea.io))

Data will be saved in separate docker volumes to enable easy upgrades!

## Requirements

* docker
* docker-compose

## Getting Started

1. Copy **.env.dist** to **.env** and make your modifications
2. Start docker containers:
```
$ docker-compose up -d
```

After that open gitea installer via browser: [http://localhost:3000](http://localhost:3000) and fill the form according your .env settings. 

Set **`gitea-db:3306`** in _Host_ field and complete setup.

After setup is completed register a new user (use link from the navigation bar).

The first registered user has admin privileges.


### Environment Configuration

| VARIABLE              | Description                       | DEFAULT       |
| ----------------------|-----------------------------------|:-------------:|               
| DB_PASS | Database password |gitea |
| DB_USER | Database user | gitea |
| DB_NAME | Database name | gitea |
| DB_PASS_FILE | Path to database password file | /run/secrets/db_pass |
| HTTP_PORT | HTTP-port Gitea | 3000 |
| PROTOCOL | Gitea web protocol | http |
| HOSTNAME | Hostname for Gitea Application | localhost
| SSH_PORT | SSH-port Gitea | 2222 |


## Create systemd unit
1. Copy **docker-gitea.service.dist** to **docker-gitea.service**
1. Adjust **WorkingDirectory** in service file if needed
1. Create symbolic link: ``ln -s docker-gitea.service /etc/systemd/system/docker-gitea.service``
1. Start service: ``systemctl start docker-gitea``
1. (optional) Enable autostart at boot: ``systemctl enable docker-gitea``

