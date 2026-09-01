# Arquitetura técnica

## Visão geral

O **Consulta Pública** era composto por uma aplicação frontend em **Vue.js** e uma API backend desenvolvida em **Ruby on Rails**.

A aplicação Rails funcionava principalmente como uma camada de API entre a interface administrativa e os módulos internos utilizados pela organização.

Os modelos e uma parte relevante das regras de negócio não ficavam diretamente neste projeto Rails. Eles eram disponibilizados por uma biblioteca interna denominada `casacivil_negocio`.

O projeto também utilizava um módulo interno específico para autenticação e permissões, denominado `casacivilgo_permissoes`.

A arquitetura reconstruída a partir do material preservado pode ser representada da seguinte forma:

```mermaid
flowchart TB
    USER["Usuário administrativo"]

    subgraph FRONT["Frontend"]
        VUE["Aplicação Vue.js"]
        ROUTER["Roteamento e telas"]
        SERVICES["Serviços de acesso à API"]
    end

    subgraph BACK["Backend - Ruby on Rails 6"]
        API["API /api/v1"]
        CONTROLLERS["Controllers"]
        JSON["Respostas JSON / Jbuilder"]
        AUTH["Autenticação e permissões"]
        MAIL["Notificações por e-mail"]
    end

    subgraph INTERNAL["Componentes internos"]
        BUSINESS["casacivil_negocio<br/>Models e regras de negócio"]
        PERMISSIONS["casacivilgo_permissoes"]
    end

    DB[("PostgreSQL")]

    USER --> VUE
    VUE --> ROUTER
    ROUTER --> SERVICES

    SERVICES -->|"HTTP / JSON"| API

    API --> CONTROLLERS
    CONTROLLERS --> JSON
    JSON -->|"HTTP / JSON"| SERVICES

    CONTROLLERS --> BUSINESS
    CONTROLLERS --> AUTH
    AUTH --> PERMISSIONS

    BUSINESS -->|"ActiveRecord"| DB

    CONTROLLERS --> MAIL
````

---

## Frontend

A interface administrativa era desenvolvida em **Vue.js**.

A estrutura recuperada do projeto frontend demonstra uma organização baseada em:

* views;
* componentes reutilizáveis;
* roteamento;
* rotas privadas;
* serviços específicos para comunicação com a API;
* configuração centralizada das requisições HTTP.

Entre os serviços identificados estavam módulos dedicados a:

* autenticação;
* consultas públicas;
* contribuições;
* painel;
* usuários.

Também existiam componentes e views específicos para os principais fluxos da aplicação, como criação, listagem, visualização e edição de consultas públicas.

O frontend consumia a API Rails e era responsável pela apresentação das informações, formulários, navegação e interação do usuário com o sistema.

> O histórico Git recuperado do frontend está incompleto. Por esse motivo, esta documentação descreve apenas a estrutura que pôde ser identificada no material preservado.

---

## Backend em Ruby on Rails

O backend recuperado utilizava:

* **Ruby 2.6.4**;
* **Ruby on Rails 6.0**;
* **PostgreSQL**;
* **Jbuilder** para composição das respostas JSON.

A aplicação utilizava `ActionController::API`, indicando que o Rails era utilizado predominantemente como backend de API, e não como aplicação tradicional baseada em páginas HTML renderizadas pelo servidor.

As rotas eram organizadas sob:

```text
/api/v1
```

o que permitia versionar a interface disponibilizada ao frontend.

---

## Organização da API

Os principais recursos identificados na versão recuperada eram:

```text
/api/v1/consultas_publicas
/api/v1/contribuicoes
/api/v1/usuarios
/api/v1/paineis
/api/v1/sessoes
```

Além das operações associadas aos recursos principais, havia endpoints auxiliares utilizados pelo frontend para obtenção de dados específicos.

No módulo de Consultas Públicas, por exemplo, existiam endpoints relacionados a:

* status;
* tipos de consulta;
* órgãos;
* órgãos coparticipantes;
* órgãos utilizados em pesquisas;
* download de anexos.

No módulo de Contribuições, havia endpoints auxiliares relacionados a:

* resultados de análise;
* status;
* consultas públicas;
* usuários;
* órgãos.

A API seguia uma estrutura orientada a recursos, combinada com endpoints adicionais necessários aos fluxos da aplicação.

---

## Controllers

Os controllers Rails funcionavam como camada de coordenação entre as requisições do frontend e os módulos responsáveis pelos dados e regras de negócio.

Entre suas responsabilidades estavam:

* receber e validar parâmetros;
* consultar os models;
* aplicar filtros;
* controlar paginação;
* restringir registros conforme o usuário logado;
* criar e atualizar entidades;
* manipular relacionamentos;
* disponibilizar informações auxiliares;
* preparar dados para as respostas da API.

Os principais controllers identificados foram:

```text
ConsultasPublicasController
ContribuicoesController
UsuariosController
PaineisController
SessoesController
```

---

## Camada de negócio

Uma característica importante da arquitetura era a separação entre a aplicação Rails administrativa e os models centrais do domínio.

Em vez de definir todos os models diretamente no projeto, o backend consumia uma biblioteca interna:

```text
casacivil_negocio
```

Ela disponibilizava entidades utilizadas pela aplicação, como:

```text
ConsultaPublica
Contribuicao
Usuario
Orgao
Voto
VotoContribuicao
ConsultaAnexo
```

Exemplos de namespaces utilizados pela aplicação incluíam:

```text
CasacivilNegocio::ParticipaGoias::Model
CasacivilNegocio::Sgu::Model
```

Essa separação permitia que regras e modelos compartilhados fossem reutilizados por diferentes aplicações internas.

---

## ActiveRecord e PostgreSQL

A persistência utilizava **PostgreSQL**, acessado por meio do **ActiveRecord**.

Os controllers utilizavam tanto recursos do ActiveRecord quanto scopes definidos nos próprios models.

Entre os tipos de operações identificadas estavam:

* `joins`;
* `where`;
* `select`;
* `order`;
* `distinct`;
* paginação;
* associações entre entidades;
* filtros compostos.

Em algumas funcionalidades também eram utilizadas consultas SQL mais específicas para restringir resultados de acordo com o órgão vinculado ao usuário logado.

---

## Comunicação frontend/backend

A comunicação entre o Vue.js e o Rails ocorria por meio de requisições HTTP e respostas JSON.

O fluxo era:

![Integração entre Vue.js e Rails](../assets/diagramas/integracao-frontend-backend.svg)

<!-- ```mermaid
sequenceDiagram
    participant U as Usuário
    participant V as Vue.js
    participant R as Rails API
    participant N as casacivil_negocio
    participant D as PostgreSQL

    U->>V: Interage com a interface
    V->>R: Requisição HTTP
    R->>N: Executa operação de negócio
    N->>D: Consulta ou altera dados
    D-->>N: Resultado
    N-->>R: Objetos do domínio
    R-->>V: Resposta JSON
    V-->>U: Atualiza a interface
``` -->

Esse modelo mantinha frontend e backend desacoplados e permitia que cada camada tivesse responsabilidades distintas.

---

## Construção das respostas JSON

O Rails utilizava **Jbuilder** para definir explicitamente a estrutura dos JSONs enviados ao frontend.

Essa camada permitia selecionar e organizar os dados que seriam expostos pela API.

Entre os dados estruturados dessa forma estavam:

* informações de consultas públicas;
* órgãos;
* órgãos coparticipantes;
* contribuições;
* usuários;
* valores formatados;
* dados agregados utilizados pelo painel.

O uso do Jbuilder permitia adaptar o contrato da API às necessidades das telas sem expor diretamente toda a estrutura dos models.

---

## Autenticação e permissões

A autenticação era integrada a uma biblioteca interna:

```text
casacivilgo_permissoes
```

O controller de sessões disponibilizava operações relacionadas a:

* autenticação;
* recuperação de senha;
* validação de token de recuperação;
* redefinição de senha;
* logout.

Após a autenticação, o backend retornava um **JSON Web Token (JWT)** utilizado pelo cliente.

O sistema também diferenciava usuários conforme suas permissões.

Um usuário com a funcionalidade administrativa global podia acessar informações de diferentes órgãos, enquanto outros usuários tinham os dados restritos ao órgão ao qual estavam vinculados.

Esse controle aparecia diretamente nas consultas executadas pelos controllers.

---

## Controle de acesso por órgão

Além da autenticação, existia uma camada de restrição funcional relacionada aos órgãos públicos.

Em diferentes pontos da aplicação, o backend verificava se o usuário possuía a funcionalidade administrativa global.

O fluxo podia ser representado de maneira simplificada como:

```text
Usuário autenticado
        │
        ▼
Possui permissão administrativa global?
        │
        ├── Sim → acesso aos registros de todos os órgãos
        │
        └── Não → acesso limitado ao próprio órgão
```

Essa lógica era aplicada principalmente aos módulos de:

* contribuições;
* usuários;
* painel;
* consultas relacionadas.

---

## Nested attributes e estruturas complexas

O módulo de Consultas Públicas lidava com estruturas mais complexas do que um CRUD simples.

Uma consulta podia possuir:

* anexos;
* diários estaduais relacionados;
* órgãos coparticipantes;
* blocos de texto aninhados.

O Rails recebia esses relacionamentos utilizando **nested attributes**.

Para o conteúdo estruturado, a API suportava vários níveis hierárquicos, incluindo:

```text
Parte
└── Livro
    └── Título
        └── Capítulo
            └── Seção
                └── Subseção
                    └── Temática
                        └── Artigo
                            └── Parágrafo
                                └── Inciso
                                    └── Alínea
                                        └── Item
```

Essa estrutura permitia representar conteúdos normativos extensos mantendo sua hierarquia.

---

## Painel e dados agregados

O backend também preparava informações destinadas ao painel administrativo.

Entre os indicadores identificados estavam:

* total de consultas públicas;
* consultas por status;
* total de contribuições;
* contribuições por status;
* resultados das análises;
* votos em consultas;
* votos em contribuições.

Parte desses dados era calculada no backend e entregue ao frontend já organizada para apresentação visual.

---

## Notificações

O projeto utilizava **ActionMailer** para envio de notificações.

No fluxo recuperado, quando uma contribuição era analisada e recebia determinados resultados, o sistema podia enviar um e-mail ao usuário relacionado àquela contribuição.

Isso conectava o fluxo de análise administrativa à comunicação com o participante.

---

## Outras dependências identificadas

O projeto também continha dependências para funcionalidades como:

* Sidekiq;
* Whenever;
* integração com Amazon S3;
* geração de PDF;
* testes com RSpec;
* FactoryBot;
* Faker.

A presença dessas bibliotecas demonstra que faziam parte do ambiente técnico do projeto recuperado.

No entanto, este estudo de caso **não atribui automaticamente a mim o desenvolvimento de funcionalidades utilizando essas bibliotecas**, já que o histórico preservado não permite comprovar minha atuação individual sobre todas elas.

---

## Separação de responsabilidades

De maneira resumida, a arquitetura seguia esta divisão:

| Camada                   | Responsabilidade principal                          |
| ------------------------ | --------------------------------------------------- |
| Vue.js                   | Interface, navegação e interação com o usuário      |
| Serviços do frontend     | Comunicação com a API                               |
| Rails API                | Coordenação das requisições e fluxos                |
| Controllers              | Filtros, parâmetros, acesso, integração e respostas |
| Jbuilder                 | Construção dos contratos JSON                       |
| `casacivil_negocio`      | Models e regras de negócio compartilhadas           |
| `casacivilgo_permissoes` | Autenticação e permissões                           |
| ActiveRecord             | Persistência e consultas                            |
| PostgreSQL               | Banco de dados                                      |

---

## Limitações da reconstrução

Esta arquitetura foi reconstruída a partir de uma cópia parcial do projeto e do material técnico que permaneceu disponível.

O backend Rails foi recuperado em estado significativamente mais completo do que o frontend Vue.js.

Além disso, os módulos internos `casacivil_negocio` e `casacivilgo_permissoes` não fazem parte do material atualmente disponível.

Por isso, este documento descreve apenas as relações arquiteturais que puderam ser identificadas com segurança, sem tentar reconstruir detalhes internos dessas bibliotecas.