# stage_data_science

Voici un graphique de distribution:

![Distribution_Graph](https://github.com/TheRealiPaul/stage_data_science/blob/main/normal%20distribution.png?raw=true)

Q: Que contiennent les tables dans les schéma louis_v004? Expliquer la structure relationelle et la fonction de chaque table.

A: louis_v004 contient les tables `ada_002`, `chunk`, `crawl`, `link`, `query` et `score`.
- ada_002: Cette table est l'enfant de la table `token`. Elle a une clé étrangère de `token`.
- token: Cette table est le parent de la table `ada_002` et est l'enfant de `chunk`. On peut voir que la table `token` a une clé primaire `id` et qu'`ada_002` possède la clé étrangère de `token`.
- chunk: Cette table contient les sections de la page HTML tels que son title et le contenu. Elle est l'enfant de `crawl`. Dans cette table, on y trouve `crawl_id` pour faire la jointure.
- crawl: Sauvegarde l'url de la page web et le contenu de la page en HTML. Un `crawl` peut contenir plusieurs `chunk`.
- link: Dans le diagramme, on peut voir qu'il y a une relation entre `crawl` et `link`. La fonction de cette table est de rediriger un lien source vers un lien destination.
- query: Cette table est indépendante. Sa fonction est de stocker des requêtes SQL.
- score: Cette table est indépendante. Dans la colonne `score_type`, il existe 2 types: `recency` et `traffic` et que pour chaque `entity id`, un `score` calculé est stocké.

Q: Quelle distribution prennent les valeurs de longueur du contenu?

A: Cela est la répartition des valeurs (longueurs du HTML) d'une population (pages HTML).

Q: Expliquer le calcul en fonction de la distribution spécifique des valeurs de longueurs de html_content script

A: J'ai appliqué la formule du score z et je l'ai appliqué en SQL.

Q: Expliquer et discuter de la performance de votre fonction recherche

A: Je crée une fonction qui se nomme `"recherche"` et qui prend en paramètre un `"mot_cle"` d'une chaîne de caractères de 255 caractères de longueur. Elle retourne un ensemble de documents. La fonction exécute une requête et affiche toutes les colonnes de la table `"documents"` en prenant en compte la condition suivante : si le contenu contient le `"mot_cle"` dans n'importe quelle position. Ensuite, elle trie les résultats par scores en ordre descendant et limite le nombre de résultats avec la clause "LIMIT 10", ce qui signifie qu'on limite à 10 résultats.

Concernant la performance de ma fonction recherche, il y a encore des améliorations à faire. En effet, je suis convaincu que mon algorithme de recherche peut être optimisé pour obtenir de meilleurs résultats.

Pour savoir la performance d'une requête, il faut qu'on fait le recours à l'aide des outils de PostgreSQL qui permet de mesurer le temps d'exécution et le temps d'exécution du plan sur le serveur.

### Performance
Avec l'essai :

`select recherche('Nomenclature');`

Voici le résultat:

![Recherche_performance](https://github.com/TheRealiPaul/stage_data_science/blob/main/stage_peformance_recherche.png?raw=true)

