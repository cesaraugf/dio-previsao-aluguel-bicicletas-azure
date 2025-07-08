# dio-previsao-aluguel-bicicletas-azure
Projeto prático do bootcamp de Análise de Dados da DIO. Criando um modelo de previsão de aluguel de bicicletas com Azure Automated ML

# Previsão de Demanda de Aluguel de Bicicletas com Azure Machine Learning

## 📖 Visão Geral do Projeto

Este projeto, desenvolvido como parte do bootcamp de Análise de Dados da DIO (Digital Innovation One), demonstra o processo de criação e treinamento de um modelo de Machine Learning para prever a demanda diária de aluguel de bicicletas. Utilizamos a plataforma **Microsoft Azure Machine Learning Studio** e seu recurso de **Machine Learning Automatizado (AutoML)** para encontrar o melhor modelo de regressão para nosso conjunto de dados.

## 🎯 Objetivo

O objetivo principal é construir um modelo preditivo funcional que estime o número de aluguéis de bicicletas com base em fatores sazonais e climáticos, como estação, dia da semana, feriado e condições meteorológicas.

## 🛠️ Ferramentas e Tecnologias Utilizadas

* **Microsoft Azure**: Plataforma de nuvem utilizada para hospedar os serviços de Machine Learning.
* **Azure Machine Learning Studio**: Ambiente de desenvolvimento integrado para projetos de ciência de dados.
* **Azure Automated ML**: Recurso para automatizar o processo de seleção e otimização de modelos de Machine Learning.
* **GitHub**: Para controle de versão e documentação do projeto.

## 📂 O Conjunto de Dados

Utilizamos o conjunto de dados `daily-bike-share.csv`, que contém registros diários de aluguel de bicicletas entre 2011 e 2012. As principais colunas incluem:

* **season**: Estação do ano (1: inverno, 2: primavera, 3: verão, 4: outono)
* **weathersit**: Condição climática (1: claro, 2: névoa/nublado, 3: neve/chuva leve)
* **temp**: Temperatura normalizada em Celsius.
* **atemp**: Sensação térmica normalizada em Celsius.
* **hum**: Umidade normalizada.
* **windspeed**: Velocidade do vento normalizada.
* **rentals**: Contagem total de bicicletas alugadas (nossa **variável alvo**).

## 📝 Passo a Passo do Processo no Azure

O fluxo de trabalho no Azure Machine Learning Studio seguiu estas etapas:

### 1. Criação do Workspace
O primeiro passo foi configurar o ambiente no Azure. Criamos um novo **Workspace do Azure Machine Learning**, definindo a assinatura, um novo grupo de recursos e a região (East US), conforme mostrado abaixo.

### 2. Registro do Conjunto de Dados (Data Asset)
O arquivo `daily-bike-share.csv` foi carregado na plataforma e registrado como um ativo de dados (Data Asset) chamado `alugueldabicicleta-211`, para que pudesse ser facilmente acessado pelo experimento.

### 3. Configuração e Execução do Experimento com AutoML
Criamos um novo trabalho de **Machine Learning Automatizado** com as seguintes configurações:

* **Nome do experimento**: `mslearn-bike-rental`
* **Dados de treinamento**: O ativo de dados `alugueldabicicleta-211`.
* **Coluna de destino (Target Column)**: `rentals` (a variável que queremos prever).
* **Tipo de tarefa**: **Regressão**, pois o objetivo é prever um valor numérico.
* **Métrica primária**: **Erro quadrático médio de raiz normalizado (Normalized Root Mean Squared Error)**, para avaliar o desempenho do modelo.

### 4. Análise dos Resultados
Após a execução do AutoML, que durou aproximadamente 10 minutos, a plataforma testou diversos algoritmos e selecionou o de melhor desempenho.

* **Melhor Algoritmo**: `VotingEnsemble`
* **Desempenho**: O modelo `VotingEnsemble` foi o que obteve o menor **Erro Quadrático Médio de Raiz Normalizado**, indicando a melhor performance entre os modelos testados.

## 📈 Resultados
O projeto resultou na criação de um modelo preditivo de alta performance, validado pela métrica de **Erro Quadrático Médio de Raiz Normalizado**. O uso do AutoML do Azure permitiu testar de forma eficiente múltiplos algoritmos, identificando o modelo `VotingEnsemble` como o mais preciso para prever a demanda de aluguel de bicicletas com base nos dados fornecidos.

## 📁 Estrutura do Repositório

```
.
├── daily-bike-share.csv  # Conjunto de dados utilizado no treinamento
├── printsdoazure.pdf # prints de tela do sistema Azure
├── projeto.txt # projeto da DIO
└── readme.md             # Documentação do projeto (este arquivo)
```
