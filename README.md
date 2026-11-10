# Classificador de exercícios com PyTorch

Modelo de visão computacional que identifica qual exercício de academia aparece em uma foto (22 exercícios, como agachamento, flexão, prancha e levantamento terra).

## Resultados

| Conjunto   | Acurácia |
|------------|----------|
| Validação  | 93,1%    |
| Teste      | 93,9%    |

## Como foi feito

- Dataset: Workout/Exercise Images (Kaggle), com cerca de 13.900 imagens em 22 classes
- Modelo: ResNet18 pré-treinado, com transfer learning (só a última camada foi treinada)
- Treino: 3 épocas na GPU T4 gratuita do Google Colab
- Tecnologias: Python, PyTorch, torchvision, Hugging Face Datasets

## Limitações

As imagens de teste vêm do mesmo dataset do treino. Com fotos de outros ângulos ou iluminação, a acurácia pode ser menor.

## Próximos passos

- Testar com fotos reais minhas
- Treinar mais camadas do modelo (fine-tuning)
- Criar uma API com FastAPI para usar o modelo
