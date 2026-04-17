# Cvičenie: Linux — základy, GNU/GPL a distribúcie

> Vyplň odpovede pod každú otázku. Pri otázkach typu áno/nie zaškrtni `- [x]`. Výstupy z terminálu prilep do code blokov.

---

## Úloha 1 — Pojmy GNU a GPL

### 1.1 Rozdiel „free as in freedom" vs. „free as in beer"

**free as in freedom:** Znamená slobodu softvéru (Free Software). Ide o slobodu softvér spúšťať, kopírovať, distribuovať, študovať, meniť a vylepšovať (vyžaduje sa prístup k zdrojovému kódu).

**free as in beer:** Znamená, že softvér je dostupný zadarmo bez platenia peňazí (Freeware). Nemusí však poskytovať zdrojový kód, takže používateľ nemá slobodu ho upravovať.

### 1.2 Čo znamená skratka GPL (celý anglický názov)?
GNU General Public License

### 1.3 Prečo sa Linux niekedy označuje ako „GNU/Linux" a nielen „Linux"?
Slovo „Linux“ technicky označuje iba jadro (kernel) operačného systému. Drvivá väčšina systémových nástrojov, utilít a základných knižníc pochádza z projektu GNU. Preto je presnejší názov celého systému „GNU/Linux“.

---

## Úloha 2 — Práca s distrowatch.com

> Otvor v prehliadači **https://distrowatch.com**

### 2.1 Na akej distribúcii je postavený Linux Mint?
Debian, Ubuntu

### 2.2 Poradie Linux Mint v rebríčku „Page Hit Ranking — Last 6 months"

- **Poradie:** 2.
- **Hodnota** (priemerná návštevnosť/deň): cca 2410

### 2.3 Distribúcia z inej rodiny ako Debian

| Položka | Tvoja odpoveď |
|---|---|
| Názov distribúcie | Fedora workstation |
| Rodina (Red Hat / Arch / SUSE / iná) | Red Hat |
| Balíčkovací systém (apt / dnf / pacman / zypper / iný) | dnf |

---

## Úloha 3 — Prihlásenie a odhlásenie

> 1. Menu → **Log Out** (Odhlásiť sa). **Pozor — nie Shut Down!**
> 2. Po odhlásení sa prihlás späť svojimi údajmi.

### 3.1 Aká obrazovka sa zobrazila po odhlásení? Čo si na nej videl?
Zobrazila sa prihlasovacia obrazovka (Display Manager). Videl som na nej zoznam používateľov, pole pre zadanie hesla, aktuálny čas a ikony pre reštart či vypnutie systému.

### 3.2 Bola plocha po opätovnom prihlásení rovnaká, alebo „čistá" (zatvorené všetky okná)?

- [ ] rovnaká ako predtým
- [x] čistá (nové okná)

---

## Úloha 4 — Tri spôsoby spustenia konzoly

### 4.1 Menu → Terminal

Aký je presný názov aplikácie v záhlaví okna?
mint@mint-~

### 4.2 Klávesová skratka `Ctrl + Alt + T`

Otvoril sa rovnaký program ako v 4.1?

- [x] áno
- [ ] nie

### 4.3 TTY (`Ctrl + Alt + F3`)

> 1. Stlač `Ctrl + Alt + F3` — uvidíš čierny obraz s textom (TTY).
> 2. Prihlás sa: meno, Enter, heslo (nevidíš ho!), Enter.
> 3. Napíš `exit` + Enter.
> 4. Vráť sa späť do GUI: skús `Ctrl + Alt + F7` (alebo F1, F2).

**Aspoň 2 rozdiely medzi TTY a grafickým terminálom:**

1. TTY beží v čistom textovom režime na celú obrazovku, chýba grafické prostredie (okná, panely, kurzor myši).
2. TTY je priamo pripojený k jadru systému (virtuálna konzola), kým grafický terminál je len emulátor (aplikácia) bežiaca v grafickom serveri.

**Cez ktoré F-tlačidlo si sa vrátil späť do GUI?**

- [ ] F1
- [ ] F2
- [x] F7
- [ ] iné:

---

## Úloha 5 — Čítanie promptu

### 5.1 Výstupy príkazov

Skopíruj výstup z terminálu sem:

```bash
$ whoami
student

$ hostname
mint

$ pwd
/home/student

$ echo $USER
student
```

### 5.2 Aký znak je na konci tvojho promptu?

- [x] `$`
- [ ] `#`

### 5.3 Čo tento znak hovorí o tvojich právach v systéme?
Znak `$` znamená, že som v systéme prihlásený ako bežný používateľ s obmedzenými právami. Administrátor (používateľ `root`) má na konci promptu znak `#`.

### 5.4 Čítanie promptu

Pozri sa na svoj prompt (príklad: `andrej@mint:~$`). Vypíš, čo všetko z neho vieš prečítať **bez napísania jediného príkazu**:

- Meno aktuálne prihláseného používateľa (`andrej`).
- Názov počítača / hostname (`mint`), na ktorom momentálne pracujem.
- Aktuálny pracovný adresár. Znak `~` (tilda) predstavuje domovský adresár používateľa.
- Úroveň oprávnení. Znak `$` indikuje, že pracujem pod bežným používateľským účtom.

---

## Záver

Čo bolo pre teba dnes nové alebo zaujímavé?
zaujímave bolo to že som zistil že som rád že mám windows.