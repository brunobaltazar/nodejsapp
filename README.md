# nodejsapp

#CI / CD com Jenkins e AKS
Motivação
As aplicações modernas requerem o desenvolvimento de código em diferentes plataformas e ferramentas, potencializando a necessidade de um mecanismo para integrar e validar suas mudanças. A Integração Contínua (CI) e a Entrega Contínua (CD) incorporam uma cultura, um conjunto de princípios operacionais e uma coleção de práticas que permitem que as equipes de desenvolvimento de aplicativos forneçam alterações de código com mais frequência e confiabilidade.

O objetivo da CI é estabelecer uma maneira consistente e automatizada de construir, empacotar e testar aplicativos. Com a consistência no processo de integração em vigor, as equipes são mais propensas a comprometer alterações de código com mais frequência, o que leva a uma melhor colaboração e qualidade de software. A maioria das equipes trabalha com vários ambientes diferentes de produção, como ambientes de desenvolvimento e teste, e o CD garante que haja uma maneira automatizada de enviar alterações de código a eles.

Este padrão visa definir um pipeline geral de CI / CD para soluções escalonáveis que requerem orquestração de contêineres usando Jenkins e AKS.

Visão geral da arquitetura

![General Architecture](/images/Pipeline.png)

A imagem acima é uma visão geral da arquitetura genérica que pode ser implementada usando diferentes tecnologias e serviços. Neste documento, estamos descrevendo as etapas para configurar um servidor Jenkins conectado a um cluster Kubernetes para receber as implantações. Estes são os serviços usados para implementação:

- **GitHub** como o repositório git;
- **Jenkins** como o servidor orquestrador de automação de CI / CD;
- **Azure** Container Registry como o repositório de contêiner;
- **Azure Kubernetes Service (AKS)** como orquestrador de contêiner.
- **Docker** Contêiner run time
- **Kubectl** Ferramenta de linha de comando kubectl permite controlar os clusters do Kubernetes
- **Azure Cli** Ferramenta de linha de comando do Azure (CLI do Azure) é um conjunto de comandos usado para criar e gerenciar recursos do Azure.
- **Azure Container Registry** Um registro de imagens Docker e Open Container Initiative (OCI), com suporte para todos os artefatos OCI




