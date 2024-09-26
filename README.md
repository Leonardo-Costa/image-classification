# Projeto: Classificação de Imagens de Monet e Renoir com Transfer Learning e CNN

Este projeto tem como objetivo classificar imagens dos pintores Monet e Renoir utilizando técnicas de Transfer Learning e uma rede convolucional (CNN) construída do zero. O projeto consiste em dois notebooks principais, cada um abordando uma abordagem diferente para o problema de classificação:

1. `./notebooks/vgg.ipynb` — Classificação com Transfer Learning utilizando o modelo VGG16.
2. `./notebooks/keras.ipynb` — Classificação com uma CNN construída do zero utilizando o Keras.

## Dataset utilizado:

O dataset utlizado contém 2696 imagens de quadros impressionistas geradas sinteticamente pela Stable Diffusion, 1320 com o estilo do pintor Claude Monet, e 1376 com o estilo do Pierre Auguste Renoir. O dataset foi gerado em agosto de 2023 como parte de um artigo apresentado no Workshop de Inteligência Artificial do ICT-Unifesp.

## 1. vgg.ipynb

Este notebook faz uso de **Transfer Learning** com o modelo **VGG16** pré-treinado no dataset **ImageNet**. As imagens são convertidas para escala de cinza e depois duplicadas em três canais para serem compatíveis com a entrada do VGG16. Os passos principais são:

- **Pré-processamento das Imagens**: As imagens são redimensionadas, convertidas para escala de cinza e normalizadas.
- **Transfer Learning com VGG16**: Um modelo baseado no VGG16 é carregado e a camada de classificação é ajustada para o problema binário (Monet ou Renoir).
- **Treinamento e Avaliação**: O modelo é treinado por 50 épocas e avaliado com métricas como acurácia, matriz de confusão e F1-Score.

### Principais Seções:
- Download e extração do dataset de imagens.
- Pré-processamento das imagens.
- Configuração e treinamento do modelo VGG16.
- Avaliação do modelo com matriz de confusão e métricas de desempenho.

### Dependências:
- TensorFlow/Keras
- Pandas
- NumPy
- Matplotlib
- Seaborn

### Principais Métricas Avaliadas:
- Acurácia
- Acurácia Balanceada
- F1-Score
- Precisão
- Recall

## 2. keras.ipynb

Este notebook constrói uma **CNN do zero** utilizando a biblioteca **Keras**. Ao contrário do primeiro notebook, este modelo não faz uso de Transfer Learning e é projetado para processar imagens diretamente em escala de cinza. O fluxo inclui:

- **Construção de uma CNN**: Um modelo CNN com várias camadas convolucionais, pooling e dropout é construído para classificar as imagens.
- **Treinamento e Avaliação**: O modelo é treinado e avaliado em termos de acurácia, matriz de confusão e outras métricas de desempenho.

### Principais Seções:
- Download e extração do dataset de imagens.
- Pré-processamento das imagens.
- Construção e treinamento de uma CNN customizada.
- Avaliação do modelo com matriz de confusão e métricas de desempenho.

### Dependências:
- TensorFlow/Keras
- Pandas
- NumPy
- Matplotlib
- Seaborn

### Principais Métricas Avaliadas:
- Acurácia
- Acurácia Balanceada
- F1-Score
- Precisão
- Recall

## Estrutura do Projeto

```
.
├── notebooks
│   ├── vgg.ipynb    # Transfer Learning com VGG16
│   ├── keras.ipynb  # CNN customizada com Keras
└── README.md        # Este arquivo
```

## Análise dos Resultados
Ambos os modelos, tanto o de Transfer Learning quanto o construído do zero, apresentaram bons resultados na tarefa de classificação de imagens de Monet e Renoir. No entanto, alguns pontos importantes devem ser destacados:

Modelo VGG16: Graças ao uso de Transfer Learning, o VGG16 conseguiu alcançar uma acurácia elevada de maneira mais rápida, aproveitando o aprendizado de características já extraídas em um dataset amplo como o ImageNet. A acurácia foi alta no conjunto de testes, e o modelo teve bom desempenho ao diferenciar entre as duas classes, como mostrado pela matriz de confusão. Isso reforça o poder de generalização de modelos pré-treinados.

Modelo CNN Customizado: Apesar de o modelo CNN construído do zero ter uma arquitetura mais simples e ser mais difícil de treinar, ele conseguiu alcançar resultados sólidos, embora um pouco inferiores ao VGG16. Isso é esperado, dado que o modelo precisa aprender todas as características diretamente das imagens do dataset, sem aproveitar o aprendizado de um modelo maior.

Desempenho Geral: Ambos os modelos mostraram acurácias equilibradas, com valores de F1-Score, Precisão, e Recall indicando que não houve um grande desbalanceamento entre as previsões de ambas as classes. A análise dos exemplos preditos, juntamente com a matriz de confusão, revela que os erros ocorrem em casos onde as características visuais podem ser bastante similares entre Monet e Renoir.

Em suma, o VGG16 é a escolha mais eficiente em termos de tempo e desempenho, mas a CNN customizada também é uma opção viável para problemas semelhantes. 