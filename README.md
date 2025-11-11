# Estudo de Caso: Fábrica de Conteúdo Automatizada (Make.com)

Este projeto é um estudo de caso de uma "Fábrica de Conteúdo" multimodal, construída inteiramente na plataforma Make.com. A automação funciona como um "jornalista-robô", criando um boletim informativo diário completo (texto e áudio) para os clientes de uma associação comercial.

---

## 🎯 O Problema de Negócio

Uma associação comercial de grande porte precisava enviar um boletim matinal diário para seus associados. Esse boletim precisava conter informações de alto valor e de diversas fontes, como:

* Notícias locais e nacionais.
* Notícias específicas do setor de varejo.
* Indicadores financeiros (Bolsa, Dólar, Petróleo).
* Previsão do tempo local.
* Datas comemorativas e uma frase motivacional.

Compilar tudo isso manualmente levava horas de trabalho de um jornalista ou profissional de marketing, todos os dias.

## solution 🛠️ A Arquitetura da Solução

Para automatizar 100% deste processo, desenhei um cenário complexo no Make.com que executa as seguintes etapas:

1.  **Web Scraping (HTTP Modules):** A automação inicia e faz requisições (GET) para 9 fontes de dados diferentes, incluindo portais de notícias, sites de finanças, previsão do tempo e bancos de dados de datas comemorativas.
2.  **Limpeza de Dados (HTML to Text):** O conteúdo HTML bruto de cada site é limpo e convertido em texto puro.
3.  **Curadoria com IA (Gemini):** Todos os pedaços de texto limpo são enviados para um "prompt mestre" no Google Gemini. A IA atua como um editor-chefe, recebendo os dados brutos e usando um template rigoroso para escrever um boletim coeso, profissional e bem formatado.
4.  **Geração de Áudio (OpenAI TTS):** O texto final do boletim é enviado para a API da OpenAI (TTS) para gerar uma versão em áudio (MP3) do boletim, criando um produto multimodal (para quem prefere ouvir no carro, por exemplo).
5.  **Hospedagem de Mídia (Google Drive):** O arquivo MP3 gerado é automaticamente enviado para uma pasta no Google Drive e seu link de compartilhamento público é criado.
6.  **Armazenamento (Make Datastore):** O texto final e o link do áudio são salvos em um banco de dados (Datastore) com o status "pendente", prontos para serem enviados ao cliente pelo próximo sistema.

## 🖼️ Visualização do Fluxo

Abaixo está um screenshot da arquitetura do cenário no Make.com. (Informações confidenciais, como nomes de clientes e chaves de API, foram omitidas).

<img width="1690" height="814" alt="image" src="https://github.com/user-attachments/assets/06524f37-a6ac-4902-8e68-9206d21edf07" />


## 🔑 Destaques Técnicos

* **Plataforma:** Make.com (Integromat)
* **Técnica Principal:** Web Scraping (HTTP Requests)
* **IA & LLMs:** Google Gemini (Curadoria e Redação), OpenAI (Geração de Áudio TTS)
* **Integrações:** Google Drive (Hospedagem de Mídia), Make Datastore (Banco de Dados)

## 📈 Resultado (Impacto no Negócio)

* **100% de Automação:** Eliminou 2-3 horas de trabalho manual *diário*, liberando a equipe de marketing para focar em estratégia.
* **Conteúdo Multimodal:** Entregou valor agregado ao fornecer o boletim em formato de texto e áudio (MP3).
* **Consistência da Marca:** Garantiu que o boletim seja sempre enviado no mesmo horário, com o mesmo tom de voz e formato.
* **Riqueza de Dados:** Criou um produto de informação que seria muito caro de se produzir manualmente todos os dias.
