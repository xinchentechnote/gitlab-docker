

## register runner
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
## unregister runner
```shell
docker exec -it gitlab-runner gitlab-runner list
docker exec -it gitlab-runner gitlab-runner unregister --name "docker-runner"
docker exec -it gitlab-runner gitlab-runner unregister --all-runners
```

## test cicd
```
#.gitlab-ci.yml
stages:
  - test

hello-job:
  stage: test
  tags:
    - mac   # 必须和你注册 runner 时填写的 tag 一致
  script:
    - echo "Hello GitLab CI"
    - uname -a
    - echo "Runner works!"

```