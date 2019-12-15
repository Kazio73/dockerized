All files under `Dockerfiles/`, `config/`, `entrypoints/`, `files/` are
generated with ansible code of iRedMail Easy.

## Requirements

* Docker has some issue on Windows/macOS platform, please use Linux system
  as Docker host.

## Usage

Create config file used to store your custom settings:

```
touch iredmail.conf
```

Check default settings in file `env.defaults`, if there's any setting you want
to change, please write the parameter in file `iredmail.conf` with proper value.

For example, MySQL root password is set to `secret` in env file `env.defaults`:

```
MYSQL_ROOT_PASSWORD=secret
```

You can change it by writing same parameter name with proper value in
`iredmail.conf` like below:

```
MYSQL_ROOT_PASSWORD=my-secret-password
```

Start the containers with `docker-compose`:

```
docker-compose up
```

[__NOT STABLE YET__] If you prefer running all applications in one container, run:

```
docker build -t iredmail:latest -f Dockerfiles/Dockerfile .
docker run --env-file env.defaults --env-file iredmail.conf iredmail:latest
```
