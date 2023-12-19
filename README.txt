ce projet realise par : Souki salma , Zineb Baraka et Meryem ELAmari

repertoire netoyage de donnees : contient le code


repertoire piece : contient le ppt et le rapport 



 

Explication du projet :
notre projet est un siple pipeline de nettoyage des données en utilisant des algorithmes d'apprentissage supervisé et qui intègre le SVM  (Support Vector Machine)  dans le SNM (Similarity Network Fusion) pour accélérer sa performance suivant ces etapes  :

1. Chargement du dataset Titanic :
   - Le code commence par charger le dataset Titanic à partir d'un fichier texte et le stocke dans un DataFrame appelé "df".

2. Encodage des variables catégorielles :
   - Les variables catégorielles "Embarked" et "Cabin" sont encodées en utilisant le LabelEncoder. Les valeurs catégorielles sont converties en valeurs numériques.

3. Imputation des valeurs manquantes :
   - Les variables avec des valeurs manquantes, telles que "Age", "Embarked" et "Cabin", sont imputées en utilisant l'algorithme KNNImputer. Les valeurs manquantes sont estimées en fonction des valeurs les plus proches des voisins.

4. Modèle prédictif pour les variables incomplètes :
   - Pour chaque variable incomplète (Embarked et Cabin), un modèle prédictif (HistGradientBoostingRegressor) est créé pour prédire les valeurs manquantes à partir des autres variables complètes. Les valeurs prédites sont ensuite remplacées dans le DataFrame.

5. Détection et traitement des valeurs aberrantes :
   - Les valeurs aberrantes pour la variable "Age" sont détectées en utilisant la méthode de l'IQR (Interquartile Range). Les valeurs situées en dehors de 1,5 fois l'écart interquartile sont considérées comme des valeurs aberrantes.
   - Les valeurs aberrantes détectées sont remplacées par la médiane de la variable.

6. Prétraitement des données supplémentaires :
   - Certaines étapes de prétraitement supplémentaires sont effectuées sur le DataFrame modifié. Par exemple, la suppression de la colonne "Cabin" et la conversion des variables catégorielles en variables binaires.

7. Entraînement du SVM :
   - Les features (caractéristiques) et la variable cible sont séparées du DataFrame prétraité.
   - Les caractéristiques sont normalisées à l'aide du MinMaxScaler.
   - Le modèle SVM (SVC avec noyau linéaire) est créé et entraîné sur les données d'entraînement.

8. Prédiction des étiquettes de similarité :
   - Les nouvelles données (nouveau dataset) sont chargées et prétraitées de la même manière que les données d'entraînement.
   - Les étiquettes de similarité sont prédites en utilisant le modèle SVM entraîné sur les données d'entraînement.

9. Application du SNM :
   - Le SNM est appliqué en utilisant les étiquettes de similarité prédites.
   - Les paires de doublons sont identifiées en comparant les noms des individus ayant des étiquettes de similarité identiques.
   - Les paires de doublons trouvées sont affichées.

10. Évaluation de la performance :
    - comparaison avec un programme qui implente l'algorithme de snm normal qui est dans le fichiers snm dans le repertoire netoyage de donnees
