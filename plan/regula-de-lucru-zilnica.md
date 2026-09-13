# Regula de lucru zilnică și unde stau fișierele

---

## 1. Cele patru fișiere și ce se întâmplă cu fiecare

| Fișier | Se schimbă | Unde stă | Când mi-l dai |
|---|---|---|---|
| `plan-invatare-KW38-2026-KW06-2027.md` | aproape niciodată | project knowledge | o singură dată |
| `metoda-de-lucru.md` | aproape niciodată | project knowledge | o singură dată |
| `regula-de-lucru-zilnica.md` (acest fișier) | rar | project knowledge | o singură dată |
| `00-STARE.md` | **zilnic** | pe disc, la tine | **în fiecare dimineață, atașat în chat** |
| `TRACKER.md` | săptămânal | pe disc, la tine | la evaluări și la ancore |

Primele trei se încarcă o singură dată, în cunoștințele proiectului. Nu le mai atingi. Singurul fișier pe care îl trimiți zilnic e `00-STARE.md`.

---

## 2. Ritualul zilnic

### Dimineața — deschizi chat nou

1. Atașezi `00-STARE.md`.
2. Scrii un singur mesaj: **„ziua N"** (sau „ziua N, KW 38" dacă vrei să fii explicit).
3. Eu citesc starea, fac recapul de 5 întrebări, apoi dau conceptul și harta pentru primul bloc.

Nu explici ce ai făcut ieri. Scrie în fișier.

### În timpul zilei

- După fiecare lab, îmi dai debrief-ul scris (5-10 rânduri).
- Dacă un artefact e mai lung de ~50 de rânduri, nu îl lipești în chat. Îl pui pe GitHub și îmi dai link-ul brut (secțiunea 4).
- Comenzile din contract se folosesc oricând: „mai mult", „doar harta", „verifică-mă", „prea mult".

### Seara — închiderea

1. Îmi spui **„închidem ziua"**.
2. Primești grila de 10 întrebări.
3. După ce răspunzi, îți regenerez `00-STARE.md` complet, cu ziua completată, bancul de greșeli actualizat și ancora următoare recalculată.
4. Salvezi fișierul peste cel vechi. Commit în repo.

---

## 3. Regula de comprimare

Ca fișierul să nu crească niciodată peste o pagină:

- **Luni dimineața:** săptămâna precedentă se comprimă în maximum două rânduri, la secțiunea „Săptămâna precedentă, pe scurt". Detaliul rămâne în README-ul săptămânii din repo.
- **Bancul de greșeli:** maximum 15 intrări active. O întrebare iese după două răspunsuri corecte consecutive. Dacă lista e plină, cea mai veche iese și devine temă de recap obligatorie.
- **Secțiunea „Deschis":** dacă o intrare stă acolo mai mult de două săptămâni, ori devine lab, ori se șterge. Nu se cară la nesfârșit.
- **Blocaje:** același blocaj trei zile la rând înseamnă că planul se ajustează, nu că se insistă. Se notează explicit și se discută la reevaluarea de la două săptămâni.

---

## 4. Unde stau rezultatele și cum ajung eu la ele

Am acces doar la ce e **în conversație** sau **în cunoștințele proiectului**. Nu văd discul tău, nu văd repo-ul tău din proprie inițiativă.

Trei canale, fiecare cu rolul lui:

### a) Cunoștințele proiectului — pentru ce nu se schimbă

Planul, metoda, regula asta. Le încarci o dată, sunt disponibile în orice chat nou din proiect, fără să le retrimiți.

### b) Atașament în chat — pentru ce se schimbă zilnic

`00-STARE.md` dimineața. `TRACKER.md` la evaluări. Fișiere mici, text.

### c) GitHub public — pentru artefacte

Repo-ul `devops-lab` trebuie să fie **public** ca să pot citi din el. Când vrei să mă uit la un lab, îmi dai link-ul direct către fișier, în format brut:

```
https://raw.githubusercontent.com/SteveJordache/devops-lab/main/KW38-linux/lab-01/unit.service
```

Sau link-ul normal către fișier, din care îl pot deduce. **Nu pot ghici structura repo-ului** — dacă îmi dai doar numele repo-ului, nu știu ce e în el. Dă-mi link-ul către ce vrei să citesc.

Ce merge pe GitHub: unit files, Dockerfile, playbooks, cod Python, config-uri, output-uri de `jstack`, README-uri de lab.
Ce **nu** merge, niciodată: chei, certificate reale, parole, hostname-uri sau config-uri de la angajatori. `.gitignore` și gitleaks din prima zi.

### d) Ce nu funcționează

Fișiere locale la care nu am atașament. Link-uri către repo privat. Screenshot-uri de cod, când textul e disponibil. Presupunerea că îmi amintesc din conversația de ieri: unele lucruri durabile se păstrează, rezultatele zilnice nu. **Fișierul e singurul mecanism sigur.**

---

## 5. Structura pe disc, la tine

```
învățare/
  plan-invatare-KW38-2026-KW06-2027.md
  metoda-de-lucru.md
  regula-de-lucru-zilnica.md
  00-STARE.md              ← singurul care se schimbă zilnic
  TRACKER.md
  devops-lab/              ← repo git, public
    KW38-linux-fundamente/
      README.md
      lab-01-systemd/
      grila.md
    KW39-.../
```

Folderul `învățare/` conține și repo-ul, ca să ai totul într-un loc. Doar `devops-lab/` e sub git.

---

## 6. Ce fac eu, ca să nu mă întrebi

- Recapul de dimineață: îl fac automat, din `00-STARE.md`. Nu trebuie cerut.
- Grila de seară: doar la „închidem ziua". Nu o dau nesolicitat.
- Regenerarea `00-STARE.md`: automat, la închiderea zilei. Primești fișierul complet, nu un fragment.
- Recalcularea ancorei și a evaluării următoare: automat, la fiecare regenerare.
- Reevaluarea planului: la fiecare două săptămâni, o spun eu dacă tu uiți.
