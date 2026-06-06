[![GitHub Actions CI](https://github.com/elderalvesf/pgats-ci/actions/workflows/ci.yml/badge.svg)](https://github.com/elderalvesf/pgats-ci/actions/workflows/ci.yml)
[![Code coverage badge](https://img.shields.io/badge/coverage-100%25-brightgreen)](https://stryker-mutator.io/robo-coasters-example/reports/coverage/lcov-report/index.html)
[![Mutation testing badge](https://img.shields.io/endpoint?style=flat&url=https%3A%2F%2Fbadge-api.stryker-mutator.io%2Fgithub.com%2Fstryker-mutator%2Frobo-coasters-example%2Fmaster)](https://dashboard.stryker-mutator.io/reports/github.com/stryker-mutator/robo-coasters-example/master)

# PGATS - CI

## CI/CD

Pipelines implementadas como parte dos exercícios da disciplina de CI/CD:

| Plataforma | Arquivo | Destaques |
|---|---|---|
| **GitHub Actions** | `.github/workflows/ci.yml` | Lint, testes unitários (Jest), E2E (Playwright), mutation tests (Stryker) + `dorny/test-reporter` para relatórios no PR |
| **Azure DevOps** | `azure-pipelines.yml` | Mesmos stages + `BuildQualityChecks` como quality gate de coverage |

**Self-hosted runner:** `runner/docker-compose.yml` — sobe agente local via Docker, ambas as pipelines configuradas para usá-lo.

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
