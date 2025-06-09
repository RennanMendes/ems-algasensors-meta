<div align="center">    
    <h1>Algasensors</h1>
</div>

Este é um projeto didático da **AlgaWorks**, desenvolvido no nível 1 do curso "Especialista Microsserviços".  
Tendo como foco principal apresentar os conceitos de **microsserviços** e **mensageria** utilizando o **RabbitMQ**.

🔗 Link do curso: [Especialista Microsserviços - AlgaWorks](https://lp.algaworks.com/curso-especialista-microsservicos-java-spring-cadastro)  
_Todos os direitos do conteúdo do curso pertencem à AlgaWorks. Este repositório é utilizado apenas para fins
educacionais._

## Visão Geral

Algasensors é uma aplicação projetada para realizar o gerenciamento e monitoramento inteligente de sensores de
temperatura por meio de uma arquitetura moderna baseada em microsserviços.  
  
[Diagrama do projeto](https://whimsical.com/ems-01-07-15-projeto-algasensors-refinando-modelagem-PL457CGTiNJAY3FGqg5oJE)  
[Design Doc: Adoção da Arquitetura de Microsserviços no AlgaSensors](https://www.notion.so/algaworks1/Design-Doc-Ado-o-da-Arquitetura-de-Microsservi-os-no-AlgaSensors-1a5731beea3580489501f870ac7f3c3e?pvs=4)

### 🔧 Principais Componentes

A solução é composta por três microsserviços independentes, cada um responsável por uma capacidade de negócio
específica:

* **Device Management Service**: Gerencia o cadastro, ativação e configuração remota dos sensores.
* **Temperature Processing Service**: Recebe os dados de temperatura em tempo real e os pública para outros serviços.
* **Temperature Monitoring Service**: Analisa, armazena e gera alertas com base nas leituras de temperatura, além de
  permitir consultas ao histórico.

### 🎯 Objetivos da Arquitetura

* **Escalabilidade independente** de cada serviço, conforme a carga.
* **Isolamento de falhas** para aumentar a resiliência do sistema.
* **Manutenção facilitada** com serviços coesos e bem definidos.
* **Desenvolvimento e implantação autônomos** para acelerar entregas.

### 🧩 Comunicação entre Serviços

* **Assíncrona** via mensageria RabbitMQ, usada para troca de dados entre processamento e monitoramento.
* **Síncrona** via REST, usada para comandos e sincronizações específicas (ex: ativação/desativação de sensores).

## Tecnologias utilizadas

| <img src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/java/java-plain.svg" alt="Java Icon" width="40" height="40" /> | <img src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/spring/spring-original-wordmark.svg" alt="Spring Icon" width="48" height="48" /> | <img src="https://cdn.jsdelivr.net/gh/devicons/devicon@latest/icons/docker/docker-plain-wordmark.svg" alt="Docker Icon" width="40" height="40" /> | <img src="https://cdn.jsdelivr.net/gh/devicons/devicon@latest/icons/rabbitmq/rabbitmq-original-wordmark.svg" alt="RabbitMQ Icon" width="40" height="40" /> |
|:---------------------------------------------------------------------------------------------------------------------------:|:---------------------------------------------------------------------------------------------------------------------------------------------:|:-------------------------------------------------------------------------------------------------------------------------------------------------:|:----------------------------------------------------------------------------------------------------------------------------------------------------------:|
|                                                            Java                                                             |                                                                    Spring                                                                     |                                                                      Docker                                                                       |                                                                          RabbitMQ                                                                          |

## Pré-requisitos

- [Java 21+](https://www.oracle.com/java/technologies/javase-downloads.html)
- [Gradle](https://gradle.org/releases/)
- [Git](https://git-scm.com/)
- [Docker](https://www.docker.com/products/docker-desktop/)

## Instalação Local

Siga estas etapas para instalar e executar o projeto:

1. Clone o repositório:

```bash
git clone --recurse-submodules -j8 git@github.com:RennanMendes/ems-algasensors-meta.git
```

2. Dentro de cada módulo, compile o projeto usando Gradle:

    * Em sistemas Unix/macOS:
        ```bash
        ./gradlew build
        ```
    * Em Windows:
      ```bash
        .\gradlew.bat build
        ```
3. Suba o container docker:

```bash
    docker-compose up
```

3. Execute o projeto:

```bash 
   java -jar target/nome-do-projeto.jar
```