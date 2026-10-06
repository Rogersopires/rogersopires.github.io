# Google Sheets e instalação Android — LuRo - Finanças

## Conectar a planilha

1. Acesse [Google Cloud Console](https://console.cloud.google.com/), crie/selecione um projeto e habilite **Google Sheets API**.
2. Configure a tela de consentimento OAuth. Para uso em modo de teste, adicione sua conta Google como usuário de teste.
3. Crie uma credencial **OAuth Client ID** do tipo **Aplicativo da Web**. Adicione o endereço exato do sistema em **Origens JavaScript autorizadas** (por exemplo, `http://localhost:5500`). O endereço deve ser HTTPS ou localhost; abrir o HTML como `file://` não funciona para o login.
4. Sirva esta pasta no endereço autorizado. Pode usar uma extensão local de servidor no VS Code ou hospedagem HTTPS.
5. No LuRo, abra **Configurações → Google Sheets**, informe o OAuth Client ID e o ID/link da planilha, depois clique **Conectar Google** e autorize o acesso.

O app cria as abas **Lancamentos** e **Configuracoes**. Se já tiver dados locais e as abas estiverem vazias, esses dados são enviados na primeira conexão. Se houver dados na planilha, eles são carregados no navegador. Depois, alterações feitas no app são salvas localmente e sincronizadas automaticamente enquanto a autorização estiver ativa. Ao expirar a autorização, conecte novamente. **Sincronizar agora** envia o estado deste aparelho para a planilha; exportar TXT continua disponível como cópia de segurança.

O OAuth Client ID e o ID da planilha ficam salvos neste navegador. O token de acesso não é salvo em armazenamento persistente. O consentimento usa o escopo de planilhas Google e o usuário autenticado precisa ter acesso de edição à planilha.

## Instalar no Android como PWA

1. Publique a pasta em um endereço HTTPS (ou abra-a em `localhost` para testes). O service worker e a instalação não funcionam abrindo diretamente como `file://`.
2. No Android, abra o endereço no Chrome e use **Instalar app** quando aparecer; alternativamente, abra o menu **⋮** do Chrome e escolha **Instalar app** ou **Adicionar à tela inicial**.
3. O LuRo pode abrir offline depois de carregado. Google Sheets exige conexão com a internet.

Arquivos do PWA: `manifest.webmanifest`, `sw.js` e `luro-icon.svg`.
