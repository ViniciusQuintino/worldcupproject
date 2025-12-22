# 📊 World Cup Project


## 📌 Visão Geral
Projeto de dashboard interativo com foco na análise histórica das Copas do Mundo,
explorando desempenho das seleções, títulos, participações e estatísticas de jogadores.


## 🎯 Objetivo
Apresentar uma visão analítica e histórica das Copas do Mundo, apoiando
explorações temporais e comparações entre seleções e jogadores.


## 📂 Fonte dos Dados
Os dados utilizados foram obtidos a partir de bases públicas relacionadas às Copas do Mundo.


## 🔄 Etapas do Projeto


### 🧹 Limpeza e Tratamento dos Dados (Python)
Na etapa inicial do projeto, foi realizada a limpeza e preparação dos dados.
Como se trata de uma base de dados abrangente, contendo informações sobre
Copas do Mundo masculinas e femininas, o primeiro passo foi aplicar
um filtro para manter somente os registros relacionados às Copas do
Mundo masculinas.

Essa decisão foi tomada considerando que o escopo do projeto está alinhado
à Copa do Mundo de 2026, que se refere a uma competição masculina, garantindo
maior coerência e consistência na análise.

<img width="714" height="371" alt="image" src="https://github.com/user-attachments/assets/251b1470-619d-4a09-8ec8-3280ae247a63" />

A limpeza e preparação dos dados foi realizada em Python, utilizando Pandas,
com foco na padronização e filtragem dos registros.

📎 O notebook completo com o processo de limpeza pode ser acessado em: [worldcupproject/limpeza.ipynb](https://github.com/ViniciusQuintino/worldcupproject/blob/main/limpeza.ipynb)



### 🧠 Modelagem e Importação dos Dados
A modelagem de dados foi estruturada seguindo boas práticas de BI, utilizando
um modelo estrela estendido (galaxy schema), no qual a tabela de partidas
representa a principal tabela fato do projeto.

As Copas do Mundo foram modeladas como dimensão, fornecendo o contexto histórico
e temporal das análises, enquanto outras tabelas fato registram
eventos específicos, como gols, prêmios individuais e participação das seleções.

Dimensões como seleções, jogadores e torneios são usadas em várias tabelas fato, 
permitindo analisar os dados de diferentes maneiras

<img width="1386" height="785" alt="image" src="https://github.com/user-attachments/assets/ada7100a-8ef0-4bfd-a126-1c18b3c79ce5" />

### 🧮 Criação de Medidas (DAX)

As medidas do projeto foram desenvolvidas utilizando DAX, seguindo boas práticas para que fiquem 
fáceis de ler e reutilizar. Elas mostram desempenho das seleções, estatísticas das partidas, 
análises históricas das Copas do Mundo e métricas individuais dos jogadores.

Para ter uma visão mais detalhada das medidas, acesse [worldcupproject
/medidas.md](https://github.com/ViniciusQuintino/worldcupproject/blob/main/medidas.md)

### 📊 Desenvolvimento da Dashboard

O projeto conclui no desenvolvimento de uma dashboard interativa,
permitindo a exploração histórica das Copas do Mundo, desempenho das seleções,
estatísticas de jogadores e comparações entre edições do torneio.

#### Tela 1 – Visão Geral do Torneio
Esta tela apresenta uma visão histórica das Copas do Mundo, incluindo
ranking de seleções por títulos, número de participações e evolução ao longo
do tempo.

<img width="1424" height="803" alt="image" src="https://github.com/user-attachments/assets/400eb705-41e5-4574-a082-f6a1d1b3595c" />

#### Tela 2 – Análise por Seleção
Aqui é possível explorar o desempenho de cada seleção em diferentes edições
do torneio, incluindo confrontos contra demais seleções, última vez que 
foi campeã, última vez que sediou uma copa e gols marcados.

<img width="1424" height="803" alt="image" src="https://github.com/user-attachments/assets/7397f7fe-b3d1-44f8-9cba-896b8550f3c0" />

#### Tela 3 – Estatísticas de Jogadores
Esta tela detalha estatísticas individuais de jogadores, como premiações individuais,
ranking dos maiores artilheiros e jogadores premiados na ultima edição de copa.

<img width="1412" height="788" alt="image" src="https://github.com/user-attachments/assets/ba86f590-7065-4fdd-965f-000ddd76374c" />

📎 O arquivo completo da dashboard pode ser acessado para download e exploração
interativa: [worldcupproject.pbix](https://github.com/ViniciusQuintino/worldcupproject/blob/main/worldcupproject.pbix)


## 🛠️ Tecnologias Utilizadas

As tecnologias foram escolhidas visando garantir qualidade na preparação dos
dados, flexibilidade analítica e uma visualização clara e interativa dos
resultados.

- **Power BI**  
  Utilizado para modelagem de dados, criação de medidas em DAX e desenvolvimento
  da dashboard interativa.

- **Python (Jupyter Notebook)**  
  Responsável pela limpeza, filtragem e preparação dos dados antes da
  importação para o Power BI.

- **Visual Studio Code**  
  Utilizado como ambiente de desenvolvimento para organização do código,
  manipulação de scripts e versionamento do projeto.

- **QGIS**  
  Empregado na criação dos mapas utilizados nas visualizações da dashboard.

## Conclusão

Este projeto demonstra a aplicação de boas práticas em preparação de dados,
modelagem analítica e visualização interativa, utilizando dados históricos da
Copa do Mundo masculina. O resultado final é uma dashboard que permite explorar
informações de forma clara, dinâmica e orientada à análise, apoiando a tomada
de decisão e a construção de insights a partir dos dados.


