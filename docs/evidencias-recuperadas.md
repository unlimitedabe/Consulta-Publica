# Evidências recuperadas e limitações

## Objetivo deste documento

Este estudo de caso foi produzido a partir de uma **cópia local parcial do projeto Consulta Pública** recuperada após o período em que participei de seu desenvolvimento.

Como o repositório corporativo original era hospedado no GitLab da organização e não está mais acessível para mim, o material atualmente disponível não corresponde ao projeto completo nem a todo o histórico da minha participação.

Por esse motivo, esta página registra de forma transparente:

- quais artefatos foram recuperados;
- quais informações puderam ser verificadas objetivamente;
- quais limitações existem no material;
- quais critérios foram utilizados para atribuir contribuições a mim;
- por que o código-fonte original não é publicado neste repositório.

> Este repositório é um estudo de caso profissional e não uma cópia ou continuação oficial do Participa Goiás.

---

# Material recuperado

Foram recuperados três grupos principais de artefatos relacionados ao projeto.

## 1. Backend Ruby on Rails

A cópia mais completa corresponde ao backend administrativo desenvolvido em **Ruby on Rails**.

O material preserva:

- estrutura do projeto Rails;
- controllers;
- rotas;
- views JSON com Jbuilder;
- configurações;
- dependências;
- parte do histórico Git;
- branches e referências do antigo repositório GitLab.

Também foi preservado o remoto originalmente associado ao projeto, permitindo identificar que essa cópia fazia parte do ambiente Git utilizado durante o desenvolvimento.

O histórico Git disponível contém commits de diferentes integrantes da equipe, incluindo commits associados ao meu usuário de desenvolvimento.

---

## 2. Frontend Vue.js

Também foi recuperada uma cópia da aplicação frontend em **Vue.js**.

O código preservado permite identificar a estrutura da aplicação, incluindo:

- views;
- componentes;
- rotas;
- rotas privadas;
- serviços de comunicação com a API;
- módulos relacionados a consultas públicas;
- contribuições;
- usuários;
- painel;
- autenticação.

Entretanto, o banco de objetos do Git dessa cópia está incompleto.

As referências das antigas branches ainda existem, mas apontam para objetos que não estão mais disponíveis localmente.

Por esse motivo, não foi possível reconstruir de maneira confiável:

- o histórico de commits;
- os autores das alterações;
- a evolução das funcionalidades;
- quais arquivos ou componentes específicos foram desenvolvidos por cada integrante.

Embora eu tenha atuado diretamente no frontend Vue.js durante o projeto, essa cópia **não é utilizada como evidência para atribuir componentes ou funcionalidades específicas a mim**.

---

## 3. Protótipo funcional

Também foi preservado um protótipo utilizado como referência durante o desenvolvimento.

O documento contempla telas relacionadas a:

- listagem de consultas públicas;
- inclusão de uma consulta;
- visualização;
- edição;
- envio do relatório final.

O protótipo ajuda a compreender o contexto funcional e a evolução esperada da interface.

Ele **não foi desenvolvido por mim** e não é publicado neste repositório como trabalho de minha autoria.

Entre as referências visuais utilizadas pela equipe durante o desenvolvimento também estava o **Legisla Goiás**, principalmente como referência para organização e apresentação de conteúdos relacionados a documentos e atos públicos.

---

# Histórico Git recuperado

A cópia do backend preservou parte do histórico original do Git.

Os commits associados ao meu usuário que permanecem acessíveis nessa cópia estão concentrados entre **junho e setembro de 2022**.

Minha atuação profissional no projeto, entretanto, se estendeu durante 2022 e 2023.

Consequentemente, o histórico atualmente disponível representa apenas uma **amostra da minha participação no projeto**, e não sua totalidade.

---

# Critério utilizado para atribuir contribuições

Para este estudo de caso, uma funcionalidade é apresentada como contribuição técnica individual apenas quando existe evidência suficiente no material recuperado.

Foram considerados principalmente:

1. autoria registrada pelo Git;
2. conteúdo do diff do commit;
3. arquivos alterados;
4. contexto da branch;
5. relação entre a alteração e o funcionamento identificado no restante da aplicação.

Commits que correspondiam apenas a merges ou sincronizações de branches não foram utilizados, isoladamente, como evidência de desenvolvimento de funcionalidades.

Esse critério evita atribuir a mim funcionalidades que apenas estavam presentes no sistema ou que foram desenvolvidas por outros integrantes da equipe.

---

# Commits de backend utilizados como evidência

Entre os commits preservados, quatro possuem alterações de código particularmente úteis para reconstruir minha atuação no módulo de **Consultas Públicas**.

## `5f45f4c` — Tipos de consulta e internacionalização

**Data:** 15/06/2022

O commit registra alterações relacionadas a:

- criação de endpoint para obtenção dos tipos de consulta;
- integração desses tipos com Rails I18n;
- formatação de status;
- formatação de tipos;
- tratamento de informações relacionadas à moderação;
- criação da rota correspondente;
- ajustes das respostas JSON com Jbuilder.

Arquivos afetados incluíam controller, rotas, arquivos de internacionalização e representações JSON da API.

---

## `e1c5d68` — Adequação do campo de moderação

**Data:** 01/07/2022

O commit registra uma adequação do contrato da API relacionada ao campo de moderação.

As alterações atingiram:

- parâmetros aceitos pelo controller;
- respostas JSON;
- internacionalização.

Esse commit é tratado neste estudo de caso como evidência de **manutenção e adaptação da API**, e não como uma nova funcionalidade independente.

---

## `f742d8d` — Paginação, órgãos e contribuições

**Data:** 12/08/2022

Este é um dos commits mais relevantes preservados.

Entre as alterações identificadas estão:

- suporte à quantidade de registros por página definida pelo frontend;
- inclusão da sigla dos órgãos nas respostas;
- criação de endpoint destinado à pesquisa de órgãos relacionados às consultas;
- inclusão da quantidade de contribuições associadas a uma consulta;
- ajustes no contrato JSON;
- ajustes em mensagens de validação com Rails I18n;
- criação da rota associada ao novo endpoint.

O commit demonstra atuação envolvendo diferentes camadas da aplicação Rails:

```text
Rota
  ↓
Controller
  ↓
ActiveRecord
  ↓
Jbuilder
  ↓
Resposta JSON consumida pelo frontend
````

---

## `b6d96a5` — Órgãos coparticipantes e nested attributes

**Data:** 06/09/2022

O commit registra alterações relacionadas ao tratamento de órgãos coparticipantes.

Entre elas:

* criação de endpoint específico para obtenção dos órgãos;
* disponibilização de identificador, nome e sigla;
* ajustes na estrutura JSON retornada;
* criação da rota correspondente;
* tratamento de estruturas aninhadas recebidas pela API;
* inclusão de `_destroy` no processo de deduplicação dos nested attributes.

Essa alteração demonstra o tratamento de relacionamentos associados durante operações de edição de uma consulta pública.

---

# Outros commits associados ao meu usuário

O histórico recuperado também contém commits relacionados a merges e sincronizações entre minha branch de desenvolvimento e a branch principal.

Eles ajudam a contextualizar o fluxo de trabalho utilizado pela equipe, mas não são apresentados neste estudo de caso como evidência isolada de implementação de funcionalidades.

A documentação prioriza os commits que possuem alterações técnicas diretamente identificáveis.

---

# Branch recuperada

Parte relevante das alterações preservadas estava associada a uma branch relacionada à criação da estrutura de **Consulta Pública**.

Isso é consistente com os arquivos modificados nos commits recuperados, que se concentram principalmente em:

```text
ConsultasPublicasController
routes.rb
Jbuilder
Rails I18n
```

Essa relação entre branch, histórico e diffs reforça a identificação da área do backend na qual as contribuições preservadas ocorreram.

---

# O que o backend recuperado permite verificar

Além dos meus commits individuais, a estrutura geral preservada permite verificar que o projeto utilizava:

* Ruby;
* Ruby on Rails 6;
* PostgreSQL;
* ActiveRecord;
* API HTTP/JSON;
* versionamento `/api/v1`;
* Jbuilder;
* Rails I18n;
* autenticação baseada em token;
* módulos internos para autenticação e permissões;
* módulos internos contendo models e regras de negócio;
* integração com frontend Vue.js;
* Git e GitLab.

Essas informações descrevem o **ambiente técnico do projeto**.

A presença de determinada biblioteca ou tecnologia no sistema, entretanto, não significa automaticamente que eu tenha implementado funcionalidades utilizando todas elas.

As tecnologias atribuídas especificamente à minha atuação são apresentadas de acordo com as evidências disponíveis.

---

# Tentativa de recuperação do frontend

A cópia do frontend ainda preservava referências das antigas branches do Git.

Entretanto, uma verificação de integridade do repositório identificou:

* referências apontando para objetos inexistentes;
* commits não disponíveis;
* blobs ausentes;
* reflogs inválidos;
* branch local sem um commit válido associado.

Também foi realizada uma tentativa de consultar o antigo repositório remoto no GitLab.

O projeto remoto não estava disponível para a minha conta, seja por remoção do repositório, alteração de sua localização ou perda das permissões de acesso.

Dessa forma, não havia uma fonte remota disponível para restaurar os objetos ausentes.

Por esse motivo, foi tomada a decisão de **não tentar reconstruir artificialmente o histórico do frontend** e de não utilizar os arquivos preservados para atribuição individual de autoria.

---

# Verificação do backend

No backend Rails também foram realizadas verificações do banco de objetos Git.

Diferentemente do frontend, o repositório preservado apresentava histórico utilizável e commits válidos.

Também foi realizada uma busca por objetos não associados às branches atuais com o objetivo de verificar se havia commits posteriores que pudessem ser recuperados.

Não foram encontrados commits adicionais desconectados que permitissem reconstruir o período restante da minha atuação.

Assim, o histórico documentado neste estudo de caso corresponde ao material efetivamente preservado.

---

# O que não foi recuperado

Não estão disponíveis atualmente:

* o histórico completo do período em que participei do projeto;
* commits posteriores da minha atuação;
* histórico íntegro do frontend Vue.js;
* o código das bibliotecas internas de negócio;
* o código da biblioteca interna de autenticação e permissões;
* documentação oficial completa do sistema;
* ambiente de execução original;
* banco de dados original.

Essas limitações são consideradas em todas as afirmações feitas neste estudo de caso.

---

# Por que o código-fonte original não está neste GitHub

Embora parte do backend tenha sido recuperada, optei deliberadamente por **não publicar o código-fonte original**.

Existem diferentes razões para isso.

## Propriedade do código

O código foi produzido dentro de um projeto institucional e não considero apropriado republicá-lo em um repositório pessoal sem autorização explícita.

## Dependências internas

O projeto dependia de módulos e bibliotecas internas da organização, que também não devem ser redistribuídos.

## Informações sensíveis

O material recuperado contém configurações e referências internas que não são adequadas para publicação.

Durante a análise também foram identificadas credenciais antigas e informações de acesso presentes no histórico.

Nenhuma dessas informações é reproduzida neste repositório.

## Histórico Git

Remover uma informação sensível apenas da versão atual de um arquivo não seria suficiente, pois versões anteriores permaneceriam acessíveis pelo histórico Git.

Por esse motivo, o repositório corporativo original não foi simplesmente copiado ou enviado ao GitHub.

---

# Estratégia adotada neste portfólio

Em vez de publicar o código proprietário, este repositório utiliza uma abordagem de **case study técnico**.

São apresentados:

* contexto do produto;
* arquitetura reconstruída;
* tecnologias utilizadas;
* fluxos funcionais;
* minhas contribuições verificáveis;
* decisões e desafios técnicos identificáveis no material recuperado;
* limitações da reconstrução.

Não são publicados:

* código-fonte institucional;
* credenciais;
* arquivos de configuração internos;
* dados de usuários;
* banco de dados;
* código das bibliotecas corporativas;
* documentos cuja autorização de redistribuição não esteja clara.

---

# Níveis de evidência utilizados

Para manter transparência, as informações deste estudo de caso podem ser entendidas em três níveis.

### 1. Evidência direta

Informações verificáveis diretamente no histórico e no código recuperado.

Exemplos:

* commits associados ao meu usuário;
* alterações em controllers;
* criação de endpoints;
* alterações de rotas;
* paginação;
* Jbuilder;
* I18n;
* nested attributes.

### 2. Evidência contextual

Funcionalidades e características identificadas no projeto recuperado, mas que não podem ser atribuídas individualmente a mim apenas pela existência no código.

Exemplos:

* autenticação;
* painel;
* notificações por e-mail;
* módulos de contribuições;
* arquitetura geral da aplicação.

### 3. Experiência profissional sem histórico preservado

Atividades das quais participei durante o projeto, mas cujo histórico técnico completo não está mais disponível.

O principal exemplo é parte significativa da minha atuação no frontend **Vue.js**, além das atividades realizadas após o período coberto pela cópia local recuperada.

Essas experiências são mencionadas como contexto profissional, mas não são apresentadas como se houvesse evidência Git disponível para cada implementação.

---

# Conclusão

Este repositório busca apresentar minha experiência no Participa Goiás de maneira tecnicamente útil e, ao mesmo tempo, responsável.

O objetivo não é reconstruir artificialmente um projeto cujo código completo já não está disponível, mas utilizar os artefatos preservados para demonstrar, com o máximo de transparência possível, o contexto técnico em que trabalhei e as contribuições que ainda podem ser verificadas.

Para detalhes adicionais:

* [Contexto funcional](contexto-funcional.md)
* [Arquitetura técnica](arquitetura.md)
* [Minhas contribuições](minhas-contribuicoes.md)
