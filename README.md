 (cd "$(git rev-parse --show-toplevel)" && git apply --3way <<'EOF' 
diff --git a/README.md b/README.md
index 035caf550cb2f03de3a73fa1dff7d2dafa7b27f4..b20bfba49f32d5970cc6db20ccb4510c75150bcb 100644
--- a/README.md
+++ b/README.md
@@ -1 +1,28 @@
+# Ingresso Conecta
+
 Seja bem vindo ao repositório de código das Olimpíadas Azure 2024!
+
+## Projetos
+
+Este repositório reúne três aplicações principais, todas baseadas em .NET 8:
+
+- **CRM.API.BEND** – API REST que expõe recursos de CRM e autenticação.
+- **CRM.WebApp.Ingresso** – interface de venda e gerenciamento de ingressos.
+- **CRM.WebApp.Site** – portal administrativo para operações de CRM.
+
+## Configuração de variáveis de ambiente
+
+Alguns valores sensíveis devem ser definidos como variáveis de ambiente antes da execução:
+
+- `ConnectionStrings__DefaultConnection` – string de conexão do banco de dados.
+- `Jwt__Key` – chave utilizada para assinatura dos tokens JWT.
+
+Utilize o formato com `__` (dois underscores) quando definir variáveis no sistema ou em provedores de ambiente. Em ambiente de desenvolvimento você pode sobrescrever esses valores em `appsettings.Development.json`.
+
+## Workflows de deploy
+
+O repositório possui o workflow `deploy-dotnet48.yml` localizado em `.github/workflows`. Ele é disparado quando há *push* para o branch `main` deste repositório. A pipeline executa as seguintes etapas:
+
+1. Restaura dependências e compila a solução.
+2. Publica o projeto `CRM.WebApp.Ingresso`.
+3. Envia o pacote gerado para o Web App `appIngressoConecta` no Azure.
 
EOF
)