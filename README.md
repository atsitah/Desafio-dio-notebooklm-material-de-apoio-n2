# Construindo um Assistente de Suporte N2 com NotebookLM

## Diagnóstico de Problemas de Acesso a Sistemas Web

> Projeto desenvolvido com o objetivo de construir uma base de conhecimento no NotebookLM, aplicando técnicas de Engenharia de Prompt para auxiliar Analistas de Suporte N2 na investigação de problemas de acesso a aplicações web.

---

## Índice

- [1. Sobre o Projeto](#1-sobre-o-projeto)
- [2. Contexto](#2-contexto)
- [3. Objetivos](#3-objetivos)
- [4. Escopo do Projeto](#4-escopo-do-projeto)
  - [Assuntos abordados](#assuntos-abordados)
  - [Fora do escopo](#fora-do-escopo)
- [5. Curadoria de Fontes](#5-curadoria-de-fontes)
  - [Fontes utilizadas](#fontes-utilizadas)
  - [Critérios de seleção](#critérios-de-seleção)
  - [Referências](#referências)
- [6. Engenharia de Prompts](#6-engenharia-de-prompts)
- [7. Validação e Testes](#7-validação-e-testes)
  - [Experimento 1 — Pergunta Genérica](#experimento-1--pergunta-genérica)
  - [Experimento 2 — Role Prompting e Contextualização do Cenário](#experimento-2--role-prompting-e-contextualização-do-cenário)
  - [Experimento 3 — Estruturação de Fluxo de Troubleshooting](#experimento-3--estruturação-de-fluxo-de-troubleshooting)
  - [Experimento 4 — Árvore de Decisão para Diagnóstico](#experimento-4--árvore-de-decisão-para-diagnóstico)
  - [Experimento 5 — Assistente Interativo de Diagnóstico](#experimento-5--assistente-interativo-de-diagnóstico)
- [8. Prompts Reutilizáveis](#8-prompts-reutilizáveis)
  - [Prompt 1 — Diagnóstico Inicial de Acesso Web](#prompt-1--diagnóstico-inicial-de-acesso-web)
  - [Prompt 2 — Análise de Erros HTTP](#prompt-2--análise-de-erros-http)
  - [Prompt 3 — Avaliação de Evidências do Chrome DevTools](#prompt-3--avaliação-de-evidências-do-chrome-devtools)
  - [Prompt 4 — Decisão de Resolução ou Escalonamento](#prompt-4--decisão-de-resolução-ou-escalonamento)
- [9. Glossário](#9-glossário)
  - [Ferramentas Utilizadas](#ferramentas-utilizadas)
- [10. Conclusão](#10-conclusão)  


# 1. Sobre o Projeto

Este repositório documenta o processo de construção de uma base de conhecimento no **NotebookLM**, onde foram aplicadas técnicas de **Engenharia de Prompt** para apoiar o diagnóstico de problemas de acesso a aplicações web.
A base de conhecimento desenvolvida neste projeto está disponível publicamente no NotebookLM.

> **Caderno:**  
> https://notebooklm.google.com/notebook/a9326a72-1d1b-4851-89d4-9b0d31d30335

---

# 2. Contexto

Analistas de suporte frequentemente precisam consultar diferentes documentações técnicas para investigar problemas de acesso a aplicações web. Esse processo pode aumentar o tempo de atendimento, gerar inconsistências durante o diagnóstico e dificultar a padronização das análises.

Este projeto tem como proposta construir um caderno temático capaz de apoiar Analistas de Suporte N2 durante o processo de investigação de incidentes relacionados ao acesso a aplicações web, auxiliando na formulação de hipóteses, definição de testes, coleta de evidências e tomada de decisão sobre escalonamento.

---

# 3. Objetivos

Os principais objetivos deste projeto são:

- Construir uma base de conhecimento especializada;
- Explorar os recursos do NotebookLM;
- Aplicar técnicas de Engenharia de Prompt;
- Desenvolver prompts reutilizáveis;
- Avaliar a qualidade das respostas produzidas pela IA;
- Documentar os aprendizados obtidos durante o processo;

---

# 4. Escopo do Projeto

Este projeto concentra-se exclusivamente no diagnóstico de problemas relacionados ao acesso a aplicações web, com foco na investigação estruturada de incidentes enfrentados por Analistas de Suporte N2.

## Assuntos abordados

- DNS;
- HTTP e HTTPS;
- VPN;
- Navegadores;
- Autenticação;
- Códigos de resposta HTTP;
- Troubleshooting;
- Escalonamento de incidentes;

## Fora do escopo

Os seguintes temas não fazem parte deste projeto:

- Administração de servidores
- Banco de dados
- Desenvolvimento de aplicações
- Configuração de infraestrutura em nuvem
- Segurança ofensiva e testes de invasão

A delimitação do escopo tem como objetivo manter o foco na construção de uma base de conhecimento especializada em diagnóstico de problemas de acesso a sistemas web, garantindo maior consistência nas respostas geradas pelo NotebookLM.

---

# 5. Curadoria de Fontes

A base de conhecimento utilizada neste projeto foi construída a partir de documentações oficiais e materiais amplamente reconhecidos pela comunidade técnica. As fontes foram selecionadas considerando critérios como confiabilidade, relevância para o tema e aplicabilidade prática ao contexto de Suporte N2.

## Fontes utilizadas

| Fonte | Objetivo | Conteúdo |
|--------|----------|----------|
| **MDN Web Docs** | Fundamentar conceitos sobre aplicações web. | HTTP, HTTPS, APIs Web, Cookies e Armazenamento. |
| **IT Process Maps – Incident Management** | Boas práticas de gerenciamento de incidentes. | Investigação, priorização e escalonamento. |
| **Chrome DevTools Documentation** | Diagnóstico via navegador. | Console, Network, Application e Security. |
| **Cloudflare Developers – SSL/TLS** | Conexões seguras. | SSL/TLS, certificados e HTTPS. |
| **Microsoft Learn – Troubleshoot** | Troubleshooting técnico. | Diagnóstico de conectividade e aplicações web. |

## Critérios de seleção

As fontes foram escolhidas com base nos seguintes critérios:

- Documentação oficial ou amplamente reconhecida pela comunidade técnica;
- Conteúdo atualizado e mantido por organizações de referência;
- Material aplicável ao contexto de diagnóstico de problemas de acesso a aplicações web;
- Cobertura dos principais domínios de conhecimento necessários para um Analista de Suporte N2;

## Referências

- [MDN Web Docs](https://developer.mozilla.org/pt-BR/docs/Learn_web_development)
- [IT Process Maps – Incident Management](https://wiki.en.it-processmaps.com/index.php/Incident_Management)
- [Chrome DevTools Documentation](https://developer.chrome.com/docs/devtools/overview?hl=pt-br)
- [Cloudflare Developers – SSL/TLS](https://developers.cloudflare.com/ssl/)
- [Microsoft Learn – Troubleshoot](https://learn.microsoft.com/en-us/troubleshoot/)

---

# 6. Engenharia de Prompts

A Engenharia de Prompt foi utilizada para orientar o NotebookLM a atuar como um assistente especializado em Suporte N2, reduzindo respostas genéricas e aproximando o comportamento da IA ao fluxo de investigação utilizado por analistas durante o atendimento de incidentes.

Em vez de buscar apenas respostas corretas, os experimentos tiveram como objetivo avaliar como diferentes estratégias de construção de prompts influenciam a qualidade do diagnóstico.

Durante o desenvolvimento foram exploradas técnicas como:

- Definição de papel (*Role Prompting*);
- Inclusão de contexto específico;
- Estruturação da resposta esperada;
- Definição de regras de comportamento;
- Refinamento iterativo a partir da análise dos resultados obtidos;

Cada experimento foi utilizado para identificar limitações da abordagem anterior e orientar a construção do próximo prompt, documentando o processo de evolução da interação com o NotebookLM.

---

# 7. Validação e Testes

Com o objetivo de avaliar o impacto das técnicas de Engenharia de Prompt, foram realizados experimentos utilizando um mesmo cenário de atendimento.

A cada iteração, novas instruções foram adicionadas ao prompt para observar como elas influenciavam a qualidade das respostas produzidas pelo NotebookLM.

Os experimentos foram conduzidos de forma incremental, permitindo comparar a evolução das respostas e identificar quais técnicas produziram maior ganho na condução do diagnóstico.

### Experimento 1 — Pergunta Genérica

#### Objetivo

Avaliar o comportamento padrão do NotebookLM diante de uma pergunta ampla, sem contexto adicional ou instruções específicas sobre o formato da resposta.

#### Técnica aplicada

- Pergunta aberta (*Open Prompt*)

#### Prompt utilizado

```text
Por que um usuário não consegue acessar um sistema web e como investigar esse problema?
```

#### Resumo da resposta

O NotebookLM apresentou uma visão abrangente das possíveis causas para problemas de acesso a aplicações web, agrupando fatores relacionados a:

- JavaScript;
- Rede;
- Segurança;
- Servidor;
- Desempenho;
- Cache e cookies;

Além disso, recomendou a utilização do Chrome DevTools como principal ferramenta de investigação, destacando painéis como **Console**, **Network**, **Security**, **Application**, **Elements** e **Sources**.

#### Avaliação

| Critério | Avaliação | Observação |
|----------|-----------|------------|
| Precisão técnica | ✅ Boa | As causas apresentadas são coerentes com a base de conhecimento. |
| Uso das fontes | ✅ Excelente | Utilizou corretamente as documentações disponíveis. |
| Estrutura do diagnóstico | ⚠️ Parcial | A resposta não apresentou uma sequência lógica de investigação. |
| Aplicação ao Suporte N2 | ⚠️ Parcial | A resposta possui caráter descritivo, semelhante a um artigo técnico. |
| Coleta de evidências | ❌ Insuficiente | Não realizou perguntas para compreender o cenário antes de sugerir hipóteses. |

#### Aprendizados

O experimento demonstrou que perguntas muito genéricas tendem a produzir respostas igualmente amplas. Embora tecnicamente corretas, elas não reproduzem o fluxo de trabalho esperado durante um atendimento de Suporte N2.

A principal limitação observada foi a ausência de um processo estruturado de investigação, iniciando diretamente pela apresentação de possíveis causas sem coletar informações sobre o incidente.

#### Refinamento para o próximo experimento

No próximo teste será utilizada a técnica de **Role Prompting**, definindo explicitamente que o NotebookLM deve atuar como um Analista de Suporte N2 especializado em aplicações web. O objetivo é verificar se essa mudança torna o diagnóstico mais orientado ao processo de investigação utilizado em atendimentos reais.

## Experimento 2 — Role Prompting e Contextualização do Cenário

### Objetivo

Avaliar como a definição de um papel específico para o NotebookLM influencia a qualidade das respostas geradas.

Neste experimento foi adicionado um contexto profissional, simulando um cenário real de atendimento de Suporte N2, com o objetivo de verificar se a IA produziria uma resposta mais próxima de um processo estruturado de troubleshooting.

### Técnica aplicada

Foram utilizadas as seguintes técnicas de Engenharia de Prompt:

- **Role Prompting:** definição da IA como Analista de Suporte N2 especializado em aplicações web.
- **Contextualização:** descrição de um cenário real de incidente.
- **Definição de formato esperado:** solicitação de hipóteses, coleta de informações e testes antes do escalonamento.
- **Restrição de conhecimento:** utilização exclusiva da base de conhecimento carregada no NotebookLM.

### Prompt utilizado

```text
Você é um Analista de Suporte N2 especializado em aplicações web.

Um usuário informa que não consegue acessar um sistema web. A internet funciona normalmente e outros usuários conseguem acessar o sistema.

Com base exclusivamente na base de conhecimento disponível, descreva:

- as hipóteses mais prováveis;
- quais informações devem ser coletadas;
- quais testes devem ser realizados antes de qualquer escalonamento;
```

### Resumo da resposta

A resposta apresentou uma evolução significativa em relação ao primeiro experimento.

O NotebookLM passou a estruturar o diagnóstico considerando que o problema estava isolado em um único usuário, direcionando a investigação para possíveis causas relacionadas ao ambiente cliente (*client-side*).

As hipóteses apresentadas envolveram:

- Cookies, cache e armazenamento local;
- Falhas de execução JavaScript;
- Problemas relacionados a certificados e protocolos HTTPS;
- Bloqueios locais de rede;
- Falhas no carregamento de recursos da aplicação;

Também apresentou uma sequência mais próxima de um atendimento real:

1. Coleta de evidências utilizando Chrome DevTools;
2. Análise de Console e Network;
3. Validação do ambiente do usuário;
4. Execução de testes antes do escalonamento;

### Avaliação

| Critério | Avaliação | Observação |
|----------|-----------|------------|
| Precisão técnica | ✅ Excelente | As hipóteses estão alinhadas com a base de conhecimento. |
| Contextualização | ✅ Excelente | A definição do papel aproximou a resposta do cenário de Suporte N2. |
| Estrutura do diagnóstico | ✅ Boa | A resposta seguiu uma sequência lógica de investigação. |
| Aplicabilidade operacional | ✅ Boa | Foram sugeridos testes antes do escalonamento. |
| Profundidade técnica | ⚠️ Parcial | Alguns testes poderiam apresentar mais detalhes operacionais. |

### Comparação com o Experimento 1

A utilização de Role Prompting apresentou uma melhoria significativa na qualidade da resposta.

No primeiro experimento, a IA apresentou uma explicação técnica ampla sobre possíveis causas de falha de acesso.

Neste experimento, a resposta passou a simular um processo de troubleshooting, considerando contexto, hipóteses, coleta de evidências e ações antes do escalonamento.

### Cicatriz

Apesar da evolução da resposta, foi identificado que a IA ainda apresenta algumas limitações:

- Algumas recomendações possuem nível técnico elevado para uma interação inicial com o usuário.
- Não existe uma priorização clara das hipóteses mais prováveis.
- A sequência de investigação poderia ser mais orientada por perguntas iniciais ao usuário.
- Alguns testes poderiam apresentar critérios objetivos de sucesso ou falha.

### Sugestões de refinamento

A partir das limitações identificadas, o próximo experimento deve explorar a criação de um fluxo de diagnóstico mais estruturado, solicitando que a IA:

- faça perguntas iniciais antes de sugerir testes;
- priorize hipóteses por probabilidade;
- organize o atendimento em etapas;
- indique critérios para escalonamento.

### Sugestões de novos prompts gerados pelo NotebookLM

Durante a interação, a própria IA sugeriu novos caminhos de investigação:

- Como limpar cookies e o armazenamento local no Chrome DevTools?
- Quais códigos de erro no painel Network indicam falha local?
- Como identificar problemas de certificado usando o painel Security?

## Experimento 3 — Estruturação de Fluxo de Troubleshooting

### Objetivo

Avaliar como a definição de uma estrutura de resposta influencia a capacidade do NotebookLM em transformar conhecimento técnico em um procedimento operacional aplicável ao atendimento de incidentes.

Após os experimentos anteriores, foi identificado que respostas técnicas isoladas não eram suficientes para representar o processo de investigação realizado por um Analista de Suporte N2.

Neste experimento foi solicitado que a IA organizasse o diagnóstico em etapas, simulando um fluxo real de troubleshooting.

### Técnica aplicada

Foram utilizadas as seguintes técnicas de Engenharia de Prompt:

- **Role Prompting:** manutenção da definição da IA como Analista de Suporte N2 especializado em aplicações web.
- **Contextualização de cenário:** utilização de um caso realista de falha de acesso.
- **Output Formatting:** definição explícita da estrutura esperada da resposta.
- **Process Prompting:** solicitação de um fluxo sequencial de investigação.

### Prompt utilizado

```text
Você é um Analista de Suporte N2 especializado em diagnóstico de aplicações web.

Um usuário informa que não consegue acessar um sistema web. A conexão com a internet está funcionando normalmente e outros usuários conseguem acessar a aplicação.

Utilizando exclusivamente a base de conhecimento disponível, crie um fluxo estruturado de troubleshooting.

Organize a resposta seguindo este formato:

- Perguntas iniciais que devem ser feitas ao usuário;
- Informações que devem ser coletadas;
- Hipóteses organizadas da mais provável para a menos provável;
- Testes técnicos que devem ser executados;
- Evidências que devem ser coletadas;
- Critérios para decidir quando resolver ou escalonar o incidente.

O objetivo é criar um procedimento que possa ser utilizado por um Analista de Suporte N2 durante um atendimento real.
```

### Resumo da resposta

A resposta apresentou uma evolução em relação aos experimentos anteriores, transformando o conhecimento técnico em um fluxo organizado de investigação.

O NotebookLM estruturou o diagnóstico em seis etapas:

1. Perguntas iniciais ao usuário;
2. Coleta de informações do ambiente;
3. Priorização das hipóteses;
4. Execução de testes técnicos;
5. Registro das evidências;
6. Critérios para resolução ou escalonamento.

Entre os principais pontos apresentados:

- Validação de mensagens de erro e códigos HTTP;
- Testes em diferentes navegadores;
- Análise de cookies, cache e armazenamento local;
- Investigação utilizando Chrome DevTools;
- Coleta de logs do Console e Network;
- Definição de cenários para escalonamento.

### Avaliação

| Critério | Avaliação | Observação |
|---|---|---|
| Precisão técnica | ✅ Excelente | As recomendações estão alinhadas com as fontes utilizadas. |
| Estrutura operacional | ✅ Excelente | A resposta passou a representar um fluxo de atendimento. |
| Aplicação ao Suporte N2 | ✅ Excelente | O conteúdo pode ser adaptado para um procedimento interno. |
| Priorização das hipóteses | ⚠️ Boa | A IA classificou causas prováveis, porém sem considerar impacto ou frequência. |
| Critérios de escalonamento | ✅ Boa | Foram definidos caminhos de encaminhamento. |

### Comparação com experimentos anteriores

Este experimento apresentou uma evolução significativa:

| Experimento | Técnica aplicada | Resultado |
|---|---|---|
| Prompt 1 | Pergunta genérica | Resposta técnica e abrangente, porém sem fluxo operacional. |
| Prompt 2 | Role Prompting + Contexto | Resposta mais próxima do papel de um Analista N2. |
| Prompt 3 | Estruturação de resposta | Criação de um fluxo organizado de troubleshooting. |

### Cicatriz

Apesar da evolução da resposta, foram identificadas algumas limitações:

- A priorização das hipóteses ainda é baseada apenas em uma ordem textual, sem considerar probabilidade, impacto ou frequência.
- Alguns testes técnicos possuem nível de detalhamento elevado para um atendimento inicial.
- A IA ainda não diferencia claramente testes de baixa complexidade para o usuário final e análises avançadas realizadas pelo suporte.
- O fluxo poderia apresentar pontos de decisão mais claros antes do escalonamento.

### Próximo refinamento

O próximo experimento deve explorar técnicas de:

- Priorização de hipóteses;
- Árvores de decisão;
- Definição de critérios objetivos de escalonamento;
- Separação entre ações realizadas pelo usuário e ações realizadas pelo Analista N2.

## Experimento 4 — Árvore de Decisão para Diagnóstico

### Objetivo

Avaliar a capacidade do NotebookLM em transformar um procedimento de troubleshooting em um fluxo de decisão, permitindo que um Analista de Suporte N2 conduza a investigação com base nas evidências coletadas durante o atendimento.

Após os experimentos anteriores, foi identificado que uma resposta estruturada ainda poderia evoluir para um modelo mais próximo da tomada de decisão realizada durante um atendimento real.

Neste experimento, o objetivo foi verificar se a IA conseguiria criar uma sequência lógica de investigação, relacionando perguntas, evidências, testes e critérios de resolução ou escalonamento.

### Técnica aplicada

Foram utilizadas as seguintes técnicas de Engenharia de Prompt:

- **Role Prompting:** manutenção da IA como Analista de Suporte N2 especializado em troubleshooting de aplicações web.
- **Decision Tree Prompting:** criação de uma árvore de decisão baseada em cenários e resultados possíveis.
- **Conditional Prompting:** definição de ações diferentes conforme as evidências encontradas.
- **Prioritização de testes:** solicitação para iniciar por validações de menor complexidade e maior probabilidade de resolução.

### Prompt utilizado

```text
Você é um Analista de Suporte N2 especializado em troubleshooting de aplicações web.

Crie uma árvore de decisão para diagnosticar problemas de acesso a sistemas web utilizando exclusivamente a base de conhecimento disponível.

O cenário inicial é:

"Um usuário informa que não consegue acessar um sistema web. A internet funciona normalmente e outros usuários conseguem acessar a aplicação."

Estruture a árvore seguindo esta lógica:

- Pergunta inicial ou validação realizada;
- Possíveis respostas encontradas;
- Próximo teste ou ação recomendada;
- Evidência esperada;
- Critério para continuar investigando, resolver ou escalonar.

Priorize inicialmente testes de menor complexidade e maior probabilidade de resolução.

A árvore deve diferenciar:

- problemas relacionados ao usuário;
- problemas relacionados ao navegador;
- problemas relacionados à rede;
- problemas relacionados à aplicação.

O objetivo é criar um fluxo que possa ser utilizado por um Analista de Suporte N2 durante um atendimento real.
```

### Resumo da resposta

A resposta apresentou uma evolução significativa, criando um fluxo de investigação baseado em decisões.

O NotebookLM organizou o diagnóstico em quatro grandes áreas:

1. Problemas relacionados ao usuário;
2. Problemas relacionados ao navegador;
3. Problemas relacionados à rede e segurança;
4. Problemas relacionados à aplicação.

A IA passou a relacionar:

- perguntas iniciais;
- respostas possíveis;
- próximos testes;
- evidências esperadas;
- critérios de resolução ou escalonamento.

Entre os principais pontos apresentados:

- Validação através de navegador alternativo e modo anônimo;
- Análise de cache, cookies e armazenamento local;
- Investigação através do Chrome DevTools;
- Identificação de códigos HTTP;
- Análise de certificados SSL/TLS;
- Definição de cenários para escalonamento.

### Avaliação

| Critério | Avaliação | Observação |
|---|---|---|
| Organização lógica | ✅ Excelente | A resposta apresenta uma sequência clara de investigação. |
| Aplicação ao Suporte N2 | ✅ Excelente | O fluxo se aproxima de um procedimento operacional real. |
| Tomada de decisão | ✅ Excelente | As ações variam conforme as evidências encontradas. |
| Priorização dos testes | ✅ Boa | A resposta inicia por validações simples antes de análises avançadas. |
| Critérios de escalonamento | ✅ Boa | Foram definidos cenários para encaminhamento técnico. |

### Comparação com experimentos anteriores

| Experimento | Técnica aplicada | Resultado |
|---|---|---|
| Prompt 1 | Pergunta genérica | Resposta técnica ampla, sem fluxo operacional. |
| Prompt 2 | Role Prompting + Contexto | Resposta direcionada ao papel de Analista N2. |
| Prompt 3 | Estruturação de saída | Criação de um procedimento de troubleshooting. |
| Prompt 4 | Árvore de decisão | Fluxo investigativo orientado por evidências. |

### Cicatriz

Apesar da evolução apresentada, algumas limitações foram identificadas:

- A árvore de decisão ainda possui alguns caminhos técnicos que dependem de conhecimento avançado do analista.
- Algumas hipóteses poderiam possuir uma priorização baseada em frequência de ocorrência e impacto.
- Alguns critérios de resolução poderiam ser mais objetivos, indicando exatamente quais evidências confirmam a correção do problema.
- A separação entre ações realizadas pelo usuário final e ações executadas pelo Analista N2 poderia ser mais clara.

### Próximo refinamento

O próximo experimento deve explorar a criação de um assistente interativo, onde a IA:

- realize perguntas progressivas ao analista;
- avalie as respostas recebidas;
- sugira o próximo passo da investigação;
- justifique a hipótese selecionada;
- recomende resolução ou escalonamento.

## Experimento 5 — Assistente Interativo de Diagnóstico

### Objetivo

Avaliar a capacidade do NotebookLM em atuar como um assistente de investigação durante um atendimento real, conduzindo o Analista de Suporte N2 através de perguntas progressivas e coleta estruturada de evidências.

Nos experimentos anteriores, a IA evoluiu de respostas técnicas para procedimentos estruturados. Neste experimento, o objetivo foi validar se o modelo conseguiria assumir um comportamento mais próximo de um analista auxiliar, evitando apresentar diagnósticos prematuros e conduzindo a investigação com base em evidências.

### Técnica aplicada

Foram utilizadas as seguintes técnicas de Engenharia de Prompt:

- **Interactive Prompting:** solicitação para que a IA conduzisse a investigação através de uma interação progressiva.
- **Socratic Prompting:** utilização de perguntas direcionadas antes da apresentação de hipóteses.
- **Context Management:** manutenção do cenário inicial durante todo o processo de diagnóstico.
- **Evidence-Based Troubleshooting:** orientação para fundamentar decisões através de evidências coletadas.

### Prompt utilizado

```text
Você é um Assistente de Suporte N2 especializado em troubleshooting de aplicações web.

Sua função é auxiliar um Analista de Suporte durante a investigação de incidentes de acesso a sistemas web.

Utilize exclusivamente a base de conhecimento disponível.

Cenário inicial:

"Um usuário informa que não consegue acessar um sistema web. A conexão com a internet funciona normalmente e outros usuários conseguem acessar a aplicação."

Sua abordagem deve seguir um processo investigativo.

Não apresente uma solução imediata.

Conduza o diagnóstico através de perguntas progressivas.

Ao final da investigação, apresente:
- Diagnóstico mais provável;
- Evidências que sustentam a hipótese;
- Ação recomendada;
- Decisão entre resolução ou escalonamento.
```

### Resumo da resposta

O NotebookLM iniciou a interação assumindo o papel de Analista de Suporte N2 e conduziu o atendimento através de perguntas investigativas.

A IA iniciou descartando problemas de infraestrutura global, considerando que outros usuários conseguiam acessar a aplicação, e direcionou a investigação para variáveis locais do usuário.

As primeiras perguntas sugeridas foram:

- O erro ocorre somente no computador principal ou também em outro dispositivo?
- Qual mensagem ou código de erro aparece no navegador?
- O problema persiste em uma aba anônima?

Após a coleta inicial, a IA solicitou evidências técnicas:

- Captura de tela do erro;
- Logs do Console do Chrome DevTools;
- Informações do painel Network;
- Evidências do painel Security.

### Avaliação

| Critério | Avaliação | Observação |
|---|---|---|
| Comportamento investigativo | ✅ Excelente | A IA conduz a investigação antes de sugerir soluções. |
| Coleta de informações | ✅ Excelente | As perguntas iniciais são relevantes para isolamento do problema. |
| Uso de evidências | ✅ Excelente | O diagnóstico é baseado em informações coletadas. |
| Aplicação em atendimento real | ✅ Excelente | O comportamento se aproxima de um assistente de suporte. |
| Autonomia de diagnóstico | ⚠️ Parcial | A IA ainda depende das respostas fornecidas pelo analista. |

### Cicatriz

Apesar da evolução significativa, algumas limitações foram identificadas:

- A IA ainda depende da qualidade das respostas fornecidas pelo usuário ou analista.
- O fluxo pode ser interrompido caso informações importantes não sejam coletadas.
- Algumas perguntas poderiam possuir uma ordem baseada em impacto e probabilidade.
- Ainda é necessário validar como a IA se comporta diante de respostas incompletas ou contraditórias.

### Resultado do experimento

Este experimento demonstrou que a combinação de contexto, definição de papel, estrutura de resposta e interação progressiva permite transformar o NotebookLM em uma ferramenta de apoio ao diagnóstico técnico.

O resultado final aproxima-se do objetivo inicial do projeto: criar um assistente capaz de auxiliar Analistas de Suporte N2 na investigação estruturada de problemas de acesso a sistemas web.

### Sugestões de continuidade geradas pela IA

Durante a interação, o NotebookLM sugeriu perguntas complementares para aprofundar a investigação:

- O erro ocorre apenas no computador principal do usuário?
- Qual é a mensagem exata exibida no navegador?
- O problema persiste ao tentar o acesso em aba anônima?

Essas sugestões demonstram que a IA conseguiu identificar informações críticas para o isolamento da causa raiz.
---

# 8. Prompts Reutilizáveis

Os prompts abaixo foram desenvolvidos para serem utilizados durante atendimentos reais de Suporte N2. O analista deve preencher as informações já coletadas no chamado antes de enviar o prompt ao NotebookLM.

---

# Prompt 1 — Diagnóstico Inicial de Acesso Web

### Objetivo

Realizar uma análise inicial do incidente utilizando as informações registradas no chamado.

### Prompt

```text
Você é um Analista de Suporte N2 especializado em troubleshooting de aplicações web.

Analise exclusivamente utilizando a base de conhecimento disponível.

Dados do chamado

Descrição do problema:
[Descrever o relato do usuário]

URL acessada:
[URL]

Mensagem de erro apresentada:
[Mensagem ou código]

Outros usuários conseguem acessar?
[Sim/Não]

O problema ocorre em apenas um usuário?
[Sim/Não]

Navegador utilizado:
[Chrome / Edge / Firefox...]

Versão do navegador:
[Versão]

Sistema operacional:
[Windows/Linux/macOS]

O teste em aba anônima foi realizado?
[Sim/Não]
Resultado:
[Descrição]

O teste em outro navegador foi realizado?
[Sim/Não]
Resultado:
[Descrição]

Informações adicionais:
[Outras evidências]

Com base nessas informações:

- identifique as hipóteses mais prováveis;
- informe quais informações ainda precisam ser coletadas;
- indique os próximos testes;
- explique o motivo de cada teste;
- informe quais evidências deverão ser anexadas ao chamado;
- indique se já existem informações suficientes para resolução ou se a investigação deve continuar;
```

---

# Prompt 2 — Análise de Erros HTTP

### Objetivo

Interpretar os códigos HTTP encontrados durante o atendimento.

### Prompt

```text
Você é um Analista de Suporte N2 especializado em aplicações web.

Utilize exclusivamente a base de conhecimento disponível.

Dados coletados

URL:
[URL]

Método HTTP:
[GET / POST / PUT...]

Código(s) HTTP encontrado(s):
[200, 302, 401, 403, 404, 500...]

Recurso afetado:
[/login /api/auth ...]

Mensagem apresentada:
[Mensagem]

Os demais recursos carregam normalmente?
[Sim/Não]

Captura do painel Network disponível?
[Sim/Não]

Com base nessas informações:

- explique o significado de cada código HTTP;
- informe as causas mais prováveis;
- identifique quais hipóteses possuem maior probabilidade;
- indique quais testes ainda devem ser executados;
- informe quais evidências técnicas ainda precisam ser coletadas;
- conclua se o incidente pode ser tratado pelo Suporte N2 ou deve ser escalonado;
```

---

# Prompt 3 — Avaliação de Evidências do Chrome DevTools

### Objetivo

Analisar as evidências técnicas coletadas durante o diagnóstico.

### Prompt

```text
Você é um Analista de Suporte N2 especializado em troubleshooting de aplicações web.

Analise exclusivamente utilizando a base de conhecimento disponível.

Dados coletados

Console

Mensagens de erro:
[Colar erros]

Network

Status HTTP encontrados:
[Lista]

Requisições com falha:
[Descrição]

Tempo de resposta:
[Tempo]

Application

Cookies limpos?
[Sim/Não]

Cache limpo?
[Sim/Não]

Local Storage:
[Descrição]

Security

Certificado válido?
[Sim/Não]

Mensagem apresentada:
[Descrição]

Informações adicionais

[Testes realizados]

Com base nas evidências:

- explique o significado de cada informação apresentada;
- identifique as hipóteses mais prováveis;
- descarte hipóteses incompatíveis com as evidências;
- informe quais testes ainda precisam ser executados;
- indique quais evidências faltam para concluir o diagnóstico;
- apresente uma recomendação técnica para continuidade do atendimento;
```

---

# Prompt 4 — Decisão de Resolução ou Escalonamento

### Objetivo

Determinar se o incidente pode ser resolvido pelo Suporte N2 ou deve ser encaminhado para outro time.

### Prompt

```text
Você é um Analista de Suporte N2 especializado em troubleshooting de aplicações web.

Utilize exclusivamente a base de conhecimento disponível.

Resumo do chamado

Descrição do incidente:
[Resumo]

Hipótese principal:
[Hipótese]

Testes executados:
[Listar]

Resultados obtidos:
[Listar]

Evidências anexadas:

- [Screenshots]
- [Logs]
- [Console]
- [Network]
- [Security]

Código(s) HTTP:
[Listar]

Mensagem de erro:
[Listar]

Tentativas de solução realizadas:
[Listar]

Com base nessas informações:

- avalie se todos os testes necessários foram executados;
- identifique possíveis lacunas na investigação;
- informe se existem novas validações antes do escalonamento;
- apresente a hipótese mais provável;
- justifique tecnicamente sua conclusão;
- informe se o chamado deve ser resolvido pelo Suporte N2 ou escalonado;
- caso seja necessário escalonar, indique qual equipe deve receber o chamado;
- gere um resumo técnico que possa ser copiado para o ticket do incidente;
```

---

## Observação

Os campos entre colchetes (`[ ]`) devem ser preenchidos pelo Analista de Suporte N2 com as informações coletadas durante o atendimento. Quanto mais completas forem as evidências fornecidas, maior tende a ser a precisão das análises produzidas pelo NotebookLM.

---

# 9. Glossário

Este glossário apresenta os principais conceitos relacionados à Engenharia de Prompt e às ferramentas utilizadas durante o desenvolvimento deste projeto.

| Conceito | Definição |
|----------|-----------|
| **Base de Conhecimento** | Conjunto de documentos utilizados pelo NotebookLM como fonte para geração das respostas. Neste projeto, foi composta por documentações oficiais sobre troubleshooting, aplicações web e gerenciamento de incidentes. |
| **Caderno Temático** | Espaço criado no NotebookLM que reúne documentos relacionados a um único assunto, permitindo consultas contextualizadas pela IA. |
| **Contexto (Context Window)** | Informações fornecidas à IA para orientar sua interpretação do problema e produzir respostas mais relevantes. |
| **Engenharia de Prompt (Prompt Engineering)** | Processo de criação, refinamento e otimização de instruções fornecidas à IA para melhorar a qualidade, consistência e utilidade das respostas. |
| **Evidência** | Informação técnica coletada durante um diagnóstico, utilizada para confirmar ou descartar hipóteses antes da tomada de decisão. |
| **Hipótese** | Possível causa de um incidente formulada a partir das evidências disponíveis e validada durante o processo de investigação. |
| **Iteração** | Processo de realizar sucessivos refinamentos em um prompt com o objetivo de melhorar a qualidade das respostas produzidas pela IA. |
| **NotebookLM** | Ferramenta de Inteligência Artificial desenvolvida pelo Google que utiliza documentos enviados pelo usuário como única fonte de conhecimento para responder perguntas, resumir conteúdos e apoiar estudos. |
| **Prompt** | Instrução enviada à IA contendo contexto, objetivo e regras para orientar a resposta esperada. |
| **Prompt Template** | Modelo reutilizável de prompt contendo campos que podem ser preenchidos pelo analista conforme o cenário do atendimento. |
| **Refinamento de Prompt** | Processo de modificar um prompt com base na análise das respostas anteriores, tornando as instruções mais claras e específicas. |
| **Role Prompting** | Técnica de Engenharia de Prompt que consiste em atribuir um papel específico à IA (por exemplo, "Você é um Analista de Suporte N2") para direcionar seu comportamento e especializar as respostas. |
| **Suporte N2** | Segundo nível de suporte responsável pela investigação técnica de incidentes, validação de hipóteses, coleta de evidências e decisão sobre resolução ou escalonamento. |
| **Troubleshooting** | Processo estruturado de investigação utilizado para identificar, analisar e solucionar problemas técnicos por meio de testes e evidências. |

## Ferramentas Utilizadas

| Ferramenta | Finalidade |
|------------|------------|
| **NotebookLM** | Construção da base de conhecimento e realização dos experimentos de Engenharia de Prompt. |
| **Google Chrome DevTools** | Referência para investigação de problemas de aplicações web e coleta de evidências técnicas. |
| **MDN Web Docs** | Fonte oficial de documentação sobre tecnologias web utilizadas como base de conhecimento. |
| **Microsoft Learn** | Documentação oficial utilizada para consultas sobre troubleshooting e resolução de problemas. |
| **Cloudflare Developers** | Fonte de referência para conceitos relacionados a SSL/TLS e segurança em aplicações web. |
| **IT Process Maps** | Material utilizado para fundamentar boas práticas de gerenciamento de incidentes e processos de suporte técnico. |

---

## 10. Conclusão

O desenvolvimento deste projeto demonstrou que a qualidade das respostas produzidas por uma Inteligência Artificial depende diretamente da forma como as instruções são elaboradas. Ao longo dos experimentos realizados no NotebookLM, foi possível observar a evolução das respostas à medida que técnicas de Engenharia de Prompt foram aplicadas de forma incremental, transformando respostas inicialmente genéricas em fluxos de investigação estruturados e orientados ao contexto de Suporte N2.

Além de consolidar conhecimentos sobre diagnóstico de problemas de acesso a aplicações web, este projeto permitiu construir uma base de conhecimento especializada, composta por documentações técnicas confiáveis e complementada por um conjunto de prompts reutilizáveis voltados para situações reais de atendimento.

Os experimentos também evidenciaram a importância de orientar a IA por meio de contexto, definição de papéis, estrutura de resposta e regras claras de comportamento. Em vez de buscar respostas prontas, a proposta foi desenvolver um assistente capaz de apoiar o raciocínio investigativo do analista, incentivando a coleta de evidências, a validação de hipóteses e a tomada de decisões fundamentadas.

Como resultado, o projeto entrega um material que pode servir tanto como guia de estudos quanto como apoio operacional para Analistas de Suporte N2, contribuindo para diagnósticos mais consistentes, padronização do processo de troubleshooting e maior eficiência na condução de incidentes relacionados ao acesso a aplicações web.

Como evolução futura, a base de conhecimento poderá ser ampliada com novos cenários de troubleshooting, estudos de caso, integrações com outras tecnologias e novos experimentos de Engenharia de Prompt, tornando o assistente cada vez mais especializado e aderente às rotinas de suporte técnico.

### * Aprendizados *

Durante este projeto desenvolvi conhecimentos sobre:

• Engenharia de Prompt;

• NotebookLM;

• Construção de bases de conhecimento;

• Troubleshooting;

• Diagnóstico de aplicações web;

• Documentação técnica;

• Experimentação orientada por evidências;