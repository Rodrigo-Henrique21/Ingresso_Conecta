# Ingresso Conecta

Seja bem vindo ao repositório de código

## Projetos

Este repositório reúne três aplicações principais, todas baseadas em .NET 8:

- **CRM.API.BEND** – API REST que expõe recursos de CRM e autenticação.
- **CRM.WebApp.Ingresso** – interface de venda e gerenciamento de ingressos.
- **CRM.WebApp.Site** – portal administrativo para operações de CRM.

## Configuração de variáveis de ambiente

Alguns valores sensíveis devem ser definidos como variáveis de ambiente antes da execução:

- `ConnectionStrings__DefaultConnection` – string de conexão do banco de dados.
- `Jwt__Key` – chave utilizada para assinatura dos tokens JWT.

Utilize o formato com `__` (dois underscores) quando definir variáveis no sistema ou em provedores de ambiente. Em ambiente de desenvolvimento você pode sobrescrever esses valores em `appsettings.Development.json`.

## Workflows de deploy

O repositório possui workflows de deploy automático para dois aplicativos Web:

* **CRM.WebApp.Ingresso** &ndash; publica usando o perfil `AZUREAPPSERVICE_PUBLISHPROFILE` no aplicativo `appIngressoConecta`.
* **CRM.WebApp.Site** &ndash; publica usando o perfil `AZUREAPPSERVICE_PUBLISHPROFILE_SITE` no aplicativo `appCrmSite`.

1. Restaura dependências e compila a solução.
2. Publica o projeto `CRM.WebApp.Ingresso` e `CRM.WebApp` .
3. Envia o pacote gerado para o Web App `appIngressoConecta` e `crmIngressoConecta` Azure.