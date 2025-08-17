# Git Repository Naming Convention

**Purpose** Keep repository names clear, consistent, searchable, and automation‑friendly across the organization.

---

## Scope

Applies to all new repositories (source, infra, libs, templates, examples). Existing repos should follow the **Migration Guidance** below when practical.

---

## Golden Rules

1. **lowercase kebab‑case** only: words separated by hyphens (`-`).
2. **ASCII letters/numbers/hyphens**; no spaces, underscores, dots, emoji, or special characters.
3. **No versions, envs, or owners** in repo names (use tags/branches for versions; environments live in deployment config).
4. **Be descriptive but concise** (ideally ≤ 30 chars; hard limit 100).
5. **One purpose per repo** (monorepo is an explicit exception and must be labeled as such).

**Allowed pattern (regex):**

```
^[a-z0-9]+(?:-[a-z0-9]+)*$
```

---

## Recommended Naming Patterns

Choose the pattern that best communicates the repo’s role. Combine elements as needed, keeping it short.

### 1) Product / Component split

- `product-frontend`, `product-backend`, `product-mobile`
- `product-admin-portal`, `product-customer-api`

### 2) Service‑oriented / Microservices

- `auth-service`, `billing-service`, `notification-service`
- `inventory-worker`, `payment-gateway`

### 3) Libraries & SDKs

- `ui-components-angular`, `ui-components-react`
- `sdk-js`, `sdk-java`, `sdk-python`
- `shared-lint-rules`, `shared-configs`

### 4) Data / ML

- `data-pipeline`, `etl-orders`, `feature-store`
- `ml-model-training`, `ml-serving-api`

### 5) Infrastructure / IaC

- `infra-terraform-modules`, `infra-k8s-manifests`
- `platform-observability`, `platform-ci-pipelines`

### 6) Templates & Examples

- `template-angular-app`, `template-node-service`
- `example-oauth-client`, `example-webhook-consumer`

### Optional qualifiers (suffixes)

- Runtime/stack: `-node`, `-spring`, `-go`, `-flutter`
- Target/platform: `-web`, `-ios`, `-android`, `-lambda`

> **Avoid:** personal names (`-john`), environments (`-dev`, `-prod`), or ticket IDs in the repo name.

---

## Branch, Tag & Release Conventions (related but separate)

- **Default branch:** `main` (or `develop` if GitFlow is enforced—choose one org‑wide).
- **Branches:**
  - `feature/<ticket-or-slug>` e.g., `feature/reg-23644-status-badges`
  - `bugfix/<ticket-or-slug>`
  - `hotfix/<ticket-or-slug>`
  - `release/<version>` e.g., `release/0.151.1`
- **Tags:** `vMAJOR.MINOR.PATCH` (e.g., `v0.151.1`).
- **Pre‑releases:** `v1.2.0-rc.1`, `v1.2.0-beta.2`.

---

## Examples (good)

- `order-service`
- `customer-portal-frontend`
- `ui-components-angular`
- `infra-terraform-modules`
- `ml-model-training`

**Anti‑examples (avoid) & fixes**

- `OrderService` → `order-service`
- `customer_portal_frontend` → `customer-portal-frontend`
- `orders-service-v2` → `orders-service` (tag `v2.0.0`)
- `billing-service-prod` → `billing-service` (env handled in config)
- `arun-new-ui` → `ui-components-angular` (branch carries personal/ticket context)

---

## Automation & Checks

- Enforce with a repository‑creation hook or bot using the regex above.
- Validate against a **deny list**: `prod`, `dev`, `qa`, `tmp`, `test`, personal names, dates.
- Optionally auto‑append area labels based on path or template (e.g., `template-*`).

---

## Migration Guidance (existing repos)

1. Propose new name in a short RFC or ticket.
2. Rename in hosting platform (**preserve redirects** if supported).
3. Update remotes: `git remote set-url origin <new-url>`.
4. Update CI/CD, webhooks, docs, badges, dependency manifests.
5. Announce to affected teams and archive any deprecated aliases after 30 days.

---

## Decision Tree (quick pick)

1. Is it a **service**? → `<domain>-service`.
2. Is it a **frontend app**? → `<product>-frontend` (or `<product>-admin-portal`).
3. Is it a **library/SDK**? → `ui-components-<framework>` or `sdk-<language>`.
4. Is it **infra**? → `infra-<scope>` or `platform-<area>`.
5. Is it a **template**? → `template-<stack-or-app-type>`.

---

## Ownership & Metadata

- Add `CODEOWNERS` for reviewers.
- Add `README.md` with purpose, owners, and links (issue tracker, docs).
- Add `LICENSE` and `SECURITY.md` where applicable.

---

**Contact:** Platform/DevEx team for exceptions or edge cases.

