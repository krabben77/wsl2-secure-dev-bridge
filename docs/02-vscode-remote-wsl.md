# 02 – VSCode mot WSL2 via Remote-WSL

**Senast ändrat:** 2026-11-09

## Mål

VSCode ska jobba mot filerna inne i WSL2 – inte mot Windows-filsystemet – så att Claude-extensionen och terminalen i VSCode hamnar i samma sandboxade miljö som steg 01.

## Steg

1. Installera tillägget **Remote - WSL** (`ms-vscode-remote.remote-wsl`) i VSCode på Windows-sidan.
2. Se till att detta repo ligger klonat inne i WSL2:s eget filsystem (t.ex. `~/projekt/wsl2-secure-dev-bridge`), **inte** under `/mnt/c/`.
3. Öppna projektet i WSL, på ett av två sätt:
   - Från en WSL-terminal, stå i projektmappen och kör:

     ```bash
     code .
     ```

   - Eller i VSCode: tryck `F1`, välj **Remote-WSL: New Window**, öppna sedan mappen via File-menyn.

   Källa: [code.visualstudio.com – Developing in WSL](https://code.visualstudio.com/docs/remote/wsl)

## Kända begränsningar

- VSCode-fönstret och dess tillägg är inte del av Claude Codes sandbox – de kör med din vanliga WSL-åtkomst, inte begränsade av `/sandbox`.
- Att klona i `/mnt/c/` istället för i WSL2:s eget filsystem är både långsammare och flyttar filerna ut ur den miljö steg 01 sandboxar.

## Verifiering

- Statusfältet längst nere till vänster i VSCode visar **WSL: Ubuntu**.
- En ny terminal i VSCode (**Terminal > New Terminal**) visar en WSL-prompt, inte PowerShell.
