# BUFFER / LOOP · Lecteur musical à boucles aléatoires

[中文](README.md) · [English](README.en.md)

Et si une connexion qui rame créait un rythme inattendu ?

## D’où vient l’idée ?

Quand une connexion se bloque pendant l’écoute d’un morceau, les dernières secondes se répètent parfois en boucle. Ce petit accident peut produire un rythme étonnamment intéressant.

Ce lecteur permet de retrouver ce plaisir par hasard : choisissez votre musique, laissez un fragment tout juste écouté se répéter, puis reprenez le fil du morceau.

## Utilisation

1. Téléchargez et décompressez le projet.
2. Ouvrez `index.html` dans Chrome, Edge ou Safari.
3. Cliquez sur **Choisir un audio**, sélectionnez un fichier sur votre appareil, puis cliquez sur **Lire**.
4. Activez le **Mode automatique**, ou cliquez sur **Bégayer** pour déclencher l’effet.
5. Cliquez sur **Reprendre** pour arrêter l’effet et continuer à la position figée.

`random_glitch_player.html` est une copie identique et autonome : chacun des deux fichiers HTML fonctionne seul, même hors ligne. Gardez les deux copies synchronisées si vous les modifiez.

Par défaut, le lecteur répète les dernières **0,5 à 3 secondes**, **2 à 6 fois**. L’effet se déclenche environ toutes les **6 à 14 secondes** de lecture normale. La progression du morceau est figée pendant les répétitions. En début de morceau, il faut attendre qu’il y ait assez de son à répéter.

Vous pouvez régler l’intervalle, la durée des fragments et le nombre maximal de répétitions. Le lecteur propose aussi la pause, le déplacement dans le morceau, le volume, un spectre audio et un journal des effets.

Raccourcis : **Espace** pour lire ou mettre en pause, **G** pour déclencher l’effet et **R** pour reprendre. Lorsque le curseur est sur un bouton ou un champ, les commandes habituelles de ce contrôle restent prioritaires.

## Langues

Le lecteur utilise la langue préférée du navigateur : chinois → chinois simplifié, français → français, toute autre langue → anglais. Vous pouvez changer de langue avec **中文 / English / Français**, sans interrompre la musique.

Pour partager une langue précise, ajoutez `#lang=fr`, `#lang=zh` ou `#lang=en` à l’adresse du lecteur. Le choix est conservé dans l’adresse, sans cookies ni stockage du navigateur. Les traductions sont intégrées au fichier HTML et restent disponibles hors ligne.

## Confidentialité

**Vos fichiers audio ne sont envoyés à aucun serveur.** Le lecteur les lit avec `File.arrayBuffer()` et les décode avec l’API Web Audio, dans la mémoire du navigateur. Il ne contient ni service d’envoi, ni outil d’analyse, ni police distante, ni CDN, ni cookies, ni stockage du navigateur, ni service worker. Après un rechargement de la page, vous devez sélectionner le fichier à nouveau.

GitHub héberge le code ; GitHub Pages fournit la page web. Chaque personne choisit ses propres fichiers locaux. Le chargement de la page depuis GitHub reste une requête web, que l’hébergeur peut enregistrer ; ce n’est pas un envoi de votre musique.

La politique de sécurité intégrée interdit les connexions réseau (`connect-src 'none'`) et l’envoi de formulaires. Vérifiez à nouveau ces garanties si vous ajoutez des scripts tiers.

## Publication sur GitHub Pages

1. Créez un dépôt GitHub, par exemple `random-glitch-player`.
2. Placez le **contenu** du dossier à la racine du dépôt, notamment `index.html`, la copie HTML, les trois README, `LICENSE`, `.gitignore` et `.nojekyll`.
3. Ouvrez **Settings → Pages → Build and deployment → Source → Deploy from a branch**.
4. Sélectionnez la branche contenant les fichiers, généralement `main`, puis **/(root)** et **Save**.
5. Une fois le déploiement terminé, ouvrez le lien affiché dans les réglages Pages.

Aucune installation ni compilation n’est nécessaire. Voir les [instructions officielles de GitHub](https://docs.github.com/en/pages/getting-started-with-github-pages/configuring-a-publishing-source-for-your-github-pages-site). La disponibilité dépend du type de dépôt et de votre offre GitHub.

N’ajoutez pas vos chansons au dépôt. `.gitignore` exclut les formats audio courants, mais ne bloque pas les envois manuels depuis le site GitHub et ne supprime pas les fichiers déjà suivis par Git.

## Compatibilité et limites

- Les formats disponibles dépendent du navigateur et de l’encodage. Essayez un MP3 classique ou un WAV PCM si le décodage échoue.
- Le morceau entier est décodé en mémoire : les longs enregistrements peuvent consommer beaucoup de mémoire.
- Le verrouillage du téléphone, les onglets en arrière-plan et l’économie d’énergie peuvent suspendre la lecture ou retarder les déclenchements.
- Les flux protégés de Spotify ou Apple Music ne sont pas pris en charge. Le projet ne contient aucune chanson et ne permet pas d’exporter un mix.
- De courts fondus atténuent les coupures, mais des changements sonores restent possibles aux limites des fragments.
- Pour un usage hors ligne fiable, téléchargez le fichier HTML plutôt que de compter sur le cache du navigateur.

## Licence

Le code est distribué sous [licence MIT](LICENSE). Vous pouvez l’utiliser, le modifier et le redistribuer en conservant la mention de droits d’auteur et le texte de la licence. Cette licence ne couvre pas les morceaux importés ni les autres contenus tiers.

## Vérifications

Le lecteur a été vérifié dans Edge sans interface, sous Windows, avec un WAV généré de 12 secondes : décodage, lecture, pause, boucles manuelles et automatiques, reprise, déplacement, changements rapides de fichier, fichier invalide, fin de lecture et nouvelle lecture.

La détection du français, la sélection des trois langues, la traduction des journaux et le changement de langue pendant la lecture ont également été vérifiés, ainsi que l’affichage à une largeur de 390 pixels. Aucun appel réseau externe de la page ni aucune exception de script n’a été observé. Cela ne constitue pas un test d’écoute ni une vérification de tous les navigateurs et appareils.
