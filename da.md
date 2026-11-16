# Le Four du Canal — Direction artistique

> Phase 4 du workflow. Direction retenue : **Cabine de plage basque — bleu cobalt, jaune beurre, crème**. Issue d'une itération Claude Design après plusieurs tentatives Claude Code qui ont dérivé vers du "AI generic". Validée le 14 novembre 2026.

---

## 1. Intention en une phrase

> Un langage visuel graphique, plat, saturé, qui évoque la cabine de plage basque sans tomber dans le folklore : rayures cobalt et crème, dômes arrondis, demi-cercles beurre, chunky serif italique. Pop sans crier, moderne sans aseptisé.

**Références mentales** : Yann Couvreur (fox emblem), Hart Bageri (custom typography), les cabines rayées de la plage basque, les parasols de guinguette, les affiches de concours de village revisitées 2026.

---

## 2. Palette

Palette de 6 couleurs, chaque teinte joue un rôle précis.

| Rôle | Nom | HEX | Usage |
| --- | --- | --- | --- |
| Fond principal | Crème | `#F6EEDF` | Fond de page, grandes zones de respiration |
| Fond secondaire | Papier | `#FFF9EE` | Cards, blocs secondaires, intérieur des cercles |
| Accent principal | Cobalt | `#2346A8` | Rayures de la frise, CTA, fonds contrastés, détails forts |
| Texte principal | Encre | `#1C3380` | Tout le corps de texte, cobalt plus foncé |
| Accent pop | Beurre | `#F2C94C` | Badges, tampon n°1, détails joyeux, cerise sur l'entremets |
| Accent doux | Ciel | `#D6E0F5` | Fond du dôme hero, surfaces apaisées |

**Règles d'emploi**
- Jamais de noir pur : le texte est en encre bleu profond (#1C3380).
- Les 3 couleurs principales (cobalt, beurre, crème) doivent se répondre dans chaque section pour signer la DA.
- Les cards de section alternent fond papier et fond cobalt plein avec texte inversé.
- Les éléments de signature (frise top/bottom, dômes rayés, badges) rythment tout le scroll.

---

## 3. Typographie

| Famille | Usage | Taille |
| --- | --- | --- |
| **Fraunces** (variable, italique chunky) | Tous les titres, chiffres géants, initiales jury, mots clés | Clamp 34px → 112px selon hiérarchie |
| **Instrument Sans** (humaniste) | Corps de texte, badges, labels uppercase, navigation | 11px à 19px selon fonction |

**Détails typo à soigner**
- L'italique Fraunces signe la page : "goûtée.", "du" dans le logo, chiffres de section (01/02/03), heures du programme (10h – 12h), rangs des lots (1er, 2e, 3e), initiales du jury (L, C, I), critères notés "/10", et la grande promesse hero "À samedi 5 décembre."
- Labels uppercase en Instrument Sans 11-13px avec letter-spacing 0.18em pour les méta.
- Pas de texte centré sauf dans quelques badges ronds.

---

## 4. Éléments de signature

### 4.1 La frise cabine de plage (top + bottom)
Suite de barres verticales alternées **cobalt / papier**, hautes de ~120px, chacune terminée en bas par un demi-cercle (**cobalt** ou **beurre**). Évoque les cabines de plage rayées d'Hendaye à Biarritz, et les parasols de guinguette. C'est l'élément signature n°1 de la page.

### 4.2 Les dômes rayés
Forme arrondie en haut / droite en bas (border-radius: 999px 999px 0 0), remplie de rayures cobalt/papier alternées. Utilisée dans le **hero** (contient l'entremets illustré) et pour les **3 portraits du jury** (contiennent les initiales L, C, I géantes italiques).

### 4.3 Les badges pilule
Pastilles arrondies (border-radius: 999px) en 3 déclinaisons :
- **Beurre plein** : pour les eyebrows de section ("Le concours", "Programme", "Les lots"...)
- **Contour cobalt** : pour les infos pratiques (dates, lieu, contraintes)
- **Cobalt plein** : pour les CTA principaux

### 4.4 Les cards à bandeau rayé
Chaque card de section a un bandeau de ~18px en haut, composé de rayures cobalt/papier alternées (ou beurre/cobalt pour la card du milieu). Signature visuelle reprise de la frise.

### 4.5 Les illustrations SVG dessinées
Pas de photo. Toutes les illustrations sont des SVG plats inline :
- **Hero** : entremets à 2 étages (plat cobalt + étage principal rayé + étage cobalt avec gouttes beurre + cerise beurre)
- **Jury** : 3 cercles rayés avec initiales italiques Fraunces géantes (L beurre sur cobalt, C cobalt sur papier, I cobalt sur beurre)

---

## 5. Composants

| Composant | Style |
| --- | --- |
| CTA principal "Je m'inscris" | Pilule cobalt plein, texte papier, flèche SVG, min-height 58px |
| CTA secondaire | Texte encre souligné, underline-offset 5px |
| Pilule d'info | Border 1.5px cobalt, fond papier ou transparent, padding 9px 18px |
| Accordéon FAQ | Bordures 1.5px cobalt haut/bas, icône +/- dans un cercle cobalt plein 40px |
| Formulaire | Inputs cobalt bordure, radius 12px, label 14px semi-bold |
| Tampon "n°1" | Cercle beurre 128px tilté -8deg, Fraunces italic 42px |
| Dôme rayé | Border-radius 999px 999px 0 0, rayures flex verticales |

---

## 6. Mobile et responsive

- Tout est pensé en flex-wrap + container queries (`container-type: inline-size`).
- Les sections stackent naturellement en dessous de 760px.
- Les clamp() gèrent les tailles typo sur toute la plage.
- La frise top/bottom reste visible mais chaque colonne garde ses 56px de largeur fixe (scroll horizontal masqué par overflow: hidden).

---

## 7. Accessibilité

- Contraste encre (#1C3380) sur crème (#F6EEDF) : 10:1 (AAA).
- CTA cobalt (#2346A8) sur papier (#FFF9EE) : 8.5:1 (AAA).
- Beurre (#F2C94C) jamais utilisé seul pour du texte lisible, uniquement pour des accents.
- Toutes les icônes SVG décoratives ont `aria-hidden="true"`.
- Les illustrations SVG utiles (entremets) ont `role="img"` + `aria-label`.
- Min-height 44px sur tous les liens de navigation.

---

## 8. Ce qu'on ne fait pas (anti-brief)

- Pas de halo flou, pas de dégradé radial, pas de blur.
- Pas de photos stock, pas de cliparts.
- Pas de typo manuscrite "fake", pas de script décoratif.
- Pas de référence folklorique au Pays Basque (béret, rouge basque, Lauburu, croix basque).
- Pas d'emoji dans les CTA ou les titres.
- Pas d'alternance de blocs clair/foncé qui se succèdent : la couleur vient des éléments (cards, badges, frise), pas des sections.

---

## 9. Historique de la DA

Plusieurs tentatives avant d'arriver à cette direction :
1. **Piste B "artisan contemporain"** (Fraunces + sauge + miel + rose dragée) — trop fade, abandonnée
2. **Piste F "pop pâtissier signé"** (framboise + pistache + chocolat) — trop fade aussi, abandonnée
3. **Piste G "Soleil d'hiver basque"** (terracotta + halos flous + guillemets éditoriaux) — dérive AI generic, rejetée en bloc
4. **Direction finale "Cabine de plage basque"** (cobalt + beurre + crème + rayures) — obtenue via Claude Design après un brief verrouillé sur formes plates + couleurs saturées + référence Eguzki. Validée le 14/11/2026.

---

## 10. Prochaine étape

Passage à la **phase 5 du workflow** : les choix techniques sont déjà documentés dans [choix-techniques.md](choix-techniques.md). La landing est codée dans [index.html](index.html) et en version WordPress dans [wp-snippet.html](wp-snippet.html).

---

_Direction artistique version 2. Finalisée le 14 novembre 2026 après itération Claude Design._
