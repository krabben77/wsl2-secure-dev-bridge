# 03 – Docker Desktop på WSL2-backend

**Senast ändrat:** 2026-11-09

## Mål

Containrar ska köras via samma WSL2-distro som steg 01 och 02, utan ett extra virtualiseringslager.

## Steg

1. Se till att WSL2 + Ubuntu redan är installerat (steg 01).
2. Installera Docker Desktop på Windows om det inte redan finns – installationsguiden frågar om WSL2-backend.
3. Öppna Docker Desktop → **Settings** → **Resources** → **WSL Integration** → kryssa i **Enable integration with my default WSL distro** och/eller den specifika Ubuntu-distron.
4. Klicka **Apply & Restart**.

   Källa: [docs.docker.com – Docker Desktop WSL 2 backend](https://docs.docker.com/desktop/features/wsl/)

## Kända begränsningar

- Docker Desktop-processen (bakgrundstjänsten) körs utanför Claude Codes sandbox – en container ger inte automatiskt samma isolering som sandboxad Bash från steg 01.
- Åtkomst till Docker-demonen motsvarar i praktiken bred åtkomst till värden (samma nivå som root). Att ge Claude Code möjlighet att köra `docker`-kommandon inifrån WSL2 är inte samma sak som att själva agenten körs inne i en container.

## Verifiering

- Kör `docker info` i WSL2-terminalen och bekräfta att den svarar (inte "cannot connect to the Docker daemon").
- Docker Desktop visar Ubuntu-distron som aktiverad under **Settings → Resources → WSL Integration**.
