# Cvičenie: Príkazový riadok OS — `ls`, `cd`, `cp`, `rm`, `mv`

> Vyplň odpovede pod každú otázku. Pri otázkach typu áno/nie zaškrtni `- [x]`. Výstupy z terminálu prilep do code blokov.

---

## Úloha 1 — Orientácia v systéme

> Otvor terminál (`Ctrl + Alt + T`). Všetky nasledujúce príkazy píš v **tvojom domove**.

### 1.1 Napíš `pwd` a zapíš výstup (absolútna cesta k tvojmu domovu):

```bash
/home/student
```

### 1.2 Napíš `ls`. Vymenuj aspoň **3 položky**, ktoré vidíš:

- Documents
- Downloads
- Pictures

### 1.3 Napíš `ls -l`. Nájdi:

- **Jeden priečinok** (začína `d`): `drwxr-xr-x 2 student student 4096 apr 24 10:15 Documents`
- **Jeden súbor** (začína `-`): `-rw-r--r-- 1 student student 8980 apr 24 10:15 examples.desktop`

### 1.4 Napíš `ls -a`. Zapíš aspoň **3 skryté položky** (začínajú `.`):

- `.bashrc`
- `.profile`
- `.config`

---

## Úloha 2 — Navigácia po strome

> Po každom kroku napíš **čo ti ukázal `pwd`**.

### 2.1 Spusti `cd ~`, potom `pwd`:

```bash
/home/student
```

### 2.2 Spusti `cd ..`, potom `pwd`:

```bash
/home
```

> **Pozor:** správna odpoveď je `/home` (nie `/home/<tvoje_meno>`). Ak máš niečo iné, nerozumel si `..`.

### 2.3 Spusti `cd /`, potom `pwd`:

```bash
/
```

### 2.4 Spusti `cd -`. Čo ti vypíše shell na obrazovku?

```bash
/home
```
*(Poznámka: Príkaz ťa zároveň presunie do tohto predchádzajúceho priečinka, z ktorého si prišiel.)*

### 2.5 Ako sa najrýchlejšie vrátiš do svojho domovského adresára? Napíš **dva spôsoby**:

1. Príkazom `cd` (bez akýchkoľvek argumentov).
2. Príkazom `cd ~` (tilda reprezentuje domovský adresár).

---

## Úloha 3 — Kopírovanie

> Postupne vykonaj nasledujúce príkazy. Po každom skontroluj výsledok cez `ls`.

### 3.1 Vytvor štruktúru:

```bash
cd ~
mkdir skola
touch poznamky.txt
touch uloha.txt
```

Napíš výstup `ls` po týchto príkazoch:

```bash
Documents  Downloads  Pictures  poznamky.txt  skola  uloha.txt
```

### 3.2 Skopíruj súbor do priečinka:

```bash
cp poznamky.txt skola/
```

Napíš výstup `ls skola/`:

```bash
poznamky.txt
```

### 3.3 Duplikuj súbor pod novým menom:

```bash
cp poznamky.txt zaloha.txt
```

Existuje teraz aj **originál** `poznamky.txt`, aj **kópia** `zaloha.txt`?

- [x] áno
- [ ] nie

### 3.4 Skús skopírovať priečinok **BEZ** `-r`:

```bash
cp skola zaloha_skola
```

**Presná chybová hláška:**

```bash
cp: -r not specified; omitting directory 'skola'
```

### 3.5 Teraz s `-r`:

```bash
cp -r skola zaloha_skola
```

Napíš výstup `ls`:

```bash
Documents  Downloads  Pictures  poznamky.txt  skola  uloha.txt  zaloha.txt  zaloha_skola
```

### 3.6 Prečo `cp` potrebuje `-r` pri priečinkoch?
Parameter `-r` znamená "rekurzívne" (recursive). Priečinok nie je len jeden súbor, ale kontajner, ktorý môže obsahovať ďalšie súbory a podadresáre. Príkaz `cp` potrebuje parameter `-r`, aby vedel, že má vojsť dnu a prekopírovať celý jeho obsah so zachovaním pôvodnej štruktúry.

---

## Úloha 4 — Premenovanie a presun

### 4.1 Premenuj súbor:

```bash
touch test.txt
mv test.txt hotovo.txt
```

Vidíš ešte `test.txt` v `ls`?

- [ ] áno — ostal
- [x] nie — zmizol (premenovaný)

### 4.2 Presuň do priečinka:

```bash
mv hotovo.txt Documents/
```

Napíš výstupy:

```bash
$ ls
Documents  Downloads  Pictures  poznamky.txt  skola  uloha.txt  zaloha.txt  zaloha_skola

$ ls Documents/
hotovo.txt
```

### 4.3 Presuň celý priečinok (**bez** `-r`!):

```bash
mv skola zaloha_skola2
```

Dostal si chybovú hlášku?

- [ ] áno
- [x] nie

### 4.4 Doplň pravidlo:

**`mv` súbor priečinok/** → presun
**`mv` súbor novy_nazov** → premenovanie

> *Ako `mv` rozozná, ktorú akciu má urobiť?*
Príkaz `mv` sa pozrie na posledný argument (cieľ). Ak cieľ existuje a je to priečinok, súbor **presunie** dovnútra. Ak cieľ neexistuje (alebo to nie je priečinok), systém pochopí, že má súbor na danom mieste vytvoriť pod novým menom, teda ho **premenuje**.

---

## Úloha 5 — Mazanie ⚠️

> **Pozor:** v Linuxe **neexistuje Kôš**. Čo zmažeš, je preč.
> **Nepúšťaj** `rm -rf` na nič mimo vlastného testovacieho priečinka.

### 5.1 Zmaž súbor:

```bash
touch zmaz.txt
rm zmaz.txt
```

Existuje ešte `zmaz.txt` v `ls`?

- [ ] áno
- [x] nie

### 5.2 Skús zmazať priečinok **BEZ** `-r`:

```bash
rm zaloha_skola
```

**Presná chybová hláška:**

```bash
rm: cannot remove 'zaloha_skola': Is a directory
```

### 5.3 Teraz s `-r`:

```bash
rm -r zaloha_skola
```

Napíš výstup `ls` po zmazaní:

```bash
Documents  Downloads  Pictures  poznamky.txt  uloha.txt  zaloha.txt  zaloha_skola2
```

### 5.4 Kde skončí vymazaný súbor v Linuxe?

> *(Pozor, otázka s pascou. Pomysli, predtým než odpovieš.)*
Nikde. Pri použití príkazu `rm` v termináli sa súbor nepresúva do žiadneho grafického koša, ale je **okamžite a natrvalo odstránený** zo súborového systému (dáta sa označia ako prepísateľné).

### 5.5 Napíš **vlastnými slovami**, prečo je príkaz `rm -rf /` **extrémne nebezpečný**:
Tento príkaz prikáže systému rekurzívne (`-r`) a bez pýtania sa (`-f` = force) vymazať úplne všetko, počnúc koreňovým adresárom (`/`). Ak ho spustíš s administrátorskými právami, systém doslova vymaže sám seba – zničí všetky systémové súbory, programy aj tvoje osobné dáta a znefunkční celý počítač.

---

## Bonus — tab completion a history

### B.1 Skús napísať `cd Doc` a stlačiť **Tab**. Čo sa stalo?
Terminál automaticky doplnil zvyšok názvu priečinka a zmenil text na `cd Documents/`. Je to takzvané "našepkávanie" (tab completion), ktoré šetrí čas a chráni pred preklepmi.

### B.2 Stlač **šípku hore** v termináli. Čo sa stalo?
Na riadku sa objavil naposledy zadaný príkaz z histórie. Opakovaným stláčaním šípky hore sa dá listovať hlbšie do minulosti všetkých zadaných príkazov.

### B.3 Napíš **tvoj obľúbený objav** z dnešnej hodiny (príkaz, skratka, trik):
Používanie klávesy **Tab** (Tabulátor) na automatické dopĺňanie názvov dlhých súborov a adresárov. Odpadá tak nutnosť vypisovať celé zložité názvy ručne.

---

## Záver

**Ktorý príkaz ti prišiel najužitočnejší a prečo?**
Najvšestrannejší je určite `ls`, pretože bez neho by sme boli v termináli "slepí" – používame ho neustále na to, aby sme videli, kde sme a čo sme urobili (napr. po vytvorení alebo presunutí súboru). Výborný je aj `cd -` pre rýchly skok na predchádzajúce miesto.