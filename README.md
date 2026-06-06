# PGATS - CI

## Exercícios da Disciplina de CI/CD

### Exercício 1 — Pipeline em outra ferramenta de CI

Implementação da pipeline no **Azure DevOps** (`azure-pipelines.yml`):

- **Stage Validate** (jobs em paralelo): Lint (TypeScript + Prettier), Testes unitários com Jest + cobertura, Testes E2E com Playwright
- **Stage Mutation Tests** (somente na branch `master`): Stryker com relatório publicado como artefato
- Quality gate de cobertura mínima via `BuildQualityChecks`

### Exercício 2 — Plugin do GitHub Marketplace

Integração do **`dorny/test-reporter`** na pipeline GitHub Actions (`.github/workflows/ci.yml`):

- Posta o resultado de cada teste (Jest e Playwright) diretamente como check no Pull Request
- Sem conta externa — instala do [GitHub Marketplace](https://github.com/marketplace/actions/test-reporter) e funciona imediatamente

### Exercício 3 — Self-hosted Runner

**Quando faz sentido usar:**
- Acesso a rede interna (bancos, serviços privados)
- Hardware específico já disponível (evita custo de minutos cloud)
- Dependências pesadas pré-instaladas (builds mais rápidos)
- Requisitos de compliance onde o código não pode sair da infraestrutura da empresa

**Outras plataformas oferecem o mesmo recurso?**
Sim — GitLab tem o *GitLab Runner*, CircleCI tem *self-hosted runners*, Bitbucket tem *Runners* e Jenkins é inteiramente self-hosted por natureza.

**Implementação:** `runner/docker-compose.yml` sobe um agente local via Docker. Ambas as pipelines (GitHub Actions e Azure DevOps) estão configuradas para usar o runner self-hosted.

---

[![GitHub Actions CI](https://github.com/elderalvesf/pgats-ci/actions/workflows/ci.yml/badge.svg)](https://github.com/elderalvesf/pgats-ci/actions/workflows/ci.yml)
[![Code coverage badge](https://img.shields.io/badge/coverage-100%25-brightgreen)](https://stryker-mutator.io/robo-coasters-example/reports/coverage/lcov-report/index.html)
[![Mutation testing badge](https://img.shields.io/endpoint?style=flat&url=https%3A%2F%2Fbadge-api.stryker-mutator.io%2Fgithub.com%2Fstryker-mutator%2Frobo-coasters-example%2Fmaster)](https://dashboard.stryker-mutator.io/reports/github.com/stryker-mutator/robo-coasters-example/master)

---

## Pré-requisitos

1. Instale o [git](https://git-scm.com)
2. Instale o [nodejs](https://nodejs.org/)
3. Instale o Yarn - `npm install -g yarn`
4. Faça um _Fork_ do projeto
5. Clone o repositório para sua máquina (seu fork)
6. Instale as dependências
   ```shell
   cd pgats-ci
   yarn
   ```
7. Execute os testes de unidade - isso vai gerar um relatório
   ```shell
   yarn run test
   ```
8. Abra o relatório de cobertura de código em `reports/coverage/lcov-report`
9. Execute os testes de mutação com o Stryker
   ```shell
   yarn run test:mutation
   ```
10. Abra o relatório de mutação em `reports/mutation`
11. Instale os navegadores do Playwright
    ```shell
    yarn playwright install
    ```
12. Execute os testes end-to-end com o Playwright
    ```shell
    yarn run e2e
    ```
13. Execute a aplicação com `yarn start`
14. Acesse a aplicação publicada [neste link](https://pgats-ci-example.netlify.app)

---

💜⚡️
# pgats-ci
