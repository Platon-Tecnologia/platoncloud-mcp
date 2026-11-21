# Platon Cloud

Plugin de integração com o servidor MCP hospedado da Platon Cloud. A skill incluída orienta inventário, diagnóstico e operações sobre projetos, VPS, VPC, DNS, domínios, armazenamento, inferência, e-mail transacional, faturamento e suporte.

Este repositório mantém os manifestos do plugin, a skill para agentes e os arquivos usados na preparação das submissões aos diretórios.

## Conexão

O endpoint é `https://api.platoncloud.com/functions/v1/mcp`, via Streamable HTTP. Cada usuário autentica sua própria conta com OAuth 2.1 e autoriza a organização ou o projeto correspondente. Depois da conexão, peça ao assistente para listar os projetos acessíveis. O resultado depende das permissões concedidas no consentimento. [Catálogo do MCP](https://api.platoncloud.com/functions/v1/mcp/llms.txt)

## Distribuição

| Canal | Pacote e submissão |
| --- | --- |
| ChatGPT e Codex | O ZIP de rascunho OpenAI inclui `plugin.json`, a pasta `skills/` e `distribution/openai/mcp.json`, copiado como `mcp.json` na raiz do ZIP, com a configuração OAuth do portal. O portal OpenAI oferece o fluxo **With MCP** para conectar o servidor, verificar o domínio e submetê-lo à revisão. |
| Cursor | O repositório Git público usa os mesmos manifestos portáveis e inclui este README. A publicação passa por revisão no Cursor Marketplace. |
| Claude | O mesmo repositório inclui `.claude-plugin/plugin.json` e `.mcp.json` para o formato Claude. O portal também aceita cadastrar apenas o servidor MCP remoto. |
| skills.sh | O repositório público expõe `skills/platon-cloud/SKILL.md`. Instale a skill com `npx skills add Platon-Tecnologia/platoncloud-mcp --skill platon-cloud`. A descoberta no diretório pode ocorrer a partir das instalações. |
| MCP Registry | `server.json` descreve o endpoint remoto. O namespace proposto `com.platoncloud` depende da comprovação de controle do domínio. |

[OpenAI](https://developers.openai.com/plugins/deploy/submission) · [Cursor](https://cursor.com/marketplace/publish) · [Claude](https://claude.com/resources/articles/build-plugins-for-claude) · [skills.sh](https://vercel.com/kb/guide/agent-skills-creating-installing-and-sharing-reusable-agent-context) · [MCP Registry](https://modelcontextprotocol.io/registry/quickstart)

## Pendências para a versão pública

- **Identidade e arquivos de publicação.** Verificar a identidade da Platon nos portais, definir a licença de distribuição, adicionar o ícone aprovado pela marca e confirmar que o aviso de privacidade cobre a integração MCP.
- **OAuth nativo.** Testar autorização, renovação e desconexão nos três clientes com um projeto de demonstração. A Platon anuncia o documento de descoberta em `console.platoncloud.com` para um recurso em `api.platoncloud.com`. A descoberta nativa do Codex falhou nessa configuração. O arquivo `mcp.json` do ZIP OpenAI declara os endpoints oficiais diretamente. Para resolver a descoberta no servidor, publicar o documento RFC 9728 no host do MCP, por exemplo em `https://api.platoncloud.com/.well-known/oauth-protected-resource/functions/v1/mcp`, e apontar o cabeçalho `WWW-Authenticate` para ele.
- **Ferramentas do diretório.** Revisar no servidor os campos e as ferramentas que expõem credenciais e identificadores fiscais. Para o ChatGPT, o catálogo público precisa excluir operações de contratação, upgrade e recarga de serviços digitais, além das ferramentas que manipulam dados restritos pelas regras do diretório. O ZIP de rascunho usa o endpoint atual para documentar o OAuth. Atualizar esse endereço para o catálogo público aprovado e testar a autorização no servidor antes de enviar para revisão.
- **Revisão OpenAI.** Publicar o desafio de domínio exigido pelo portal e preparar um vídeo demonstrativo e uma conta de teste isolada para os revisores. O manifesto contém cinco cenários positivos e três negativos. Fornecer os dados de acesso pelo formulário seguro do portal.

[Autenticação OpenAI](https://developers.openai.com/plugins/build/auth) · [Regras de privacidade e comércio do diretório](https://developers.openai.com/plugins/plugin-guidelines) · [Requisitos da revisão](https://developers.openai.com/plugins/deploy/submission) · [Política de privacidade da Platon](https://platon.com.br/central/dl.php?type=d&id=63)
