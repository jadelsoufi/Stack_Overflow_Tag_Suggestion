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

![image](https://user-images.githubusercontent.com/76253068/171588016-fc773006-df44-47ce-9488-8b50e35ef3e2.png)

![image](https://user-images.githubusercontent.com/76253068/171588031-df3b310b-ed07-4dfc-b1d6-6c3a09f47a01.png)

![image](https://user-images.githubusercontent.com/76253068/171588066-27f1d9d9-636d-49aa-8de6-967978085b94.png)

### Multiplications matricielles

![image](https://user-images.githubusercontent.com/76253068/171588681-9eba9650-a0ed-49e3-aab0-311b7803ad97.png)


### Test de la matrice de probabilité post/probabilité des mots

![image](https://user-images.githubusercontent.com/76253068/171588405-d3b09483-7769-4d24-bb7f-7a83fdfae2e6.png)

## Modélisation: méthode supervisée

### TFIDF

![image](https://user-images.githubusercontent.com/76253068/171589311-e500f413-0429-4237-abf8-746823cd3b22.png)

### PCA

![image](https://user-images.githubusercontent.com/76253068/171590005-335a444a-b971-411e-866a-924d2be4814f.png)

### GridSearchCV

![image](https://user-images.githubusercontent.com/76253068/171590374-d0cdf027-c13b-4441-9084-fb9598454743.png)

![image](https://user-images.githubusercontent.com/76253068/171590405-bbedfe1d-3b54-48dc-94b8-1e6cbbf143dd.png)

### Test et Evaluation avec Jaccard Score

![image](https://user-images.githubusercontent.com/76253068/171590530-c745b8e7-2556-4c2b-bf98-c680b754a14c.png)


## Word2Vec

![image](https://user-images.githubusercontent.com/76253068/171590654-b827dee7-12fe-45f0-bac3-f031d2202886.png)

## BERT

![image](https://user-images.githubusercontent.com/76253068/171590758-dc1c9661-0161-4b71-ace6-0b12bef5bbff.png)

## USE

![image](https://user-images.githubusercontent.com/76253068/171590862-58df97df-e96b-4db3-ab5a-b481e98e5fc2.png)

## Evaluation Word2Vec/BERT/USE

![image](https://user-images.githubusercontent.com/76253068/171590912-54fd6b35-2f76-4ea8-a9c3-4009aac6f6c4.png)

## Conclusion

Approche Supervisée privilégiée

Modèle final sélectionné: OneVsRest SVC avec modélisation BERT

Pistes d’améliorations:
- Augmenter le nombre de posts
- Modifier le nombre de labels (tags)
- Effectuer un gridsearch sur les approches Word2Vec, BERT et USE


