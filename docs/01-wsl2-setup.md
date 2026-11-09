# 01 – WSL2, Ubuntu och sandboxad Claude Code

**Senast ändrat:** 2026-11-09

> **Claude Desktop ≠ Claude Code Desktop:** "Claude Desktop" är den allmänna chatt-appen för claude.ai. "Claude Code Desktop" är ett eget GUI för Claude Code. Den här lathunden handlar om Claude Code CLI inne i WSL2 – ingen av de två Desktop-apparna behövs för det.

## Mål

Få WSL2 med Ubuntu igång, och Claude Code CLI installerat och sandboxat *inifrån* WSL2 – inte på native Windows, där Bash-kommandon annars körs helt oskyddade.

## Steg

1. **Installera WSL2 + Ubuntu.** I PowerShell (som vanlig användare, inte Administrator):

   ```powershell
   wsl --install
   ```

   Detta installerar WSL och standarddistributionen Ubuntu, och sätter WSL2 som standardversion. Om WSL redan finns men utan en distro:

   ```powershell
   wsl --install -d Ubuntu
   ```

   Källa: [Microsoft Learn – Install WSL](https://learn.microsoft.com/windows/wsl/install)

2. **Verifiera att det är WSL2, inte WSL1:**

   ```powershell
   wsl -l -v
   ```

   Ubuntu ska visa `VERSION 2`.

3. **Installera Claude Code CLI inifrån WSL2** (öppna Ubuntu-terminalen, inte PowerShell):

   ```bash
   curl -fsSL https://claude.ai/install.sh | bash
   ```

   Källa: [code.claude.com – Setup](https://code.claude.com/docs/en/setup)

4. **Installera paketen sandboxen kräver** på Linux/WSL2:

   ```bash
   sudo apt-get update && sudo apt-get install -y bubblewrap socat
   ```

   Källa: [code.claude.com – Sandboxing](https://code.claude.com/docs/en/sandboxing)

5. **Aktivera sandboxen.** Starta en Claude Code-session i WSL2-terminalen och kör:

   ```
   /sandbox
   ```

   Välj ett läge i panelen som öppnas.

## Kända begränsningar

- Sandboxen skyddar bara Bash-, PowerShell- och Monitor-kommandon och deras barnprocesser. Claude Codes filverktyg (Read/Edit/Write), MCP-servrar och hooks körs ändå direkt på WSL2-värden.
- WSL2 kan vidarebefordra anrop till Windows-binärer (`cmd.exe`, `powershell.exe`, allt under `/mnt/c/`) via en Unix-socket om inte det begränsas explicit i inställningarna.
- Detta steg ger inget skydd på native Windows – hela poängen är att flytta arbetet in i WSL2.

## Verifiering

- `wsl -l -v` visar Ubuntu med `VERSION 2`.
- I Claude Code, kör `/sandbox` → fliken **Dependencies** visar `ripgrep`, `bubblewrap`, `socat` och seccomp-filtret som tillgängliga (inte bara en tom flik).
