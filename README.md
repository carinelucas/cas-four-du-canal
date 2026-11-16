# Le Four du Canal — Cas pratique Uncode School

> Premier concours amateur de pâtisserie organisé par la boulangerie fictive **Le Four du Canal**, à Bidart (Pays Basque). Solution no-code livrée en **niveau 3** : landing publique, outil interne de notation pour le jury, et e-mails automatiques pour les participants.

## Contexte

Le Four du Canal (pâtisserie fictive, laboratoire de 2 à 4 personnes) organise son premier concours amateur de pâtisserie le **samedi 5 décembre 2026**, de 14 h à 18 h. Vingt participants maximum, deux catégories (Adultes 16 ans et plus, Juniors 10 à 15 ans avec un parent), inscription gratuite. Un jury de trois personnes note chaque création en aveugle sur trois critères (goût, présentation, originalité).

## Niveau retenu : niveau 3

- **Niveau 1 — Landing page** : page web publique de présentation du concours et formulaire d'inscription.
- **Niveau 2 — Outil interne jury** : base Airtable, interface Softr dédiée au jury (notation en aveugle, classement pour la cheffe rafraîchi au rechargement de la page).
- **Niveau 3 — E-mails** : deux e-mails automatiques (confirmation d'inscription et rappel J-1).

Le périmètre a été élargi par étapes, une fois chaque niveau livré et vérifié. Le cadrage initial (v1) ciblait le niveau 1 ferme et le niveau 2 comme option ; le niveau 3 a été ajouté le 16 novembre après livraison et vérification des deux premiers.

## Stack technique

| Outil | Rôle |
| --- | --- |
| Netlify Drop | Hébergement de la landing (HTML standalone avec SVG inline) |
| Tally | Formulaire public d'inscription, embarqué sur la landing |
| Airtable | Base de données centrale (Participants, Jurés, Notes) + 2 automatisations natives pour les e-mails, envoyés depuis l'adresse générique `@airtableemail.com` |
| Softr | Interface interne du jury (4 pages : accueil, dashboard juré, formulaire de notation, classement cheffe) |

Les trois documents de cadrage obligatoires (ERD, BPMN, architecture globale) sont produits dans Notion et joints à la note de cadrage.

## Liens à tester

- **Landing** : https://concours-le-four-du-canal.netlify.app
- **Formulaire d'inscription Tally** : https://tally.so/r/je64pJ
- **Interface jury Softr** : https://verla11329.softr.app
  - Connexion par e-mail + mot de passe. Deux comptes de test (Léa cheffe, Pierre juré) avec identifiants dans la page Livraison Notion.
- **Base Airtable "Notation - Le Four du Canal"** : lien de partage en lecture seule dans la page Livraison Notion.

## Comment ça fonctionne

1. Un participant remplit le formulaire Tally depuis la landing. L'inscription tombe automatiquement dans Airtable (statut Inscrit).
2. Airtable Automations envoie immédiatement un e-mail de confirmation (contenu : catégorie, allergènes déclarés, date, lieu, créneau de dépôt). Un e-mail de rappel est programmé le vendredi 4 décembre à 10 h, un par participant.
3. Le jour J, la cheffe reçoit les pâtisseries entre 10 h et 12 h et attribue manuellement un numéro de création à chacune directement dans Airtable. Le statut passe à Déposé.
4. Les trois jurés se connectent à Softr avec leur email. Chacun note en aveugle les créations déposées sur trois critères (goût, présentation, originalité), chaque note sur 10. Le total par création se calcule automatiquement (/30 par note, rollup /90 pour la note totale).
5. Quand les trois jurés ont noté une création, la cheffe passe manuellement son statut à Noté complet dans Airtable (automatisation non construite dans cette version, prévue comme prochaine étape).
6. La cheffe consulte en délibération le classement (séparé par catégorie, trié par note totale décroissante) sur une page Softr réservée à son user group. Le nom du participant n'apparaît qu'une fois les 3 notes attribuées. Les deux autres jurés n'y ont pas accès. L'affichage se rafraîchit au rechargement de la page.
7. La cheffe annonce les lauréats oralement sur scène vers 17 h 30.

## Vérifications effectuées

- **Formulaire Tally** : soumission test OK, logique conditionnelle Juniors (Q6 et Q7 apparaissent uniquement si Juniors sélectionné) OK, intégration Airtable OK (une soumission crée bien une ligne dans la table Participants avec la catégorie correctement mappée).
- **Interface Softr** : parcours bout en bout testé — un juré se connecte, voit la liste des créations à noter (N° et catégorie uniquement, pas de nom), note un participant sur les 3 critères, la carte disparaît de sa liste (anti-double vote). Le total /30 par note et la note totale /90 par participant se calculent automatiquement côté Airtable (formule + rollup). La cheffe consulte le classement séparé par catégorie. Permission denied vérifié pour un juré qui tente d'accéder à la page de classement.
- **E-mail de confirmation** : testé en réel sur une soumission Tally, bien reçu avec les bonnes informations.
- **Rappel J-1** : testé via le bouton « Tester l'automatisation » d'Airtable sur un seul destinataire. L'envoi en boucle à tous les participants inscrits n'a pas encore été vérifié en conditions réelles.
- **Responsive mobile** : stacking propre à 400 px de large (hero, cards, podiums, footer de la landing).
- **Accessibilité** : contrastes AAA (encre sur crème 10:1, CTA cobalt sur papier 8.5:1), aria-label sur illustrations utiles, min-height 44 px sur navigation.

## Ce qui reste manuel dans cette version

- Le **N° de création** est saisi à la main par la cheffe le jour J au moment du dépôt.
- Le **passage au statut Noté complet** se fait à la main par la cheffe dans Airtable, aucune automatisation ne le déclenche.
- Les **tests d'envoi d'e-mails** ont été réalisés sur des alias de l'adresse de la conceptrice, pas sur de vrais participants.

## Limites assumées

- **Expéditeur des e-mails** : adresse générique Airtable Automations (`@airtableemail.com`), les e-mails arrivent souvent dans l'onglet Promotions de Gmail. En production, l'envoi se ferait depuis l'adresse de la pâtisserie (Make + Gmail du domaine, ou domaine vérifié côté Airtable).
- **Automatisation du rappel** : programmée comme occurrence hebdomadaire, à désactiver manuellement après le 5 décembre 2026 pour ne pas réexpédier les semaines suivantes.
- **E-mail de remerciement post-événement** : pas construit dans cette version, identifié comme prochaine étape.
- **Photos réelles des créations** : volontairement absentes, remplacées par des illustrations SVG plates dans la direction artistique (entremets du hero, initiales italiques L/C/I du jury). Zéro photo stock.
- **Montants des lots** : placeholder plausibles, à valider avec la cliente lors du vrai cadrage.

## Démarche

Workflow studio en 10 phases suivi : cadrage, conception UX, copywriting, direction artistique, choix techniques, maquette, développement, vérifications, mise en ligne, livraison. Les trois schémas (ERD, BPMN, architecture) ont été produits avant la construction Softr pour aligner la solution sur la méthode Product Builder, puis ajustés lors de l'ajout du niveau 3 pour rester cohérents avec ce qui a été livré.

La landing a été écrite en HTML/CSS inline (vibe coding dans Claude Code à partir d'une maquette obtenue par itération avec Claude Design). Le niveau 2 et le niveau 3 ont été montés directement dans les outils no-code (Airtable, Softr, automatisations natives).
