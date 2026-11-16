# Le Four du Canal — Choix techniques

> Phase 5 du workflow. Stack retenue pour la landing du concours amateur. Contexte pédagogique : cas d'exercice du module Vibe coding d'Uncode School.

---

## 1. Principe directeur

Le cas s'inscrit dans le module **Vibe coding** du cursus Uncode. L'intention n'est pas de montrer la maîtrise d'un outil no-code précis, c'est de montrer la capacité à **construire une solution avec une IA en direct, dans un cadre serré, avec un rendu propre**.

Donc : HTML + CSS vanilla écrit dans Claude Code, pas d'outil visuel intermédiaire type Softr, Framer ou Webflow.

---

## 2. Stack

| Brique | Choix | Raison |
| --- | --- | --- |
| Landing (structure + style) | HTML + CSS vanilla, écrits dans Claude Code | Démo pure du vibe coding, zéro dépendance externe, maîtrise totale de la DA |
| Typographie | Fraunces + Inter, chargées via Google Fonts | Validé en DA, gratuites, performantes |
| Formulaire d'inscription | Tally (iframe embarqué dans la landing) | Gère les champs conditionnels Juniors, email de confirmation en natif, stockage dans sa propre base |
| Hébergement principal | Netlify Drop, mappé sur `concours.lefourducanal.fr` | Même flux que carinelucas.fr, HTTPS Let's Encrypt automatique, zéro coût |
| Alternative WordPress | Fichier `wp-snippet.html` prêt pour bloc Gutenberg | Si la cliente préfère intégrer la landing dans son WP existant plutôt qu'un sous-domaine |
| Interactivité | Zéro JS côté landing (tout est géré par Tally) | Léger, portable, zéro bug à prévoir |

---

## 3. Deux livrables depuis une source unique

Pour couvrir les deux options du client, un seul fichier source, deux sorties.

### 3.1 Version standalone — `index.html`

Page complète autonome, à déposer telle quelle sur Netlify. Contient `<!doctype>`, `<html>`, `<head>` avec meta viewport et les Google Fonts, `<body>` avec la landing complète. Destination : sous-domaine `concours.lefourducanal.fr`.

### 3.2 Version WordPress — `wp-snippet.html`

Même code, mais sans les balises `<html>`, `<head>` et `<body>`. On ne garde que le `<style>` et le contenu du corps de page. Destination : bloc HTML personnalisé Gutenberg dans une page WordPress, ou template Blank Canvas si le thème de la cliente en propose un.

---

## 4. Règles de codage imposées par la portabilité WordPress

Sans ces règles, la landing collée dans WordPress casse le thème (ou se fait casser par lui).

1. **Classes préfixées `fdc-`** (pour Four du Canal) sur tous les sélecteurs CSS. Zéro collision possible avec les classes du thème.
2. **Pas de reset CSS global** (`* { … }`). Le reset est scoped à `.fdc-root *`, qui enveloppe toute la landing.
3. **Tokens CSS déclarés sur `.fdc-root`**, pas sur `:root`. Idem, pas de pollution globale.
4. **Styles inline dans un unique `<style>` au début du bloc**. Pas de CSS externe à faire charger côté WP.
5. **Pas de JavaScript inline hors du nécessaire minimal**. Idéalement zéro JS, l'iframe Tally gère tout.
6. **Google Fonts chargées via `<link>` dans la version standalone**. Dans la version WP, mettre le lien dans le même bloc HTML personnalisé fonctionne pour la majorité des thèmes.

---

## 5. Hébergement et DNS

### 5.1 Sous-domaine `concours.lefourducanal.fr`

À configurer chez l'hébergeur DNS actuel de `lefourducanal.fr` (OVH, Gandi, ou autre) :

- **CNAME** `concours` → `<site-netlify>.netlify.app`
- HTTPS activé automatiquement par Netlify (Let's Encrypt)
- Propagation DNS : 15 min à 2 h

### 5.2 Suppression propre après l'événement

Une fois le concours passé, la suppression du sous-domaine est une action unique chez OVH/Gandi. Le WordPress principal reste intact.

---

## 6. Ce qu'on ne fait pas (anti-stack)

- Pas d'intégration Softr, Airtable ou Make dans le niveau 1. L'inscription est 100% Tally.
- Pas de passerelle de paiement (inscription gratuite).
- Pas de système d'emails transactionnels Make + Gmail. Tally s'en charge nativement pour la confirmation.
- Pas de CMS headless, pas de framework JS. Une landing statique de 100 lignes de CSS ne mérite pas Next.js.
- Pas d'iframe de la landing Netlify dans WordPress en cas de changement d'option. Mauvais pour SEO, mobile et partage social. On fait du vrai HTML natif à la place.

---

## 7. Prochaine étape

Phase 6 + 7 condensées : développement direct du fichier `index.html` depuis le wireframe de la phase 2 et la DA de la phase 4, suivi de la génération du `wp-snippet.html`.

---

_Choix techniques version 1. Produits le 14 novembre 2026._
