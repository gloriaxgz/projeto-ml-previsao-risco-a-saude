## TL;DR

- Sistema de **Machine Learning** para previsão de risco à saúde, capaz de classificar múltiplas condições médicas com **91.22% de acurácia**.
- Modelo final baseado em **Random Forest**, priorizando desempenho e interpretabilidade.
- Aplicação interativa desenvolvida em **Streamlit**, permitindo a inserção de dados clínicos e a obtenção de previsões em tempo real.
- Análise visual complementar em **Power BI**, orientada por *Storytelling with Data*, focada em identificar **fatores de risco clínicos e comportamentais**.
- Apresentação da **interpretação clínica e com insights de apoio à decisão**, mostrando que o risco é definido por padrões consistentes e passíveis de intervenção precoce.

### Acesse a aplicação clicando <a href='https://projeto-risco-saude.streamlit.app/'> aqui</a>.

# Sistema Inteligente de Previsão de Risco à Saúde

Este projeto consiste no desenvolvimento e deploy de um sistema de Machine Learning (ML) capaz de prever o risco de um indivíduo desenvolver diversas condições médicas (como Diabetes, Hipertensão, Obesidade, etc.) com base em fatores de risco clínicos e comportamentais.

A aplicação final do sistema foi realizada utilizando **Streamlit**, focando em uma experiência interativa e **interpretável** para profissionais de saúde.

Como etapa complementar ao desenvolvimento do modelo preditivo e ao deploy da aplicação, foi realizada uma **análise visual orientada a storytelling**, com o objetivo de transformar os resultados do modelo e os dados clínicos em **insights acionáveis para apoio à decisão em saúde**.

---
## Estrutura do Repositório

| Arquivo/Pasta | Descrição |
| :--- | :--- |
| `Notebook_EDA_Treinamento_completo.ipynb` | **Notebook principal do projeto.** Contém toda a Análise Exploratória de Dados (EDA), pré-processamento, a experimentação com a Clusterização (K-Means) e o treinamento e avaliação do modelo Random Forest final. |
| `Dashboards.pdf` |PDF que contém os Dashboards criados no PowerBI, trazendo importantes insights sobre os dados obtidos. |
| `Apresentação - Análise de Saúde e Prevenção.pdf` |Apresentação de Slides que visa guiar **decisões informadas**, a partir dos dados obtidos demonstrando que o risco à saúde não é definido por um único fator, mas por padrões consistentes que podem ser monitorados, explicados e tratados de forma preventiva. |
| `deploy` / `app.py` | O script principal do Streamlit. Contém a lógica para carregar os artefatos (`.pkl`) e rodar a interface web para que o usuário insira os dados e obtenha a previsão. |
| **`deploy`/`modelo_random_forest.pkl`** | **O modelo de classificação treinado.** Contém o objeto `RandomForestClassifier` final com a acurácia de 91.22%. Utilizado para fazer a previsão do diagnóstico no Streamlit. |
| **`deploy`/`scaler_base.pkl`** | **O objeto de padronização (StandardScaler).** Armazena as médias e desvios-padrão das features de treino. Crucial para garantir que os dados de entrada do usuário sejam transformados na mesma escala em que o modelo foi treinado. |
| **`deploy`/`label_encoder.pkl`** | **O decodificador da variável alvo.** Mapeia os números preditos pelo modelo de volta para os nomes das condições médicas (e.g., 0 → 'Diabetes', 1 → 'Healthy'). |

---

## Problema e Objetivo

O **problema central** abordado é a avaliação de risco e diagnóstico de saúde, dada a multiplicidade de diagnósticos possíveis em um indivíduo. O objetivo primário é desenvolver um sistema que auxilie na identificação de perfis de alto risco e que justifique a predição através da interpretabilidade.

### Metodologia Inicial (Abordagem Híbrida)

Inicialmente, o projeto foi concebido com uma abordagem de ML de duas etapas para maximizar a interpretabilidade:

1. **Clusterização (K-Means):** Agrupar indivíduos em perfis de risco latentes (e.g., Alto Risco, Baixo Risco), gerando a feature `Risk_Profile_Cluster`.
2. **Classificação (Random Forest):** Usar o cluster como uma feature adicional para prever o diagnóstico final.

### Decisão do Modelo Final

Após o treinamento e avaliação, o modelo final escolhido foi o **Random Forest** treinado diretamente com as features originais (Modelo Base).

| Modelo | Acurácia |
| :--- | :--- |
| Abordagem Híbrida (com Cluster) | **90.70%** |
| Modelo Base (sem Cluster) | **91.22%** |

Apesar da abordagem híbrida ter sido desenvolvida para aumentar a interpretabilidade, o **Modelo Base (91.22% de acurácia)** demonstrou um desempenho um pouco superior, sendo o modelo selecionado para o deploy.

---

## Nova Etapa: Análise Visual e Storytelling com Dados

Essa etapa foi desenvolvida utilizando o **Power BI**, seguindo os princípios do livro *Storytelling with Data* (Cole Nussbaumer Knaflic), priorizando clareza, hierarquia visual e mensagens orientadas à decisão — e não ao modelo.

### Pergunta Central da Análise

> **Quais fatores mais aumentam o risco de doenças crônicas e como esses fatores podem apoiar decisões clínicas e intervenções precoces?**

### Abordagem de Storytelling

O foco da narrativa não é o algoritmo em si, mas os **padrões de risco aprendidos a partir dos dados**, com destaque para:

- Identificação dos **fatores clínicos e comportamentais mais associados ao risco**
- Comparação entre condições crônicas e indivíduos saudáveis
- Tradução dos resultados em **insights clínicos interpretáveis**

O modelo de Machine Learning atua como **evidência estatística** que reforça os padrões observados, e não como o protagonista da análise.

### Principais Insights Extraídos

- **BMI como fator dominante:** O Índice de Massa Corporal apresentou a maior importância relativa, atuando como um amplificador de risco para múltiplas condições (Obesity, Hypertension, Diabetes e Arthritis).
- **Marcadores metabólicos decisivos:** Glicose foi determinante para a previsão de Diabetes, evidenciando sinais clínicos claros e detectáveis precocemente.
- **Estilo de vida como modulador de risco:** Horas de sono, nível de estresse, atividade física e dieta funcionam como fatores de ajuste fino, aumentando ou reduzindo a probabilidade de doenças crônicas.
- **Idade como multiplicador, não determinante:** A idade isoladamente apresentou menor impacto do que marcadores clínicos atuais, reforçando a importância de intervenções no presente.
- **Co-ocorrência de condições:** A confusão entre Hipertensão e Artrite sugere sobreposição de marcadores clínicos, reforçando a necessidade de avaliação integrada.

### Visualizações Utilizadas

- **KPIs** para contextualização geral da população
- **Gráficos de barras, scatterplots e violinplots** para análise de marcadores clínicos
- **Anotações textuais** para reforçar as mensagens-chave de cada visual

### Objetivo Final da Etapa Visual

> Transformar dados e modelos em **decisões informadas**, demonstrando que o risco à saúde não é definido por um único fator, mas por padrões consistentes que podem ser monitorados, explicados e tratados de forma preventiva.

Essa etapa reforça o caráter **analítico, interpretável e aplicado** do projeto, conectando Machine Learning, visualização de dados e tomada de decisão em saúde.

---

## Como Rodar o Projeto

Acesse o link da aplicação em:  
<a href='https://trabalhoiagh.streamlit.app/'>https://trabalhoiagh.streamlit.app/</a>

Para rodar a aplicação Streamlit localmente, siga os passos abaixo:

1. **Clone o repositório:**
    ```bash
    git clone https://github.com/gloriaxgz/projeto-ml-previsao-risco-a-saude.git
    cd projeto-ml-previsao-risco-a-saude
    cd deploy
    ```

2. **Instale as dependências:**
    (Assumindo que você tem um arquivo `requirements.txt` com `streamlit`, `pandas`, `scikit-learn`, `joblib`, etc.)
    ```bash
    pip install -r requirements.txt
    ```

3. **Execute o aplicativo Streamlit:**
    ```bash
    streamlit run app.py
    # ou
    streamlit run streamlit_app.py
    ```

A aplicação será aberta automaticamente no seu navegador padrão.

---
