# Analýza: Možnosti spustenia Linuxu na notebooku

## Prehľad
Táto analýza porovnáva hlavné spôsoby, ako spustiť Linux na notebooku, vrátane výhod, nevýhod a vhodného použitia.

---

## 1. Dual Boot (Windows + Linux)

### Popis
Linux je nainštalovaný vedľa existujúceho operačného systému. Pri štarte si používateľ vyberá, ktorý systém chce použiť.

### Výhody
- Plný výkon hardvéru (CPU, GPU, RAM)
- Vhodné pre náročné úlohy (vývoj, gaming, AI)
- Natívna kompatibilita

### Nevýhody
- Zložitejšia inštalácia
- Nutnosť rozdelenia disku
- Nutnosť reštartu pri prepínaní OS

### Vhodné použitie
- Programovanie
- Gaming na Linuxe
- Pokročilí používatelia

---

## 2. Virtuálny stroj (Virtual Machine)

### Popis
Linux beží ako virtuálny systém vo vnútri hlavného operačného systému (napr. cez VirtualBox alebo VMware).

### Výhody
- Jednoduché nastavenie
- Bez zásahu do disku
- Bezpečné testovanie

### Nevýhody
- Obmedzený výkon
- Slabá alebo žiadna podpora GPU
- Vyššie nároky na RAM

### Vhodné použitie
- Učenie Linuxu
- Testovanie
- Nenáročné aplikácie

---

## 3. WSL (Windows Subsystem for Linux)

### Popis
Linuxové prostredie bežiace priamo vo Windows bez potreby virtualizácie.

### Výhody
- Rýchla inštalácia
- Integrácia s Windows
- Vhodné pre vývoj

### Nevýhody
- Nie je plnohodnotný Linux kernel (WSL1)
- Obmedzenia pri GUI a GPU (závisí od verzie)
- Menej vhodné pre systémové operácie

### Vhodné použitie
- Programovanie (Python, Node.js, Docker)
- DevOps
- Skriptovanie

---

## 4. Live USB

### Popis
Linux sa spúšťa priamo z USB kľúča bez inštalácie na disk.

### Výhody
- Žiadna inštalácia
- Bezpečné testovanie bez zásahu do systému
- Prenositeľnosť (môžeš použiť na viacerých zariadeniach)

### Nevýhody
- Pomalší výkon (závisí od USB)
- Dáta sa neukladajú (bez persistent storage)
- Obmedzená životnosť USB pri častom používaní

### Vhodné použitie
- Rýchle testovanie Linuxu
- Diagnostika systému
- Záchrana dát

---

## 5. Online Linux (cez webový prehliadač)

### Popis
Linux beží v prehliadači pomocou online služieb bez potreby inštalácie (napr. virtuálne terminály alebo celé desktop prostredie streamované cez web).

### Výhody
- Okamžité použitie bez inštalácie
- Funguje na akomkoľvek zariadení s internetom
- Ideálne na rýchle testy a učenie

### Nevýhody
- Závislosť od internetu
- Veľmi obmedzený výkon
- Obmedzené možnosti (často len terminál alebo základné GUI)

### Príklady služieb
- https://distrosea.com/
- https://www.onworks.net/
- https://copy.sh/v86/

### Vhodné použitie
- Rýchle vyskúšanie Linuxu
- Výučba a prezentácie
- Práca z cudzieho zariadenia

---
## Záver

Keďže väčšina mojich spolužiakov má počítače, ktoré sú zastarané a pomalé a ja sa dokážem prispôsobiť , najlepšou možnosťou bude online Linux.