# Lab 5: Integração e Mensageria com SQS e SNS

## Objetivo
Este projeto tem como objetivo configurar um sistema de notificações utilizando Amazon S3, Amazon SNS (Simple Notification Service) e Amazon SQS (Simple Queue Service) para monitorar eventos de upload e exclusão de arquivos em um bucket S3.

## Cenário
Você trabalha em uma empresa de mídia que armazena arquivos de imagem e vídeo em um bucket S3. Para monitoramento, segurança e auditoria, é necessário:
- Receber notificações por e-mail sempre que um novo arquivo for carregado ou excluído do bucket.
- Registrar todos esses eventos em uma fila SQS para análise posterior e integração com outras ferramentas.

## Tecnologias Utilizadas
- **Amazon S3**: Armazena os arquivos e gera eventos de notificação.
- **Amazon SNS**: Envia notificações por e-mail quando ocorrem eventos no S3.
- **Amazon SQS**: Armazena os eventos de upload/exclusão para processamento posterior.

## Requisitos
Antes de iniciar, garanta que você tem:
- Uma conta AWS ativa.
- Permissões adequadas para acessar S3, SNS e SQS.
- Um e-mail válido para receber notificações.

## Configuração Passo a Passo
1. **Criar um bucket S3**
   - Nome: `eventos-s3-seunome-data`
   - Região: `us-east-1`
   - Copiar o ARN do bucket

2. **Criar um tópico SNS**
   - Nome: `notificacoes-s3-seunome-data`
   - Copiar o ARN do tópico
   - Criar uma assinatura de e-mail e confirmar via link enviado pela AWS

3. **Criar uma fila SQS**
   - Nome: `fila-eventos-s3-seunome-data`
   - Copiar o ARN da fila

4. **Configurar permissões**
   - Atualizar a política do tópico SNS para permitir publicação de eventos do S3.
   - Atualizar a política da fila SQS para permitir recebimento de mensagens do SNS.

5. **Habilitar eventos no S3**
   - Criar uma notificação de evento para eventos `s3:ObjectCreated:*` e `s3:ObjectRemoved:*`
   - Associar essa notificação ao tópico SNS criado anteriormente

6. **Testar a implementação**
   - Fazer upload de um arquivo no bucket S3 e verificar se o e-mail foi recebido e se a mensagem chegou à fila SQS.
   - Excluir o arquivo e validar novamente as notificações.

7. **Limpeza de recursos**
   - Excluir o bucket S3, fila SQS, tópico SNS e assinaturas para evitar custos desnecessários.

8. **Prints de cada etapa do Projeto**
![NOTIFICAÇÃO DE EVENTO: objeto removido do Bucket S3 - 1](imagens/Captura%20de%20Tela%20(397).png)
![NOTIFICAÇÃO DE EVENTO: objeto removido do Bucket S3 - 2](imagens/Captura%20de%20Tela%20(400).png)
![NOTIFICAÇÃO DE EVENTO: objeto removido do Bucket S3 - 3](imagens/Captura%20de%20Tela%20(401).png)
![NOTIFICAÇÃO DE EVENTO: objeto removido do Bucket S3 - 1](imagens/Captura%20de%20Tela%20(402).png)
![NOTIFICAÇÃO DE EVENTO: objeto removido do Bucket S3 - 2](imagens/Captura%20de%20Tela%20(403).png)
![NOTIFICAÇÃO DE EVENTO: objeto removido do Bucket S3 - 3](imagens/Captura%20de%20Tela%20(403).png)
![NOTIFICAÇÃO DE EVENTO: objeto removido do Bucket S3 - 1](imagens/Captura%20de%20Tela%20(404).png)
![NOTIFICAÇÃO DE EVENTO: objeto removido do Bucket S3 - 2](imagens/Captura%20de%20Tela%20(405).png)
![NOTIFICAÇÃO DE EVENTO: objeto removido do Bucket S3 - 3](imagens/Captura%20de%20Tela%20(406).png)



## Conclusão
Este laboratório ensina como integrar serviços da AWS para monitorar eventos do S3, enviando notificações por e-mail e registrando os eventos em uma fila para processamento futuro. Essa solução é útil para auditoria, monitoramento de arquivos e integração com outros sistemas.