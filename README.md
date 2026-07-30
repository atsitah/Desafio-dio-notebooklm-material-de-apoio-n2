# Construindo um Assistente de Suporte N2 com NotebookLM

## Diagnóstico de Problemas de Acesso a Sistemas Web

> Projeto desenvolvido com o objetivo de construir uma base de conhecimento no NotebookLM, aplicando técnicas de Engenharia de Prompt para auxiliar Analistas de Suporte N2 na investigação de problemas de acesso a aplicações web.

---

# 1. Sobre o Projeto

Este repositório documenta o processo de construção de uma base de conhecimento no **NotebookLM**, onde foram aplicadas técnicas de **Engenharia de Prompt** para apoiar o diagnóstico de problemas de acesso a aplicações web.

---

# 2. Contexto

Analistas de suporte frequentemente precisam consultar diferentes documentações técnicas para investigar problemas de acesso a aplicações web. Esse processo pode aumentar o tempo de atendimento, gerar inconsistências durante o diagnóstico e dificultar a padronização das análises.

Este projeto tem como proposta construir um caderno temático capaz de apoiar Analistas de Suporte N2 durante o processo de investigação de incidentes relacionados ao acesso a aplicações web, auxiliando na formulação de hipóteses, definição de testes, coleta de evidências e tomada de decisão sobre escalonamento.

---

# 3. Objetivos

Os principais objetivos deste projeto são:

- Construir uma base de conhecimento especializada.
- Explorar os recursos do NotebookLM.
- Aplicar técnicas de Engenharia de Prompt.
- Desenvolver prompts reutilizáveis.
- Avaliar a qualidade das respostas produzidas pela IA.
- Documentar os aprendizados obtidos durante o processo.

---

# 4. Escopo do Projeto

Este projeto concentra-se exclusivamente no diagnóstico de problemas relacionados ao acesso a aplicações web, com foco na investigação estruturada de incidentes enfrentados por Analistas de Suporte N2.

## Assuntos abordados

- DNS
- HTTP e HTTPS
- VPN
- Navegadores
- Autenticação
- Códigos de resposta HTTP
- Troubleshooting
- Escalonamento de incidentes

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

- Documentação oficial ou amplamente reconhecida pela comunidade técnica.
- Conteúdo atualizado e mantido por organizações de referência.
- Material aplicável ao contexto de diagnóstico de problemas de acesso a aplicações web.
- Cobertura dos principais domínios de conhecimento necessários para um Analista de Suporte N2.

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
- Refinamento iterativo a partir da análise dos resultados obtidos.

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
- Cache e cookies.

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

> **Os resultados detalhados de cada experimento serão apresentados nas próximas atualizações deste projeto.**

---

# 8. Cicatrizes

Nesta seção serão documentadas as principais dificuldades encontradas durante o desenvolvimento dos prompts, bem como os ajustes realizados para melhorar a qualidade das respostas geradas pelo NotebookLM.

---

# 9. Prompts Reutilizáveis

Serão disponibilizados os prompts refinados durante o projeto, permitindo sua reutilização em novos estudos ou em cenários semelhantes de diagnóstico de problemas de acesso a aplicações web.

---

# 10. Glossário

Esta seção reunirá os principais conceitos técnicos utilizados ao longo do projeto, servindo como material de consulta rápida para futuras revisões.

---

# 11. Conclusão

Ao término do projeto serão apresentados os principais aprendizados obtidos durante a construção da base de conhecimento, a evolução dos prompts e uma análise sobre o potencial do NotebookLM como ferramenta de apoio ao diagnóstico de problemas de acesso a aplicações web.