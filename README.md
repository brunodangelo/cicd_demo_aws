# CI/CD con GitHub Actions, deplegando app en ECS Fargate
Al detectar un Pull request en la rama main (abierto o reabierto), se ejecuta el WorkFlow de GitHub Actions. Este crear la imagen de Docker a partir del Dockerfile, la sube a ECR y luego actualiza la task definition en ECS para que los cambios se vean reflejados.

## NOTAS
* Para replicar este proyecto es necesario infraestructura previa en AWS como un Cluster ECS y un repositorio en ECR. Se puede utilizar la siguiente con Terraform: https://github.com/brunodangelo/aws_ecs_fargate_terraform
* Ademas de la creación de un rol IAM que tenga asociadas las politicas para trabajar con ECS y ECR.
* Se deben crear 2 secrets: AWS_REGION y AWS_IAM_ROLE (arn del rol descrito arriba).
* Para establecer una conexión segura con la cuenta de AWS, se debe utilizar los Identity Provider de Amazon con GitHub. Puede basarse en el siguiente ejemplo: https://www.youtube.com/watch?v=HEOU6o-Eazs
