#Create multi platform

```
docker buildx create --use --platform=linux/arm64,linux/amd64 --name multi-platform-builder
docker buildx inspect --bootstrap
```

#Build

```
docker buildx build --platform linux/arm64,linux/amd64 -t lyni/phpqa:8.2 .  
```

#Build and Push

```
docker buildx build --platform=linux/arm64,linux/amd64 --push --tag lyni/phpqa:8.2 -f ./Dockerfile .
docker image inspect lyni/phpqa:8.2
```

#Push only

```
docker push lyni/phpqa:8.2
```

#Test

```
docker run --init -it --rm -v "$(pwd):/project" -v "$(pwd)/tmp-phpqa:/tmp" -w /project lyni/phpqa:8.2 phpstan analyse src/app
docker run --init -it --rm -v "$(pwd):/project" -v "$(pwd)/tmp-phpqa:/tmp" -w /project lyni/phpqa:8.2 phpstan analyse src/app
docker run --init -it --rm -v "$(pwd):/project" -v "$(pwd)/tmp-phpqa:/tmp" -w /project lyni/phpqa:8.2 phpcpd src/app src/modules
docker run --init -it --rm -v "$(pwd):/project" -v "$(pwd)/tmp-phpqa:/tmp" -w /project lyni/phpqa:8.2 local-php-security-checker src
```