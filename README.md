# Run OpenWebUI no Google Colab

Este repositório contém um notebook Jupyter especialmente preparado para ser executado no Google Colab. Ele demonstra, de forma automatizada, como configurar e executar o **OpenWebUI** integrado com ferramentas como **ngrok** e **ollama**, possibilitando a criação de um ambiente prático para testar aplicações de IA diretamente na nuvem.

## Funcionalidades

- **Execução do OpenWebUI:** Lança a interface web do OpenWebUI em uma porta específica (por padrão, a 8081).
- **Integração com Ollama:** Permite (opcionalmente) baixar e executar um modelo de IA com Ollama.
- **Acesso Remoto com ngrok:** Cria um túnel seguro para expor o serviço localmente em uma URL pública.
- **Gerenciamento de Processos:** Utiliza o `tmux` para iniciar e manter os serviços em background, garantindo que eles continuem rodando mesmo se a sessão do Colab for encerrada.

## Requisitos

- **Google Colab:** O notebook foi desenvolvido para ser executado no ambiente do Colab.
- **Tokens de Acesso:**
  - `HF_TOKEN`: Token de autenticação para acessar recursos e modelos no Hugging Face.
  - `NGROK_TOKEN`: Token para configuração do ngrok, necessário para a criação do túnel.
- Conhecimentos básicos sobre o uso de notebooks e definição de variáveis de ambiente.

## Como Utilizar

1. **Abra o Notebook:**
   - Você pode clonar este repositório ou abrir o arquivo [run_openwebui_colab.ipynb](https://github.com/rodrigocardosodev/run-openweb-ui-google-colab/blob/master/run_openwebui_colab.ipynb) diretamente no Google Colab.

2. **Configure as Variáveis de Ambiente:**
   - Defina os tokens de acesso necessários (`HF_TOKEN` e `NGROK_TOKEN`). No Colab, isso pode ser feito com os comandos:
     ```python
     # Exemplo:
     %env HF_TOKEN=seu_token_aqui
     %env NGROK_TOKEN=seu_token_aqui
     ```
     
3. **Execute os Blocos de Código:**
   - O notebook está dividido em várias etapas:
     - **Atualização e Instalação de Dependências:** Atualiza o sistema, instala o tmux, atualiza o pip e instala as bibliotecas necessárias (como `huggingface_hub` e `open-webui`), além de configurar o ngrok e o ollama.
     - **Login no Hugging Face:** Realiza a autenticação com o token `HF_TOKEN` para acessar os recursos da plataforma.
     - **(Opcional) Download do Modelo:** Caso deseje utilizar um modelo específico com Ollama, descomente o comando correspondente para fazer o download.
     - **Configuração do ngrok:** Adiciona o token ao ngrok para permitir a criação do túnel.
     - **Início dos Serviços:** Utiliza o `tmux` para iniciar os serviços do Ollama, OpenWebUI e ngrok em sessões separadas, garantindo que continuem ativos em background.
     - **Verificação das Sessões:** Executa `!tmux ls` para listar as sessões ativas e confirmar que os serviços estão rodando corretamente.
   
4. **Acesse o Serviço:**
   - Após a criação do túnel pelo ngrok, você receberá uma URL pública que pode ser utilizada para acessar a interface do OpenWebUI remotamente.

## Possíveis Problemas e Soluções

- **Tokens não Definidos:**  
  Se o script exibir “Token não encontrado”, verifique se os tokens `HF_TOKEN` e `NGROK_TOKEN` foram corretamente definidos.

- **Serviço Não Iniciado:**  
  Use o comando `!tmux ls` para confirmar se as sessões estão ativas. Caso alguma sessão esteja faltando, tente reexecutar a célula correspondente.

- **Limitações do Google Colab:**  
  O Colab pode impor restrições em sessões de longa duração ou em termos de desempenho. Planeje o uso do ambiente de acordo com essas limitações.

## Considerações Finais

Este script oferece uma solução prática para rodar o openweb-ui e testar aplicações de IA diretamente no Google Colab, integrando com ferramentas como ngrok e ollama. Ele automatiza todo o processo de configuração e execução dos serviços, proporcionando uma experiência simples e integrada para desenvolvedores e entusiastas. Se você busca um fluxo de trabalho eficiente para experimentar com interfaces de IA sem precisar de uma infraestrutura local complexa, esta ferramenta é uma excelente escolha.

Caso tenha dúvidas ou sugestões, sinta-se à vontade para abrir uma _issue_ neste repositório.

## Licença

Este projeto está licenciado sob a [MIT License](LICENSE).

---

Bom uso e boas experimentações!
