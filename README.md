# Tutorial ao Terraform no AWS

Este tutorial orienta você a começar a usar o Terraform para provisionar recursos na AWS. Você criará uma instância EC2, configurará o armazenamento S3 e configurará o balanceamento de carga.

## Pré-requisitos
- Uma conta na AWS
- Instalar a AWS CLI
- Instalar o Terraform

## Configurar suas credenciais da AWS

Configure suas credenciais da AWS para permitir que o Terraform acesse sua conta AWS.

Defina a AWS_ACCESS_KEY_IDvariável de ambiente.
```bash
exportar AWS_ACCESS_KEY_ID = 
```
defina sua chave secreta
```bash
exportar AWS_SECRET_ACCESS_KEY =
```



## Escreva sua configuração do Terraform

Crie um diretório para o seu projeto e navegue até ele:

```bash
mkdir terraform-aws
cd terraform-aws
```

Crie um arquivo chamado `main.tf`  ele irá conter sua estrutura e adicione a seguinte configuração para criar uma instância EC2:

```hcl
terraform {
  required_providers {
    aws = {
      source  = "hashicorp/aws"
      version = "~> 4.16"
    }
  }

  required_version = ">= 1.2.0"
}

provider "aws" {
  region  = "us-west-2"
}

resource "aws_instance" "app_server" {
  ami           = "ami-830c94e3"
  instance_type = "t2.micro"

  tags = {
    Name = "ExampleAppServerInstance"
  }
}

```

## Inicializar o Terraform

Inicialize o Terraform no seu diretório de projeto:

```bash
terraform init
```
![image](https://github.com/Ra2861/Terraform/assets/99209068/f8477005-c590-4d33-8e76-4bf6d448dea5)


## Executar um plano do Terraform

Crie um plano de execução para verificar se a configuração está correta:

```bash
terraform plan
```
![image](https://github.com/Ra2861/Terraform/assets/99209068/e65f551f-ee62-4969-9667-c014782cc8d5)

## Aplicar a configuração do Terraform

Aplique a configuração para provisionar os recursos na AWS:

```bash
terraform apply
```
![image](https://github.com/Ra2861/Terraform/assets/99209068/77480b5f-988f-498d-ab2a-dce550e15f28)



## Limpar os recursos

Para limpar todos os recursos provisionados, execute o seguinte comando:

```bash
terraform destroy
```
