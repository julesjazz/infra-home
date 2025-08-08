# Directory structure
Proposed, building as needed.
```sh
infra-home/
├─ stacks/
│  └─ base-proxy/          # one small demo stack to start
│     ├─ compose.yaml
│     ├─ caddy/
│     │  └─ Caddyfile
│     └─ .env.example
├─ .env.example             # shared defaults you can override per-stack
├─ .gitignore
└─ README.md
```