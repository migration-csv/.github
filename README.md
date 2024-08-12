
# Projeto de Migração e Visualização de Dados MovieLens

## Descrição 
Este projeto tem como objetivo migrar os dados do conjunto de dados MovieLens 20M para um banco de dados relacional, criar um programa para ler e inserir esses dados no banco, e desenvolver uma aplicação web que permita aos usuários filtrar e visualizar informações relevantes sobre os filmes. A otimização do tempo de leitura e busca dos dados foi um foco principal do projeto.

## Tecnologias Utilizadas
* Frontend: Next.js
* Backend: Flask
* Banco de Dados: PostgreSQL

## Estrutura do Projeto
### Frontend
O frontend da aplicação é composto por:

* Home: Uma página inicial com um input para upload de arquivos CSV.
* NavBar: Uma barra de navegação que lista todos os arquivos enviados.
* Arquivos salvos: uma lista com detalhamento de todos os arquivos que foram armazenados no banco de dados.
* Busca: Uma aba de busca que permite ao usuário realizar buscas específicas na tabela de filmes e classificações. Ao clicar em um filme específico, o usuário pode visualizar detalhes sobre o filme usando APIs do IMDB e do TMDB.

## Stack utilizada

**Front-end:** Next.js, TailwindCSS

**Back-end:** Flask

**Banco de Dados:** PostgreSQL

## Estrutura do Projeto
**Front-end**

O frontend da aplicação é composto por:

* **Home:** Uma página inicial com um input para upload de arquivos CSV.
* **NavBar:** Uma barra de navegação que lista todos os arquivos enviados.
* **Arquivos salvos:** uma lista com detalhamento de todos os arquivos que foram armazenados no banco de dados.
* **Busca:** Uma aba de busca que permite ao usuário realizar buscas específicas na tabela de filmes e classificações. Ao clicar em um filme específico, o usuário pode visualizar detalhes sobre o filme usando APIs do IMDB e do TMDB.



## Documentação das API's do Back-end

#### Retorna os dados de uma tabela específica com paginação

```http
  GET /tables/{table_name}
```

| Parâmetro    | Tipo       | Descrição                                         |
| :----------- | :--------- | :------------------------------------------------ |
| `table_name` | `string`   | **Obrigatório**. Nome da tabela a ser consultada. |
| `page`       | `integer`  | Número da página a ser retornada. Default: 1      |
| `per_page`   | `integer`  | Número de registros por página. Default: 30       |

---

#### Busca filmes com base em critérios específicos

```http
  GET /search
```

| Parâmetro      | Tipo       | Descrição                                                    |
| :------------- | :--------- | :----------------------------------------------------------- |
| `genres`       | `string`   | Lista de gêneros separados por vírgula.                      |
| `min_rating`   | `integer`  | Classificação mínima dos filmes. Default: 1                  |
| `year`         | `integer`  | Ano de lançamento dos filmes.                                |
| `page`         | `integer`  | Número da página a ser retornada. Default: 1                 |
| `per_page`     | `integer`  | Número de registros por página. Default: 30                  |
| `total_ratings` | `integer` | Número total de classificações dos filmes.                   |

---

#### Retorna a lista de arquivos enviados com paginação

```http
  GET /files
```

| Parâmetro    | Tipo       | Descrição                                         |
| :----------- | :--------- | :------------------------------------------------ |
| `page`       | `integer`  | Número da página a ser retornada. Default: 1      |
| `per_page`   | `integer`  | Número de registros por página. Default: 30       |

---

#### Faz o upload de um arquivo CSV e o processa

```http
  POST /files/{table_name}
```

| Parâmetro    | Tipo       | Descrição                                         |
| :----------- | :--------- | :------------------------------------------------ |
| `table_name` | `string`   | **Obrigatório**. Nome da tabela onde os dados serão inseridos. |
| `file`       | `file`     | **Obrigatório**. Arquivo CSV a ser enviado.       |

---

#### Faz o download de um arquivo enviado

```http
  GET /files/download/{file_name}
```

| Parâmetro    | Tipo       | Descrição                                         |
| :----------- | :--------- | :------------------------------------------------ |
| `file_name`  | `string`   | **Obrigatório**. Nome do arquivo a ser baixado.   |

---

#### Deleta um arquivo enviado e seus dados associados

```http
  DELETE /files/{file_name}
```

| Parâmetro    | Tipo       | Descrição                                         |
| :----------- | :--------- | :------------------------------------------------ |
| `file_name`  | `string`   | **Obrigatório**. Nome do arquivo a ser deletado.  |

---

#### Retorna o ID do TMDB para um filme específico

```http
  GET /movie/get-tmd-id/{movieId}
```

| Parâmetro    | Tipo       | Descrição                                         |
| :----------- | :--------- | :------------------------------------------------ |
| `movieId`    | `integer`  | **Obrigatório**. ID do filme no banco de dados.   |

---

#### Retorna as colunas de uma tabela específica

```http
  GET /tables/columns/{table_name}
```

| Parâmetro    | Tipo       | Descrição                                         |
| :----------- | :--------- | :------------------------------------------------ |
| `table_name` | `string`   | **Obrigatório**. Nome da tabela a ser consultada. |



## Modelo Lógico

![image](https://github.com/user-attachments/assets/4671b2fe-2eaf-46ee-938e-96ad786750b1)
## Referência ao dataset

 - [MovieLens 20M Dataset](https://grouplens.org/datasets/movielens/20m/)



## Explicação Detalhada do Projeto

O objetivo deste projeto é facilitar a migração, análise e visualização dos dados do MovieLens 20M. Os principais componentes do projeto incluem:

**Migração de Dados:** Desenvolvimento de scripts para leitura e inserção dos dados no banco de dados PostgreSQL.

**Frontend:** Criação de uma interface amigável para upload de arquivos CSV, navegação pelos dados e busca específica de filmes.

**Backend:** Implementação de rotas em Flask para gerenciar a interação com o banco de dados e fornecer dados para o frontend.


## Passos Seguidos Durante o Desenvolvimento

**Configuração do Ambiente:** Configuração do ambiente de desenvolvimento com PostgreSQL, Flask e Next.js.

**Desenvolvimento do Backend:** Implementação das rotas e funções para manipulação dos dados.

**Desenvolvimento do Frontend:** Criação das páginas e componentes necessários para interação do usuário.

**Otimização de Consultas:** Uso de views materializadas e indexação para melhorar a performance das consultas.

**Integração com APIs Externas:** Implementação de chamadas às APIs do IMDB e TMDB para enriquecer os dados dos filmes.


## Instalação e Configuração

Para configurar e rodar este projeto, você precisará clonar dois repositórios do GitHub: um para o front-end e outro para o back-end.

```sh
# Clonar o repositório do front-end
git clone https://github.com/organizacao/frontend-repo.git

# Clonar o repositório do back-end
git clone https://github.com/organizacao/backend-repo.git
```

#### Configurando o Back-end

1. Navegue até o diretório do back-end:

```sh
cd backend-repo
```

2. Crie um ambiente virtual e ative-o:

```sh
# No Windows
python -m venv venv
venv\Scripts\activate

# No macOS/Linux
python3 -m venv venv
source venv/bin/activate
```

3. Instale as dependências:

```sh
pip install -r requirements.txt
```

4. Configure as variáveis de ambiente no arquivo `.env`:

```
BD_USER=your_db_user
BD_PASSWORD=your_db_password
BD_HOST=localhost
BD_PORT=5432
BD_NAME=your_db_name
```

5. Inicie o servidor do back-end:

```sh
flask run
```

#### Configurando o Front-end

1. Navegue até o diretório do front-end:

```sh
cd ../frontend-repo
```

2. Instale as dependências:

```sh
npm install
```

3. Configure as variáveis de ambiente no arquivo `.env.local`:

```
NEXT_PUBLIC_API_BASE="http://localhost:port"
NEXT_PUBLIC_API_KEY_TMDB="key"
NEXT_PUBLIC_API_BASE_TMDB="https://api..."
```

4. Inicie o servidor do front-end:

```sh
npm run dev
```

## Autores

- [Lucas Rafael da Silva Costa](https://github.com/Todpig)

- [Renan Andrade de Almeida](https://github.com/RenanMaestrya)
