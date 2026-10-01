# Site vitrine — Alexis Rivière

Site statique en HTML et CSS, sans framework, sans JavaScript, sans dépendance externe.
Les polices sont hébergées dans `assets/fonts/` : aucune requête vers Google ou un autre service tiers.

## Structure

```
index.html              page d'accueil
mentions-legales.html   mentions légales (obligatoires, LCEN)
confidentialite.html    politique de confidentialité (RGPD)
404.html                page d'erreur
merci.html              confirmation après envoi du formulaire
robots.txt, sitemap.xml référencement
assets/css/style.css    toute la mise en forme
assets/fonts/           Fraunces et Karla (licence OFL)
assets/img/favicon.svg
```

## Avant la mise en ligne

1. **Adresse du site.** Le site est en ligne sur `https://alexis.riviere-pro.workers.dev`.
   En cas de passage sur un nom de domaine propre, remplacer cette adresse partout :
   ```
   grep -rl "alexis.riviere-pro.workers.dev" . | xargs sed -i 's#alexis.riviere-pro.workers.dev#www.mondomaine.fr#g'
   ```
   (sur macOS : `sed -i ''`)

2. **Formulaire de contact.** Un site statique ne peut pas envoyer d'e-mail tout seul.
   Le formulaire est branché sur Web3Forms (offre gratuite, sans compte).
   - Sur web3forms.com, saisir `alexis.riviere@outlook.fr` pour recevoir une clé d'accès par e-mail
   - Dans `index.html`, remplacer `VOTRE_CLE_WEB3FORMS` dans le champ caché `access_key`
     (cette clé n'est pas secrète : elle peut figurer dans le HTML public)
   - Après l'envoi, le champ caché `redirect` renvoie le visiteur vers `merci.html`.
     L'adresse doit être absolue : elle est mise à jour par la commande de l'étape 1.
   - Le champ caché `botcheck` sert d'anti-spam : il est masqué par la classe `hp`.

3. **Hébergeur.** Le bloc « Hébergement » de `mentions-legales.html` indique Cloudflare (mention obligatoire).
   Le mettre à jour en cas de changement d'hébergeur.

4. **Vérifier** : délai de réponse annoncé (« sous 48 heures », section contact),
   et la formulation des réalisations.

## Hébergement

Le site tient dans moins de 200 Ko et n'a besoin d'aucun serveur applicatif.
N'importe quel hébergement statique convient : Netlify, Cloudflare Pages, GitHub Pages, OVH, o2switch…
Déposer le contenu du dossier à la racine. La page `404.html` est reconnue automatiquement
par Netlify, Cloudflare Pages et GitHub Pages.

## Après la mise en ligne

- Déclarer le site dans Google Search Console et soumettre `sitemap.xml`
- Créer ou mettre à jour la fiche Google Business Profile, avec le lien du site
- Tester le formulaire de bout en bout
