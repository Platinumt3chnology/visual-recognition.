---

copyright:
  years: 2015, 2019
lastupdated: "2019-03-06"

keywords: new features,updates to Visual Recognition,what's new with Visual Recognition

subcollection: visual-recognition

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:tip: .tip}
{:important: .important}
{:note: .note}
{:deprecated: .deprecated}
{:pre: .pre}
{:codeblock: .codeblock}
{:screen: .screen}

<!-- Link definitions -->

[watson-studio-reg]: https://dataplatform.ibm.com/registration/stepone?target=watson_vision_combined&context=wdp&apps=watson_studio&cm_sp=WatsonPlatform-WatsonPlatform-_-OnPageNavCTA-IBMWatson_VisualRecognition-_-docs
[demo]: https://www.ibm.com/watson/services/visual-recognition/demo

# Notes sur l'édition
{: #release-notes}

Les nouvelles fonctions et modifications apportées au service
ci-après sont disponibles.
{: shortdesc}

## Gestion des versions d'API du service
{: version}

Les demandes d'API nécessitent un paramètre de version qui prend une date au format `version=AAAA-MM-JJ`. Chaque fois que nous modifions l'API de manière irréversible, nous publions une nouvelle version mineure de l'API. 

Envoyez le paramètre de version avec chaque demande d'API. Le service utilise la version d'API correspondant à la date que vous spécifiez ou la toute dernière version avant cette date. Ne laissez pas la date du jour par défaut. Indiquez à la place une date correspondant à une version compatible avec votre application et ne la changez pas tant que votre application n'est pas prête pour une version ultérieure. 

Version actuelle : `2018-03-19`.

## Fonctions bêta
{: #beta}

{{site.data.keyword.IBM_notm}} propose, pour évaluation, des services, des fonctions et une prise en charge de langue, qui sont en version bêta. Ces fonctions peuvent être instables, changer fréquemment ou être arrêtées dans un délai très court. Les fonctions bêta, qui risquent de ne pas fournir le même niveau de performances ou de compatibilité que les fonctions de l'édition GA (General Availability), ne sont pas destinées à être utilisées dans un environnement de production. Les fonctions bêta sont prises en charge uniquement sur [IBM Developer Answers ![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](https://developer.ibm.com/answers/topics/visual-recognition.html){: new_window}.

## Modifications
{: #changelog}

Les nouvelles fonctions et modifications apportées au service et décrites ci-après sont disponibles.

### 15 janvier 2019
{: #15january2019}

- **Traduction du sexe dans Detect Faces**
    - Les méthodes **Detect Faces** renvoient désormais des libellés traduits pour "Male" et "Female" lorsque vous indiquez la langue dans l'en-tête de demande **Accept-Language**. Pour des détails, voir [API reference ![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](https://{DomainName}/apidocs/visual-recognition#detect-faces-in-images){: new_window}.

### 1er octobre 2018
{: #01october2018}

- **Les instances de service créées avant le 23 mai 2018 sont supprimées.**

    - Comme précédemment signalé, aucune des instances de {{site.data.keyword.visualrecognitionshort}} créées avant le 23 mai 2018 n'est plus active. Les données provenant de ces instances sont désormais supprimées. Voir [Migration](/docs/services/visual-recognition?topic=visual-recognition-migrating#migrating) pour des détails sur le passage à une nouvelle instance de service.
    - Les instances de service créées après cette date ne sont pas concernées.
    - Si vous avez des questions, contactez le [support IBM ![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](https://ibm.biz/ibmcloudsupport){: new_window}.

### 1er août 2018
{: #01august2018}

- **Disponibilité générale des modèles Food et Explicit**

    Les modèles Food et Explicit sont passés de la version bêta à la disponibilité générale (GA). Le modèle Food reconnaît davantage de nourriture et de plats que le modèle General (default). Le modèle Explicit identifie ce qui pourrait être considéré comme des images à caractère pornographique.

    Aucune modification du code n'est requise. Les deux modèles sont gratuits dans le plan Lite et coûtent 0,002 $ par image pour le plan Standard.

    Pour plus d'informations, voir [Updates to Watson Visual Recognition ![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](https://ibm.biz/visrec-price-reduction){: new_window} dans le <em>blog Watson</em>.

### 1er juillet 2018
{: #01july2018}

- **Nouvelle tarification pour les modèles personnalisés**
    - A compter du 1er juillet, la classification d'une image avec un modèle personnalisé coûte moitié moins que le taux antérieur, soit désormais 0,002 dollar l'image. Pour plus de détails et pour prendre connaissance des informations importantes, voir [Updates to Watson Visual Recognition \- Price reduction for Custom Classification ![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](https://ibm.biz/visrec-price-reduction){: new_window} dans le <em>blog Watson</em>.

### 21 juin 2018
{: #21june2018}

- **Support de langue supplémentaire**

    - Les méthodes **Classify** prennent désormais en charge le chinois (simplifié et traditionnel), ainsi que le portugais (brésilien) dans la sortie des classes du modèle `default` (General). Pour obtenir la liste complète des langues, voir [Langues prises en charge](/docs/services/visual-recognition?topic=visual-recognition-supported-languages#supported-languages).
    - Toutes les langues sont désormais prises en charge dans les réponses provenant des modèles **Food** et **Explicit**.


### 22 mai 2018
{: #22may2018}

- **Nouveau processus d'authentification d'API**:

    Vous pouvez désormais vous authentifier avec IAM (Identity and Access Management) sur un nouveau noeud final. 

    - Utilisez une URL de noeud final différente pour les nouvelles instances. Le noeud final par défaut est `https:/gateway.watsonplatform.net/visual-recognition/api/`. Pour déterminer l'URL de votre instance de service, vérifiez les données d'identification en cliquant sur l'instance depuis le [tableau de borde ![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](https://console.bluemix.net/dashboard/apps?watson){: new_window} {{site.data.keyword.cloud_notm}}.
    - Modifiez la façon dont vous vous authentifier auprès de l'API. Vous indiquez une clé IAM ou un jeton d'accès pour votre instance de service. Voir [Migration](/docs/services/visual-recognition?topic=visual-recognition-migrating#migrating) pour des exemples. 

    Pour les instances de service créées avant le 23 mai 2018, le processus d'authentification et le noeud final n'ont pas changé. Authentifiez-vous en fournissant le paramètre de requête `api_key`.

- **Mises à jour du plan Lite**

    Les plans Lite créés après le 22 mai 2018 changent :

    - Les nouvelles instances du plan Lite restent disponibles au-delà de plan 30 jours si vous les utilisez chaque mois. 
    - Vous pouvez créer et recycler deux modèles personnalisés sous le nouveau plan Lite. 
    - Les plans Lite incluent jusqu'à 1 000 événements par mois. Chaque image envoyée pour classification, détection ou entraînement constitue un événement. Le téléchargement d'un modèle Core ML n'est pas pris en compte dans le nombre maximal d'événements. 

    Si vos besoins dépassent le plan Lite, effectuez une mise à jour vers un compte facturable. [Explorez ![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](https://console.bluemix.net/catalog/services/visual-recognition){: new_window} les plans de tarification. 

- **Sécurité des informations**:

    Nous avons mis à jour la documentation afin d'inclure certains détails nouveaux concernant la confidentialité de données. Consultez ces informations détaillées dans [Sécurité des informations](/docs/services/visual-recognition?topic=visual-recognition-information-security#information-security).

### 12 avril 2018
{: #12april2018}

- **Prise en charge du recyclage d'un modèle personnalisé dans le plan Lite**

    Sous le plan Lite, vous n'avez plus besoin de supprimer puis de créer un autre modèle lorsque vous souhaitez mettre à jour ou entraîner à nouveau le modèle. Vous pouvez désormais mettre à jour un modèle personnalisé dans la mesure où vous restez sous les [limites](https://console.bluemix.net/catalog/services/visual-recognition) quotidienne et mensuelle du plan.

    Si vous avez besoin de disposer de plusieurs modèles ou de plusieurs versions d'un même modèle, passez du plan Lite à un compte facturable.

- **Nouvelle version secondaire avec prise en charge pour CORS**

    **Version :** `2018-03-19`

    Nous prenons désormais en charge les en-têtes de partage de ressources d'origine croisée (CORS) lorsque vous spécifiez `version=2018-03-19` dans les demandes.

### 5 avril 2018
{: #5april2018}

- **Correctif pour le problème de score du modèle Face**

  La plage d'origine du score d'âge dans le modèle Face a été restaurée (plage de 0 à 1). Pour des détails, voir les [Problèmes connus](#2april2018) du 2 avril 2018.

- **Nouveaux paramètres de données de formulaire**

    Les méthodes **Classify images** et **Detect faces in images** prennent en charge de nouveaux paramètres de paramètres. La classification des images prend en charge les paramètres `url`, `classifier_ids`, `threshold` et `owners`, et la détection des visages prend en charge le paramètre `url`.

    Par le passé, vous codiez les valeurs dans une chaîne JSON et transmettiez le paramètre de données de formulaire **parameters**. Vous pouvez désormais utiliser la nouvelle méthode d'acheminement de ces valeurs dans des paramètres de données de formulaire distincts pour tout développement d'application. Pour des détails, voir [API reference ![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](https://{DomainName}/apidocs/visual-recognition){: new_window}.

### 2 avril 2018
{: #2april2018}

- **Disponibilité générale du modèle Face amélioré**

    Le modèle mis à jour de détection des visages est désormais en disponibilité générale (GA).

    Ce modèle étendu utilise des ensembles de données d'apprentissage plus grands pour une précision accrue de la détection faciale pour l'âge et le sexe. Par exemple, les prévisions d'âge sont améliorées en réduisant la plage entre `min` et `max`. La plage d'âges fixe de 9 ans dans le modèle précédent a été remplacée par une plage dynamique et plus petite. La plage moyenne est désormais de 4,9 ans.

    - Changements apportés à l'API

    Autres différences entre le modèle Face étendu et le modèle précédent : 
        - Le modèle étendu prend en charge les formats d'image .gif et .tif.
        - Le modèle amélioré prend en charge des tailles de fichier plus importantes : jusqu'à 10 Mo pour des fichiers image et 100 Mo pour des fichiers .zip.
        - Le modèle amélioré n'inclut pas d'informations `FaceIdentity` dans la réponse. Les informations d'identité font référence au `name` (nom) de la personne, au `score` et au graphique de connaissances `type_hierarchy` (hiérarchie de types).

    Pour des détails sur l'API, voir [API reference ![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](https://{DomainName}/apidocs/visual-recognition/#detect-faces-in-images){: new_window}.

    - Problèmes connus

        - Les paramètres de formulaire ne peuvent pas inclure le **Content-Type**. Par exemple, la demande suivante échoue dans l'analyse du paramètre **url** car elle inclut `;type=text/plain`:

            ```bash
            curl -F url="https://example.com/images/prez.jpg;type=text/plain" \
            "https://gateway-a.watsonplatform.net/visual-recognition/api/v3/detect_faces?api_key={api-key}&version=2016-05-20"
            ```
            {: pre}

        - Le score d'âge a une plage comprise entre 0 et 0.3. Nous travaillons à la restauration de la plage d'origine (de 0 à 1).

    - Noeud final bêta déprécié

    Le noeud final bêta sur `/v3/detect_faces_beta` est déprécié et ne sera plus accessible à compter du 17 mai 2018. Assurez-vous que vos demandes pointent sur `/v3/detect_faces`.

### 20 mars 2018
{: #20march2018}

- **Intégration avec Apple Core ML**

    {{site.data.keyword.visualrecognitionshort}} inclut désormais la prise en charge du format de modèle Apple Core ML. Vous pouvez utiliser une version Core ML de votre modèle {{site.data.keyword.visualrecognitionshort}} dans vos applications iOS.

    **Commencer le développement** : Pour commencer à développer avec {{site.data.keyword.visualrecognitionshort}} et Core ML, consultez les projets suivants sur GitHub :

    - Classification d'images en local : [{{site.data.keyword.visualrecognitionshort}} with Core ML ![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](https://github.com/watson-developer-cloud/visual-recognition-coreml){: new_window}.
    - Intégration d'{{site.data.keyword.discoveryfull}} aux résultats : [{{site.data.keyword.visualrecognitionshort}} and Discovery with Core ML ![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](https://github.com/watson-developer-cloud/visual-recognition-with-discovery-coreml){: new_window}.
    - Exploration du kit SDK : [Swift SDK ![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](https://github.com/watson-developer-cloud/swift-sdk){: new_window}.

- **Changements apportés à l'API**

    Les changements suivants apportés à l'API, compatibles en amont, sont inclus dans l'intégration :

    - Nouvelle zone `core_ml_enabled` indiquant si un modèle de discriminant peut être téléchargé en tant que modèle Core ML. La zone est renvoyée en réponse à des appels envoyés à `GET and POST /v3/classifiers` et `GET /v3/classifiers/{classifier_id}`.
    - Nouvelle méthode `GET /v3/classifiers/{classifier_id}/core_ml_model` pour télécharger un modèle Core ML en tant que fichier .mlmodel. Vous pouvez télécharger des fichiers modèle Core ML pour des modèles personnalisés créés après le 19 mars. 
    - Nouvelle zone `updated` correspondant aux données d'apprentissage les plus récentes du modèle. La zone `updated` correspond à la zone `retrained` ou à la zone `created`. 

    Pour des détails sur les modifications de l'API concernant Core ML, voir [API reference ![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](https://https://{DomainName}/apidocs/visual-recognition#/retrieve-a-core-ml-model-of-a-classifier){: new_window}.

- **Nouvel outil disponible : Watson Studio**

    [Watson Studio ![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](https://dataplatform.ibm.com/registration/stepone?target=watson_vision_combined&context=wdp&apps=watson_studio&cm_sp=WatsonPlatform-WatsonPlatform-_-OnPageNavCTA-IBMWatson_VisualRecognition-_-docs){: new_window} est le nouvel environnement intégré qui inclut un remplacement de l'outil {{site.data.keyword.visualrecognitionshort}} bêta. Watson Studio prend en charge non seulement {{site.data.keyword.visualrecognitionshort}}, mais aussi de nombreux autres services et ressources {{site.data.keyword.cloud_notm}}. Vous pouvez utiliser Watson Studio avec l'ensemble de vos instances et discriminants {{site.data.keyword.visualrecognitionshort}} existants. 

     Watson Studio fournit un environnement collaboratif dans le cloud. Avec Watson Studio, les développeurs, les experts de domaines, les analystes scientifiques des données, etc., peuvent générer et entraîner {{site.data.keyword.visualrecognitionshort}} et d'autres modèles d'IA. Vous pouvez également utiliser Watson Studio pour accéder aux modèles intégrés General et Face.

     Watson studio prend également en charge Core ML. Vous pouvez télécharger un fichier modèle Core ML pour votre modèle personnalisé.

    [Initiation à ![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](https://dataplatform.ibm.com/registration/stepone?target=watson_vision_combined&context=wdp&apps=watson_studio&cm_sp=WatsonPlatform-WatsonPlatform-_-OnPageNavCTA-IBMWatson_VisualRecognition-_-docs){: new_window} avec Watson Studio.

- **Architecture d'apprentissage en profondeur mise à jour pour les modèles personnalisés**

    {{site.data.keyword.visualrecognitionshort}} utilise désormais une architecture de réseau d'apprentissage en profondeur plus rapide et efficace pour la classification. Les modèles mis à jour sont également capables de mieux distinguer la classe supérieure des autres classes. Cette approche peut entraîner des temps d'apprentissage quelque peu plus longs. La nouvelle architecture est utilisée pour entraîner les nouveaux modèles personnalisés. Lorsque vous entraînez à nouveau des modèles existants, l'architecture d'origine est utilisée. 

    L'exemple suivant illustre les différences avec la nouvelle architecture : 

    ![Arc et flèche pour tir à l'arc. Photo d'Annie Spratt sur Unsplash](images/archery.jpg)

    <table>
      <tr>
        <th>Classe et score d'origine</th>
        <th>Classe et score mis à jour</th>
      </tr>
      <tr>
        <td>Archery</br>0.99 </td>
        <td><strong>archery<strong></br>0.9</td>
      </tr>
      <tr>
        <td>Auto Racing</br>0.996398</td>
        <td><strong>biking</strong></br>0.004</td>
      </tr>
      <tr>
        <td>Biking</br>0.0500174</td>
        <td><strong>fishing</strong></br>0.001</td>
      </tr>
      <tr>
        <td>Fishing</br>0.11029</td>
        <td><strong>golf</strong></br>0.031</td>
      </tr>
      <tr>
        <td>Golf</br>0.0980796</td>
        <td><strong>gymnastics</strong></br>0.029</td>
      </tr>
      <tr>
        <td>Gymnastics</br>0.964391</td>
        <td><strong>judo</strong></br>0.021</td>
      </tr>
      <tr>
        <td>Judo</br>0.339119</td>
        <td><strong>racing</strong></br>0.002</td>
      </tr>
      <tr>
        <td>Skating</br>0.0393602</td>
        <td><strong>skating</strong></br>0.061</td>
      </tr>
      <tr>
        <td>Skiing</br>0.0310527</td>
        <td><strong>skiing</strong></br>0.003</td>
      </tr>
      <tr>
        <td>Track and Field</br>0.208147</td>
        <td><strong>track</strong></br>0.035</td>
      </tr>
    </table>

- **Prise en charge du français**

    Les méthodes **Classify** prennent désormais en charge le français dans la sortie des classes du modèle `default`. Pour obtenir la liste complète des langues, voir [Langues prises en charge](/docs/services/visual-recognition?topic=visual-recognition-supported-languages#supported-languages).

### 23 février 2018
{: #23february2018}

- **Modèle Face amélioré disponible en version bêta**

    Un modèle mis à jour de détection des visages est disponible. Ce modèle bêta utilise des ensembles de données d'apprentissage plus grands pour une précision accrue de la détection faciale pour l'âge et le sexe. Pour plus d'informations, voir [Increasing the Accuracy of IBM’s Watson {{site.data.keyword.visualrecognitionshort}} service ![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](https://www.ibm.com/blogs/watson/2018/02/increasing-accuracy-ibms-watson-visual-recognition-service/){: new_window} et [Mitigating Bias in AI Models ![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](https://www.ibm.com/blogs/research/2018/02/mitigating-bias-ai-models/){: new_window}.

    - Vous pouvez afficher les résultats du modèle mis à jour dans la [démonstration ![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](https://www.ibm.com/watson/services/visual-recognition/demo){: new_window} et l'outil [Visual Recognition Tool ![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](https://watson-visual-recognition.ng.bluemix.net/){: new_window}.
    - Le modèle bêta est disponible sur `/v3/detect_faces_beta`.

    Différences entre les modèles en version bêta et en disponibilité générale (GA) :
    - Le modèle bêta prend en charge les formats d'image .gif et .tif. Il est prévu d'appliquer cette amélioration au modèle GA. 
    - Le modèle bêta prend en charge des tailles de fichier plus importantes : jusqu'à 10 Mo pour des fichiers image et 100 Mo pour des fichiers .zip. Il est prévu d'appliquer cette amélioration au modèle GA. 
    - La informations des visages en version bêta n'inclut pas d'informations `FaceIdentity` dans la réponse. 
    - La demande POST du modèle bêta requiert que le nom de fichier soit spécifié. Le modèle Face GA n'applique pas cette contrainte.
    - La demande POST du modèle bêta prend en charge un paramètre de formulaire distinct, appelé `url`. Le modèle GA place ces informations dans l'objet JSON `parameters`. Pour des détails, voir [API explorer ![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](https://watson-api-explorer.mybluemix){: new_window}.

- **Identité des visages dépréciée**

    Les informations d'identité dans la réponse du modèle Face GA sont dépréciées et seront retirées de l'API le **2 avril 2018**. Les informations d'identité font référence au `name` (nom) de la personne, au `score` et au graphique de connaissances `type_hierarchy` (hiérarchie de types).

### 16 janvier 2018
{: #16january2018}

- **Plan et compte Lite remplacent le plan Free**

    Un compte Lite est gratuit, aucune carte de crédit n'est requise. Toutefois, les instances de service du plan Lite sont supprimées après 30 jours. 

    Le nombre maximal d'appels API que vous pouvez effectuer avec le plan Lite est légèrement différent de celui du plan Free. Vous pouvez effectuer jusqu'à 7 500 appels API par mois, à raison de 250 appels par jour pour le plan Lite. 

    Pour effectuer une mise à jour vers un compte facturable lorsque vous possédez des discriminants personnalisés, créez une autre instance de service puis recréez vos discriminants personnalisés. 

### 11 décembre 2017
{: #11december2017}

<ul>
  <li>
    <strong>Précision accrue et sortie avec le modèle General</strong>
      <p>
        Le modèle General, qui contient des milliers de libellés, détecte désormais un plus grand nombre d'objets secondaires et offre une détection de scène optimisée. Ces améliorations permettent de reconnaître les aspects les moins proéminents d'une image. De plus, le nombre moyen de libellés retournées par image est monté à 10.
      </p>
      <p>
        L'image suivante montre un exemple de libellés renvoyés avant la mise à jour et des libellés supplémentaires qui sont maintenant renvoyés.
      </p>
      <img src="images/tree-flower.jpg" alt="Photographie d'un azalée">
      <table>
        <tr>
          <th>Libellés d'origine</th>
          <th>Libellés supplémentaires</th>
        </tr>
        <tr>
          <td></td>
          <td>
          Tag: tree<br/>
          Score: 0.799</td>
        </tr>
        <tr>
          <td></td>
          <td>
          Tag: flower<br/>
          Score: 0.792</td>
        </tr>
        <tr>
          <td>
          Tag: alpine azalea<br/>
          Score: 0.696</td>
          <td></td>
        </tr>
        <tr>
          <td>
          Tag: plant<br/>
          Score: 0.868</td>
          <td></td>
        </tr>
        <tr>
          <td>
          Tag: azalea<br/>
          Score: 0.617</td>
          <td></td>
        </tr>
        <tr>
          <td>
            Tag: swamp azalea<br/>
          Score: 0.5</td>
          </td>
          <td></td>
        <tr>
          <td>
            Tag: reddish orange color<br/>
          Score: 0.1</td>
          </td>
          <td></td>
        </tr>
      </table>
    <li>
      <strong>Nouveau modèle, Explicit, disponible dans la version bêta</strong>
      <p>
        Le modèle Explicit, lancé dans la bêta, classifie les images en indiquant si elles contiennent un contenu à caractère pornographique et sont donc inadaptées à une utilisation générale. Vous pouvez associer le modèle Explicit à d'autres modèles pour une analyse combinée. Ainsi, incluez à la fois les ID de discriminant `default` et `explicit` dans votre demande pour retourner les libellés d'une image et savoir si l'image contient un contenu explicite.
      <p>
        Pour des détails sur l'appel d'API, voir la méthode **Classify images** dans [API reference ![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](https://{DomainName}/apidocs/visual-recognition/#classify-images).
      </p>
    </li>
    <li>
      <strong>Prise en charge de fichiers de plus grande taille</strong>
      <p>
        Les méthodes <strong>Classify images</strong> prennent désormais en charge des fichiers image jusqu'à 10 Mo et des fichiers .zip jusqu'à 100 Mo.
    </li>
    <li>
      <strong>Tableau requis lors du transfert d'un ID de discriminant</strong>
      <p>
        L'API impose désormais un tableau quand vous transférez les paramètres `classifier_ids` en tant qu'élément de l'objet **parameters** dans la méthode **Classify images**. Auparavant, vous pouviez passer un ID de discriminant sous forme de chaîne. Pour plus d'informations, voir la description de parameters et un fichier exemple dans [API Reference ![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](https://{DomainName}/apidocs/visual-recognition/#classify-images).
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

    Pour plus détails sur l'appel API, voir la méthode **Classify images** dans [API Reference ![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](https://{DomainName}/apidocs/visual-recognition/#classify-images){: new_window}.

### 16 mai 2017
{: #16may2017}

- **Un nouveau discriminant food est disponible : bêta**

    Un nouveau modèle bêta de reconnaissance de tout ce qui est lié à la nourriture fournit de meilleures spécificités et une précision plus grande dans la reconnaissance des images liées à ce domaine. La méthode **Classify images** vous permet d'ajouter ce nouveau discriminant, "food", au paramètre `classifier_ids`.

### 5 avril 2017
{: #5april2017}

- **Un nouvel outil {{site.data.keyword.visualrecognitionshort}} est disponible : bêta**

    Une nouvelle fonction bêta, l'outil {{site.data.keyword.visualrecognitionshort}}, est disponible sur [https://watson-visual-recognition.ng.bluemix.net/ ![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](https://watson-visual-recognition.ng.bluemix.net/){: new_window}. Il vous permet d'utiliser plus facilement le service {{site.data.keyword.visualrecognitionshort}}. En entrant votre clé d'API {{site.data.keyword.cloud_notm}}, vous pouvez vous servir d'une interface utilisateur graphique pour accéder aux fonctions d'étiquetage général et de détection de visage, et facilement créer, effectuer un réapprentissage ou supprimer des discriminants personnalisés associés à votre clé d'API, sans qu'aucun codage ne soit nécessaire.

### 8 mars 2017
{: #8march2017}

- **Mise à jour de la prise en charge des langues pour l'étiquetage du discriminant General**

    Le discriminant General renvoie maintenant des libellés dans toutes les langues prises en charge.

- **Problèmes connus**

    **CORRIGE le 13/04/2017** : des appels répétés de `GET /classifiers` pour vérifier le statut alors qu'un apprentissage ou un réapprentissage est en cours peuvent provoquer l'arrêt de la tâche d'apprentissage. Pour contourner ce problème, demandez le statut d'un nouveau discriminant en utilisant `GET /classifiers/{classifier_id}`. En d'autres termes, utilisez le discriminant `GET` pour un ID de discriminant unique plutôt que `GET /classifiers`, qui porte sur tous les discriminants, ce qui risque de provoquer le problème évoqué plus haut. Sachez aussi que `GET /classifiers/{classifier_id}` est également plus rapide.

### 15 décembre 2016
{: #15december2016}

- **Amélioration de l'étiquetage du discriminant General**

    - Les algorithmes d'apprentissage en profondeur du discriminant General ont été mis à jour. La qualité des libellés pour toutes les langues a été considérablement améliorée et le volume des libellés renvoyés en anglais par le service a augmenté de façon significative. Cette sortie de libellés de haute qualité est aussi disponible quand vous créez votre propre discriminant personnalisé.
    - Une fonction d'étiquetage utilisant la couleur a été ajoutée. Le service repère désormais par des couleurs la valeur la plus haute (ou les deux premières).

- **Problèmes connus**

    - Les images soumises pour démonstration avec des libellés de métadonnées EXIF ne spécifient pas correctement l'orientation (paysage ou portrait) dans le service. Les images iPhone téléchargées peuvent contenir des libellés de métadonnées EXIF. La solution pour contourner ce problème est de mettre à jour vos métadonnées afin qu'elles ne se fient pas aux libellés EXIF pour spécifier l'orientation de votre image. Souvent, cette opération peut s'effectuer simplement en ouvrant l'image sur votre ordinateur puis en la sauvegardant. Ainsi, sur un Mac, une ouverture des ensembles d'images dans l'aperçu, suivie d'une sauvegarde, suffit à définir des libellés d'orientation correctes.
    - L'envoi d'images vers le service {{site.data.keyword.visualrecognitionshort}} avec des valeurs de [libellé EXIF![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](https://en.wikipedia.org/wiki/Exif){: new_window} risque d'augmenter le temps de latence. Le service fait pivoter les pixels de l'image dans le point de vue codé. Vous pouvez gagner du temps en procédant à une pré-rotation de vos images, ou en retirant les en-têtes EXIF s'ils ne sont pas importants pour votre tâche {{site.data.keyword.visualrecognitionshort}}.

### 1er décembre 2016
{: #1december2016}

- **Nouvelle tarification**

    {{site.data.keyword.IBM_notm}} a réduit le prix des discriminants personnalisés sur le service {{site.data.keyword.visualrecognitionshort}} et augmenté le nombre d'éléments disponibles sur le plan gratuit. Pour plus d'informations, voir la page Pricing [{{site.data.keyword.visualrecognitionshort}}](http://www.ibm.com/watson/developercloud/visual-recognition.html#pricing-block).

### 7 octobre 2016
{: #7october2016}

- **Améliorations au niveau de la détection des visages**

    Le service dispose d'un nouvel algorithme de détection des visages qui améliore les réponses des méthodes `GET` et `POST /v3/detect_faces`. Le filtrage des détections faciales d'âge, de nom et de sexe dont l'indice de fiabilité est bas a été ajusté. En résultat, un plus grand nombre de visages sont détectés, avec des plages de fiabilité plus importantes.

### 8 septembre 2016
{: #8september2016}

- **Bêta Similarity Search**

    Les utilisateurs peuvent maintenant télécharger leur propre collection d'images, utiliser une image pour rechercher des images similaires dans cette collection, et le service retourne les 100 premières images les plus similaires. Similarity Search peut être utilisé pour divers objectifs et les utilisateurs ont la possibilité d'entraîner le service sur des collections pouvant aller jusqu'à 1 million d'images chacune. Pour plus d'informations sur l'utilisation de la nouvelle fonctionnalité Similarity Search, voir les pages [Tutorial](/docs/services/visual-recognition/tutorial-collections.html) et [API Reference ![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](https://www.ibm.com/watson/developercloud/visual-recognition/api/v3/#collections){: new_window}.

- **La version bêta de la reconnaissance de texte est fermée**

    Les méthodes `POST` et `GET /v3/recognize_text` sont en version bêta fermée. Les clients BETA utilisant ce service sont toujours pris en charge par {{site.data.keyword.IBM_notm}}, et aucun plan n'est actuellement prévu pour l'ouverture d'une autre version bêta.

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
- **Détection des visages : ** utilisez les méthodes `POST` ou `GET /v3/detect_faces` pour détecter des visages dans des images et obtenir des informations à leur sujet, comme l'emplacement du visage sur l'image ainsi qu'une estimation de la plage d'âge et du sexe de chaque personne dont le visage est représenté. Le service est également capable d'identifier par leur nom de nombreuses célébrités et de fournir une base de connaissance Knowledge Graph de façon à vous permettre d'effectuer des agrégations intéressantes dans des concepts de niveau supérieur.
- **Discriminants personnalisés multi-facettes :** vous pouvez maintenant créer et entraîner des discriminants hautement spécialisés qui sont définis par plusieurs classes. Ainsi, vous pouvez créer un discriminant "new\_red\_car" qui est défini par les classes "new\_cars" et and "red\_cars". Pour en savoir plus sur la création de discriminants multi-facettes, voir [Structure des données d'apprentissage](/docs/services/visual-recognition?topic=visual-recognition-customizing#structure).
- **Apprentissage asynchrone : ** l'apprentissage des discriminants personnalisés est maintenant une procédure asynchrone, ce qui fait que les appels d'apprentissage s'exécutent rapidement pendant que votre discriminant personnalisé continue d'apprendre en arrière-plan. Pour vérifier le statut d'apprentissage de votre discriminant personnalisé et savoir quand il est disponible pour utilisation, appelez la méthode `GET /v3/classifiers/{classifier_id}` et vérifiez le paramètre de réponse `status`.

### 2 décembre 2015
{: #2december2015}

La nouvelle édition du service {{site.data.keyword.visualrecognitionshort}} constitue une modification avec rupture qui introduit une nouvelle version de l'API {{site.data.keyword.visualrecognitionshort}} API (v2). La version 1 du service {{site.data.keyword.visualrecognitionshort}} est disponible pour utilisation jusqu'à ce que le service quitte la version bêta.

Pour commencer immédiatement à utiliser la version 2 de l'API, vous devez comprendre et mettre à jour votre code pour refléter ces changements :

- Dans la version 1 du service, vous analysiez les images par libellés. Dans la version 2 du service, les libellés sont appelés **discriminants**. Les discriminants ont un ID de discriminant unique indiqué par le paramètre `classifier_id` et un nom abrégé indiqué par le paramètre `name`.
- La méthode `POST /v1/recognize` pour analyser une image est désormais [`POST /v2/classify` ![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](https://www.ibm.com/watson/developercloud/visual-recognition/api/v2/#classify_an_image){: new_window}. Le paramètre `labels_to_check` s'appelle maintenant `classifier_ids`.
- La méthode `GET /v1/tag/labels` d'extraction d'une liste de libellés dans V1 est devenue la méthode d'extraction d'une liste de discriminants, [`GET /v2/classifiers` ![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](https://www.ibm.com/watson/developercloud/visual-recognition/api/v2/#retrieve_a_list_of_classifiers){: new_window}.
- En plus de l'extraction d'une liste de discriminants, vous pouvez aussi extraire les détails d'un discriminant spécifique avec la nouvelle méthode [`GET /v2/classifiers/{classifier_id}` ![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](https://www.ibm.com/watson/developercloud/visual-recognition/api/v2/#retrieve_classifier_details){: new_window}.
- La version 2 de l'API {{site.data.keyword.visualrecognitionshort}} bêta vous permet de créer des discriminants personnalisés avec la nouvelle méthode [`POST /v2/classifiers` ![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](https://www.ibm.com/watson/developercloud/visual-recognition/api/v2/#create_a_classifier){: new_window}. Pour en savoir plus sur la création de discriminants personnalisés, voir [Creating custom classifiers](/docs/services/visual-recognition?topic=visual-recognition-tutorial-custom-classifier#tutorial-custom-classifier).
- La version 2 de l'API {{site.data.keyword.visualrecognitionshort}} bêta vous permet aussi de supprimer des discriminants personnalisés avec la nouvelle méthode [`DELETE /v2/classifiers` ![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](https://www.ibm.com/watson/developercloud/visual-recognition/api/v2/#delete_a_classifier){: new_window}.
- La version 2 de l'API {{site.data.keyword.visualrecognitionshort}} bêta requiert le paramètre `version`. Spécifiez la date d'édition de la version de l'API que vous voulez utiliser au format `MM-DD-YYYY`.
