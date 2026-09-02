#  Documentação do Projeto

Repositório central para regras de negócio, padrões de código e fluxo de trabalho da equipe do Portal Contábil.

---

##  Guia de Padronização de Branches

Este repositório possui regras automáticas de proteção ativas. Para garantir que as integrações sigam o fluxo de CI/CD e não quebrem o ambiente de produção ou desenvolvimento, todas as branches devem seguir estritamente o padrão de nomenclatura abaixo.

### Regras de Criação de Branch (Fluxo de 2 Etapas)

**1. Branch de Entrega (Short-Release)**
*   **Nomenclatura:** `DD-MM-short-release-Nome-Entrega-Example`
    *   *DD-MM*: Data de criação ou previsão de deploy (ex: 09-03, 15-10).
    *   *short-release*: Termo fixo identificador.
    *   *Nome-Entrega*: Descrição sucinta do escopo da release.
*   **Origem:** Deve ser criada obrigatoriamente a partir da branch `develop`.
*   *Exemplos Válidos:* `09-03-short-release-front`, `01-11-short-release-Front-Header-Teste`

>  *Atenção:* Nomes como `09-03-short-release-` (terminados em hífen sem contexto) ou fora do padrão não acionam as regras de segurança do GitHub corretamente.

** Exemplo Prático de Criação:**

    git checkout develop
    git pull origin develop
    git checkout -b 09-03-short-release-front


**2. Branch de Release do Produto (Trabalho)**
*   **Nomenclatura:** `release/Example-Test`
*   **Origem:** Deve ser criada obrigatoriamente a partir da branch `DD-MM-short-release-Nome-Entrega-Example`.
*   **Objetivo:** Facilitar a abertura dos Pull Requests (PRs) e minimizar erros.

---

## Regras de Proteção Aplicadas

Assim que uma branch é enviada (push) com o padrão correto, o GitHub aplica automaticamente as seguintes travas:

1.  **Bloqueio de Push Direto:** Não é permitido dar git push com alterações diretamente para a branch de release.
2.  **Merge Apenas via PR:** Toda alteração deve ser enviada através de um *Pull Request*.
3.  **Aprovação Obrigatória:** O PR exige a revisão e *aprovação de pelo menos 1 membro* da equipe para liberar o botão de merge.
4.  **Validação Automática (CI/CD):** Os testes de lint e build devem passar 100% no GitHub Actions.

---

##  Padrão de Commits e Issues

### 1. Como nomear as Issues
Toda tarefa criada no board começa com o número da issue, o prefixo correspondente e o que vai ser feito.
* **Formato:** `[Número]) [prefixo]: [O que será feito]`
* **Exemplo:** `1.1) feat: Implementação do Header no Dashboard`

### 2. Tabela de Prefixos para o dia a dia
*   `feat:` — Criar uma nova funcionalidade
*   `fix:` — Corrigir um bug
*   `chore:` — Ajustes técnicos ou de configuração
*   `docs:` — Mexer em documentação
*   `refactor:` — Limpar ou reestruturar código sem mudar a regra
*   `test:` — Escrever testes
*   `ui:` — Mexer puramente na parte visual / estilo

### 3. Como exigir na hora do Commit
O desenvolvedor deve commitar usando o **mesmo prefixo** da tarefa que ele pegou para fazer.

*Exemplos corretos:*
*   `git commit -m "feat: cria estrutura inicial do header"`
*   `git commit -m "ui: ajusta alinhamento do carrossel"`
*   `git commit -m "chore: adiciona arquivo mock de dados"`
