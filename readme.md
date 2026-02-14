


```shell
docker exec -it gitlab-runner gitlab-runner register \
  --non-interactive \
  --url "http://gitlab:8929/" \
  --registration-token "n4mRDhfzz9gqycbQSzwN" \
  --executor "docker" \
  --docker-image "alpine:latest" \
  --description "docker-runner" \
  --tag-list "mac" \
  --run-untagged="true" \
  --docker-network-mode "gitlab-net"


```