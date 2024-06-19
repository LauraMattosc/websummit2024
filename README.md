
# Web Summit 2024 Data Analysis

Este Jupyter Notebook contém scripts e análises relacionados ao Web Summit 2024. Ele faz uso de várias bibliotecas Python para coletar, processar e visualizar dados do evento.

## Objetivos

- Coletar dados sobre os eventos e palestrantes do Web Summit 2024.
- Analisar e visualizar as informações coletadas para identificar padrões e insights.

## Estrutura do Notebook

1. **Instalação de Bibliotecas**: As bibliotecas necessárias são instaladas no início do notebook.
    ```python
    pip install pandas matplotlib requests tabulate seaborn
    ```

2. **Importação de Bibliotecas**: Importação das bibliotecas necessárias.
    ```python
    import requests
    import pandas as pd
    import matplotlib.pyplot as plt
    from tabulate import tabulate
    ```

3. **Função para Coletar Dados**: Uma função `fetch_data` é definida para coletar os dados do site do Web Summit.
    ```python
    def fetch_data():
        base_url = 'https://rio.websummit.com/api/list/?slug=schedule&typename=DefaultTemplate_Custompage_FlexibleContent_ScheduleList'
        headers = {
            'sec-ch-ua': '"Google Chrome";v="123", "Not:A-Brand";v="8", "Chromium";v="123"',
            'Referer': 'https://rio.websummit.com/schedule/',
            'sec-ch-ua-mobile': '?0',
            'User-Agent': 'Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/123.0.0.0 Safari/537.36',
            'sec-ch-ua-platform': '"Windows"'
        }

        all_items = []
        page = 1
        while True:
            response = requests.get(f"{base_url}&page={page}", headers=headers)
            if response.status_code != 200:
                print(f"Failed to fetch data: {response.status_code}")
                break

            data = response.json()
            items = data['data']['listItems']
            if not items:
                break

            all_items.extend(items)
            page += 1

        return all_items
    ```

## Como Usar

1. **Clone o repositório**:
    ```sh
    git clone <URL_DO_REPOSITORIO>
    ```

2. **Instale as dependências**:
    ```sh
    pip install pandas matplotlib requests tabulate seaborn
    ```

3. **Execute o notebook**:
    Abra o arquivo `WebSummit2024.ipynb` no Jupyter Notebook ou Jupyter Lab e execute as células.

## Resultados Esperados

- Coleta de dados detalhados sobre os eventos e palestrantes do Web Summit 2024.
- Visualizações gráficas que ajudam a entender a distribuição e características dos eventos.
- Análise tabular que facilita a visualização de informações específicas.

## Contribuições

Sinta-se à vontade para contribuir com este projeto abrindo issues e pull requests. Sugestões e melhorias são bem-vindas!


