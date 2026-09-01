# Minhas contribuições técnicas

Este documento detalha parte das contribuições que realizei no desenvolvimento do **Participa Goiás** durante minha atuação na Casa Civil do Estado de Goiás.

Atuei no projeto como desenvolvedor **full stack**, trabalhando com **Ruby on Rails** no backend e **Vue.js** no frontend.

O histórico Git que consegui recuperar posteriormente corresponde apenas a uma parte do período em que participei do projeto. Por isso, esta página prioriza as contribuições de backend que puderam ser verificadas diretamente no material preservado.

> O código-fonte original não é publicado neste repositório. Os exemplos abaixo descrevem as soluções implementadas sem reproduzir código proprietário.

---

## Backend com Ruby on Rails

O backend administrativo era desenvolvido em **Ruby on Rails 6** e expunha uma API HTTP/JSON versionada em `/api/v1`.

Os modelos e parte importante das regras de negócio eram fornecidos por módulos internos reutilizados pelos sistemas da organização, enquanto esta aplicação concentrava responsabilidades como:

- controllers da API;
- autenticação e autorização;
- filtros e consultas;
- paginação;
- tratamento dos parâmetros recebidos;
- composição das respostas JSON;
- integração com o frontend.

Minha atuação recuperada está concentrada principalmente no módulo de **Consultas Públicas**.

---

## API de Consultas Públicas

Participei da evolução da API responsável pelo gerenciamento das consultas públicas.

O módulo contemplava operações de listagem, criação, visualização, edição e exclusão, além de endpoints auxiliares utilizados pelo frontend.

Entre as contribuições recuperadas estão:

### Tipos de consulta pública

Implementei um endpoint para disponibilizar ao frontend os tipos de consulta pública existentes no domínio da aplicação.

Os valores eram obtidos a partir do modelo da aplicação e apresentados utilizando as traduções configuradas no Rails I18n.

Isso permitia que o frontend trabalhasse com valores internos estáveis enquanto apresentava descrições adequadas ao usuário.

---

## Internacionalização com Rails I18n

Trabalhei na adequação das respostas da API para retornar valores formatados em português.

Foram tratados, entre outros:

- status das consultas;
- tipos de consulta;
- informações relacionadas à moderação;
- mensagens de validação.

A utilização do **Rails I18n** permitia manter separados os valores utilizados internamente pelo sistema e os textos apresentados na interface.

---

## Paginação controlada pelo frontend

A API originalmente utilizava paginação sem permitir que o cliente definisse a quantidade de registros exibidos por página.

Implementei o suporte a um parâmetro de quantidade por página enviado pelo frontend.

Com isso, a interface passou a poder controlar dinamicamente o volume de resultados retornados pela API.

---

## Informações de órgãos públicos

As consultas públicas eram relacionadas a órgãos da administração pública.

Participei da evolução das respostas da API para disponibilizar informações adicionais sobre esses órgãos, incluindo:

- identificador;
- nome;
- sigla.

Também foram criados endpoints auxiliares para diferentes contextos de utilização no frontend, como pesquisa de órgãos e seleção de órgãos coparticipantes.

---

## Órgãos coparticipantes

Uma consulta pública podia envolver, além do órgão de origem, outros órgãos coparticipantes.

Implementei um endpoint específico para disponibilizar esses órgãos ao frontend e participei dos ajustes necessários para manipular esse relacionamento dentro da API.

O tratamento envolvia estruturas aninhadas recebidas pelo Rails e suporte a operações de inclusão e remoção dos relacionamentos.

---

## Nested attributes

O módulo utilizava **nested attributes** para manipular relacionamentos associados a uma consulta pública.

No caso dos órgãos coparticipantes, trabalhei no tratamento da estrutura recebida pela API, incluindo a eliminação de registros duplicados e o suporte ao campo `_destroy`, utilizado pelo Rails para remover relacionamentos aninhados durante uma atualização.

Esse mecanismo permitia que alterações na consulta e em seus relacionamentos fossem realizadas dentro do mesmo fluxo de edição.

---

## Quantidade de contribuições

As consultas públicas recebiam contribuições dos usuários da plataforma.

Implementei a inclusão da quantidade de contribuições associadas a cada consulta pública nas respostas utilizadas pela listagem.

Essa informação podia então ser apresentada diretamente pelo frontend sem a necessidade de uma consulta adicional para cada item exibido.

---

## Respostas JSON com Jbuilder

A API utilizava **Jbuilder** para estruturar os JSONs enviados ao frontend.

Trabalhei em alterações dessas representações para incluir informações necessárias às telas, como:

- status formatado;
- tipo formatado;
- sigla do órgão;
- dados dos órgãos coparticipantes;
- número de contribuições.

Esse trabalho fazia parte da integração entre o backend Rails e a aplicação Vue.js.

---

## ActiveRecord e consultas ao banco

O projeto utilizava **ActiveRecord** como camada de acesso aos dados.

Nas funcionalidades recuperadas, trabalhei com consultas relacionadas a:

- consultas públicas;
- órgãos;
- relacionamentos entre órgãos e consultas;
- contribuições;
- filtros utilizados pela interface.

Os modelos principais ficavam em um módulo interno de negócio compartilhado entre aplicações da organização.

---

## Integração com o frontend Vue.js

O frontend administrativo era desenvolvido em **Vue.js** e consumia os endpoints disponibilizados pelo Rails.

Parte importante do trabalho no backend consistia em adequar os contratos da API às necessidades das telas, incluindo:

- novos endpoints;
- novos campos nos JSONs;
- filtros;
- paginação;
- valores formatados;
- estruturas necessárias a formulários e componentes de seleção.

Também atuei diretamente no desenvolvimento do frontend Vue.js durante o projeto.

O histórico Git recuperado dessa aplicação, entretanto, está incompleto e não permite reconstruir com a mesma precisão as alterações que realizei nela. Por esse motivo, este estudo de caso não atribui a mim componentes ou funcionalidades específicas do frontend apenas com base no código preservado.

---

## O que o material recuperado demonstra

Mesmo representando apenas parte do período em que participei do projeto, o histórico preservado permite verificar experiência prática com:

- Ruby;
- Ruby on Rails;
- APIs HTTP/JSON;
- ActiveRecord;
- controllers Rails;
- rotas e endpoints;
- Jbuilder;
- Rails I18n;
- paginação;
- nested attributes;
- relacionamentos entre entidades;
- integração backend/frontend;
- Vue.js;
- PostgreSQL;
- Git e GitLab.

---

## Limitação do histórico recuperado

Minha participação no projeto ocorreu durante 2022 e 2023.

A cópia local recuperada posteriormente preserva apenas parte do histórico do backend, principalmente entre junho e setembro de 2022.

Portanto, as implementações descritas nesta página **não representam a totalidade das atividades realizadas durante minha permanência na equipe**.

Elas representam as contribuições que puderam ser verificadas de maneira objetiva no material técnico que ainda estava disponível.