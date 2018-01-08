---

copyright:
  years: 2015, 2017
lastupdated: "2017-12-11"

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:tip: .tip}
{:pre: .pre}
{:codeblock: .codeblock}
{:screen: .screen}
{:javascript: .ph data-hd-programlang='javascript'}
{:java: .ph data-hd-programlang='java'}
{:python: .ph data-hd-programlang='python'}
{:swift: .ph data-hd-programlang='swift'}

# Notes sur l'édition

Les nouvelles fonctions et modifications apportées au service
ci-après sont disponibles.
{: shortdesc}

## Fonctions bêta
{: #beta}

{{site.data.keyword.IBM_notm}} propose, pour évaluation, des services, des fonctions et une prise en charge de langue, qui sont en version bêta. Ces fonctions peuvent être instables, changer fréquemment ou être arrêtées dans un délai très court. Les fonctions bêta, qui risquent de ne pas fournir le même niveau de performances ou de compatibilité que les fonctions de l'édition GA (General Availability), ne sont pas destinées à être utilisées dans un environnement de production. Le support des fonctions bêta ne s'effectue que sur [developerWorks - dW Answers ![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](https://developer.ibm.com/answers/topics/visual-recognition.html){: new_window}.

## Modifications
{: #changelog}

Les nouvelles fonctions et modifications apportées au service et décrites ci-après sont disponibles.

### 11 décembre 2017
{: #11december2017}

<ul>
  <li>
    <strong>Précision accrue et sortie avec le modèle General</strong>
      <p>
        Le modèle General, qui contient des milliers d'étiquettes, détecte maintenant un plus grand nombre d'objets secondaires et offre une détection de scène optimisée. Ces améliorations permettent de reconnaître les aspects les moins proéminents d'une image. De plus, le nombre moyen d'étiquettes retournées par image est monté à 10.
      </p>
      <p>
        L'image suivante montre un exemple d'étiquettes retournées avant la mise à jour et les étiquettes supplémentaires qui sont maintenant retournées.</p>
      <img src="images/antarctica-iceberg.jpg" alt="Iceberg en Antarctique">
      <table>
        <tr>
          <th>Etiquettes d'origine</th>
          <th>Etiquettes supplémentaires</th>
        </tr>
        <tr>
          <td>
          Tag: iceberg<br/>
          Score: 0.919</td>
          <td></td>
        </tr>
        <tr>
          <td></td>
          <td>
          Tag: ice mass<br/>
          Score: 0.801</td>
        </tr>
        <tr>
          <td></td>
          <td>
          Tag: nature<br/>
          Score: 0.770</td>
        </tr>
        <tr>
          <td>
          Tag: blue color<br/>
          Score: 0.975</td>
          <td></td>
        </tr>
        <tr>
          <td>
          Tag: alabaster color<br/>
          Score: 0.5</td>
          <td></td>
        </tr>
      </table>
    <li>
      <strong>Nouveau modèle, Explicit, disponible dans la version bêta</strong>
      <p>
        Le modèle Explicit, lancé dans la bêta, classifie les images en indiquant si elles contiennent un contenu à caractère pornographique et sont donc inadaptées à une utilisation générale. Vous pouvez associer le modèle Explicit à d'autres modèles pour une analyse combinée. Ainsi, incluez à la fois les ID de discriminant `default` et `explicit` dans votre demande pour retourner les étiquettes d'une image et savoir si l'image contient un contenu explicite. <p>
        Pour plus détails sur l'appel API, voir la méthode **Classify images** dans [API Reference ![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](https://www.ibm.com/watson/developercloud/visual-recognition/api/v3/#classify_an_image), ou essayez le modèle de [Watson API Explorer ![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](https://watson-api-explorer.mybluemix.net/apis/visual-recognition-v3#!/Classify/classify).
      </p>
    </li>
    <li>
      <strong>Prise en charge de fichiers de plus grande taille</strong>
      <p>
        Les méthodes  <strong>Classify images</strong> prennent désormais en charge des fichiers image jusqu'à 10 Mo et des fichiers .zip jusqu'à 100 Mo.
    </li>
    <li>
      <strong>Tableau requis lors du transfert d'un ID de discriminant</strong>
      <p>
        L'API impose désormais un tableau quand vous transférez les paramètres `classifier_ids` en tant qu'élément de l'objet **parameters** dans la méthode **Classify images**. Auparavant, vous pouviez passer un ID de discriminant sous forme de chaîne. Pour plus d'informations, voir la description de parameters et un fichier exemple dans [API Reference ![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](https://www.ibm.com/watson/developercloud/visual-recognition/api/v3/?curl#classify_an_image).
      </p>
    </li>
</ul>

### 8 septembre 2017
{: #8september2017}

- **Fermeture de la version bêta de Similarity Search et des collections**: depuis le 8 septembre 2017, la période bêta de Similarity Search est terminée. Pour plus d'informations, voir [Visual Recognition API – Similarity Search Update ![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](https://www.ibm.com/blogs/bluemix/2017/08/visual-recognition-api-similarity-search-update/){: new_window}.

### 30 juin 2017
{: #30june2017}

- **Etiquetage amélioré** : le discriminant default dispose désormais d'un plus grand nombre d'images d'entraînement, ce qui améliore les capacités du système à reconnaître de façon plus précise la "scène" générale d'une image. Pour plus de détails, voir [Watson Visual Recognition Sees Further Enhancements for General Tagging Feature![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](https://www.ibm.com/blogs/bluemix/2017/07/watson-visual-recognition-sees-enhancements-general-tagging-feature/){: new_window}
- **Langues supplémentaires** : la méthode **Classify images** prend désormais en charge le coréen, l'italien et l'allemand en plus de l'anglais, l'arabe, l'espagnol et le japonais.

    Pour plus détails sur l'appel API, voir la méthode **Classify images** dans [API Reference ![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](https://www.ibm.com/watson/developercloud/visual-recognition/api/v3/#classify_an_image){: new_window}Icône de lien externe.

### 16 mai 2017
{: #16may2017}

- **Un nouveau discriminant food est disponible : bêta**

    Un nouveau modèle bêta de reconnaissance de tout ce qui est lié à la nourriture fournit de meilleures spécificités et une précision plus grande dans la reconnaissance des images liées à ce domaine. La méthode **Classify images** vous permet d'ajouter ce nouveau discriminant, "food", au paramètre `classifier_ids`.

### 5 avril 2017
{: #5april2017}

- **Un nouvel outil {{site.data.keyword.visualrecognitionshort}} est disponible : bêta**

    Une nouvelle fonction bêta, l'outil {{site.data.keyword.visualrecognitionshort}}, est disponible sur [https://watson-visual-recognition.ng.bluemix.net/ ![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](https://watson-visual-recognition.ng.bluemix.net/){: new_window}. Il vous permet d'utiliser plus facilement le service {{site.data.keyword.visualrecognitionshort}}. En entrant votre clé d'API {{{site.data.keyword.cloud_notm}}, vous pouvez vous servir d'une interface utilisateur graphique pour accéder aux fonctions d'étiquetage général et de détection de visage, et facilement créer, effectuer un réapprentissage ou supprimer des discriminants personnalisés associés à votre clé d'API, sans qu'aucun codage ne soit nécessaire.

### 8 mars 2017
{: #8march2017}

- **Mise à jour de la prise en charge des langues pour l'étiquetage du discriminant General**

    Le discriminant General retourne maintenant des étiquettes dans toutes les langues prises en charge.

- **Problèmes connus**

    **CORRIGE le 13/04/2017** : des appels répétés de `GET /classifiers` pour vérifier le statut alors qu'un apprentissage ou un réapprentissage est en cours peuvent provoquer l'arrêt de la tâche d'apprentissage. Pour contourner ce problème, demandez le statut d'un nouveau discriminant en utilisant `GET /classifiers/{classifier_id}`. En d'autres termes, utilisez le discriminant `GET` pour un ID de discriminant unique plutôt que `GET /classifiers`, qui porte sur tous les discriminants, ce qui risque de provoquer le problème évoqué plus haut. Sachez aussi que `GET /classifiers/{classifier_id}` est également plus rapide.

### 15 décembre 2016
{: #15december2016}

- **Amélioration de l'étiquetage du discriminant General**

    - Les algorithmes d'apprentissage en profondeur du discriminant General ont été mis à jour. La qualité des étiquettes pour toutes les langues a été considérablement améliorée et le volume des étiquettes en anglais retournées par le service a augmenté de façon significative. Cette sortie d'étiquettes de haute qualité est aussi disponible quand vous créez votre propre discriminant personnalisé.
    - Une fonction d'étiquetage utilisant la couleur a été ajoutée. Le service repère désormais par des couleurs la valeur la plus haute (ou les deux premières).

- **Problèmes connus**

    - Les images soumises pour démonstration avec des étiquettes de métadonnées EXIF ne spécifient pas correctement l'orientation (paysage ou portrait) dans le service. Les images iPhone téléchargées peuvent contenir des étiquettes de métadonnées EXIF. La solution pour contourner ce problème est de mettre à jour vos métadonnées afin qu'elles ne se fient pas aux étiquettes EXIF pour spécifier l'orientation de votre image. Souvent, cette opération peut s'effectuer simplement en ouvrant l'image sur votre ordinateur puis en la sauvegardant. Ainsi, sur un Mac, une ouverture des ensembles d'images dans l'aperçu, suivie d'une sauvegarde, suffit à définir des étiquettes d'orientation correctes.
    - L'envoi d'images vers le service {{site.data.keyword.visualrecognitionshort}} avec des valeurs d'[étiquette EXIF![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](https://en.wikipedia.org/wiki/Exif){: new_window} risque d'augmenter le temps de latence. Le service fait pivoter les pixels de l'image dans le point de vue codé. Vous pouvez gagner du temps en procédant à une pré-rotation de vos images, ou en retirant les en-têtes EXIF s'ils ne sont pas importants pour votre tâche {{site.data.keyword.visualrecognitionshort}}.

### 1er décembre 2016
{: #1december2016}

- **Nouvelle tarification**

    IBM a diminué le prix des discriminants personnalisés sur le service {{site.data.keyword.visualrecognitionshort}} et augmenté le nombre d'éléments disponibles sur le plan gratuit. Pour plus d'informations, voir la page Pricing [{{site.data.keyword.visualrecognitionshort}}](http://www.ibm.com/watson/developercloud/visual-recognition.html#pricing-block).

### 7 octobre 2016
{: #7october2016}

- **Améliorations au niveau de la détection des visages**

    Le service dispose d'un nouvel algorithme de détection des visages qui améliore les réponses des méthodes `GET` et `POST /v3/detect_faces`. Le filtrage des détections faciales d'âge, de nom et de sexe dont l'indice de confiance est bas a été ajusté. En résultat, un plus grand nombre de visages sont détectés, avec des plages de confiance plus importantes.

### 8 septembre 2016
{: #8september2016}

- **Bêta Similarity Search**

    Les utilisateurs peuvent maintenant télécharger leur propre collection d'images, utiliser une image pour rechercher des images similaires dans cette collection, et le service retourne les 100 premières images les plus similaires. Similarity Search peut être utilisé pour divers objectifs et les utilisateurs ont la possibilité d'entraîner le service sur des collections pouvant aller jusqu'à 1 million d'images chacune. Pour plus d'informations sur l'utilisation de la nouvelle fonctionnalité Similarity Search, voir les pages [Tutorial](/docs/services/visual-recognition/tutorial-collections.html) et [API Reference ![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](https://www.ibm.com/watson/developercloud/visual-recognition/api/v3/#collections){: new_window}.

- **La version bêta de la reconnaissance de texte est fermée**

    Les méthodes `POST` et `GET /v3/recognize_text` sont en version bêta fermée. Les clients BETA utilisant ce service sont toujours pris en charge, et aucun plan n'est actuellement prévu pour l'ouverture d'une autre version bêta.

### 1er août 2016

- **Informations sur la tarification**

    L'apprentissage et le réapprentissage des discriminants personnalisés, la classification des images personnalisées et le stockage des discriminants personnalisés n'est plus gratuit. Pour plus d'informations sur la tarification, voir la [page Pricing](http://www.ibm.com/watson/developercloud/visual-recognition.html#pricing-block) du service {{site.data.keyword.visualrecognitionshort}}.

### 5 juillet 2016
{: #5july2016}

- **Mise à jour des discriminants personnalisés**

    Les discriminants personnalisés ne sont plus limités à un ensemble fixe de données d'apprentissage. Un utilisateur peut désormais mettre à jour des discriminants existants avec de nouvelles images ou ajouter des discriminants exemple négatifs ou positifs supplémentaires à un discriminant entraîné existant. En fournissant des images exemple supplémentaires à Watson pour son apprentissage, le service peut rendre plus précis le discriminant d'un utilisateur. Les discriminants peuvent maintenant être formés dans la durée, en progressant de façon continue dans la compréhension des informations visuelles mises à leur disposition.

- **Problèmes connus**

    **CORRIGE le 13/04/2017** : les utilisateurs peuvent recevoir un code d'erreur 500 après 30 ou 90 secondes lors de la mise à jour d'un discriminant existant. En dépit de cette erreur, il y a de grandes chances que la demande de réapprentissage se soit déroulée correctement. Attendez au moins 2 minutes puis vérifiez le statut du discriminant en utilisant la méthode `GET classifiers/{classifier\_id}`. Si le statut est "ready" et que l'horodatage "retrained" a été mis à jour, la demande de réapprentissage qui a généré le code 500 a abouti. Sinon, si l'horodatage "retrained" n'a pas été mis à jour, une explication est ajoutée à la réponse indiquant la raison de l'échec du réapprentissage, et le service remet le discriminant dans la version dans laquelle il était avant l'émission de la demande de réapprentissage.

### 20 mai 2016
{: #20 may 2016}

Il s'agit d'une édition en disponibilité générale (ou édition GA, pour General Availability) du service {{site.data.keyword.visualrecognitionshort}}. Cette édition, qui introduit la version 3 du service, constitue une modification avec rupture. Elle incorpore des fonctionnalités provenant du service AlchemyVision, qui a été déprécié.

Tous les discriminants personnalisés qui ont été créés alors que le service était en version bêta doivent être recréés dans une instance GA du service.

Les modifications et mises à jour suivantes ont été effectuées dans le service {{site.data.keyword.visualrecognitionshort}} :

- **Date de version :** pour utiliser les fonctionnalités de cette édition, utilisez `2016-05-20` comme valeur pour le paramètre `version`.
- **Classes et discriminants :** les discriminants uniques portent désormais le nom de "classes". Dans la version GA, un groupe de classes s'appelle un "discriminant".
- **Classification :** utilisez les méthodes `POST` ou `GET /v3/classify` pour identifier rapidement et précisément une variété de sujets et de scènes avec les classes par défaut.
- **Détection des visages : ** utilisez les méthodes `POST` ou `GET /v3/detect_faces` pour détecter des visages dans des images et obtenir des informations à leur sujet, comme l'emplacement du visage sur l'image ainsi qu'une estimation de la plage d'âge et du sexe de chaque personne dont le visage est représenté. Le service est aussi capable d'identifier par leur nom de nombreuses célébrités et de fournir une base knowledge graph de façon à vous permettre d'effectuer des agrégations intéressantes dans des concepts de niveau supérieur.
- **Discriminants personnalisés multi-facettes :** vous pouvez maintenant créer et entraîner des discriminants hautement spécialisés qui sont définis par plusieurs classes. Ainsi, vous pouvez créer un discriminant "new\_red\_car" qui est défini par les classes "new\_cars" et and "red\_cars". Pour en savoir plus sur la création de discriminants multi-facettes, voir [Structure des données d'apprentissage](/docs/services/visual-recognition/customizing.html#structure).
- **Apprentissage asynchrone : ** l'apprentissage des discriminants personnalisés est maintenant une procédure asynchrone, ce qui fait que les appels d'apprentissage s'exécutent rapidement pendant que votre discriminant personnalisé continue d'apprendre en arrière-plan. Pour vérifier le statut d'apprentissage de votre discriminant personnalisé et savoir quand il est disponible pour utilisation, appelez la méthode `GET /v3/classifiers/{classifier_id}` et vérifiez le paramètre de réponse `status`.

### 2 décembre 2015
{: #2december2015}

La nouvelle édition du service {{site.data.keyword.visualrecognitionshort}} constitue une modification avec rupture qui introduit une nouvelle version de l'API {{site.data.keyword.visualrecognitionshort}} API (v2). La version 1 du service {{site.data.keyword.visualrecognitionshort}} est disponible pour utilisation jusqu'à ce que le service quitte la version bêta.

Pour commencer immédiatement à utiliser la version 2 de l'API, vous devez comprendre et mettre à jour votre code pour refléter ces changements :

- Dans la version 1 du service, vous analysiez les images par libellés. Dans la version 2 du service, les libellés sont appelés **discriminants**. Les discriminants ont un ID de discriminant unique indiqué par le paramètre `classifier_id` et un nom abrégé indiqué par le paramètre `name`.
- La méthode `POST /v1/recognize` pour analyser une image est désormais [`POST /v2/classify` ![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](https://www.ibm.com/watson/developercloud/visual-recognition/api/v3/#classify_an_image){: new_window}. Le paramètre `labels_to_check` s'appelle maintenant `classifier_ids`.
- La méthode `GET /v1/tag/labels` d'extraction d'une liste de libellés dans V1 est devenue la méthode d'extraction d'une liste de discriminants, [`GET /v2/classifiers` ![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](https://www.ibm.com/watson/developercloud/visual-recognition/api/v3/#retrieve_a_list_of_classifiers){: new_window}.
- En plus de l'extraction d'une liste de discriminants, vous pouvez aussi extraire les détails d'un discriminant spécifique avec la nouvelle méthode [`GET /v2/classifiers/{classifier_id}` ![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](https://www.ibm.com/watson/developercloud/visual-recognition/api/v3/#retrieve_classifier_details){: new_window}.
- La version 2 de l'API {{site.data.keyword.visualrecognitionshort}} bêta vous permet de créer des discriminants personnalisés avec la nouvelle méthode [`POST /v2/classifiers` ![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](https://www.ibm.com/watson/developercloud/visual-recognition/api/v3/#create_a_classifier){: new_window}. Pour en savoir plus sur la création de discriminants personnalisés, voir [Creating custom classifiers](/docs/services/visual-recognition/customizing.html).
- La version 2 de l'API {{site.data.keyword.visualrecognitionshort}} bêta vous permet aussi de supprimer des discriminants personnalisés avec la nouvelle méthode [`DELETE /v2/classifiers` ![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](https://www.ibm.com/watson/developercloud/visual-recognition/api/v3/#delete_a_classifier){: new_window}.
- La version 2 de l'API {{site.data.keyword.visualrecognitionshort}} bêta requiert le paramètre `version`. Spécifiez la date d'édition de la version de l'API que vous voulez utiliser au format `MM-DD-YYYY`.
