# Projeto — Saúde no Trabalho & Saúde da Natureza

**Tecnologias:** IoT + Deep Learning (Regressão & Classificação) + Visão Computacional (YOLO)
**Arquivos principais:** Notebook Colab + JSONs para consumo externo

---

Link Video: https://www.youtube.com/watch?v=EFWH0EfX4wM

---

## Objetivo Geral

Desenvolver uma aplicação baseada em Deep Learning, apoiada por dados simulados de IoT, capaz de:

* Avaliar a saúde do ambiente de trabalho (térmico, acústico, CO₂, iluminação)
* Avaliar o impacto ambiental da rotina de trabalho (previsão de consumo de energia)
* Usar Visão Computacional (YOLO) para analisar o ambiente por imagem (detecção de cadeira, pessoa, laptop, plantas e outros objetos relevantes)

O sistema produz arquivos JSON, prontos para serem consumidos por qualquer outra disciplina futuramente (Web, Mobile, BD etc.).

---

## Componentes de IA Implementados

### Deep Learning – Regressão

* Modelo Keras que prevê o consumo de energia da próxima hora (`pred_kwh_next_1h`).

### Deep Learning – Classificação

* Modelo Keras que classifica o ambiente como:

  * saudável
  * moderado
  * não_saudável
* Baseado nos sensores IoT (temperatura, umidade, ruído, CO₂, iluminação).

### Visão Computacional – YOLOv8

* Detecta objetos em uma imagem do ambiente de trabalho: person, chair, laptop, keyboard, cell phone, plant
* Calcula `postura_saudavel` e `eco_score` (presença de plantas)

---

## Arquivos Gerados

Ao executar o Notebook, são criados automaticamente:

```
/content/resultado_previsao_energia.json
/content/resultado_classificacao.json
/content/resultado_yolo.json
```

Outros arquivos do projeto:

```
dados_iot_14dias.json           # dados simulados
Projeto_Saude_Trabalho_Natureza_IA_14dias.ipynb  # notebook principal
style.css                       # CSS para dashboard
index.html                       # Dashboard HTML/JS
```

---

## Como Executar no Google Colab

1. Abra `Projeto_Saude_Trabalho_Natureza_IA_14dias.ipynb`
2. Execute célula por célula
3. O notebook automaticamente:

   * Lê o dataset `dados_iot_14dias.json`
   * Treina os modelos de regressão e classificação
   * Pede upload de imagem para YOLO
   * Gera os JSONs de saída no `/content`
4. Faça download dos JSONs para consumir em dashboards ou outros projetos

---

## Técnicas de IA utilizadas

* Deep Learning (TensorFlow / Keras)
* Arquiteturas simples (Dense) para regressão e classificação
* Normalização MinMax, Train/Test split

**Métricas:**

* Regressão: MAE
* Classificação: Accuracy

---

## Dashboard HTML/JS

* Consome os JSONs gerados pelo notebook
* Mostra:

  * Previsão de energia (gráfico ou texto)
  * Status do ambiente (tabela)
  * Objetos detectados (YOLO) + postura + eco score

**Exemplo de URLs públicas para teste:**

```
https://raw.githubusercontent.com/seu_usuario/repositorio/main/resultado_previsao_energia.json
https://raw.githubusercontent.com/seu_usuario/repositorio/main/resultado_classificacao.json
https://raw.githubusercontent.com/seu_usuario/repositorio/main/resultado_yolo.json
```

---

## Exemplo de JSON

### resultado_previsao_energia.json

```json
{
  "timestamp": "2025-11-13T18:20:00",
  "pred_kwh_next_1h": 27.8,
  "mae_test": 1.25
}
```

### resultado_classificacao.json

```json
{
  "timestamp": "2025-11-13T18:20:00",
  "ultima_leitura": {
    "temperatura": 27.45,
    "umidade": 50,
    "co2": 420,
    "ruido": 35,
    "luminosidade": 350
  },
  "pred_probabilidades": {
    "saudavel": 0.7,
    "moderado": 0.25,
    "nao_saudavel": 0.05
  },
  "pred_label": "saudavel",
  "accuracy_test": 0.92
}
```

### resultado_yolo.json

```json
{
  "timestamp": "2025-11-13T18:20:00",
  "objetos_detectados": [
    {"classe": "person", "conf": 0.98},
    {"classe": "chair", "conf": 0.95},
    {"classe": "plant", "conf": 0.88}
  ],
  "postura_saudavel": true,
  "indicadores_natureza": {
    "eco_score": 0.88,
    "plantas_detectadas": 3
  }
}
```

---

## Como isso atende aos requisitos da disciplina

| Requisito                         | Atendido? | Onde?                                                     |
| --------------------------------- | --------- | --------------------------------------------------------- |
| Uso de API de Visão Computacional | ✔         | YOLOv8 para análise de imagens                            |
| Modelo de IA Generativa ou DL     | ✔         | Modelos DL de regressão e classificação                   |
| Integração com outras disciplinas | ✔         | Geração dos JSONs para serem consumidos por Web/Mobile/BD |
| Documentação                      | ✔         | Este README + Notebook comentado                          |
| Código executável                 | ✔         | Notebook testado 100%                                     |
| Demonstração funcional da IA      | ✔         | Previsão + Classificação + YOLO funcionando               |

---

## Roteiro de vídeo de apresentação

1. Apresentar objetivo do projeto (saúde no trabalho + impacto ambiental)
2. Mostrar notebook Colab:

   * Simulação de sensores IoT
   * Treinamento de modelos DL (regressão e classificação)
   * Upload de imagem e detecção YOLO
3. Mostrar JSONs gerados (`resultado_previsao_energia.json`, etc.)
4. Abrir dashboard no navegador:

   * Gráficos / tabelas / lista de objetos
   * Evidenciar integração com front-end
5. Conclusão: destacar integração interdisciplinar e uso de IA para monitoramento ambiental

---

## Observações Finais

* Dados IoT são simulados para demonstração
* Bibliotecas usadas: TensorFlow, Keras, Ultralytics YOLOv8, Pandas, Numpy
* Projeto desenvolvido por **Heitor Ortega Silva**
* Notebook pronto para ser executado no Google Colab

---

Equipe WorkClean


Heitor Ortega Silva - 557825

Pedro Cardoso Saraiva - 555160

Marcos Lourenço - 556496

Curso: Análise e Desenvolvimento de Sistemas - FIAP
