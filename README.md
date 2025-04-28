# Airflow DAG - Fetch Movie Data from OMDB API

Este projeto utiliza **Apache Airflow** para orquestrar um pipeline de dados que busca informações de um filme via **OMDB API**, processa e filtra os dados com base nos votos do IMDb, e salva os resultados como arquivos CSV.

---

## Objetivo

Automatizar a extração de dados de filmes da API OMDB, limpá-los e filtrar apenas os filmes mais populares com base no número de votos no IMDb.

---

## Estrutura do Pipeline

O DAG `fetch_movie_data_from_api` executa as seguintes etapas:

1. **`check_api`** - Usa um `HttpSensor` para verificar se a API da OMDB está respondendo.
2. **`get_api`** - Usa `PythonOperator` para buscar os dados do filme via API e salvar como CSV.
3. **`clean_films`** - Limpa os dados, convertendo o campo `imdbVotes` de string para número.
4. **`get_best_films`** - Filtra os filmes com mais de 800 votos no IMDb.

---

##  Estrutura de Diretórios

```plaintext
/opt/airflow/
├── dags/
│   └── fetch_movie_data_from_api.py
├── data/
    ├── df_films.csv              # Dados brutos do filme
    ├── df_films_cleaned.csv      # Dados tratados
    └── best_films.csv            
