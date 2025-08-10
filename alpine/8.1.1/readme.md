```
docker buildx build --platform linux/amd64 -t lyni/phpqa:8.1.1 .
```

```
docker buildx build --platform linux/arm64 -t lyni/phpqa:8.1.1 .
```

```
docker buildx build --platform=linux/arm64,linux/amd64 --push --tag lyni/phpqa:8.1.1 -f ./Dockerfile .

docker image inspect lyni/phpqa:8.1.1
docker push lyni/phpqa:8.1.1

docker run --init -it --rm -v "$(pwd):/project" -v "$(pwd)/tmp-phpqa:/tmp" -w /project lyni/phpqa:8.1.1 phpstan analyse src/app
docker run --init -it --rm -v "$(pwd):/project" -v "$(pwd)/tmp-phpqa:/tmp" -w /project lyni/phpqa:8.1.1 phpstan analyse src/app
docker run --init -it --rm -v "$(pwd):/project" -v "$(pwd)/tmp-phpqa:/tmp" -w /project lyni/phpqa:8.1.1 phpcpd src/app src/modules
docker run --init -it --rm -v "$(pwd):/project" -v "$(pwd)/tmp-phpqa:/tmp" -w /project lyni/phpqa:8.1.1 local-php-security-checker src
```
