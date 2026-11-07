# Configurateur de style

Un outil d'une seule page pour régler le style graphique d'un site (couleurs, polices, formes, mise en page, animations), le voir en direct sur un faux site, puis exporter un **brief** que Claude suivra quand il crée le site.

## Utiliser l'outil

**En ligne :** ouvre la page GitHub Pages du dépôt.

**En local :** télécharge `index.html` et ouvre-le dans ton navigateur. Il n'y a rien à installer et aucune étape de build.

1. Règle le style dans l'onglet **Style**. Tu peux partir d'une direction toute faite, d'une image de référence ou des curseurs de personnalité.
2. Si tu veux, organise des pages de test dans l'onglet **Structure**.
3. Clique sur **Exporter le brief**. Tu as trois formats :
   - **Bloc de prompt** : à coller sous ta demande de création de site.
   - **DESIGN.md** : à mettre à la racine du projet.
   - **JSON** : l'état complet, que tu peux réimporter plus tard avec « Importer un JSON ».

## Brancher Claude (facultatif)

Sans Claude, la barre de directives comprend les demandes simples en mode local (« boutons en pilule », « ajoute une FAQ », « plus aéré »…).

Pour les directives en langage libre et l'analyse d'image par Claude :

1. Crée une clé API sur [console.anthropic.com](https://console.anthropic.com).
2. Dans l'onglet **Directives**, colle la clé et clique sur **Utiliser**.

À savoir sur la clé :

- Elle est gardée dans le `localStorage` de ton navigateur.
- Elle n'est envoyée qu'à `api.anthropic.com`. Il n'y a aucun serveur intermédiaire.
- Les appels sont facturés sur ton compte Anthropic. Ils utilisent le modèle `claude-opus-5-5` avec l'effort `low`.
- **Oublier** efface la clé de ton navigateur.
- N'utilise pas ta clé sur un ordinateur partagé.

Ouvert comme artifact dans Claude.ai, l'outil utilise directement Claude, sans clé.

## Vérifier après une modification

Ouvre la page avec `#test` à la fin de l'URL, par exemple `index.html#test`. La console du navigateur doit afficher « Auto-vérification terminée », sans aucune erreur d'assertion.

## Licence

MIT, voir [LICENSE](LICENSE).
