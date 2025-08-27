# Deteccao-de-Caes-e-Gatos
Este projeto implementa um sistema de detecção de objetos para identificar cães e gatos utilizando YOLOv5. O modelo é treinado em um dataset especializado e oferece detecção em tempo real com alta precisão.


## 📋 Descrição
O projeto utiliza a arquitetura YOLOv5 (You Only Look Once version 5) para detectar e classificar cães e gatos em imagens. O sistema inclui todo o pipeline de machine learning, desde o download do dataset até o treinamento e validação do modelo.


## 🚀 Funcionalidades
- **Download Automático do Dataset:** Integração com Roboflow para baixar o dataset de cães e gatos  
- **Treinamento Customizado:** Configuração personalizada do modelo YOLOv5  
- **Monitoramento Visual:** Acompanhamento em tempo real do progresso do treinamento  
- **Validação Automática:** Avaliação do modelo com métricas de performance  
- **Predição em Imagens:** Interface para fazer detecções em novas imagens  
- **Análise de Resultados:** Visualização de gráficos e matriz de confusão  


## 📊 Dataset
O projeto utiliza o dataset Dog and Cat Detection do Roboflow, contendo:
- 2 classes: cat e dog 
- Imagens balanceadas e anotadas  
- Divisão em train/val/test  


## 🛠️ Instalação
**Pré-requisitos:**
- Python 3.8+
- GPU (recomendado)
- Notebook Google Colab (GPUs: T4)

**Configuração**

1. Instale as dependências:
```
pip install -r requirements.txt
```

2. Configure sua chave API do Roboflow: 
```
# No Google Colab:  
from google.colab import userdata  
userdata.set('Roboflow', 'sua_chave_api')
```

# 🎯 Uso
**Treinamento do Modelo**
Execute o pipeline completo:
```
from DeteccaoRedeYolo import main

# Executar treinamento completo
model_path = main()
```

**Configuração Personalizada**
```
# Treinar com parâmetros customizados
model_path = train_with_visual_feedback(
    config_path='dog_cat_config.yaml',
    epochs=100,
    batch_size=16,
    img_size=640
)
```

**Predição em Imagens**
```
# Fazer detecção em uma imagem
results = predict_image(
    model_path='runs/train/dog_cat_model',
    image_path='caminho/para/imagem.jpg',
    conf_threshold=0.25
)

# Visualizar resultados
results.show()
results.save()
```

## ⚙️ Configurações de Treinamento
Parâmetros padrão:
- **Épocas:** 50-100
- **Batch Size:** 16
- **Tamanho da Imagem:** 640x640
- **Otimizador:** SGD
- **Learning Rate:** Automático
- **Pesos Iniciais:** YOLOv5s pretreinado


## 📈 Resultados
O modelo produz várias métricas de performance:

- **mAP@0.5:** Precisão média em IoU 0.5
- **mAP@0.5:0.95:** Precisão média em múltiplos IoUs
- **Precision:** Taxa de verdadeiros positivos
- **Recall:** Capacidade de detecção
- **F1-Score:** Balanceamento entre precision e recall


## 📊 Métricas de Performance
O modelo typically alcança:

- **mAP@0.5:** >90%
- **Precision:** >85%
- **Recall:** >88%
- **FPS:** 30-60 (dependendo da hardware)


## 🏆 Reconhecimentos
**Ultralytics** pelo YOLOv5
**Roboflow** pelo dataset e infraestrutura
Comunidade de Visão Computacional
