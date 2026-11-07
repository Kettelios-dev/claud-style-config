# Configurateur de style pour Claude

**Règle le style de ton futur site en le voyant en direct, puis donne à Claude un brief précis au lieu de « fais-moi un site moderne ».**

Cet outil tient en une seule page HTML. Tu choisis les couleurs, les polices, les formes, la mise en page et les animations sur un faux site d'exemple. L'outil génère ensuite un brief : un bloc de prompt, un `DESIGN.md` ou un JSON. Claude (Claude.ai, Claude Code, l'API…) s'en sert pour créer un site qui a vraiment ce style, plutôt qu'un rendu générique.

👉 **Utiliser l'outil en ligne :** https://kettelios-dev.github.io/claud-style-config/

---

## Sommaire

- [Ce que fait l'outil](#ce-que-fait-loutil)
- [Démarrage rapide](#démarrage-rapide)
- [Configurer Claude (facultatif)](#configurer-claude-facultatif)
- [Guide des onglets](#guide-des-onglets)
- [Exporter et utiliser le brief](#exporter-et-utiliser-le-brief)
- [Confidentialité et sécurité](#confidentialité-et-sécurité)
- [Héberger sa propre copie](#héberger-sa-propre-copie)
- [Problèmes fréquents](#problèmes-fréquents)
- [Pour les développeurs](#pour-les-développeurs)

---

## Ce que fait l'outil

- **Aperçu en direct** d'un site complet : navigation, hero, sections, pages et sous-pages, en version bureau ou mobile, en thème clair ou sombre.
- **Six directions toutes faites** pour démarrer : Éditorial, Néo-brutal, Doux organique, Tech précis, Rétro imprimé, Minimal calme.
- **Curseurs de personnalité** (sérieux ↔ ludique, minimal ↔ maximal…) : l'outil propose un style complet à partir d'eux.
- **Style tiré d'une image** : importe une capture ou une photo d'ambiance. Les couleurs, la luminosité et la densité sont analysées directement dans ton navigateur.
- **Palette calculée** à partir d'une seule couleur. Les contrastes respectent la norme d'accessibilité WCAG AA.
- **Directives en français** : « boutons en pilule », « ajoute une FAQ après les tarifs », « fond sombre sur cette section »…
- **Choix de ce qui part dans le brief** : chaque réglage peut être *imposé* ou laissé *libre* à Claude.
- **Export** en bloc de prompt, en `DESIGN.md` ou en JSON (réimportable).
- **Annuler** avec Ctrl+Z. Ton travail est sauvegardé automatiquement dans le navigateur.

## Démarrage rapide

1. Ouvre l'outil, en ligne ou en local (voir plus bas).
2. Dans **Style → Point de départ**, clique sur une direction toute faite, ou règle les curseurs puis clique sur « Proposer un style ».
3. Ajuste les détails dans les groupes Couleurs, Typographie, Mise en page, etc.
4. Remplis **Contexte** (nom, accroche, cible) et **Garde-fous** (ce qui est interdit, l'élément signature du site).
5. Clique sur **Exporter le brief**, puis copie le résultat ou télécharge-le.

Aucun compte n'est nécessaire et il n'y a rien à installer.

## Configurer Claude (facultatif)

Sans Claude, l'outil marche entièrement. La barre de directives comprend alors les demandes simples en **mode local** : arrondis, couleurs (« accent bleu »), ombres, grain, densité, majuscules, ajout, suppression ou déplacement de sections…

Avec Claude, tu peux écrire des directives libres (« un côté plus artisanal, comme une affiche des années 70 »). Le bouton « Affiner avec Claude » apparaît aussi après l'import d'une image : il en déduit la police, la mise en page et les formes.

### Avec une clé API Anthropic

1. Va sur [console.anthropic.com](https://console.anthropic.com), crée un compte, ajoute du crédit, puis va dans **API Keys → Create Key**.
2. Dans l'outil, ouvre l'onglet **Directives**.
3. Colle la clé (elle commence par `sk-ant-`) et clique sur **Utiliser**.
4. Le point devient vert et le texte indique « Claude interprète tes directives en langage libre ».

| Détail | Valeur |
|---|---|
| Modèle | `claude-opus-5-5`, effort `low` (réponses rapides) |
| Coût | Facturé sur ton compte Anthropic. Une directive coûte en général quelques centimes au plus. |
| Où va la clé | Uniquement vers `api.anthropic.com`, directement depuis ton navigateur. Il n'y a aucun serveur intermédiaire. |
| Où elle est stockée | Dans le `localStorage` de ton navigateur, pour cette adresse seulement |
| L'effacer | Bouton **Oublier** |

Pour changer de modèle, modifie la constante `API_MODEL` dans `index.html`, par exemple `claude-sonnet-5-5` (moins cher).

### Dans Claude.ai (artifact)

Si tu ouvres le fichier comme artifact dans Claude.ai, l'outil utilise directement le Claude de la conversation. Aucune clé n'est demandée et le champ de clé est masqué.

## Guide des onglets

### Style

| Groupe | Ce que tu règles |
|---|---|
| 00 · Point de départ | Les directions toutes faites et les 5 curseurs de personnalité |
| IM · Depuis une image | L'analyse d'une image de référence |
| 01 · Contexte | Le type de site, le nom, l'accroche, l'action principale, la cible, les adjectifs, les sites de référence |
| 02 · Couleurs | La couleur principale, la stratégie de palette, la saturation, la teinte des gris, les thèmes clair/sombre, les dégradés |
| 03 · Typographie | Les polices des titres et du texte, l'écart de taille, la graisse, la casse, l'interlettrage |
| 04 · Mise en page | La structure (centrée, asymétrique, éditoriale, bento, écran partagé) et la densité |
| 05 · Formes et matières | L'arrondi, les bordures, les ombres, le grain |
| 06 · Images | Le style du visuel principal et des icônes |
| 07 · Animations | Le niveau, de 0 (statique) à 3 (très animé) |
| 08 · Composants | Le style des boutons et de la navigation |
| 09 · Réglages fins | La taille du texte, les interlignes, la largeur max, la taille des boutons, les couleurs exactes forcées |
| 10 · Garde-fous | Les interdits, l'élément obligatoire, l'élément signature |

Deux interrupteurs contrôlent ce qui part dans le brief :
- **« Inclure dans le brief »** sur chaque groupe : décoché, le groupe entier est laissé au choix de Claude.
- **« imposé / libre »** sur chaque réglage : *libre* veut dire que Claude choisit lui-même ce réglage, dans l'esprit du reste.

### Structure

- **Arborescence des pages** : ajoute, renomme, réordonne et range des pages en sous-pages (→ / ←).
- **Sections de la page** : ajoute (hero, FAQ, tarifs, galerie, contact…), glisse-dépose, masque ou supprime.
- Par défaut, la structure **ne part pas** dans le brief : elle sert à tester le style sur plusieurs pages. Coche l'option pour l'inclure.

### Directives

- Écris une directive dans la barre sous l'aperçu, puis clique sur **Appliquer**.
- **Cibler une section** : clique sur ce bouton, puis sur une section de l'aperçu. La directive ne s'appliquera qu'à elle.
- L'historique des directives est listé ici. « Retirer » enlève une directive du brief. Pour annuler son effet, utilise **Annuler**.

## Exporter et utiliser le brief

Clique sur **Exporter le brief** et choisis le format :

| Format | Usage |
|---|---|
| **Bloc de prompt** | À coller sous ta demande dans Claude.ai : « Crée-moi le site de mon atelier… » suivi du bloc. |
| **DESIGN.md** | À mettre à la racine du projet pour Claude Code, puis à demander : « Respecte DESIGN.md ». |
| **JSON** | Une sauvegarde complète de l'état. Avec **Importer un JSON**, tu la recharges, sur un autre navigateur ou chez quelqu'un d'autre. |

Deux raccourcis en haut de la fenêtre d'export :
- **Style graphique seulement** (par défaut) : le brief ne fixe que l'apparence. Le contenu vient de ta demande.
- **Tout inclure** : il ajoute le contexte, l'arborescence et les directives sur le contenu.

## Confidentialité et sécurité

- Tout se passe dans ton navigateur. L'outil n'a ni serveur, ni compte, ni suivi.
- Les images importées sont analysées localement. Elles ne sont envoyées à Claude que si tu cliques sur « Affiner avec Claude ».
- Ta clé API n'est envoyée qu'à Anthropic. Ne l'enregistre pas sur un ordinateur partagé, et clique sur **Oublier** quand tu as fini.
- Les polices viennent de Google Fonts dans l'outil. Le brief recommande de les héberger toi-même sur le site final (RGPD).
- Un JSON importé est vérifié avant d'être chargé. Les fichiers invalides ou piégés sont refusés.

## Héberger sa propre copie

**Le plus simple :** télécharge `index.html` et double-clique dessus. Si les appels à Claude échouent depuis un fichier local, utilise la version en ligne ou lance un petit serveur : `python -m http.server`, puis ouvre `http://localhost:8000`.

**Sur GitHub Pages :**
1. Fais un *fork* de ce dépôt.
2. Va dans **Settings → Pages**, choisis « Deploy from a branch », la branche `main` et le dossier `/ (root)`, puis clique sur **Save**.
3. Ton outil est en ligne à `https://<ton-pseudo>.github.io/claud-style-config/`.

Tout autre hébergement de fichiers statiques convient aussi (Netlify, Cloudflare Pages, un serveur web…).

## Problèmes fréquents

| Symptôme | Solution |
|---|---|
| « Clé API refusée » | La clé est invalide ou a été révoquée, ou le compte n'a plus de crédit. Recrée une clé sur la console. |
| « Trop de demandes à Claude » | Limite de débit atteinte. Attends une minute. |
| « Claude n'a pas pu répondre » | Problème réseau ou réponse illisible. L'outil a appliqué l'analyse locale à la place. Réessaie. |
| L'image n'est pas lue | Utilise un PNG ou un JPEG. |
| Je veux tout remettre à zéro | Efface les données du site dans ton navigateur (cadenas de la barre d'adresse → Effacer les données). |
| Le style ne change pas après une directive | La directive est gardée dans le brief pour Claude. Le mode local ne comprend que les demandes simples. |

## Pour les développeurs

- Tout le code est dans `index.html` : HTML, CSS et JavaScript, sans dépendance ni build.
- **Auto-vérification** : ouvre `index.html#test`. La console doit afficher « Auto-vérification terminée », sans aucune erreur d'assertion. Elle vérifie les contrastes des palettes, l'arrondi des valeurs renvoyées par Claude, le filtrage du CSS et la validation des JSON importés.
- Les appels à Claude passent par l'API Messages (`fetch`) avec l'en-tête `anthropic-dangerous-direct-browser-access`, qui autorise les appels directs depuis un navigateur.

## Licence

[MIT](LICENSE) © Kettelios-dev
