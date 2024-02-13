## Machine learning com Azure
**1. Passo a Passo para Criar um Modelo de Machine Learning no Azure:**

**1.1. Criar uma Conta no Azure:**

-   Acesse o portal Azure em [https://portal.azure.com](https://portal.azure.com/).
-   Crie uma conta se ainda não tiver uma.

**1.2. Criar um Recurso:**

-   Clique em "Create resource" no portal Azure.

**1.3. Pesquisar por Azure Machine Learning:**

-   Na barra de pesquisa, digite "Azure Machine Learning".

**1.4. Selecionar Projeto e Criar:**

-   Escolha o projeto desejado e clique em "Create".

**1.5. Escolher Grupo e Nome do Serviço:**

-   Escolha um grupo existente ou crie um novo.
-   Defina um nome para o serviço.

**1.6. Configurar Região:**

-   Selecione a região como "US".

**1.7. Validar Informações:**

-   Na página de validação, revise as informações inseridas.

**1.8. Aguardar a Conclusão:**

-   Após a validação, aguarde o término do progresso do serviço.

**1.9. Lançar o Studio:**

-   Clique em "Launch studio" quando o serviço for concluído.

**1.10. Selecionar o Workspace:** - Escolha o workspace do seu projeto.

**1.11. Acessar o Automated ML:** - No painel lateral esquerdo, clique em "Automated ML".

**1.12. Configurar as Configurações Básicas:**

-   Job name: mslearn-bike-automl
-   New experiment name: mslearn-bike-rental
-   Description: Automated machine learning for bike rental prediction
-   Tags: none

**1.13. Configurar Tarefa e Dados:**

-   Select task type: Regression
-   Select dataset: Crie um novo dataset com as configurações fornecidas.

**1.14. Configurar as Configurações da Tarefa:**

-   Task type: Regression
-   Dataset: bike-rentals
-   Target column: Rentals (integer)
-   Primary metric: Normalized root mean squared error
-   Explain best model: Unselected
-   Use all supported models: Unselected
-   Allowed models: RandomForest e LightGBM
-   Max trials: 3
-   Max concurrent trials: 3
-   Max nodes: 3
-   Metric score threshold: 0.085
-   Timeout: 15
-   Iteration timeout: 15
-   Enable early termination: Selected

**1.15. Configurar Validação e Teste:**

-   Validation type: Automatic
-   Test dataset: None

**1.16. Configurar Computação:**

-   Select compute type: Serverless
-   Virtual machine type: CPU
-   Virtual machine tier: Dedicated
-   Virtual machine size: Standard_DS3_V2*
-   Number of instances: 1

Ao seguir esses passos, você estará configurando e executando um trabalho de Automated ML no Azure para previsão de aluguel de bicicletas. Certifique-se de ajustar as configurações conforme necessário para atender aos requisitos específicos do seu projeto. 
#
**2. Próxima Etapa: Criar um Modelo Testável no Azure:**

**2.1. Acessar o Job Melhor Classificado:**

-   Após a conclusão de todos os jobs, vá para o job marcado como o melhor (best).

**2.2. Analisar Métricas:**

-   Na aba 'metrics', selecione todos os gráficos disponíveis para análise.

**2.3. Acessar a Aba 'Model':**

-   Vá para a aba 'model'.
-   Clique em "Deploy" e selecione 'Web Service'.

**2.4. Preencher Detalhes do Serviço Web:**

-   Insira um nome e uma descrição para o serviço.
-   Em "Compute type", selecione "Azure Container Instance".
-   Deixe a opção "Enable authentication" selecionada.

**2.5. Iniciar o Deploy:**

-   Clique em "Deploy" e aguarde até que o progresso seja concluído.

Após esses passos, você terá criado e implantado um serviço web a partir do modelo selecionado como o melhor no job de Automated ML. Esse serviço estará hospedado no Azure Container Instance e terá autenticação habilitada.

Lembre-se de que essas instruções podem ser ajustadas conforme as necessidades específicas do seu projeto. Certifique-se de revisar e personalizar as configurações conforme necessário para atender aos requisitos do seu ambiente e aplicação.
#
**3. Como Testar o Modelo Implandato:**

**3.1. Acessar a Barra Lateral:**

-   Na barra lateral esquerda, selecione "Endpoints".

**3.2. Selecionar o Modelo:**

-   Escolha o modelo que você implantou anteriormente.

**3.3. Clicar em Testar:**

-   Dentro das configurações do modelo, clique em "Testar".

**3.4. Inserir JSON de Request:**

-   Uma tela será exibida para inserir um JSON de request. Utilize um formato semelhante ao exemplo fornecido:

jsonCopy code


    {
       "Inputs": {
          "data": [
             {
                "day": 1,
                "mnth": 1,
                "year": 2022,
                "season": 2,
                "holiday": 0,
                "weekday": 1,
                "workingday": 1,
                "weathersit": 2,
                "temp": 0.3,
                "atemp": 0.3,
                "hum": 0.3,
                "windspeed": 0.3
             }
          ]
       },
       "GlobalParameters": 1.0
    }


**3.5. Obter Resultados:**

-   Após inserir o JSON, clique em "Testar" e aguarde a resposta.
-   O retorno será semelhante ao exemplo abaixo:


    {

          "Results": [
              444.27799000000000
           ]
               
    }
#
**4. Para Mais Informações:**

-   Para obter detalhes adicionais ou esclarecimentos, consulte a [documentação completa](https://microsoftlearning.github.io/mslearn-ai-fundamentals/Instructions/Labs/01-machine-learning.html) disponibilizada, que contém o passo a passo detalhado e informações adicionais sobre o laboratório.
