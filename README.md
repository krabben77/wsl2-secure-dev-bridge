# wsl2-secure-dev-bridge

Lathundar som flyttar Claude Code-arbete från osandboxad native Windows till en sandboxad WSL2-miljö, dokumenterat och stegvis förbättringsbart.

## Lathundar, i ordning

1. [docs/01-wsl2-setup.md](docs/01-wsl2-setup.md) – WSL2, Ubuntu och sandboxad Claude Code CLI
2. [docs/02-vscode-remote-wsl.md](docs/02-vscode-remote-wsl.md) – VSCode mot WSL2 via Remote-WSL
3. [docs/03-docker-desktop-wsl2.md](docs/03-docker-desktop-wsl2.md) – Docker Desktop på WSL2-backend

## Bakgrund

Design och motivering finns i [claude-code-larande](https://github.com/krabben77/claude-code-larande)-repot, i [PR #1](https://github.com/krabben77/claude-code-larande/pull/1) tills den är sammanslagen: [designspecen](https://github.com/krabben77/claude-code-larande/blob/ccr-21d21d0f-imcnm2/docs/superpowers/specs/2026-11-09-wsl2-security-bridge-design.md) och [implementationsplanen](https://github.com/krabben77/claude-code-larande/blob/ccr-21d21d0f-imcnm2/docs/superpowers/plans/2026-11-09-wsl2-security-bridge-plan.md).
