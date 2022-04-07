# Chatbot_Front_End
Chatbot widget with Angular and REST for a chatbot developed with RASA

O modulo/serviço/componente está na pasta Chatbot-Widget, com as respetivas imagens.

### A mudar
* O id para passar ao rasa (estou a gerar de forma aleatória no ficheiro __chat-widget.component.ts__ linha 135)
* o url no file __chat-widget.component.ts__ linha 25

### A ter em atenção
* Não ter o chatbot disponível quando o estudante está a responder às outras perguntas de carácter teórico.
* Store das conversas para análise posterior e para completar os dados de treino (não preocupar muito com isto agora).
    * O store seria (provavelmente) da informação no array wholeConversation no chat-widget.component.ts

### Mandar o erro ao rasa
```
this.chatbotService
      // Manda mensagem ao RASA --> chatbot.service.ts
      .sendMessage(this.url, this.userName, { contexto, mensagem })
}
```

A função referida acima encontra-se no ficheiro __Chatbot-Widget/chatbot/chatbot.service.ts__, sendo que depois ele emite um evento ao __chat-widget.component.ts__ para fazer update da conversa.
* O url para em que o rasa se vai conectar
* O id para passar ao rasa (estou a gerar de forma aleatória no file __chat-widget.component.ts__ linha 135)
* A mensagem para passar ao rasa 
    * contexto: __"Função" || "Condição" || "Repetição" || "Variável"__
    * mensagem: __mensagens simplificadas dos ficheiros tiposErros....ts__
* CUIDADO, a localização dos ficheiros consoante o tipo/erro pode ser encontrado em __Chatbot/actions/custon/Docs/ErrorGuidance/....txt__, ou seja o que é passado tem de coincidir exatamente com o que está no ficheiro, sendo que a categoria do erro também tem de coincidir com o nome da pasta.
