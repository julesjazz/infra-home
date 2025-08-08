# Key practices to bake in now

- **Parametrize with .env.example** (Compose) and kustomization.yaml + ConfigMapGenerator (K8s).
- **Secrets**: commit only SOPS-encrypted secrets (AGE). Document key creation & decryption.
- **CI/CD:**
    - Lint: `hadolint`, `yamllint`, `kubeconform`.
    - Build: `docker buildx`, multi-arch optional.
    - Scan: `trivy` (images + IaC).
    - Test: `docker compose up -d && healthcheck`, kubeconform for k8s.
    - Publish on tag → GHCR.
    - Provide reusable workflows so private repos can call:
        ```yaml
        jobs:
        call-shared-ci:
            uses: julesjazz/infra-home/.github/workflows/ci.yml@v1
            with: stack: obsidian-indexer
        ```
    - Versioning: tag releases per stack (obsidian-indexer-v0.1.0), or monorepo tags with matrix.
    - Pre-commit: formatting/lint security checks run locally before commits.
    - Docs: short “How to fork/clone as a new project” and “Secrets with SOPS” sections.
