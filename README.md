# git-agent
a docker image helps you pull all git volumes automatically


## Usage

1. Create a `git-agent` container

```sh
docker run -d -v /:/rootfs \
-v /var/run/docker.sock:/var/run/docker.sock:ro \
hyperapp/git-agent
```

You need to mount `/` to `/rootfs` to allow `git-agent` to update all other containers' volumes.


2. Start your container with `git-agent` ENV

```sh
docker run --rm -it -e GIT_VOLUME='/srv' \
-e GIT_REMOTE='https://https://github.com/waylybaye/git-agent.git' \
-v /srv s alpine sh
```

### git-agent ENV


### other container's ENV

```
GIT_VOLUME: the volume inside your container
GIT_REMOTE: remote git repo, NOTE ssh need interactive confirm when first clone
GIT_INTERVAL: check for update every GIT_INTERVAL seconds, default to 5*60
GIT_FORCE_PULL: force pull, default to false
```
