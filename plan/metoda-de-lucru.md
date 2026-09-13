# Metoda de lucru

Documentul ăsta nu conține materie. Conține **cum** lucrăm. Se citește o dată și se aplică zilnic.

---

## 1. Principiul de bază

Eu nu îți dau pași. Îți dau **conceptul**, **harta unde să cauți** și **criteriul de succes**. Tu cauți, tu greșești, tu rezolvi. Apoi îmi spui cum ai procedat și primești feedback pe metodă.

Consecința practică: vei auzi des de la mine propoziții de forma *„asta e baza. Caută în `man 5 sshd_config`, secțiunea Match. Spune-mi apoi cum ai proceda."* Nu e lene din partea mea, e singurul mod în care logica se fixează.

---

## 2. Structura zilei

Cinci blocuri. Duratele sunt orientative, ordinea nu.

| Bloc | Durată | Ce se întâmplă |
|---|---|---|
| **0 · Recap** | 15 min | 5 întrebări de la mine, din zilele anterioare |
| **1 · Fir 1** | ~3h | Un ciclu de învățare complet (vezi secțiunea 3) |
| **2 · Mișcare** | 45-60 min | Nu e opțional. Blocul ăsta ține restul în picioare. |
| **3 · Fir 2** | ~3h | Un ciclu de învățare complet |
| **4 · Puzzle** | 45-60 min | O piesă la miniproiect |
| **5 · Închidere** | 20 min | Commit, jurnal, grilă de 10 întrebări |

Aplicările la joburi rulează în afara blocurilor. Nu se amână.

---

## 3. Ciclul de învățare — patru pași, mereu aceiași

Fiecare bloc de materie (F1 sau F2) are exact structura asta.

### Pasul 1 — Conceptul (de la mine, ~10 min de citit)

Doar modelul mental: ce e lucrul ăsta, ce problemă rezolvă, de ce a apărut, cum se leagă de ce știi deja. **Fără comenzi, fără sintaxă, fără exemple de configurare.** Maximum 15 rânduri. Dacă vrei mai mult, ceri (secțiunea 6).

### Pasul 2 — Harta de explorare (de la mine, ~5 rânduri)

Îți spun **unde** să cauți, nu **ce** vei găsi. Exemple de hartă:

> `man 7 systemd.directives`, apoi `man systemd.service` — secțiunile `Type=` și `Restart=`.
> `systemctl --help` și `systemctl list-units --type=service`.
> Întrebarea la care trebuie să răspunzi singur: de ce un serviciu cu `Type=simple` poate fi raportat activ înainte să fie de fapt gata?

### Pasul 3 — Laboratorul (tu, 60-90 min)

Primești: **obiectivul**, **mediul de pornire**, **criteriul de acceptare**. Nu primești pașii.

Exemplu de format:

> **Obiectiv:** un serviciu systemd propriu care pornește o aplicație Java, repornește automat la crash, dar se oprește după 5 eșecuri consecutive.
> **Criteriu de acceptare:** omor procesul de 5 ori la rând; la a șasea, serviciul rămâne oprit și `systemctl status` arată clar de ce.
> **Nu ai voie:** să copiezi un unit file de pe internet. Poți citi `man`, poți citi unit files existente din sistem.

### Pasul 4 — Debrief (15 min)

Îmi spui în 5-10 rânduri: ce ai făcut, unde te-ai blocat, ce ai căutat, ce ai înțeles greșit la început. Eu îți dau feedback **pe metodă**, nu pe rezultat:

- unde ai căutat inefficient și unde era răspunsul mai aproape
- ce întrebare ar fi trebuit să-ți pui mai devreme
- ce ai învățat corect dar din motivul greșit (ăsta e cel mai important)

Abia aici primești explicații suplimentare, și doar pe ce ceri.

---

## 4. Cele trei tipuri de laborator

**A · Lab independent.** Un obiectiv închis, fără legătură cu proiectul. Se face 100% de tine. Produce un folder în repo cu README.

**B · Piesă de puzzle.** Un task independent în sine, dar al cărui artefact intră în miniproiect. Exemplu: „scrie un Dockerfile multi-stage pentru o aplicație Java" e lab independent; peste trei săptămâni, imaginea aia devine baza stack-ului din proiect. Fiecare piesă e utilizabilă și singură, la interviu.

**C · Lab de sabotaj.** Eu descriu un **simptom**, tu diagnostichezi. Nu îți spun ce am stricat. Exemplu: *„aplicația răspunde în 30 de secunde la primul request de dimineață și în 200ms după. Ce verifici, în ce ordine, și de ce?"*

Tipul C e cel mai valoros pentru profilul tău și va apărea din ce în ce mai des, mai ales în Fir 2.

---

## 5. Grila zilnică — 10 întrebări

La închiderea zilei. **Nu definiții.** Format de certificare reală:

- **LPIC / CKA:** scenariu operațional. *„Un pod rămâne în `CrashLoopBackOff`. Care comandă îți dă cel mai repede cauza?"*
- **AWS SAA:** *„Care e cea mai potrivită soluție, dat fiind constrângerea X?"* — mai multe variante corecte tehnic, una singură potrivită.
- **Capcane:** o întrebare din zece are un distractor care pare corect dacă ai învățat superficial.

Întrebările greșite se acumulează într-un banc separat și revin în recap peste 3 zile și peste 2 săptămâni. Astea sunt singura formă de repetiție pe care o facem.

---

## 6. Contractul de interacțiune

Patru comenzi scurte pe care mi le dai oricând. Le folosești fără explicații.

| Tu spui | Eu fac |
|---|---|
| **„mai mult"** | Adaug un nivel de profunzime pe ultimul punct. Doar pe acela. |
| **„doar harta"** | Nu explic nimic. Îți dau doar unde să cauți. |
| **„verifică-mă"** | Îți spui planul înainte să execuți. Îți dau feedback pe raționament, nu soluția. |
| **„prea mult"** | Am depășit. Tai și reformulez scurt. |

Regula implicită, până îmi ceri altceva: **maximum 15 rânduri per concept**. Dacă ai nevoie de mai mult, ceri. Dacă nu ceri, presupun că e suficient.

---

## 7. Recap la început de sesiune

Cinci întrebări, 15 minute, fără carduri:

- 2 din ziua precedentă
- 2 din urmă cu 3-4 zile
- 1 din săptămâna anterioară, sau din bancul de greșeli

Formatul e întotdeauna **„cum ai proceda dacă..."**, niciodată **„ce înseamnă X"**. Recapitulezi decizii, nu definiții.

---

## 8. Evaluarea, pe trei niveluri

**Zilnic** — grila de 10 plus calitatea debrief-ului. Nu se notează, se observă.

**Săptămânal (vineri, 90 min)** — un lab de sabotaj pe materia săptămânii, plus întrebările greșite din bancul săptămânii. La final, actualizezi tracker-ul.

**La ancore** — evaluările E1 până la E8 din planul principal. Astea sunt singurele cu miză: dacă una nu trece, se repetă înainte de a merge mai departe.

### Tracker-ul de nivel

Fiecare topic are exact trei stări. Le notezi tu, onest, în `00-STARE.md`:

| Stare | Înseamnă |
|---|---|
| **R** — recunosc | Știu că există și ce rezolvă. Nu îl pot folosi. |
| **M** — pot cu man | Îl pot face dacă am documentația deschisă. |
| **F** — pot fără ajutor | Îl pot face și îl pot explica altcuiva. |

Ținta la o ancoră: **F** pe conceptele centrale, **M** pe restul. **R** e acceptabil doar pe ce am declarat explicit periferic.

Auto-evaluarea generoasă e singurul mod în care metoda asta eșuează. Dacă la o evaluare rezultatul contrazice tracker-ul, tracker-ul se corectează, nu evaluarea.

---

## 9. Repo-ul

Un singur repo de jurnal, `devops-lab`, cu un folder pe săptămână. Fiecare folder:

```
KW38-linux-fundamente/
  README.md          ← ce am rezolvat, cum, ce n-a mers
  lab-01-systemd/
  lab-02-permisiuni/
  grila.md           ← întrebările greșite ale săptămânii
```

Commit zilnic, nu bulk. Zero secrete, `.gitignore` și gitleaks din prima zi.

Separat, repo-urile de vitrină: miniproiectul și write-up-urile de troubleshooting. Alea intră în CV. Jurnalul nu.

**Regula fără excepție:** nu publici nimic ce nu poți explica linie cu linie.
