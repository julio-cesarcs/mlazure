# Trabalhando com Machine Learning na Prática no Azure ML

1 - Selecionei a opção Create a resource

2- Procurarei por machine learning

3 - Selecionei Azure Machine Learning

4 - Selecionei a opção Create

5 - No input Resource group, selecionei Create new e criei um novo resource com o nome de LAB-AI-900

6 - Name: labmachinelearning

7 - Region: East US

8 - Os demais valores, mantive os valores gerados automaticamente

9 - Fui na aba Review + create e verifiquei que a validação passou

10 - Selecionei o botão Create para finalizar a criação

11 - Selecionei o botão go to resource 

12 - Selecionei o botão Launch studio

13 - Selecionei a opção ML automatizado

14 - Selecionei a opção Novo trabalho de ML automatizado

15 - Nome do trabalho: mslearn-bike-automl

16 - Novo nome do experimento: mslearn-bike-rental

17 - Descrição: Aprendizado de máquina automatizado para previsão de aluguel de bicicletas

18 - Em Selecionar tipo de tarefa, selecionei a opção Regressão

19 - Em selecionar os dados, cliquei no botão + Criar

20 - Tipos de dados: 

- Nome: alugueldebicicletas
- Descrição: dados hitóricos de aluguel de bicicletas
- Tipo: Tabular

21 - Fonte de dados:

- Selecionei a opção, De arquivos Web

22 - URL da Web

- URL da Web: https://aka.ms/bike-rentals

23 - Configurações

- Formato do arquivo: Delimitado
- Delimitador: Vírgula
- Codificação: UTF-8

24 - Esquema

- Mantive os valores gerados automáticamente

25 - Examinar

- Criar

26 - Selecionei a opção: alugueldebicicletas

27 - Coluna de destino: rentals (Integer)

28 - Selecionar, Exibir definições de configuração adicionais

29 - Métrica primária: NormalizedRootMeanSquaredError

30 - Desmarcar as opções abaixo

31 - Modelos permitidos: RandomForest e LightGBM

32 - Limites:

- Máximo de avaliações: 3
- Máximo de avaliações simultâneas: 3
- Máximo de nós: 3
- Limite de pontuação da métrica: 0,085
- Tempo limite do experimento (minutos): 15
- Tempo limite de iteração (minutos): 15
- Marcar Habilitar encerramento antecipado

33 - Validar e testar

- Tipo de validação: Divisão de validação de treinamento
- Validação de percentual de dados: 10
- Dados de teste: Nenhum

34 - Computação

- Mantive os valores gerados automáticamente


35 - Enviar trabalho de treinamento

36 - Aguardei o Status mudar para concluído 

37 - Em ML automatizado, selecionei a opção Modelos + trabalhos filho, em seguida selecionei Implantar

38 - Selecionei a opção serviço Web e configurei as seguintes opções:

Nome: predict-rentals
Descrição: Predict cycle rentals
Tipo de computação: Azure Container Instance
Habilitar autenticação: Selecionado

39 - Em Modelos, selecionei mslearnbikeauto0, depois fui em Pontos de extremidade, selecionei predict-rentals e selecionei a aba Testar

40 - Em Testar inseri as informações do JSON abaixo:

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

41 O Resultado foi: 

{
  "Results": [
    444.277099014669
  ]
}
