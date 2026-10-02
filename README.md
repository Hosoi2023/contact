# Contactez-nous – MFM Digital

Intégration de la page « Contactez-nous » de MFM Digital à partir de la maquette Figma, en HTML et CSS uniquement.

**Démo en ligne :** https://hosoi2023.github.io/contact/

## Structure

La page est découpée en trois parties : le `header` avec l'image, puis dans le `main` la carte avec le formulaire (`section`) et les infos de contact (`aside`). L'adresse de l'agence est dans une balise `<address>`.

Dans le CSS, les couleurs, la police et la marge latérale sont dans des variables (`:root`). Le fichier suit l'ordre de la page : hero, carte, toggle, champs du formulaire, case à cocher, bouton, colonne d'infos, puis le responsive à la fin.

## Quelques choix

- **Mise en page en CSS Grid.** Le `main` a deux colonnes (infos à gauche, carte à droite) définies avec `grid-template-areas`, ce qui me permet de simplement changer l'ordre sur mobile. Les champs du formulaire sont aussi dans une grille à deux colonnes.
- **Toggle Crapaud / Grenouille sans JavaScript.** Ce sont deux boutons radio cachés avec leurs `label`. La pastille verte se déplace grâce à `:checked` et au sélecteur `~`. Comme ce sont de vrais boutons radio, le choix est envoyé avec le formulaire et le toggle fonctionne au clavier.
- **Case à cocher personnalisée.** La vraie checkbox est invisible mais toujours là (elle garde le `required` et le focus clavier), et c'est le `span` juste à côté qui affiche le style de la maquette.
- **Accessibilité.** Le titre du toggle est dans une `legend` masquée visuellement (`.visually-hidden`) pour les lecteurs d'écran, les éléments personnalisés ont un contour visible au focus clavier et les champs ont un `autocomplete`.
- **Fidélité à la maquette.** Les tailles, couleurs, ombres et arrondis viennent directement de Figma. Pour les espacements autour du texte, je n'ai pas repris tels quels les chiffres mesurés dans Figma. Figma mesure le texte à partir du haut des majuscules jusqu'à la ligne de base, alors qu'en CSS la hauteur de ligne ajoute de l'espace au-dessus et en dessous du texte. Il existe une propriété CSS qui mesure le texte comme Figma (`text-box: trim-both cap alphabetic`), mais j'ai choisi de ne pas l'utiliser parce qu'elle n'est pas encore prise en charge par tous les navigateurs. J'ai préféré adapter moi-même les valeurs dans le CSS pour compenser cet espace : c'est moins direct, mais le rendu est le même dans tous les navigateurs.
- **La ligne sous « Prénom » est un peu plus claire** (`#dcdcdc` au lieu de `#d0d0d0`). C'est voulu, c'est comme ça dans la maquette.

## Ce qui n'était pas dans la maquette

La maquette montre seulement la version desktop, avec « Crapaud » sélectionné. J'ai donc choisi moi-même l'état « Grenouille » du toggle, la couleur du bouton au survol, les contours de focus et les deux versions responsive (900px et 520px).

Le formulaire n'est relié à aucun serveur pour l'instant (`action="#"`) : il s'agit uniquement de l'interface.
