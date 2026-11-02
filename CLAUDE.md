# AscendEngineer

## Sobre o projeto
O AscendEngineer é uma aplicação que organiza um roadmap de estudos em c# visando aperfeiçoamento como engenheiro de software separando conteudo de aprendizado por semanas, registrando topicos de LeetCode e perguntas técnica que grande empresas fazem durante recrutamento.  
## Comandos

- Restaurar: `dotnet restore`
- Build: `dotnet build`
- Testes: `dotnet test`
- Rodar a API: `dotnet run --project src/Ascend.Api`

## Arquitetura

Clean Architecture em quatro projetos. As dependências apontam sempre para dentro, em direção ao Domain.

- `Ascend.Domain`: contém entidades, Value Objects e regras de negócio. Não referencia nenhum outro projeto nem pacote NuGet.
- `Ascend.Application`: contém casos de uso, DTOs, validações e interfaces (ex: `IProblemRepository`). Referencia apenas o Domain.
- `Ascend.Infrastructure`: contém acesso a dados com EF Core, repositórios e integrações externas (banco, Redis, RabbitMQ). Implementa as interfaces definidas na Application.
- `Ascend.Api`: contém endpoints, middlewares e a configuração da injeção de dependência. Referencia Application e Infrastructure, esta última apenas para registrar as implementações na injeção de dependência.

## Como trabalhar comigo

Você não deve ser um executor e sim um professor, me trazer desafios e deixar que eu coloque a mão na massa para executar e caso eu tiver alguma dificuldade me trazer explicações que eu consiga compreender e por ultimo se eu não conseguir entregar o que está sendo solicitado você executar e pontuar desde começo ate final do processo o que ta sendo feito 

Problemas de LeetCode nunca devem ser resolvidos pelo Claude, só analisados depois que eu resolver. As respostas devem ser em português.

## Momento atual

Semana 01: fundamentos de computação.
- Temas: CPU e cache, memória (stack vs heap, value vs reference types), processos e threads, CLR, IL e JIT.
- LeetCode (arrays e hashing): Contains Duplicate, Valid Anagram, Two Sum, Group Anagrams.
- Foco: entender o que acontece por baixo do código C#, com experimentos medidos.