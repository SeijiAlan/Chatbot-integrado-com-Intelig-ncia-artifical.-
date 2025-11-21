# Chatbot-integrado-com Inteligencia Artificial 


<p align="center">🤖Integração de bot (Telegram) com Inteligência Artificial (Gemini 2.5 flash) realizada por intermédio de uma plataforma de automação de processos (ActivePieces)</p>


✅Este projeto utiliza o Activepieces para criar um fluxo de automação sem código (no-code) que conecta o Telegram à API do Google Gemini.O bot recebe mensagens de usuários, as processa com a inteligência artificial do Gemini e envia a resposta de volta ao chat.

🛠️ Pré-requisitos

Para importar e ativar este fluxo, você precisará dos seguintes itens:
1-Conta Activepieces: Para hospedar e gerenciar a automação.


2-Token do Bot Telegram: O token HTTP exclusivo fornecido pelo BotFather no Telegram (ex: 123456:ABC-DEF1234...).


3-Chave da API do Google Gemini: Uma chave de acesso ativa para o modelo de IA.

⚙️ Lógica do Fluxo (Workflow)


O fluxo de automação é uma sequência de três passos que estabelece um ciclo de chat entre o Telegram e o Google Gemini.

Passo 1: New Message (Gatilho), que utiliza o componente Telegram Bot. Sua principal Função é a de iniciar a automação, sendo ativado a cada nova mensagem que o bot recebe. Este passo é Configurado com o Token do Bot para garantir a autenticação.

Passo 2: Chat Gemini, que emprega o componente Google Gemini. A Função deste passo é processar a mensagem do usuário (recebida do Passo 1), utilizando a inteligência artificial para gerar uma resposta textual. A Configuração requer o uso da Chave da API do Gemini. (Pode ser a Open AI também, funciona do mesmo jeito)

Passo 3: Send Text Message, que utiliza o componente Telegram Bot. A Função é enviar a resposta (response) gerada pelo Gemini (Passo 2) de volta para o chat do Telegram. A Configuração crucial deste passo exige que o campo Format seja definido como HTML (opção que funcionou) para evitar erros de análise de caracteres especiais e garantir a correta renderização da mensagem no Telegram



🚀 Como Usar e Configurar


Siga estes passos para colocar o bot em funcionamento:

1.Importação do Fluxo

1.1 Baixe o arquivo de fluxo (o JSON ou .piece modificado) deste repositório.

1.2 Acesse o Activepieces e utilize a opção Import Flow (Importar Fluxo).

2.Configuração das Credenciais
O fluxo importado contém placeholders (marcadores) no lugar dos dados confidenciais para garantir a segurança. Você deve configurar suas próprias credenciais:

Passo 1 – New Message:
É necessário o Token do Bot do Telegram. Crie uma nova conexão usando o token que você obteve no BotFather.

Passo 2 – Chat Gemini:
É necessária a Chave da API do Gemini. Crie uma nova conexão usando a chave da API do Google Gemini.
No prompt é possível influênciar a forma com que o bot irá interagir com o usuário (Forncecer as instruções).Deve-se clicar em "Insert" em no campo "New message" para encaminhar a mensagem enviada ao bot para o Gemini Chat processar e responder.

Passo 3 – Send Text Message:
É necessário o Token do Bot do Telegram novamente. Utilize a mesma conexão que você criou no Passo 1.No campo de preenchimento "Message" clicar em "Insert" no Gemini chat.

↗️Ativação
Após configurar as conexões, clique em Publicar (Publish Flow ou Activate) para que o Activepieces registre o Webhook e comece a "escutar" as mensagens do Telegram.


⚠️ Solução de Problemas Comuns

1.Conflito de Webhook
   
Problema: Conflict: can't use getUpdates method while webhook is active...

Causa: O bot tem um Webhook antigo ativo.

Solução: Delete o webhook acessando no navegador: https://api.telegram.org/bot[SEU_TOKEN]/deleteWebhook

2.Erro de Formatação
   
Problema: Bad Request: can't parse entities: Character '.' is reserved...

Causa: O Telegram não está conseguindo interpretar corretamente o formato do texto.

Solução: No passo 3 – Send Text Message, certifique-se de que o campo Format está definido como HTML (ou a opção que funcionou) para garantir que o Telegram interprete o texto corretamente.
