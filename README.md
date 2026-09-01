# Consulta-Pública — Estudo de Caso Técnico

Estudo de caso sobre minha atuação no desenvolvimento do **Consulta-Pública**, durante minha experiência profissional na área de tecnologia da Casa Civil do Estado de Goiás.

> **Nota:** este não é o repositório oficial do Consulta-Pública e não contém o código-fonte original do sistema.  
> O objetivo deste repositório é documentar minha experiência técnica sem expor código, credenciais, dados ou outros ativos institucionais.

## Sobre o projeto

O Consulta-Pública era uma plataforma voltada à participação pública, com recursos relacionados ao gerenciamento de consultas públicas, contribuições dos cidadãos, análise dessas contribuições e acompanhamento administrativo.

A solução era composta por uma aplicação web com:

- frontend desenvolvido em **Vue.js**;
- backend desenvolvido em **Ruby on Rails**;
- banco de dados **PostgreSQL**;
- comunicação frontend/backend por **API HTTP/JSON**;
- autenticação e controle de permissões integrados a componentes internos;
- módulos internos responsáveis pelos modelos e parte das regras de negócio.

## Minha atuação

Atuei no projeto como desenvolvedor **full stack**, trabalhando tanto no frontend em Vue.js quanto no backend em Ruby on Rails.

O material técnico que consegui recuperar do projeto preserva principalmente uma parte do histórico do backend entre junho e setembro de 2022. Por isso, as implementações documentadas neste repositório representam apenas uma parcela do trabalho realizado durante minha permanência na equipe.

Entre as contribuições que puderam ser verificadas no código e no histórico Git recuperado estão:

- desenvolvimento e evolução de endpoints da API de Consultas Públicas;
- consultas e filtros utilizando ActiveRecord;
- paginação de resultados;
- manipulação de relacionamentos e nested attributes;
- tratamento de órgãos de origem e órgãos coparticipantes;
- disponibilização da quantidade de contribuições por consulta pública;
- construção de respostas JSON com Jbuilder;
- internacionalização com Rails I18n;
- integração entre o backend Rails e o frontend Vue.js.

Também desenvolvi funcionalidades no frontend em Vue.js, embora o histórico Git dessa parte do projeto não tenha sido recuperado integralmente.

## Stack

**Backend**

`Ruby` · `Ruby on Rails` · `ActiveRecord` · `Jbuilder` · `Rails I18n`

**Frontend**

`Vue.js` · `JavaScript`

**Dados e integração**

`PostgreSQL` · `HTTP/JSON` · `REST API`

**Ferramentas**

`Git` · `GitLab`

## Arquitetura

![Arquitetura do Participa Goiás](assets/diagramas/arquitetura-consulta-publica.drawio.svgsvg)

<!-- ```text
┌──────────────────────────┐
│        Vue.js            │
│   Interface web/admin    │
└────────────┬─────────────┘
             │ HTTP / JSON
             ▼
┌──────────────────────────┐
│    Ruby on Rails 6       │
│        API v1            │
│                          │
│ Consultas Públicas       │
│ Contribuições            │
│ Usuários                 │
│ Painel                   │
│ Sessões                  │
└────────────┬─────────────┘
             │
             ▼
┌──────────────────────────┐
│   Módulos internos       │
│ Models e regras          │
│ de negócio               │
└────────────┬─────────────┘
             │ ActiveRecord
             ▼
┌──────────────────────────┐
│       PostgreSQL         │
└──────────────────────────┘
``` -->

## Interface e referências de produto

O desenvolvimento partia de protótipos funcionais definidos para o projeto, contemplando fluxos como:

**Listagem → Cadastro → Visualização → Edição → Publicação/encerramento**

Entre as referências visuais utilizadas pela equipe estava também o **Legisla Goiás**, especialmente como referência de organização e apresentação de conteúdo relacionado a atos e documentos públicos.

Essas referências serviram como base conceitual e visual para o desenvolvimento da aplicação; os protótipos originais não foram produzidos por mim.

## Mais detalhes

* [Arquitetura técnica](docs/arquitetura.md)
* [Minhas contribuições](docs/minhas-contribuicoes.md)
* [Contexto funcional](docs/contexto-funcional.md)
* [Material recuperado e limitações](docs/evidencias-recuperadas.md)

## Sobre o material apresentado

Minha atuação no projeto ocorreu entre **2022 e 2023**.

A cópia local recuperada posteriormente contém apenas parte do histórico original do projeto. Por esse motivo, este estudo de caso diferencia explicitamente:

* funcionalidades existentes no sistema;
* contribuições que puderam ser verificadas no histórico recuperado;
* atividades das quais participei, mas cujo histórico original não pôde ser recuperado.

Nenhum código-fonte proprietário ou informação sensível é publicado neste repositório.