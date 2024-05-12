# ProjetoGeminiAI

Este projeto demonstra como usar a API Gemini Pro para criar um chatbot simples em Python. O chatbot pode manter uma conversa, lembrar do histórico da conversa e gerar texto criativo. 

## Funcionalidades

* **Integração com a API Gemini Pro:** Utiliza a biblioteca `google-generativeai` para interagir com a API Gemini.
* **Gerenciamento de Conversa:** Armazena o histórico da conversa para contextualizar as respostas.
* **Configurações Flexíveis:** Permite configurar parâmetros como temperatura, top_k e top_p para controlar a criatividade e a aleatoriedade das respostas.
* **Segurança:** Implementa filtros de segurança para garantir que as respostas sejam apropriadas.

## Pré-requisitos

* **Python 3.6 ou superior:** [https://www.python.org/downloads/](https://www.python.org/downloads/)
* **Conta Google Cloud:** [https://cloud.google.com/](https://cloud.google.com/)
* **API Key da Gemini:** Crie uma API Key no Google Cloud Console e ative a API Gemini.

## Configuração do Ambiente

1. **Instalação de dependências:**
    ```bash
    pip install -U -q google-generativeai
    ```
    > **Nota:** Certifique-se de atualizar o `pip` antes de instalar as dependências.

2. **Configuração da API Key:**
    * Armazene a sua API Key no arquivo `secrets.py`:
        ```python
        API_KEY = 'SUA_API_KEY'
        ```
    * **Alternativamente**, você pode armazenar a API Key no Secrets Manager do Google Colab e acessá-la usando:
        ```python
        from google.colab import userdata
        API_KEY = userdata.get('API_KEY')
        ```

3. **Importe as bibliotecas:**
    ```python
    import google.generativeai as genai
    import json
    import base64
    import pathlib
    import pprint
    import requests
    import mimetypes
    from IPython.display import Markdown
    ```

## Execução do Chatbot

1. **Inicialização do Modelo:**
    ```python
    model = 'gemini-1.5-pro-latest'
    genai.configure(api_key=API_KEY)
    gemini = genai.GenerativeModel(model_name=model)
    ```

2. **Início da Conversa:**
    ```python
    chat = gemini.start_chat()
    ```

3. **Envio de Mensagens:**
    ```python
    user_input = "Olá, como você está?"
    response = chat.send_message(user_input)
    print(response.text)
    ```

## Exemplo de Uso

```python
from secrets import API_KEY
import google.generativeai as genai
# ... other imports

# Configurar a API Key
genai.configure(api_key=API_KEY)

# Inicializar o Modelo
model = 'gemini-1.5-pro-latest'
gemini = genai.GenerativeModel(model_name=model)

# Iniciar a conversa
chat = gemini.start_chat()

# Enviar uma mensagem e receber a resposta
user_input = "Qual a capital da França?"
response = chat.send_message(user_input)
print(response.text)
