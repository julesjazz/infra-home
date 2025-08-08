# Directory structure

```sh
infra-home/
├─ .github/
│  ├─ workflows/
│  │  ├─ ci.yml                    # lint, build, scan, test (matrix by stack)
│  │  ├─ release.yml               # tag → build & push to ghcr.io/julesjazz/*
│  │  └─ reusable-*.yml            # called by downstream repos
│  └─ ISSUE_TEMPLATE/…             # optional
├─ stacks/                         # docker-compose stacks (LAN services, db, proxy, etc.)
│  ├─ base-proxy/
│  │  ├─ compose.yaml              # traefik/caddy + whoami demo
│  │  └─ .env.example
│  └─ obsidian-indexer/            # example RAG/ingest service
│     ├─ compose.yaml
│     └─ .env.example
├─ k8s/                            # k8s learning env (kind/k3d/k3s), kustomize overlays
│  ├─ base-proxy/
│  │  ├─ base/                     # Deploy/Service/Ingress, no secrets
│  │  └─ overlays/
│  │     ├─ dev/
│  │     └─ home/
│  └─ tooling/
│     ├─ kind-cluster.yaml
│     └─ kustomize-configs/…
├─ ops/
│  ├─ Makefile                     # make up/down/scan/lint/k8s-up/release
│  ├─ pre-commit-config.yaml
│  ├─ renovate.json                # dep updates
│  └─ backup/restore scripts
├─ sec/
│  ├─ .sops.yaml                   # AGE recipients
│  ├─ policies/                    # e.g., OPA/Conftest (optional)
│  └─ docs-hardening.md
├─ scripts/                        # tiny helpers (bootstrap, env checks)
├─ Dockerfiles/                    # shared base images if needed
├─ LICENSE (MIT)
└─ README.md
```