# Stackoverflow_Tag_Suggestion
Déployer une application de suggestion de tag pour les utilisateurs de Stack Overflow

## Problématique

Stack Overflow est un site célèbre de questions-réponses liées au développement informatique.

Pour poser une question sur ce site, il faut entrer plusieurs tags afin de retrouver facilement la question par la suite. Pour les utilisateurs expérimentés, cela ne pose pas de problème, mais pour les nouveaux utilisateurs, il serait judicieux de suggérer quelques tags relatifs à la question posée.

Amateur de Stack Overflow, qui vous a souvent sauvé la mise, vous décidez d'aider la communauté en retour. Pour cela, vous développez un système de suggestion de tags pour le site. Celui-ci prendra la forme d’un algorithme de machine learning qui assignera automatiquement plusieurs tags pertinents à une question.

## Base de données

Les données sont téléchargeables par requête SQL au lien suivant :
https://data.stackexchange.com/stackoverflow/query/new

Requête utilisée pour le projet:
![image](https://user-images.githubusercontent.com/76253068/170725433-3271cc91-8e54-429d-ba92-2e1fe4da59ad.png)

## Traitement et nettoyage de la base de données :

- Suppression des balises HTML via le module BeautifulSoup
- Suppression des caractères ASCII via re.compile
- Suppression des chiffres et majuscules
- Cleaning des tags : suppression des balises HTML et suppression des tags avec une faible occurence dans une optique d'optimisation des performances.

## Feature Engineering

- Tokenization des mots via RegexpTokenizer
- Lemmatization avec repérage du contexte des mots via POS
- Suppression des StopWords anglais rallongée de mots non pertinents dans l'univers de coding informatique

## Analyse Exploratoire

![image](https://user-images.githubusercontent.com/76253068/170726737-3a4bf8fc-ec28-40c9-b3e2-1a4363461221.png)

![image](https://user-images.githubusercontent.com/76253068/170726767-a355dbbc-2f99-42ad-8bfe-41fc285b3bbb.png)

![image](https://user-images.githubusercontent.com/76253068/170726795-868a55a1-abd1-4968-ae5d-d54ac3eb7173.png)

### Wordcloud 

![image](https://user-images.githubusercontent.com/76253068/170726861-295d6c9d-3f24-4d31-aa3e-cabd26fc4ee8.png)

### Wordcloud posts tagués python

![image](https://user-images.githubusercontent.com/76253068/170726947-dbb81800-5f11-4968-ac1b-8116b1869705.png)

## Modélisation: méthode non-supervisée
