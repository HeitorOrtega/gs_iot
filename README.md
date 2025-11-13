## 📘 Projeto — Saúde no Trabalho & Saúde da Natureza
- IoT + Deep Learning (Regressão & Classificação) + Visão Computacional (YOLO)
Notebook Colab + JSONs para Consumo Externo

---

## 🎯 Objetivo Geral

### Desenvolver uma aplicação baseada em Deep Learning, apoiada por dados simulados de IoT, capaz de:

- Avaliar a saúde do ambiente de trabalho:
  
```bash
(térmico, acústico, CO₂, iluminação)
```

- Avaliar o impacto ambiental da rotina de trabalho
```bash
(previsão de consumo de energia)
```
- Usar Visão Computacional (YOLO) para analisar o ambiente por imagem
```bash
(detecção de cadeira, pessoa, laptop, plantas e outros objetos relevantes)
```

O sistema produz arquivos JSON, prontos para serem consumidos por qualquer outra disciplina futuramente (Web, Mobile, BD etc.).

## ✅ Componentes de IA Implementados
### ✔ Deep Learning – Regressão

- Modelo Keras que prevê o consumo de energia da próxima hora (pred_kwh_next_1h).

### ✔ Deep Learning – Classificação

- Modelo Keras que classifica o ambiente como:

- saudavel

- moderado

- nao_saudavel

- Com base nos sensores IoT (temperatura, umidade, ruído, co2, iluminação).

### ✔ Visão Computacional – YOLOv8

- Detecta objetos em uma imagem do ambiente de trabalho:

- person

- chair

- laptop

- keyboard

- cell phone

- plant


### Além disso:

- calcula postura_saudavel

- calcula eco_score pela presença de plantas

---

## 📂 Arquivos Gerados

Ao executar o Notebook, são criados automaticamente:
```bash
/content/resultado_previsao_energia.json
/content/resultado_classificacao.json
/content/resultado_yolo.json
```
```bash
dados_iot_14dias.json       # dados simulados
Projeto_Saude_Trabalho_Natureza_IA_14dias.ipynb   # notebook principal
```

---

## ⚙ Como Executar no Google Colab (recomendado)
```bash
Abra o arquivo Projeto_Saude_Trabalho_Natureza_IA_14dias.ipynb

Execute célula por célula

O notebook automaticamente:

lê o dataset dados_iot_14dias.json

treina o modelo de regressão

treina o modelo de classificação

pede upload de imagem para o YOLO

gera os JSONs de saída no /content

Depois basta baixar os JSONs.

```

---

## 🧪 Técnicas de IA utilizadas

- Deep Learning

- TensorFlow / Keras

- Arquiteturas simples (Dense) para regressão e classificação

- Normalização MinMax

- Train/Test split

### Métricas:

- Regressão: MAE

- Classificação: Accuracy

---
## IoT Simulation

| Sensor       | Exemplo                                  |
| ------------ | ---------------------------------------- |
| Temperatura  | 22–29°C                                  |
| Umidade      | 40–70%                                   |
| CO₂          | 350–1200 ppm                             |
| Ruído        | 30–70 dB                                 |
| Luminosidade | 100–500 lux                              |
| Consumo      | variável por uso de laptop, monitor etc. |

---

## Visão Computacional

- YOLOv8n (Ultralytics) pré-treinado

- Extração de objetos por classe + confiança

- Voto simples para postura saudável

- Score ecológico baseado em plantas detectadas

---

## 🧩 Como isso atende aos requisitos da disciplina

| Requisito                         | Atendido? | Onde?                                                     |
| --------------------------------- | --------- | --------------------------------------------------------- |
| Uso de API de Visão Computacional | ✔         | YOLOv8 para análise de imagens                            |
| Modelo de IA Generativa ou DL     | ✔         | Modelos DL de regressão e classificação                   |
| Integração com outras disciplinas | ✔         | Geração dos JSONs para serem consumidos por Web/Mobile/BD |
| Documentação                      | ✔         | Este README + Notebook comentado                          |
| Código executável                 | ✔         | Notebook testado 100%                                     |
| Demonstração funcional da IA      | ✔         | Previsão + Classificação + YOLO funcionando               |

---




