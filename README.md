# Pràctica Kaggle APC UAB 2021-22
### Nom: Jofre Gómez González
### DATASET: Topic Labeled News Dataset
### URL: [kaggle](https://www.kaggle.com/kotartemiy/topic-labeled-news-dataset)
## Resum
Les dades del dataset son una recopilació d'articles de notícies.<br><br>
La BD té 108.774 dades i està formada per 6 atributs:
* **topic:** topic en el que s'ha classificat l'article, segons el Kaggle n'hi han 8 tipos(BUSINESS, ENTERTAINMENT, HEALTH, NATION, SCIENCE, SPORTS, TECHNOLOGY i WORLD)
* **link:** link d'on trobar l'article
* **domain:** domini de la pàgina en que va ser publicat l'article
* **published_date:** data en que l'article va ser publicat
* **title:** títol de l'article
* **lang:** llengua en el que està escrit l'article, podem observar com tots els articles estàn en Anglés

### Objectius del dataset
Volem classificar un article a partir del seu títol en diferents tópics (BUSINESS, ENTERTAINMENT, HEALTH, NATION, SCIENCE, SPORTS, TECHNOLOGY i WORLD).
## Experiments
Durant aquesta pràctica hem realitzat diferents experiments.
### Preprocessat
Primer de tot hem revisat que no hi haguéssin dades incoherents com dates d'articles incoherents, camps buits en registres de la BD, dades desbalancejades. S'ha utilitzat la llibreria "gensim.parsing.preprocessing" per eliminar els "stopwords" (paraules que no aporten cap informació útil per decidir en quina categoria s'ha de classificar un text) en els títols dels articles.
### Model
| Model | % train | % test | Hiperparametres | Accuracy |
| -- | -- | -- | -- | -- |
| Naive Bayes | 90 | 10  | -- | 79,32% |
| Naive Bayes | 80 | 20  | -- | 79,42% |
| Naive Bayes | 60 | 40  | -- | 78,23% |
| -- | -- | -- | -- | -- |
| SVM | 90 | 10 | alpha = 0.01, penalty='l2' | 73,44% |
| SVM | 80 | 20 | alpha = 0.01, penalty='l2' | 73,27% |
| SVM | 60 | 40 | alpha = 0.01, penalty='l2' | 73,02% |
| SVM | 90 | 10 | alpha = 0.1, penalty='l2' | 23,99% |
| SVM | 80 | 20 | alpha = 0.1, penalty='l2' | 25,65% |
| SVM | 60 | 40 | alpha = 0.1, penalty='l2' | 13,98% |
| SVM | 90 | 10 | alpha = 0.5, penalty='l2' | 13,78% |
| SVM | 80 | 20 | alpha = 0.5, penalty='l2' | 13,89% |
| SVM | 60 | 40 | alpha = 0.5, penalty='l2' | 25,63% |
| SVM | 90 | 10 | alpha = 0.001, penalty='l2' | 73,32% |
| SVM | 80 | 20 | alpha = 0.001, penalty='l2' | 73,34% |
| SVM | 60 | 40 | alpha = 0.001, penalty='l2' | 73,24% |
| SVM | 90 | 10 | alpha = 0.01, penalty='l1' | 14,20% |
| SVM | 80 | 20 | alpha = 0.01, penalty='l1' | 13,74% |
| SVM | 60 | 40 | alpha = 0.01, penalty='l1' | 13,87% |
| SVM | 90 | 10 | alpha = 0.1, penalty='l1' | 13,96% |
| SVM | 80 | 20 | alpha = 0.1, penalty='l1' | 14,05% |
| SVM | 60 | 40 | alpha = 0.1, penalty='l1' | 13,96% |


## Demo
No he generat cap tipus de demo
## Conclusions
Podem conloure dient que amb la BD actual, el classificador Naive Bayes ens està donant un accuracy significativament superior (6%) respecte el classificador SVM alhora de classificar els articles segons el tópic en un temps molt similar (1s aprox.).<br><br>

Encara que el classificador Naive Bayes no és un classificador perfecte i té bastant marge de millora, en un futur s'hauria de provar amb una base de dades que contingués molts més articles (milions) i més classes a classificar, així el nostre classificador podria observar una major diverisitat de paraules en els títols dels articles i donar classificacions més precises.<br><br>

També, mencionar la importància d'escollir uns bons paràmetres en els diferents classificadors ja que com hem pogut observar, al escollir uns paràmetres dolents en el classificador SVM com una alpha massa gran on una regularitazció l1 ens ha arrribat a reduir l'accuracy d'un 73% aproximadament a un 13-25% aprox.
## Idees per treballar en un futur
Seria interesant:
* Aumentar la BD i provar si obtenim millors accuracy amb un volum de dades major i amb més topics a classificar
* Afegir a la BD una columna de "rating" dels usuaris sobre l'article, així també podriem fer recomenadors "Collaborative-filtering"
* Comparar més classificadors i observar si ens donen millor accuray i el seu cost computacional

