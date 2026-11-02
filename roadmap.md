# AscendEngineer — Roadmap de Engenharia de Software

Início: 2 de novembro de 2026

## Visão geral

Em 24 semanas, sair de desenvolvedor C# para engenheiro de software pronto para entrevistas de LeetCode, perguntas técnicas, System Design e Clean Architecture.

Ponto de partida: 3 anos de experiência profissional com C# e 2h de estudo por dia, de segunda a sexta (cerca de 10h por semana).

Tudo o que for estudado vira código no **AscendEngineer**, uma aplicação que é o próprio roadmap: semanas, tópicos, problemas de LeetCode resolvidos, banco de perguntas técnicas e progresso. No fim, o projeto conta a história do aprendizado e serve de portfólio.

## Princípios

- **Mão primeiro, Claude depois.** Todo tema novo é implementado sozinho primeiro. Depois, o Claude Code revisa, sugere alternativas e gera testes. Só se automatiza o que já foi feito à mão duas ou três vezes.
- **LeetCode 100% sem IA.** Na entrevista não há ajuda. A IA só entra depois, para analisar a solução já pronta.
- **CI e Docker desde a Semana 1, TDD desde a Fase 2.** Nenhum deles é uma fase isolada: começam simples e evoluem junto com o projeto.
- **Medir, não supor.** Performance, cache e escala são validados com números (profiler, testes de carga), que depois viram histórias para contar em entrevista.

## Rotina

Cada dia útil tem 2h divididas em 40 min de LeetCode e 1h20 de teoria e projeto.

Cada semana segue o mesmo formato:

1. Teoria do tema da semana
2. Exercício prático pequeno, isolado do projeto (pasta `labs/`)
3. Entrega de uma feature no AscendEngineer
4. Problemas de LeetCode do padrão da semana
5. De 5 a 10 perguntas de entrevista sobre o tema, respondidas por escrito na sexta

Lembrete diário: evento recorrente no calendário, de segunda a sexta, com aviso 10 min antes. Na fase de mensageria, ele é substituído por um job do próprio AscendEngineer que envia o tema do dia no WhatsApp.

## Roadmap em 24 semanas

As fases rodam em sequência; LeetCode, CI/CD, Docker e Claude Code atravessam as 24 semanas em paralelo.

| Fase | Semanas | O que estudar | Entrega no AscendEngineer |
| --- | --- | --- | --- |
| 0. Fundamentos | 1–2 | CPU, memória, stack vs heap, processos e threads; CLR, JIT e IL; o que é um container (namespaces e cgroups) | Solution em camadas, primeiro pipeline de CI, PostgreSQL em container, primeiro `CLAUDE.md` |
| 1. C# por dentro | 3–4 | async/await como state machine, gerações do GC, `Span<T>` e `Memory<T>`, boxing, struct vs class, `IEnumerable` vs `IQueryable` | Entidades e regras do Domain, medidas com o profiler do Visual Studio |
| 2. Design e DI | 5–7 | SOLID, patterns (Strategy, Factory, Repository, Decorator), lifetimes de DI, captive dependency, keyed services, decorators com Scrutor, mini container de DI com reflection, TDD (ciclo Red, Green, Refactor; katas String Calculator e Bowling Game; escolas clássica e mockista), testes com xUnit e NSubstitute | Regras do Domain e casos de uso da Application escritos com TDD, testes rodando no CI |
| 3. Backend | 8–10 | ASP.NET Core, middlewares, EF Core, SQL, migrations, autenticação JWT, Docker Compose básico, testes de integração com WebApplicationFactory e Testcontainers, pirâmide de testes | Infrastructure e API completas, banco e API subindo juntos, testes de integração com banco real em container |
| 4. Frontend | 11–12 | HTML semântico, CSS (flexbox e grid), JS moderno, DOM, fetch, módulos ES | Interface em HTML, CSS e JS puro consumindo a API |
| 5. Containers e CI/CD | 13 | Dockerfile multi-stage, camadas e cache de build, redes, variáveis de ambiente, imagem gerada no CI | App inteiro subindo com um comando |
| 6. Tempo real | 14–15 | WebSocket nativo (handshake, frames, reconexão), depois SignalR para comparar | Painel ao vivo de progresso |
| 7. Mensageria | 16–17 | RabbitMQ (exchanges, filas, acks), retry, dead letter, padrão Outbox, jobs agendados | Worker de conquistas e estatísticas; lembrete diário no WhatsApp |
| 8. Escala | 18–20 | Cache com Redis, load balancing com YARP ou Nginx, backplane para WebSocket, testes de carga com k6 | 3 instâncias da API e relatório de latência p95 e requisições por segundo |
| 9. System Design | 21–22 | CAP, sharding, replicação, filas, rate limiting, design de sistemas clássicos | Documento de arquitetura do AscendEngineer |
| 10. Entrevistas | 23–24 | Mock interviews, revisão do banco de perguntas, comportamental com método STAR | Deploy final e README com as métricas medidas |

## Semana 01 — Fundamentos de computação

Segunda-feira foi usada na preparação (repositório, solution, CI e `CLAUDE.md`). A teoria vai de terça a sexta. Os experimentos ficam em `labs/semana-01`, fora da solution principal.

| Dia | Teoria | Experimento em C# | LeetCode |
| --- | --- | --- | --- |
| Terça | CPU: ciclo de execução, registradores, cache L1/L2/L3, localidade de memória | Percorrer uma matriz grande por linha e por coluna e medir o tempo de cada forma | Contains Duplicate |
| Quarta | Memória: stack vs heap, value vs reference types, boxing | Comparar `struct` e `class` num loop grande e observar as alocações no Diagnostic Tools do Visual Studio | Valid Anagram |
| Quinta | Processos e threads: context switch, `Thread` vs `ThreadPool` vs `Task`, race condition | Várias threads incrementando o mesmo contador sem proteção, ver o resultado errado e corrigir | Two Sum |
| Sexta | Do C# ao processador: CLR, IL, JIT, tiered compilation | Escrever um método simples e ler o IL gerado no sharplab.io | Group Anagrams |

Containers, namespaces e cgroups ficam para a Semana 02, junto com o primeiro contato com Docker. Top K Frequent Elements abre o LeetCode da Semana 02.

**Perguntas de entrevista para sexta** (responder por escrito, sem consultar):

1. Qual a diferença entre stack e heap?
2. Um value type sempre fica na stack?
3. O que é boxing e por que ele tem custo?
4. Qual a diferença entre processo e thread?
5. O que é context switch e por que ele é caro?
6. Qual a diferença entre `Thread`, `ThreadPool` e `Task`?
7. O que é uma race condition e quais as formas de evitá-la em C#?
8. O que é IL e qual o papel do JIT?
9. Por que percorrer uma matriz por linha costuma ser mais rápido que por coluna?
10. O que é um cache miss?

## Trilha de LeetCode

Um problema por dia, em C#, sem IA, organizado por padrão (referência: lista NeetCode 150). Cada problema é registrado no AscendEngineer com padrão, dificuldade e complexidade de tempo e espaço.

| Semanas | Padrão | Problemas de partida |
| --- | --- | --- |
| 1–2 | Arrays e hashing | Two Sum, Contains Duplicate, Valid Anagram, Group Anagrams, Top K Frequent Elements |
| 3–4 | Two pointers e sliding window | Valid Palindrome, 3Sum, Container With Most Water, Longest Substring Without Repeating Characters |
| 5–6 | Stack e binary search | Valid Parentheses, Daily Temperatures, Search in Rotated Sorted Array |
| 7–8 | Linked list | Reverse Linked List, Merge Two Sorted Lists, LRU Cache |
| 9–11 | Árvores e tries | Invert Binary Tree, Validate BST, Lowest Common Ancestor, Implement Trie |
| 12–13 | Heaps | Kth Largest Element, Merge K Sorted Lists, Find Median from Data Stream |
| 14–15 | Backtracking | Subsets, Permutations, Combination Sum, Word Search |
| 16–18 | Grafos | Number of Islands, Clone Graph, Course Schedule, Rotting Oranges |
| 19–21 | Programação dinâmica | Climbing Stairs, House Robber, Coin Change, Longest Common Subsequence |
| 22–24 | Revisão mista | Problemas aleatórios com tempo cronometrado de 30 min, simulando entrevista |

## Trilha de Docker

Docker entra na Semana 1 e cresce até orquestrar seis ou sete containers na fase de escala.

| Semanas | O que aprender | Uso no AscendEngineer |
| --- | --- | --- |
| 1–2 | O que é um container: processos isolados por namespaces e cgroups; diferença para uma VM | Ligação direta com a teoria de processos da Semana 01 |
| 2 | Imagem vs container, `run`, `ps`, `logs`, `exec`, portas e volumes | PostgreSQL em container, sem instalar nada na máquina |
| 8–10 | Docker Compose básico | Banco e API rodando juntos; Testcontainers subindo banco real nos testes de integração |
| 13 | Dockerfile multi-stage, camadas e cache, imagens enxutas, redes, variáveis de ambiente | API containerizada, imagem gerada no CI |
| 16–20 | Compose com vários serviços, healthchecks, réplicas | RabbitMQ, Redis, 3 instâncias da API e balanceador com um único `docker compose up` |

## Trilha de Claude Code

Cada recurso do Claude Code entra no momento em que o projeto precisa dele, sempre depois do trabalho feito à mão. Os detalhes evoluem rápido: conferir a [documentação oficial](https://docs.claude.com/en/docs/claude-code/overview) em cada etapa.

| Fase | Recurso | Uso no AscendEngineer |
| --- | --- | --- |
| 0. Fundamentos | Instalação, uso básico, `CLAUDE.md` | Regras da arquitetura escritas para o Claude respeitar (dependências apontam para dentro, Domain sem pacotes) |
| 2. Design e DI | Comandos personalizados e skills | Skill "criar caso de uso no padrão do projeto", escrita só depois de alguns casos feitos à mão; TDD com IA: você escreve os testes, o Claude propõe a implementação |
| 3. Backend | Revisão e geração de testes | Revisão crítica dos endpoints e testes de casos de borda |
| 5. Containers e CI/CD | Integração com GitHub Actions | Revisão automática de pull requests no pipeline |
| 7–8. Mensageria e Escala | Subagents e hooks | Agente revisor de performance e concorrência; hooks rodando `dotnet test` e `dotnet format` |
| 9. System Design | MCP | Conexão ao banco ou ao GitHub para analisar dados reais do projeto |

## Arquitetura do projeto

Clean Architecture em quatro projetos, com as dependências apontando sempre para dentro, em direção ao Domain. O nome completo AscendEngineer fica no repositório e na interface; o código usa o prefixo `Ascend`.

```
AscendEngineer/
├── src/
│   ├── Ascend.Domain/          → Entidades, Value Objects, regras de negócio (zero dependências)
│   ├── Ascend.Application/     → Casos de uso, DTOs, interfaces (ex: IProblemRepository), validações
│   ├── Ascend.Infrastructure/  → EF Core, PostgreSQL, repositórios, Redis, RabbitMQ
│   └── Ascend.Api/             → Endpoints, DI, middlewares
│       └── wwwroot/            → Frontend em HTML, CSS e JS puro
├── tests/
│   ├── Ascend.Domain.Tests/
│   ├── Ascend.Application.Tests/
│   └── Ascend.Api.IntegrationTests/
├── labs/                       → Experimentos de estudo, fora da solution
├── docs/                       → Roadmap e documentação
├── .github/workflows/          → Pipeline de CI
├── docker-compose.yml
└── CLAUDE.md
```

**Por que Domain separado de Application:** o Domain responde "quais são as regras do negócio"; a Application responde "o que o sistema faz" e orquestra. Em projetos separados, o compilador impede que uma entidade dependa de DTOs ou de outros projetos (validado na prática: a referência circular Domain → Application falha no restore com `MSB4006`). Em sistemas pequenos, juntar os dois (estilo eShopOnWeb) também é válido; conhecer os dois modelos e o trade-off é o que conta em entrevista.

## Ambiente e ferramentas

| Ferramenta | Papel no roadmap |
| --- | --- |
| .NET 10 (SDK 10.0.403, fixado no `global.json`) | Runtime e SDK de todo o backend |
| Visual Studio | Backend em C#, testes, debug e profiler de memória e CPU (muito usado nas Fases 0 e 1) |
| VS Code | Frontend em HTML, CSS e JS, Dockerfiles, Compose, YAML do CI, scripts do k6 |
| Extensão Docker (VS Code) | Visualizar containers, imagens e logs enquanto os comandos ainda são novos |
| Extensão Claude Code (VS Code) | Trilha de IA |
| Git e GitHub | Repositório e GitHub Actions |
| Docker Desktop | Containers locais |
| Ferramentas futuras | PostgreSQL, Redis, RabbitMQ, YARP ou Nginx, k6, todos via Docker |

## Backlog de features do AscendEngineer

| Feature | Fase | O que exercita |
| --- | --- | --- |
| Cadastro de semanas e tópicos do roadmap | 2–3 | Domain, casos de uso, EF Core |
| Registro de problemas de LeetCode (padrão, dificuldade, complexidade, anotações) | 2–3 | Regras de domínio, validação |
| Banco de perguntas técnicas para revisão | 3 | CRUD, filtros, `IQueryable` |
| Autenticação | 3 | JWT, middlewares |
| Interface web | 4 | HTML, CSS, JS puro, fetch |
| Painel ao vivo de progresso | 6 | WebSocket e SignalR |
| Conquistas, sequência de dias e estatísticas | 7 | RabbitMQ, worker, Outbox |
| Lembrete diário no WhatsApp com o tema do dia | 7 | Job agendado, integração com API externa (WhatsApp Business ou Twilio), templates aprovados |
| Cache das consultas mais pesadas | 8 | Redis |
| Três instâncias atrás de um balanceador | 8 | YARP ou Nginx, backplane no Redis |
| Relatório de testes de carga | 8 | k6, latência p95, requisições por segundo |

## Progresso

**Começo**

- [ ] Criar evento recorrente de estudo no calendário (seg–sex)
- [ ] Instalar .NET 10, Git, Docker Desktop, Visual Studio, VS Code e Claude Code
- [x] Criar o repositório AscendEngineer no GitHub
- [x] Montar a solution com os 4 projetos e os 3 de testes, digitando os comandos à mão
- [x] Criar o primeiro pipeline de CI (build e testes a cada push)
- [x] Escrever o primeiro `CLAUDE.md` com as regras da arquitetura

**Fases**

- [ ] Fase 0. Fundamentos (semanas 1–2)
- [ ] Fase 1. C# por dentro (semanas 3–4)
- [ ] Fase 2. Design e DI (semanas 5–7)
- [ ] Fase 3. Backend (semanas 8–10)
- [ ] Fase 4. Frontend (semanas 11–12)
- [ ] Fase 5. Containers e CI/CD (semana 13)
- [ ] Fase 6. Tempo real (semanas 14–15)
- [ ] Fase 7. Mensageria (semanas 16–17)
- [ ] Fase 8. Escala (semanas 18–20)
- [ ] Fase 9. System Design (semanas 21–22)
- [ ] Fase 10. Entrevistas (semanas 23–24)
