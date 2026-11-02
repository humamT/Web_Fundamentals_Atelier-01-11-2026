# 📒 Mon carnet de bord

**Nom :** 

**Prénom :** 

**Adresse de mon site :** https://______.pythonanywhere.com

> Modifiez ce fichier directement sur GitHub (icône crayon ✏️) pour répondre aux questions de chaque exercice.
> Écrivez avec vos propres mots : une réponse courte et juste vaut mieux qu'un long copier-coller ! 🙂

---

## 🟢 Exercice 1 — Mon premier déploiement

1. Où se trouve physiquement le code qui fabrique votre page : sur votre ordinateur, sur GitHub ou sur PythonAnywhere ?

   >  Le code qui fabrique la page se trouve sur PythonAnywhere. GitHub ne fait que stocker le code et son historique, et GitHub Actions le livre au serveur. C’est sur PythonAnywhere que le programme Flask s’exécute et génère la page. Rien ne se trouve sur mon ordinateur.

2. Pourquoi votre voisin(e) peut-il voir votre site, alors que vous n'avez rien installé sur son ordinateur ?

   >  Mon voisin peut voir le site parce que le programme tourne sur un serveur allumé en permanence et accessible depuis Internet, pas sur son ordinateur. Son navigateur envoie simplement une requête à l’adresse du site et reçoit la page en réponse. Il n’a donc rien à installer.

---

## 🟢 Exercice 2 — Les URL et les routes

1. Dans l'URL `https://www.google.com/maps`, quel est le nom de domaine ? Quel est le chemin ?

   >  Dans https://www.google.com/maps, le nom de domaine est www.google.com (le serveur) et le chemin est /maps (la page demandée).

2. Que veut dire le message *Not Found* ? Qui l'a envoyé : votre navigateur ou le serveur ?

   >  Not Found veut dire que le serveur n’a aucune route associée à ce chemin. Ce message a été envoyé par le serveur, pas par le navigateur : le serveur a bien reçu la requête, mais il ne connaît pas cette page (c’est l’erreur 404).

3. Que se passe-t-il si deux fonctions portent le même nom dans `flask_app.py` ? (Indice : essayez, puis lisez l'Error log.)

   >  Si deux fonctions portent le même nom, Flask lève une erreur au démarrage : AssertionError: View function mapping is overwriting an existing endpoint function. Le site affiche alors une erreur (« Something went wrong ») et plus rien ne fonctionne. On le voit à la fin de l’Error log.

---

## 🔵 Exercice 3 — Le langage HTML

1. Quelle est la différence entre ce que le serveur **envoie** et ce que le navigateur **affiche** ?

   > Le serveur envoie uniquement du texte brut contenant des balises HTML (par exemple `<h1>Léa Martin</h1>`). Le navigateur interprète ces balises et les transforme en une page mise en forme, avec des titres, des paragraphes, des listes et des images. Le texte reçu et la page affichée ne sont donc pas la même chose.

2. À quoi servent les balises `<h1>`, `<p>`, `<ul>` et `<li>` ?

   > Ces balises servent à structurer la page :
   > `<h1>` : un titre principal (`<h2>` est un sous-titre).
   > `<p>` : un paragraphe de texte.
   > `<ul>` : une liste à puces (unordered list).
   > `<li>` : un élément de cette liste (list item).

3. Pourquoi l'image s'affiche-t-elle alors qu'elle n'est pas sur votre serveur ?

   > L’image s’affiche parce que la balise `<img src="...">` contient l’adresse (URL) de l’image. Le navigateur lit cette adresse, envoie une seconde requête au serveur qui l’héberge (ici Wikimedia) et affiche l’image dans la page. Elle n’a pas besoin d’être sur mon serveur.

---

## 🔵 Exercice 4 — Les templates

1. Pourquoi est-ce une bonne idée de séparer le code Python et le HTML ? (Pensez à une équipe avec un développeur et un graphiste.)

   > Séparer le code Python et le HTML rend le projet plus lisible et plus facile à maintenir. Chacun peut travailler sur sa partie sans toucher à celle de l’autre : le développeur s’occupe de la logique dans flask_app.py, et le graphiste modifie l’apparence dans les fichiers HTML, sans risquer de casser le code Python. Le même template peut aussi être réutilisé avec des données différentes.

2. Les `{{ prenom }}` sont-ils remplacés par le serveur ou par le navigateur ? Comment l'avez-vous vérifié ?

   > Les `{{ prenom }}` sont remplacés par le serveur, avant l’envoi de la page. Je l’ai vérifié avec Ctrl + U (afficher le code source) : on y voit « Humam Altoukhi » à la place de `{{ prenom }}` `{{ nom }}`. Le navigateur ne reçoit donc jamais le template original, seulement le résultat final.

---

## 🔵 Exercice 5 — Le CSS et les liens

1. Quelle est la différence de rôle entre le HTML et le CSS ?

   > Le HTML décrit la structure de la page (ceci est un titre, un paragraphe, une liste, un lien…). Le CSS décrit son apparence (couleurs, polices, marges…). Le HTML dit ce qu’il y a sur la page, et le CSS dit comment c’est présenté.

2. Pour afficher votre page `/presentation`, combien de fichiers le navigateur doit-il télécharger ? (Vous pourrez le vérifier à l'exercice suivant !)

   > Le navigateur doit télécharger 2 fichiers : la page HTML (/presentation) et la feuille de style (/static/style.css). Si la page contient une image, comme celle de l’exercice 3, cela fait un fichier de plus.

3. Pourquoi faut-il parfois faire **Ctrl + F5** pour voir les changements de CSS ?

   > Il faut parfois faire Ctrl + F5 parce que le navigateur garde en mémoire (cache) une ancienne version du fichier CSS pour ne pas le retélécharger à chaque visite. Ctrl + F5 force le téléchargement de la version la plus récente.

---

## 🟣 Exercice 6 — Espionner le navigateur

1. Que signifie HTTP ? Qui envoie la **requête** et qui envoie la **réponse** ?

   > HTTP signifie HyperText Transfer Protocol. C’est le langage de communication entre le navigateur et le serveur. Le navigateur envoie la requête et le serveur envoie la réponse.

2. Combien de requêtes votre page `/presentation` a-t-elle déclenchées ? Lesquelles ?

   > Ma page /presentation a déclenché 3 requêtes : la page HTML (presentation), la feuille de style (style.css) et la petite icône (favicon.ico).

3. Que signifie le code `200` ? Et le code `404` de la favicon ?

   > Le code 200 signifie « OK » : le serveur a trouvé la ressource et l’a renvoyée. Le code 404 de la favicon signifie « introuvable » : le navigateur a cherché l’icône de l’onglet tout seul, mais mon site n’en a pas. 

4. Pourquoi les modifications faites dans l'onglet Éléments ne sont-elles pas visibles par les autres visiteurs ?

   > Les modifications de l’onglet Éléments ne changent que la copie de la page qui est dans mon navigateur. Le serveur n’est pas touché, donc les autres visiteurs reçoivent toujours la page d’origine. Quand je recharge, le navigateur redemande la page au serveur et mes changements disparaissent.

---

## 🟣 Exercice 7 — Envoyer des informations dans l'URL

1. Dans l'URL `https://www.youtube.com/results?search_query=chat`, quel est le nom du paramètre ? Quelle est sa valeur ?

   > Dans https://www.youtube.com/results?search_query=chat, le nom du paramètre est search_query et sa valeur est chat.

2. Pourquoi le serveur plante-t-il avec `a=bonjour` ? Que faudrait-il faire pour l'éviter ?

   > Le serveur plante avec a=bonjour parce que int("bonjour") essaie de convertir du texte en nombre, ce qui est impossible et provoque une erreur (ValueError). Pour l’éviter, il faudrait vérifier la valeur avant de la convertir (avec un try/except, par exemple) et afficher un message d’erreur clair si ce n’est pas un nombre.

3. Pourquoi est-il dangereux d'afficher **tel quel** ce que l'utilisateur envoie ?

   > Il est dangereux d’afficher tel quel ce que l’utilisateur envoie, car il peut y glisser du code HTML ou JavaScript qui sera exécuté dans le navigateur des visiteurs. Un attaquant pourrait ainsi modifier l’apparence de la page, voler des informations ou rediriger vers un site malveillant. C’est ce qu’on appelle une faille d’injection (XSS).

---

## 🟣 Exercice 8 — Les formulaires

1. Quelle est la différence visible entre GET et POST ?

   > En GET, les données apparaissent dans l’URL (par exemple /salut?prenom=Léa&ville=Paris), alors qu’en POST elles voyagent dans le corps de la requête et l’URL reste /salut.

2. Pour un formulaire de **recherche**, quelle méthode choisiriez-vous ? Et pour un formulaire de **connexion avec mot de passe** ? Pourquoi ?

   > Pour un formulaire de recherche, je choisirais GET : l’URL contient la recherche, donc on peut la copier, la partager ou la mettre en favori. Pour un formulaire de connexion avec mot de passe, je choisirais POST : le mot de passe ne doit pas apparaître dans l’URL, qui peut être enregistrée dans l’historique du navigateur, dans les favoris ou dans les journaux du serveur.

3. Les données envoyées en POST sont-elles vraiment « secrètes » ? (Pensez à ce que vous avez vu dans l'onglet Réseau.)

   > Non, les données POST ne sont pas vraiment « secrètes » : elles sont simplement absentes de l’URL. On peut les lire dans l’onglet Réseau (Charge utile) du navigateur, et sans HTTPS elles circuleraient en clair sur le réseau. Seul le chiffrement (HTTPS) les protège pendant le trajet.

---

## 🔴 Exercice 9 — Les codes de statut

1. Quelle est la différence entre une erreur `4xx` et une erreur `5xx` ? Qui est « fautif » dans chaque cas ?

   > Une erreur 4xx est une erreur du client : la demande est mauvaise (page inexistante, accès interdit…), donc le « fautif » est celui qui a envoyé la requête. Une erreur 5xx est une erreur du serveur : la demande était correcte, mais le serveur a eu un bug ou une panne (par exemple une erreur dans le code Python).

2. Comment fonctionne une redirection ? Qui fait la deuxième requête : le serveur ou le navigateur ?

   > Avec une redirection, le serveur répond par un code 3xx (par exemple 302) accompagné d’un en-tête Location qui indique la nouvelle adresse. C’est ensuite le navigateur qui fait la deuxième requête vers cette adresse, automatiquement. Le serveur ne fait que dire « va voir ailleurs ».

3. Donnez un exemple de situation où un vrai site utilise une redirection.

   > Un exemple : quand on tape `http://` sur un site sécurisé, il nous redirige automatiquement vers `https://`. Autre exemple : après avoir rempli le formulaire de connexion, le site nous redirige vers notre page de profil ou vers l’accueil.

---

## 🔴 Exercice 10 — Ce que le serveur sait de vous

1. Citez trois informations que le serveur connaît sur vous, sans que vous ayez rien rempli.

   > Sans rien remplir, le serveur connaît par exemple : mon adresse IP, mon navigateur et mon système d’exploitation (en-tête User-Agent), et mes langues préférées (en-tête Accept-Language).

2. À quoi peut servir l'en-tête `Accept-Language` pour un site comme Wikipédia ?

   > L’en-tête Accept-Language indique la langue que je préfère. Un site comme Wikipédia peut s’en servir pour afficher automatiquement la page dans ma langue (en français plutôt qu’en anglais, par exemple), sans que j’aie à la choisir.

3. Dans l'Access log, retrouvez une requête qui a reçu un code `404`. Quelle page était demandée ?

   > Dans l’Access log, j’ai retrouvé une requête avec le code 404 pour la page /favicon.ico (ou /nimportequoi, selon mes tests).

4. Après cet exercice, que pensez-vous de la notion de « navigation anonyme » ?

   > La « navigation anonyme » est moins anonyme qu’on ne le croit. Elle empêche surtout le navigateur de garder l’historique et les cookies sur mon ordinateur, mais le serveur reçoit toujours mon adresse IP, mon navigateur et mes langues. Je ne suis donc pas invisible : je suis seulement moins tracé sur mon propre appareil.

---

## 🔴 Exercice 11 — Le Web des machines : API et JSON

1. Quelle est la différence entre une page HTML et une réponse JSON ? À qui chacune est-elle destinée ?

   > _Ma réponse :_ 

2. Dans la page `/horloge`, quel code s'exécute sur le **serveur** et quel code s'exécute dans le **navigateur** ?

   > _Ma réponse :_ 

3. Citez une application de votre téléphone qui, selon vous, utilise une API. Quelles données échange-t-elle ?

   > _Ma réponse :_ 

---

## 🏁 Pour conclure

En quelques phrases, expliquez à un ami ce qui se passe entre le moment où il tape une adresse dans son navigateur et celui où la page s'affiche :

> _Ma réponse :_ 
