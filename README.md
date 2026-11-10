# Classificador de exercícios com PyTorch

Modelo de visão computacional que identifica qual exercício de academia aparece em uma foto (22 exercícios, como agachamento, flexão, prancha e levantamento terra).

Notebook: `classificador_exercicios.ipynb` (tem o botão "Open in Colab" no topo).

## Resultado final

| Conjunto   | Acurácia |
|------------|----------|
| Validação  | 96,4%    |
| Teste      | 96,4%    |

Treino de 10 épocas, execução completa do notebook de cima para baixo. Os números variam alguns décimos entre execuções, por causa da aleatoriedade do treino (em outra execução obtive 97,0% na validação e 96,7% no teste).

## Curva de aprendizado

Acurácia na validação ao longo do treino:

| Época | Acurácia na validação |
|-------|-----------------------|
| 1     | 86,9%                 |
| 3     | 93,6%                 |
| 5     | 95,2%                 |
| 8     | 96,6% (melhor)        |
| 10    | 96,4%                 |

O maior salto acontece nas primeiras épocas, e o "joelho" da curva fica por volta da época 4. Depois a melhora é pequena e a curva achata em torno de 96,5%. Não observei sinais de overfitting: a perda de treino caiu e a validação subiu junto.

## Como foi feito

- Tipo de problema: classificação de imagens (aprendizado supervisionado)
- Dataset: Workout/Exercise Images (Kaggle), cerca de 13.900 imagens em 22 classes, já dividido em treino, validação e teste
- Modelo: ResNet18 pré-treinado, com transfer learning (só a última camada foi treinada)
- Treino: GPU T4 gratuita do Google Colab
- Tecnologias: Python, PyTorch, torchvision, Hugging Face Datasets, matplotlib

O arquivo do modelo treinado (cerca de 45 MB) não está neste repositório. Ele é gerado ao rodar o notebook.

## Limitações

- As imagens de teste vêm do mesmo dataset do treino. Com fotos de outros ângulos ou iluminação, a acurácia pode ser menor.
- Nos primeiros experimentos, consultei o conjunto de teste mais de uma vez. O ideal é escolher tudo pela validação e usar o teste uma única vez no final.

## Próximos passos

- Testar com fotos reais minhas
- Data augmentation (girar, espelhar e cortar as imagens)
- Fine-tuning de mais camadas do modelo
- Demo na web (Gradio) e API (FastAPI)
