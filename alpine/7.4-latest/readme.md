#Create multi platform

```
docker buildx create --use --platform=linux/arm64,linux/amd64 --name multi-platform-builder
docker buildx inspect --bootstrap
```

#Build

```
docker buildx build --platform linux/arm64,linux/amd64 -t lyni/phpqa:7.4-latest .  
```

#Build and Push

```
docker buildx build --platform=linux/arm64,linux/amd64 --push --tag lyni/phpqa:7.4-latest -f ./Dockerfile .
docker image inspect lyni/phpqa:7.4-latest
```

#Push only

```
docker push lyni/phpqa:7.4-latest
```

#Test

```
docker run --init -it --rm -v "$(pwd):/project" -v "$(pwd)/tmp-phpqa:/tmp" -w /project lyni/phpqa:7.4-latest phpstan analyse src/app
docker run --init -it --rm -v "$(pwd):/project" -v "$(pwd)/tmp-phpqa:/tmp" -w /project lyni/phpqa:7.4-latest phpstan analyse src/app
docker run --init -it --rm -v "$(pwd):/project" -v "$(pwd)/tmp-phpqa:/tmp" -w /project lyni/phpqa:7.4-latest phpcpd src/app src/modules
docker run --init -it --rm -v "$(pwd):/project" -v "$(pwd)/tmp-phpqa:/tmp" -w /project lyni/phpqa:7.4-latest local-php-security-checker src
```