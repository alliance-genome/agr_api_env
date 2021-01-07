>**Note:**  
>This archived repository is no longer actively used nor maintained.  
>It was intended as a platform-specific repository to build a docker image for java (docker) application deployment,
>but its functionality has been replaced by the more general [agr_base_linux_env repository](https://github.com/alliance-genome/agr_base_linux_env) due to inter-technology dependencies.

# AGR Loader Environment Documentation

This repo follows the HubFlow conventions for releasing the versions of the code as specified here: [HubFlow](https://datasift.github.io/gitflow/)

Versions of this repos do not need to be done at the same time as the agr_api. When the developer is ready to make a verions of the code they should use the following command.

```bash
git hf init
git hf release start <version>
git hf release finish <version>
```

After a version has been created the user should create a tagged docker container with the following command

```bash
docker build -t agrdocker/agr_api_env:<version> .
docker docker push agrdocker/agr_api_env:<version>
```
This will make it so that there is a agr_api_env container available via DockerHub. If you would like to use this version feel free to specify the version in the agr_api's Dockerfile. The agr_loader Dockerfile should specify a specific version when pushing code to develop. This way we will know exactly what is running in dev, staging and production environments.  

In order to make changes and test them you might want to create a "develop" container. To do this you can use commands available in the Makefile:

*These are commands done on the development machine. If you are developing locally feel free to use the commands but don't push to DockerHub

## Bulding develop container
```bash
make all
```
## Share by pushing to DockerHub
```bash
make push
```

## Using develop container on Dockerhub
```bash
make pull
```

## Running Bash inside container
```bash
make bash
```



