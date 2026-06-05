# Cvičenie: Súborové systémy + monitorovanie procesov

**Meno:** Marko Marek
**Dátum:** 5.6.2026

> Vyplň odpovede pod každú otázku. Výstupy z terminálu prilep do code blokov.
> **Dnes nič nepripájame, nemontujeme ani neukladáme natrvalo** — iba pozeráme a používame **bezpečné** príkazy.

---

## Úloha 1 — Pripojené disky

### 1.1 Spusti `mount | grep "^/dev"`. Vymenuj **disky, ktoré sú pripojené**:

```bash
mount | grep "^/dev"
```

**Výstup:**

```text
/dev/sda2 on / type ext4 (rw,relatime,errors=remount-ro)
/dev/sda1 on /boot/efi type vfat (rw,relatime,fmask=0077,dmask=0077,codepage=437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
```

### 1.2 Spusti `df -T /`. Aký **súborový systém** má tvoj koreňový disk?

```bash
df -T /
```

**Odpoveď (názov FS):** ext4

### 1.3 Spusti `cat /etc/fstab`. Koľko **trvalých pripojení** je tam definovaných (riadky, ktoré nezačínajú `#`)?

```bash
cat /etc/fstab | grep -v "^#" | grep -v "^$" | wc -l
```

**Počet:** 2

### 1.4 Aký je rozdiel medzi `/mnt` a `/media`?

> *(Jedna veta.)*

Priečinok `/mnt` slúži na dočasné manuálne pripojenie diskov administrátorom, zatiaľ čo `/media` využíva operačný systém na automatické pripájanie vymeniteľných médií (ako sú USB kľúče).

---

## Úloha 2 — Stav diskov

### 2.1 Spusti `df -h`. Aká je **celková veľkosť** tvojho koreňového disku (`/`)?

```bash
df -h
```

**Výstup pre `/`:**

```text
Filesystem      Size  Used Avail Use% Mounted on
/dev/sda2       110G   45G   59G  44% /
```

### 2.2 Z toho istého výstupu — koľko **% je obsadené** na `/`?

**Use%:** 44%

### 2.3 Spusti `du -sh ~`. Koľko zaberá tvoj **domov**?

```bash
du -sh ~
```

**Veľkosť:** 12G

### 2.4 Spusti `du -sh ~/* 2>/dev/null`. Ktorý priečinok v home zaberá **najviac**?

```bash
du -sh ~/* 2>/dev/null
```

**Najväčší priečinok:** `/home/user/Downloads`

---

## Úloha 3 — Tvoje procesy

### 3.1 Spusti `ps aux | wc -l`. Koľko procesov **celkom beží** v systéme?

```bash
ps aux | wc -l
```

**Počet procesov:** 233

> *(Tip: výstup `wc -l` zahŕňa aj hlavičku, takže odpočítaj 1.)*

### 3.2 Spusti `ps aux | grep bash`. Nájdi **svoj `bash`** — aké je jeho **PID**?

```bash
ps aux | grep bash
```

**Tvoje PID `bash`:** 4512

> *(Pozor: jeden riadok bude tvoj `grep` — ten neráta.)*

### 3.3 Spusti `ps -p 1`. Aký **proces má PID 1**?

```bash
ps -p 1
```

**Odpoveď:** systemd

### 3.4 Spusti `ps aux --sort=-%mem | head -3`. Ktoré **3 procesy** žerú najviac RAM?

```bash
ps aux --sort=-%mem | head -3
```

1. firefox
2. gnome-shell
3. Xorg

---

## Úloha 4 — Live monitoring s `top`

> Spusti `top` a **30 sekúnd sleduj**, ako sa hodnoty menia. Potom ukončenie klávesou **`q`**.

### 4.1 Aké je **`load average`** (prvé číslo — priemer za 1 minútu)?

> *(Hlavička `top` hore vpravo: `load average: X.XX, X.XX, X.XX`)*

**Load average (1 min):** 0.45

### 4.2 Stlač **`M`** (veľké M) v `top` na zoradenie podľa pamäte. Aký **proces je na vrchu**?

**Najväčší žrút RAM:** firefox

### 4.3 Z hlavičky `top` — koľko procesov **celkom beží** (`Tasks: ___ total`)?

**Tasks total:** 241

### 4.4 Z hlavičky `top` — aký je **uptime** systému?

> *(Hľadaj `up X:YY` alebo `up X days`.)*

**Uptime:** up 3:45

---

## Úloha 5 — Zabitie procesu

### 5.1 Spusti **bezpečný** dlho-bežiaci proces na pozadí:

```bash
sleep 600 &
```

**Výstup terminálu** (zapíš PID, ktoré sa vypíše v `[1] _____`):

```text
[1] 8934
```

### 5.2 Nájdi proces v `ps aux`:

```bash
ps aux | grep sleep
```

**Tvoje PID procesu `sleep`:** 8934

### 5.3 Zabi proces obyčajným `kill`:

```bash
kill 8934
```

> *(Nahraď `<PID>` číslom z 5.2.)*

### 5.4 Skontroluj, že proces zmizol:

```bash
ps aux | grep sleep
```

**Vidíš ešte riadok so `sleep 600`?**

- [ ] áno (zabitie nefungovalo)
- [x] nie (proces je preč) ✅

### 5.5 Aký je **rozdiel** medzi `kill <PID>` a `kill -9 <PID>`?

> *(Jedna-dve vety.)*

Obyčajný `kill` pošle signál `SIGTERM`, ktorý procesu umožní bezpečne sa ukončiť a uložiť dáta, zatiaľ čo `kill -9` pošle `SIGKILL`, ktorý proces okamžite a násilne zruší bez akejkoľvek možnosti na bezpečné ukončenie.

---

## Bonus — pre rýchlejších

### B.1 Spusti `free -h`. Koľko **RAM** má tvoj systém celkom a koľko je voľnej?

```bash
free -h
```

**Total RAM:** 15Gi
**Free RAM:** 4.2Gi

### B.2 Skús `lsblk` — vypíše všetky **blokové zariadenia** (disky a partície):

```bash
lsblk
```

**Výstup:**

```text
NAME   MAJ:MIN RM   SIZE RO TYPE MOUNTPOINT
sda      8:0    0 111.8G  0 disk 
├─sda1   8:1    0   512M  0 part /boot/efi
└─sda2   8:2    0 111.3G  0 part /
```

### B.3 Aký súborový systém by si použil v týchto situáciách? *(Vyber: ext4, exFAT, ntfs, btrfs)*

| Situácia | FS |
|----------|----|
| Inštalácia Linux Mint na nový disk | ext4 |
| USB kľúč pre prenos súborov medzi Macom a Windowsom | exFAT |
| Externý disk, ktorý budem čítať aj na Windows PC | ntfs |
| Domáci NAS so snapshotmi | btrfs |

---

## Záver

### Z dnešnej hodiny — ktorý príkaz **najviac využiješ v praxi** a prečo?

Najviac využijem zrejme `top` (alebo `htop`) a `kill`, pretože pri práci sa často stáva, že nejaká aplikácia zamrzne alebo nadmerne vyťaží systém, a toto je najrýchlejší spôsob, ako ju nájsť a ukončiť.

### Aký bol **najprekvapivejší** poznatok dnešnej hodiny?

Zistenie, že v Linuxe je všetko vrátane hardvéru reprezentované ako súbor alebo proces a že celý stav systému viem zistiť pár jednoduchými textovými príkazmi.