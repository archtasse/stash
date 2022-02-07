# Generating a new Nightly Dockerfile

```
cat _gitlab_token | docker login ghcr.io -u "archtasse" --password-stdin
```

Make the project:
```
make docker-build
docker tag stash/build:latest ghcr.io/archtasse/stash:nightly
docker tag stash/build:latest ghcr.io/archtasse/stash:$(git rev-parse --short HEAD)
docker push ghcr.io/archtasse/stash:nightly && docker push ghcr.io/archtasse/stash:$(git rev-parse --short HEAD)
```
