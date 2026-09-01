# Contexto funcional do Consulta Pública

## Visão geral

O **Consulta Pública** era uma aplicação voltada ao gerenciamento de processos de participação pública no âmbito do Governo do Estado de Goiás.

O sistema permitia administrar **consultas públicas**, organizar o conteúdo submetido à participação da sociedade, acompanhar as contribuições recebidas e apoiar o processo de análise dessas manifestações.

Este documento apresenta o contexto funcional do sistema a partir do material técnico e dos protótipos que puderam ser recuperados.

> Este repositório não representa documentação oficial do Consulta Pública.
> O conteúdo foi reconstruído exclusivamente para fins de portfólio técnico.

---

## Estrutura geral

A aplicação possuía uma área administrativa utilizada para gerenciamento das informações relacionadas às consultas públicas.

Entre os principais domínios identificados no material recuperado estavam:

- consultas públicas;
- contribuições;
- usuários;
- órgãos públicos;
- painel administrativo;
- autenticação e permissões.

A interface administrativa era desenvolvida em **Vue.js**, enquanto o backend era disponibilizado por uma **API em Ruby on Rails**.

---

# Consulta Pública

A Consulta Pública era uma das entidades centrais do sistema.

O fluxo administrativo permitia criar, visualizar, editar e acompanhar consultas disponibilizadas para participação.

Entre as informações associadas a uma consulta estavam:

- título;
- órgão responsável;
- status;
- data de abertura;
- data de encerramento;
- tipo da consulta;
- processo;
- resumo;
- anexos;
- órgãos coparticipantes;
- documentos relacionados;
- conteúdo estruturado da consulta.

---

## Listagem

A área de listagem permitia localizar e acompanhar consultas públicas existentes.

Os protótipos recuperados mostram filtros relacionados a informações como:

- texto;
- órgão;
- status;
- data de abertura;
- data de encerramento.

Os resultados apresentavam informações resumidas da consulta e ações disponíveis para cada registro.

O backend também permitia paginação e filtragem das consultas.

---

## Cadastro

O fluxo de criação permitia cadastrar uma nova consulta pública e definir seus principais metadados.

Entre os elementos presentes no fluxo estavam:

- título;
- órgão responsável;
- processo;
- período de abertura e encerramento;
- resumo;
- anexos;
- conteúdo da consulta.

Também era possível associar mais de um órgão à consulta por meio do conceito de **órgãos coparticipantes**.

---

## Conteúdo estruturado

Uma característica importante do sistema era a possibilidade de representar documentos com diferentes níveis hierárquicos.

O backend recuperado permitia estruturas aninhadas correspondentes a:

- Parte;
- Livro;
- Título;
- Capítulo;
- Seção;
- Subseção;
- Temática;
- Artigo;
- Parágrafo;
- Inciso;
- Alínea;
- Item.

Essa estrutura permitia representar documentos normativos ou outros conteúdos extensos de forma organizada dentro de uma consulta pública.

---

## Visualização e edição

O sistema possuía fluxos específicos para visualização e edição das consultas cadastradas.

A visualização consolidava as informações da consulta, enquanto a edição permitia alterar seus dados e os conteúdos associados.

Os protótipos também previam ações relacionadas à publicação da consulta e ao envio de documentação complementar.

---

# Órgãos públicos

As consultas eram relacionadas a órgãos da administração pública.

O sistema diferenciava o **órgão de origem** da consulta de possíveis **órgãos coparticipantes**.

Essa estrutura permitia representar consultas conduzidas por um determinado órgão, mas com participação de outras unidades da administração.

O backend também possuía mecanismos para disponibilizar listas de órgãos utilizadas nos filtros e formulários da interface.

---

# Contribuições

Uma consulta pública podia receber contribuições dos participantes.

O módulo administrativo permitia pesquisar e acompanhar essas contribuições utilizando diferentes critérios, incluindo:

- consulta pública;
- status;
- órgão;
- usuário;
- resultado da análise;
- intervalo de datas;
- conteúdo textual.

As contribuições eram apresentadas em ordem cronológica e podiam passar por processo de análise administrativa.

---

## Análise das contribuições

O material recuperado indica diferentes possíveis resultados de análise de uma contribuição, entre eles:

- acatada;
- acatada parcialmente;
- não acatada;
- não pertinente.

Quando determinadas contribuições eram acatadas ou parcialmente acatadas, o backend possuía fluxo para envio de notificação por e-mail ao participante.

---

# Usuários e controle de acesso

O sistema possuía autenticação e controle de permissões.

A API incluía operações relacionadas a:

- autenticação;
- recuperação de senha;
- validação do link de recuperação;
- redefinição de senha;
- logout.

Após autenticação, a aplicação trabalhava com um token utilizado pela comunicação entre cliente e servidor.

Além disso, os dados apresentados ao usuário administrativo podiam variar de acordo com suas permissões e com o órgão ao qual estava vinculado.

Usuários com perfil administrativo amplo podiam visualizar informações de todos os órgãos, enquanto outros usuários tinham acesso restrito às informações relacionadas ao próprio órgão.

---

# Painel administrativo

O sistema também possuía um painel com indicadores relacionados à utilização da plataforma.

Entre as informações identificadas no backend estavam:

- quantidade de consultas públicas;
- consultas em rascunho;
- consultas em andamento;
- consultas encerradas;
- quantidade de contribuições;
- contribuições aguardando análise;
- contribuições analisadas;
- resultados das análises;
- votos relacionados às consultas;
- votos relacionados às contribuições.

Essas informações eram preparadas pelo backend para apresentação visual no frontend.

---

# Fluxo funcional simplificado

De maneira resumida, o fluxo administrativo do sistema podia ser representado como:

```text
Criação da Consulta Pública
            │
            ▼
Definição do conteúdo e documentos
            │
            ▼
Associação de órgãos
            │
            ▼
Publicação / disponibilização
            │
            ▼
Recebimento de contribuições
            │
            ▼
Análise das contribuições
            │
            ▼
Resultado da análise
            │
            ▼
Acompanhamento pelo painel
````

---

# Referências visuais

Durante o desenvolvimento, a equipe utilizou protótipos para orientar os principais fluxos da interface administrativa.

O material recuperado contempla referências para:

* listagem de consultas públicas;
* criação de uma nova consulta;
* visualização;
* edição;
* upload de relatório final.

Uma das referências visuais utilizadas pela equipe também foi o **Legisla Goiás**, especialmente no que diz respeito à organização e apresentação de conteúdos relacionados a documentos públicos e atos normativos.

Essas referências orientaram o desenvolvimento visual do sistema, mas os protótipos originais não foram produzidos por mim.

---

# Limitações desta reconstrução

O material disponível representa apenas uma parte do projeto original.

O código completo, a documentação funcional oficial e parte do histórico do frontend não puderam ser recuperados.

Por esse motivo, este documento descreve apenas funcionalidades que puderam ser identificadas a partir dos artefatos preservados e da experiência profissional no projeto.
