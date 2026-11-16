# Formulaire Tally — Concours amateur Le Four du Canal

> Spec à recréer dans Tally en 10 min. Source : copywriting phase 3.

---

## Infos formulaire

- **Nom du formulaire** : `Concours amateur de pâtisserie — Le Four du Canal`
- **Nom technique interne** : `concours-four-du-canal-2026`
- **Visibilité** : Public
- **Thème** : Sobre (le formulaire est embarqué en iframe sur la landing qui porte déjà la DA, donc pas besoin de styliser Tally)

---

## Écran d'intro (optionnel, tu peux sauter)

**Titre** : On se lance ?
**Texte** : Deux minutes pour réserver votre place au premier concours amateur du Four du Canal, samedi 5 décembre à Bidart.
**Bouton** : Je m'inscris

---

## Questions

### Q1 — Prénom (obligatoire)
- Type : Short answer
- Label : "Votre prénom"
- Required : oui

### Q2 — Nom (obligatoire)
- Type : Short answer
- Label : "Votre nom"
- Required : oui

### Q3 — Email (obligatoire)
- Type : Email
- Label : "Votre email"
- Required : oui

### Q4 — Téléphone (obligatoire)
- Type : Phone number
- Label : "Votre téléphone"
- Required : oui
- Placeholder : "06 XX XX XX XX"

### Q5 — Catégorie (obligatoire)
- Type : Multiple choice (choix unique)
- Label : "Dans quelle catégorie souhaitez-vous participer ?"
- Options :
  - `Adultes - 16 ans et plus`
  - `Juniors - 10 à 15 ans avec un parent`
- Required : oui
- ⚠️ **Attention** : pas de virgule dans les libellés d'options (règle apprise sur ton bug Tally ↔ Airtable)

### Q6 — Prénom et âge de l'enfant (conditionnel, si Juniors)
- Type : Short answer
- Label : "Prénom et âge de votre enfant"
- Placeholder : "Ex : Léa, 12 ans"
- Required : oui
- Logic : Show when Q5 = "Juniors - 10 à 15 ans avec un parent"
- Hide par défaut (⌘⇧H sur le bloc)

### Q7 — Lien de parenté (conditionnel, si Juniors)
- Type : Multiple choice (choix unique)
- Label : "Votre lien avec l'enfant"
- Options :
  - `Parent`
  - `Grand-parent`
  - `Oncle ou tante`
  - `Autre`
- Required : oui
- Logic : Show when Q5 = "Juniors - 10 à 15 ans avec un parent"
- Hide par défaut

### Q8 — Indice sur la pâtisserie (facultatif)
- Type : Short answer
- Label : "Un indice sur ce que vous préparez ?"
- Placeholder : "Ex : Bûche coco passion, tarte aux agrumes…"
- Required : non
- Helper text : "Facultatif, juste pour nous mettre l'eau à la bouche."

### Q9 — Allergènes (facultatif)
- Type : Long answer
- Label : "Allergènes présents dans votre création"
- Placeholder : "Gluten, lactose, fruits à coque, œuf…"
- Required : non
- Helper text : "Vous pourrez compléter le jour J sur l'étiquette de dépôt."

### Q10 — Règlement (obligatoire)
- Type : Checkbox (single checkbox)
- Label : "J'accepte le règlement du concours : création faite maison, format 6 personnes minimum, dépôt le samedi 5 décembre entre 10h et 12h."
- Required : oui

### Q11 — Droit à l'image (obligatoire)
- Type : Checkbox (single checkbox)
- Label : "J'accepte que ma création et moi-même soyons photographiés pendant l'événement, et que ces photos puissent être utilisées par Le Four du Canal pour sa communication."
- Required : oui

### Q12 — Canal de découverte (facultatif, pour la fin)
- Type : Multiple choice (choix unique)
- Label : "Comment avez-vous entendu parler du concours ?"
- Options :
  - `Instagram`
  - `Facebook`
  - `Bouche à oreille`
  - `En boutique`
  - `Autre`
- Required : non

---

## Bouton de soumission

- Texte du bouton final : `Je m'inscris`

---

## Écran de remerciement

**Titre** : Votre inscription est enregistrée !

**Texte** :
```
Merci, nous avons bien reçu votre candidature au premier concours amateur de pâtisserie du Four du Canal.

Voici ce qui va se passer maintenant :
- Vous recevrez d'ici 48 heures le règlement complet et les infos pratiques par email.
- Si le nombre maximum de 20 participants est déjà atteint, nous vous proposerons la liste d'attente.
- Rendez-vous le samedi 5 décembre entre 10h et 12h pour le dépôt de votre création.

En attendant, à vos fours !
L'équipe du Four du Canal
```

---

## Paramètres à activer

- ✅ **Email de confirmation automatique à l'inscrit** (Settings > Email notifications > Respondent notifications). Tally gère ça nativement en plan gratuit, pas besoin de Make pour un cas fictif.
- ✅ **Email de notification à Carine** (Settings > Email notifications > Owner notifications) pour tester la soumission si tu veux.

---

## Une fois le formulaire créé

1. Rendre le formulaire **Public** (Settings > Publication)
2. Récupérer l'**ID du formulaire** (visible dans l'URL publique : `https://tally.so/r/XXXXX` → l'ID c'est `XXXXX`)
3. Me le coller ici
4. Je l'insère dans `index.html` et `wp-snippet.html` à la place de `FORM_ID_A_REMPLACER` (2 secondes)

---

_Spec produite le 14 novembre 2026 pour accompagner la livraison du cas Le Four du Canal._
