# Chatbot_Front_End
Chatbot widget with Angular and REST for a chatbot developed with RASA

O módulo/serviço/componente está na pasta Chatbot-Widget, com as respetivas imagens.

### Leonardo
* O id para passar ao rasa (estou a gerar de forma aleatória no ficheiro __chatbot.service.ts__ linha 13) [aqui](https://github.com/gusmcarreira/Chatbot_Front_End/blob/main/Chatbot-Widget/chatbot/chatbot.service.ts)
* [Verificar] Está correto eu dar o url da plataforma para ele se conectar ao rasa? "www.32b.com.br:5005" [aqui](https://github.com/gusmcarreira/Chatbot_Front_End/blob/main/Chatbot-Widget/chatbot/chat-widget/chat-widget.component.ts) linha 25
  * Se não lhe estiver a parecer bem diga-me que assim também tenho de mudar por parte do RASA

<a id="atencao"></a>
### A ter em atenção
* Não ter o chatbot disponível quando o estudante está a responder às outras perguntas de carácter teórico.
* Store das conversas para análise posterior e para completar os dados de treino
    * O store seria (provavelmente) da informação no array wholeConversation no chat-widget.component.ts [aqui](https://github.com/gusmcarreira/Chatbot_Front_End/blob/main/Chatbot-Widget/chatbot/chat-widget/chat-widget.component.ts) linha 35
      * Contém cada mensagem composta por: 
        * from (estudante ou chatbot)
        * text (o que foi dito)
        * type (talvez desnecessário, é a maneira como foi apresentado (i.e, texto, código, butões))
        * date (a data)
  
### Problemas/TODO
* Quando é adicionada uma nova mensagem o chatbot faz logo scroll para baixo (penso que seja devido ao CSS), perfeito seria que ele se mantivesse na mesma posição para o aluno depois ler e não ter de voltar para cima (estou a ter problemas nesta parte).

### Mandar o erro ao rasa
```
this.chatbotService
      // Manda mensagem ao RASA --> chatbot.service.ts
      .sendMessage(this.url, this.userName, { contexto, mensagem })
}
```

A função referida acima encontra-se no ficheiro __Chatbot-Widget/chatbot/chatbot.service.ts__, sendo que depois ele emite um evento ao __chat-widget.component.ts__ para fazer update da conversa.
* O url para a que o rasa se vai conectar
* O id para passar ao rasa (estou a gerar de forma aleatória no file __chatbot.service.ts__ linha 13) [aqui](https://github.com/gusmcarreira/Chatbot_Front_End/blob/main/Chatbot-Widget/chatbot/chatbot.service.ts)
* A mensagem para passar ao rasa:
  * Quando é para mandar o __erro de sintaxe__:
    * contexto: __"Função" || "Condição" || "Repetição" || "Variável"__
    * mensagem: __mensagens simplificadas dos ficheiros tiposErros....ts__
  * Mensagem normal apenas:
    * mensagem: texto da mensagem

