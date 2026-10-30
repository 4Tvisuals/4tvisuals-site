# 4Tvisuals — version 3

Site vitrine responsive en français, avec portfolio Films / Photographie, projets individuels, deux mises en page, galerie agrandissable et vidéo d’accueil. Les visuels et projets actuels sont **fictifs / provisoires**.

## Tester

Décompresser le ZIP. Dans ce dossier, lancer `python3 -m http.server 8000` puis ouvrir `http://localhost:8000` dans un navigateur. Ouvrir directement `index.html` depuis Fichiers peut bloquer le chargement de `content.json`.

## Publication

1. Créer un dépôt GitHub privé ou public nommé `4tvisuals` et y placer les fichiers de ce dossier (à la racine).
2. Relier le dépôt à Cloudflare Pages, commande de build **aucune**, dossier de sortie **/** (racine). Pour une application statique sans build, préférer un déploiement direct ou vérifier la configuration de Cloudflare Pages.
3. Vérifier l’adresse temporaire `*.pages.dev`, puis acheter / connecter `4tvisuals.fr` après vérification de sa disponibilité et de son prix de renouvellement.
4. Tester le site sur iPhone et ordinateur.

## Administration Decap CMS : configuration indispensable

`/admin/` contient l’interface Decap CMS et le formulaire de gestion des projets, **mais la connexion ne fonctionnera pas tant que l’authentification GitHub OAuth n’est pas configurée**.

- Modifier `admin/config.yml` : remplacer `VOTRE_COMPTE/4tvisuals` par le dépôt GitHub réel.
- Configurer une application OAuth GitHub et un service OAuth compatible Decap CMS (par exemple un proxy OAuth auto-hébergé sur Cloudflare Workers) ; renseigner `base_url` et, selon le service, `auth_endpoint`.
- Configurer les URL de retour et secrets **dans le service OAuth**, jamais dans ce dépôt.
- Tester l’ajout d’un projet, son image, la publication Git et le redéploiement Cloudflare.
- Attention : les services OAuth tiers peuvent être payants ; choisir une option gratuite compatible pour respecter 50 €/an.

Une alternative sans proxy OAuth est d’utiliser un éditeur de contenu GitHub externe (par exemple Pages CMS) connecté au dépôt, ce qui exige une configuration différente.

## Contenus

`content.json` contient les textes et les projets. Le champ `video` ouvre un lien externe ; les liens vidéo YouTube/Vimeo ne sont **pas intégrés dans un lecteur embarqué** dans cette version. Les images ajoutées via l’administration seront stockées dans `assets/uploads` et versionnées dans Git : éviter d’y envoyer de très grosses vidéos.

## Limites / à faire avant ouverture publique

- Remplacer les images et la vidéo de démonstration par des médias autorisés.
- Finaliser les textes et les mentions légales / confidentialité adaptées à l’activité.
- Tester le lien de contact (actuellement ouverture du logiciel email, pas un formulaire).
- Configurer le CMS et l’authentification ; vérifier les droits d’écriture et le redéploiement.
- Optimiser les images et héberger les vidéos lourdes à l’extérieur.
