# Detecção de SPAM com Modelos de Aprendizado de Máquina

## TL;DR
Todos os gráficos e detalhes referentes a este documento estão disponíveis no Jupyter Notebook
[Assignment LSTM With Glove For SPAM Detection.ipynb](Assignment_LSTM_with_Glove_for_SPAM_Detection.ipynb)

Este projeto compara dois modelos para a detecção de mensagens SPAM:

- **Modelo LSTM com vetorização GloVe**: Utiliza uma rede neural recorrente para capturar relações sequenciais nas mensagens.
- **Rede Neural Simples com TF-IDF**: Emprega uma rede neural densa usando vetorização TF-IDF para representar as mensagens com base na frequência dos termos.

Ambos os modelos apresentaram alta acurácia, mas com diferenças nas métricas de precisão e recall para as classes "ham" (não-spam) e "spam".

## Introdução

Este repositório contém um estudo comparativo entre duas abordagens distintas para a detecção de mensagens SPAM:

1. **Modelo LSTM com Embeddings GloVe**: Utiliza uma rede LSTM com embeddings de palavras pré-treinados para capturar contextos semânticos.
2. **Rede Neural Simples com TF-IDF**: Aplica uma rede neural densa simples com vetorização TF-IDF, focando na importância dos termos específicos do dataset.

## Dataset

Utilizamos o dataset disponível no [Kaggle](https://www.kaggle.com/datasets/team-ai/spam-text-message-classification), composto por mensagens rotuladas como "ham" (não-spam) ou "spam".

## Análise Exploratória dos Dados

- **Distribuição das Classes**: O dataset é desbalanceado, com predominância de mensagens "ham".
- **Comprimento das Mensagens**: Mensagens "ham" geralmente são mais longas que mensagens "spam".
- **Nuvens de Palavras**: Visualizamos os termos mais frequentes em cada categoria através de nuvens de palavras, identificando padrões e palavras-chave.

## Pré-Processamento dos Dados

Etapas realizadas:

- **Conversão para minúsculas**.
- **Remoção de pontuação**.
- **Tokenização**.
- **Remoção de stopwords**.
- **Lematização**.

## Modelos Utilizados

### Modelo 1: LSTM com Embeddings GloVe

- **Vetorização**: Embeddings GloVe pré-treinados.
- **Arquitetura**:
  - Camada de Embedding (não treinável) com vetores GloVe.
  - Camadas LSTM bidirecionais para capturar dependências sequenciais.
  - Camadas densas com função de ativação ReLU.
  - Camada de saída com função de ativação sigmoide.

### Modelo 2: Rede Neural Simples com TF-IDF

- **Vetorização**: TF-IDF para capturar a importância dos termos específicos do dataset.
- **Arquitetura**:
  - Camada densa de entrada com função de ativação ReLU.
  - Camada de dropout para evitar overfitting.
  - Camada de saída com função de ativação sigmoide.

## Avaliação e Resultados

### LSTM com GloVe

- **Acurácia**: **97,31%**.
- **Erros**:
  - 15 mensagens "ham" classificadas como "spam".
  - 15 mensagens "spam" classificadas como "ham".
- **Observações**:
  - Bom desempenho na identificação de mensagens "ham".
  - Espaço para melhorias na detecção de mensagens "spam".

### Rede Neural Simples com TF-IDF

- **Acurácia**: **97,58%** Levemente superior ao modelo LSTM.
- **Erros**:
  - 3 mensagens "ham" classificadas como "spam".
  - 24 mensagens "spam" classificadas como "ham".
- **Observações**:
  - Excelente em minimizar falsos positivos (mensagens "ham" como "spam").
  - Maior número de falsos negativos (mensagens "spam" não detectadas).

## Comparação dos Resultados

- **Modelo LSTM com GloVe**:
  - Melhor na detecção de mensagens "spam" em comparação com a rede neural simples.
  - Pode ter sido limitado pelo tamanho reduzido do dataset e por não ajustar os embeddings durante o treinamento.
  
- **Rede Neural Simples com TF-IDF**:
  - Melhor em evitar falsos positivos, classificando corretamente as mensagens "ham".
  - Deixa passar mais mensagens "spam" não detectadas.

### Possíveis Razões para os Resultados

- **Tamanho do Dataset**: Modelos LSTM geralmente requerem mais dados para generalizar bem.
- **Embeddings GloVe**: Por serem treinados em textos genéricos, podem não capturar peculiaridades de mensagens de SPAM.
- **TF-IDF**: Captura termos específicos do dataset, beneficiando a detecção baseada em frequência de palavras.
- **Complexidade do Modelo**: Modelos mais simples podem generalizar melhor em datasets menores.

## Conclusão

Ambas as abordagens são eficazes na detecção de SPAM, porém apresentam trade-offs:

- **Modelo LSTM com GloVe**: Melhor na detecção de "spam", mas requer mais dados e ajustes.
- **Rede Neural com TF-IDF**: Simples e eficaz para datasets menores, excelente em identificar mensagens "ham", mas pode não detectar todo o "spam".


## Como Executar o Projeto

O código completo está disponível no Jupyter Notebook [Assignment - LSTM with Glove for SPAM Detection.ipynb.ipynb](Detecção_de_SPAM.ipynb) neste repositório.

## Referências

- [Embeddings GloVe](https://nlp.stanford.edu/projects/glove/)
- [NLTK Documentation](https://www.nltk.org/)
- [TensorFlow Keras Documentation](https://www.tensorflow.org/api_docs/python/tf/keras)
- [Scikit-learn Documentation](https://scikit-learn.org/stable/)
- [Basics of Using Pre-trained GloVe Vectors in Python](https://medium.com/analytics-vidhya/basics-of-using-pre-trained-glove-vectors-in-python-d38905f356db)
- [Simple Guide for LSTM and Glove Embeddings](https://www.kaggle.com/code/samarthsarin/simple-guide-for-lstm-and-glove-embeddings)
- [Dataset de Spam - Kaggle](https://www.kaggle.com/datasets/team-ai/spam-text-message-classification)

---

**Observação**: Este projeto foi desenvolvido para fins educacionais, ilustrando a aplicação de diferentes técnicas de processamento de linguagem natural e aprendizado de máquina na detecção de SPAM.