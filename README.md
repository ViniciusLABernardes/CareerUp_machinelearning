# CareerUp  
### Plataforma Inteligente de Recomendação Profissional  

---

## 👥 **Integrantes**

- **Vinicius Leandro de Araujo Bernardes** – RM554728 – Turma **2TDSPY**  
- **Edvan Davi Murilo Santos do Nascimento** – RM554733 – Turma **2TDSPZ**  
- **Rafael Romanini de Oliveira** – RM554637 – Turma **2TDSPZ**  

---

#  **Descrição Geral do Projeto **

O CareerUp é uma plataforma criada para ajudar pessoas a evoluírem profissionalmente de forma personalizada. A ideia central é simples: cada usuário informa seu cargo atual e suas principais habilidades, e a ferramenta entrega recomendações feitas sob medida para o perfil dele.
A plataforma analisa as informações inseridas pelo usuário e retorna:
- 🎓 Sugestões de cursos
Indica cursos realmente relevantes para o crescimento daquela pessoa, explicando por que cada curso faz sentido e o que ela vai aprender.
Os cursos são pensados para fortalecer habilidades atuais e desenvolver novas competências importantes para o mercado.
- 💼 Oportunidades de vaga compatíveis
A ferramenta aponta tipos de vagas que combinam com o perfil e com as habilidades do usuário, indicando:
por que aquela vaga é adequada,
quais competências costumam ser exigidas,
e qual o nível estimado (júnior, pleno ou sênior).
- 🚀 Plano de evolução profissional
Além das recomendações imediatas, o CareerUp também sugere habilidades a reforçar, habilidades a adquirir e próximos passos para que o usuário continue crescendo com segurança e clareza.
- 🎯 Objetivo principal
 Ajudar pessoas a darem o próximo passo na carreira com confiança, oferecendo orientações personalizadas, claras e inteligentes — tudo baseado no perfil real de cada usuário.
---


- 1º Baixar a pasta completa do modelo para o computador.

- 2º Converter o modelo HuggingFace para GGUF
- - Clonar o repositório llama.cpp (de preferencia no diretorio onde tambem esta localizado a pasta com o modelo e seus arquivos(OBS NÃO É DENTRO DA PASTA DO MODELO E SIM NA PASTA QUE CONTEM A PASTA DO MODELO)): git clone https://github.com/ggerganov/llama.cpp
- - Instalar dependências: pip install -r llama.cpp/requirements.txt pip install sentencepiece
- - Rodar o script de conversão: python convert_hf_to_gguf.py ../careerup-model-fp16 --outfile ../careerup.gguf --outtype f16
- - O arquivo careerup.gguf será gerado no caminho passado no parâmetro --outfile.

- 3º Instalar o Ollama

- - Baixar e instalar o Ollama no Windows, Linux ou Mac: https://ollama.com/download

- 4º Colocar o modelo GGUF na pasta do Ollama
- - Criar uma pasta para o modelo: C:\Users\<seu-usuario>\.ollama\models
- - Mover o arquivo careerup.gguf para dentro dessa pasta.

- 5º Criar o arquivo Modelfile

- - Dentro da mesma pasta, criar: Modelfile
- - Com conteúdo:
  
        FROM ./careerup.gguf
        TEMPLATE """
        {{ .Prompt }}
        """

- 6º Registrar o modelo no Ollama
- - Rodar no terminal: ollama create careerup -f Modelfile
- - após a criação podemos seguir para a próxima etapa

- 7º Extraia o projeto, dentro de applications.yaml coloque suas credenciais(banco de dados, gmail e endereço do rabbitmq e queue)
- 8º Caso você clique em rodar o projeto no intellij e de um erro como: TypeError: attempted to access missing method … ou TYPETAG :: UNKNOWN RODE esses comandos abaixo no terminal do projeto:
   -   - $env:JAVA_HOME="C:\Program Files\Java\jdk-21"(ou onde o jdk esteja instalado em sua maquina)
       - $env:PATH="$env:JAVA_HOME\bin;$env:PATH"
- 9º Após isso é so rodar o projeto e testar as funções(caso rode com seu database é necessario cadastrar primeiro um usuário)

# **Arquitetura da Aplicação**

A aplicação é estruturada seguindo boas práticas de desenvolvimento, utilizando:

- **Java + Spring Boot**  
- **Arquitetura MVC (Model–View–Controller)**  
- **Validações e serviços desacoplados**  
- **Regras de negócio concentradas em Services e Models**  
- **Repositórios JPA para integração com o banco de dados**  
- **Uso de cache para otimizar recomendações**

### ✔ **Controller**
Responsável por receber requisições REST, validar os dados de entrada e direcionar a execução para os serviços adequados (Services).

### ✔ **Service**
Onde estão as regras de negócio principais:
- Cadastro de usuários  
- Geração de recomendações com base no perfil  
- Armazenamento de feedbacks(emails enviados) 
- Consultas otimizadas  
- Uso de cache para melhorar a performance  

### ✔ **Model**
Classes que representam entidades como:
- **Usuário**
- **Recomendação**
- **Email**
- **Habilidades**

### ✔ **Repository**
Interfaces Spring Data JPA que fazem a comunicação direta com o Oracle Database.

---

# **Mecanismo de Recomendação**

O CareerUp utiliza:
- Análise das habilidades informadas pelo usuário  
- Identificação automática das mais relevantes para o cargo  
- Geração de recomendações profissionais formatadas e personalizadas  
- Cache para economizar chamadas repetidas e acelerar respostas  

---

#  **Funcionalidades Principais**

- Cadastro completo do usuário  
- Autenticação e segurança (Spring Security)  
- Envio de e-mails  
- Registro de feedbacks sobre a plataforma  
- Recomendação profissional dinâmica  
- Histórico de recomendações  
- Operações CRUD para profissionais e habilidades




