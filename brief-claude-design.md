# Brief Claude Design — Landing concours amateur Le Four du Canal

> Brief prêt à coller dans une nouvelle conversation Claude Design (claude.ai, mode Design). Objectif : obtenir une maquette visuelle de la landing avant de la coder.

---

## Prompt à coller dans Claude Design

```
Je te demande de créer la maquette d'une landing page one-page pour le premier concours amateur de pâtisserie du Four du Canal, une pâtisserie indépendante à Bidart (Pays Basque, côte). Le concours a lieu le samedi 5 décembre 2026, inscription gratuite, 20 participants maximum, deux catégories (Adultes 16 ans et +, Juniors 10-15 ans).

CE QUE JE VEUX comme direction visuelle :

Un style POP PÂTISSIER signé, inspiré de la vague des identités tendance pour pâtisseries indépendantes (Yann Couvreur, Hart Bageri, Baek Bakery, Mamiche, et surtout l'esprit d'une DA "Eguzki" que j'ai vue : palette solaire chaude, typo italique chunky, frise décorative de demi-cercles en haut de page, soleil + vaguelettes en logo, badges ronds colorés avec texte dedans comme des étiquettes de pâtisserie).

CE QUI EST OBLIGATOIRE :
- Formes géométriques PLATES, couleurs SATURÉES, zéro blur, zéro halo flou, zéro dégradé radial. Tout doit être net et graphique.
- Une typo italique chunky serif pour les titres (type DM Serif Display, Instrument Serif, Playfair Display)
- Une typo sans serif moderne pour le corps (Instrument Sans, Inter)
- Une frise décorative en haut de page (type parasols ou demi-cercles qui alternent)
- Des badges ronds colorés avec du texte (comme "Chou crème coco", "Gâteau basque" dans Eguzki)
- Des illustrations SVG simples et plates (soleil plein, vaguelettes, pin basque, parasol rayé, étoile)
- Une palette solaire chaude à 5-6 couleurs : corail/terracotta, pêche/sable, bleu océan, jaune soleil, bleu encre pour le texte

CE QUI EST INTERDIT :
- Pas de halos flous, pas de blur en overlay
- Pas de guillemets géants éditoriaux
- Pas d'alternance bloc clair / bloc foncé qui se succèdent
- Pas d'esthétique "éditorial magazine" sage et sobre
- Pas d'emoji dans les boutons ou CTA
- Pas de référence folklorique au Pays Basque (béret, rouge basque, Lauburu)

STRUCTURE de la page, dans l'ordre :

1. HERO : frise décorative colorée en haut, logo rond "Le Four du Canal" (ou monogramme F.C. dans un cercle coloré), titre géant italique "Votre pâtisserie mérite d'être goûtée", sous-titre court, CTA rond coloré "Je m'inscris", petites infos clés en badges (date, lieu, gratuit)
2. TROIS POINTS CLÉS : "Trois choses à savoir avant de vous lancer" — Quand/où, Thème (pâtisserie de fin d'année), Catégories (Adultes + Juniors)
3. DÉROULÉ DE LA JOURNÉE : 4 étapes avec horaires (10h-12h dépôt, 14h ouverture au public, 15h-16h30 dégustation du jury, 17h30 remise des prix)
4. QUI PEUT PARTICIPER : conditions, catégories détaillées, règles (fait maison, allergènes à signaler, désistement = place perdue)
5. LES LOTS : podium Adultes (panier gourmand 100€ + bon 50€, coffret 50€, carte 25€) et podium Juniors (mêmes lots adaptés), plus une mention "chaque participant repart avec une douceur maison"
6. LE JURY : 3 jurés (chef pâtissière, client fidèle tiré au sort, personnalité locale invitée) et 3 critères notés sur 10 (goût, présentation, originalité)
7. FAQ : 6 questions courtes et chaleureuses
8. FORMULAIRE D'INSCRIPTION : bloc pour embarquer un formulaire Tally en iframe
9. FOOTER : contact (3 rue du Canal, 64210 Bidart), horaires boutique, liens utiles, réseaux sociaux

COPY À UTILISER :

Hero :
- Titre : "Votre pâtisserie mérite d'être goûtée"
- Sous-titre : "Le Four du Canal lance son tout premier concours amateur de pâtisserie. Jury gourmand, lots à gagner, pas besoin d'être pro. Inscription gratuite en 2 minutes."
- CTA : "Je m'inscris"

Trois points :
- Quand et où : Samedi 5 décembre, 14h à 18h, boutique rue du Canal à Bidart
- Thème : Pâtisserie de fin d'année, libre dans la recette, format 6 personnes minimum
- Pour qui : Adultes (16 ans +) et Juniors (10-15 ans, avec accord parental)

Déroulé :
- 10h-12h : Vous déposez votre création
- 14h : Ouverture au public
- 15h-16h30 : Le jury déguste et délibère
- 17h30 : Remise des prix et verre de l'amitié

Jury : "Pas de piège, pas de grille cachée. Juste trois gourmands qui prennent le temps de goûter votre création en toute honnêteté."

LIVRABLE ATTENDU :
Une maquette visuelle complète de la landing en artefact, scrollable du hero jusqu'au footer, responsive (desktop + mobile), que je pourrai ensuite transcrire en HTML. Si tu veux me proposer 2 ou 3 variantes de palette à l'intérieur de la même direction, c'est bienvenu.

NE FAIS PAS :
- Pas de code HTML réel, juste la maquette visuelle
- Pas de structure de blocs successifs clair/foncé/clair/foncé
- Pas de design "AI generic" (halos flous, titres centrés, rounded-lg partout)
```

---

## Mode d'emploi

1. Va sur **claude.ai**
2. Ouvre une **nouvelle conversation**
3. Colle le prompt ci-dessus en entier
4. Claude Design te produira une maquette visuelle (artefact)
5. Itère avec Claude Design jusqu'à ce que le visuel te plaise (ajuste les couleurs, les formes, les illustrations)
6. Une fois la maquette validée, reviens dans Claude Code avec soit **le lien de l'artefact**, soit **une capture d'écran**, soit **le code HTML que Claude Design a généré**
7. Je transcris en HTML propre dans `/le-four-du-canal/index.html` (avec la logique WordPress-ready préfixée `fdc-`)

## Garde-fous à utiliser dans Claude Design

Si la première proposition dérive vers du flou ou de l'éditorial :
- "Je ne veux aucun halo flou ni blur, uniquement des formes géométriques plates"
- "Je ne veux pas de guillemets géants ni d'esthétique magazine"
- "Rapproche-toi davantage de l'ambiance Eguzki : frise de demi-cercles, soleil plein non flouté, badges ronds colorés"

---

_Brief produit le 14 novembre 2026, à utiliser pour la refonte complète de la DA après plusieurs tentatives Claude Code qui ont dérivé._
