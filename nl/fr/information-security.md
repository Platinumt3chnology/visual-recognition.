---

copyright:
  years: 2015, 2019
lastupdated: "2019-03-06"

keywords: GDPR,General Data Protection Regulation,deleting customer data,privacy

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

# Sécurité de l'information
{: #information-security}

IBM se donne pour mission de fournir à ses clients et partenaires des solutions innovantes de confidentialité, de sécurité et de gouvernance des données.
{: shortdesc}

**Remarque :**
Il appartient à chaque entreprise de se conformer aux lois et réglementations, notamment relatives à la protection des données personnelles. Il relève de la seule responsabilité du client de consulter les services juridiques compétents aussi bien pour identifier et interpréter les lois et règlements susceptibles d’affecter son activité, que pour toute action à entreprendre pour se mettre en conformité avec ces lois et réglementations.

Les produits, services et autres fonctionnalités décrits ici ne sont pas adaptés à toutes les situations client et ne pourront être proposés que sous réserve de disponibilité. IBM ne fournit ni audit ni conseil juridique, ni déclaration, ni garantie que ses services ou produits assurent au client d’être en conformité avec la loi. Si vous avez besoin d'une assistance RGPD pour les ressources {{site.data.keyword.cloud}} {{site.data.keyword.watson}} qui sont créées

- Pays de l'Union européenne : voir [Demande de support pour des ressources IBM Cloud Watson créées dans l'Union européenne](/docs/services/watson?topic=watson-gdpr-sar#request-EU).
- Pays hors Union européenne : voir [Demande de support pour des ressources hors Union européenne](/docs/services/watson?topic=watson-gdpr-sar#request-non-EU).

## Règlement général sur la protection des données (RGPD) de l'Union Européenne
{: #gdpr}

IBM se donne pour mission de fournir à ses clients et partenaires des solutions innovantes de confidentialité, de sécurité et de gouvernance des données pour les accompagner dans leur mise en conformité au RGPD.

Pour en savoir plus sur le parcours préparatoire au RGPD d'IBM ainsi que sur nos session proposées et offres liées au RGPD pour la prise en charge de votre parcours de conformité, cliquez [ici ![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](../../icons/launch-glyph.svg "Icône de lien externe")](http://www.ibm.com/gdpr){: new_window}.

## Etiquetage et suppression de données dans {{site.data.keyword.visualrecognitionshort}}
{: #gdpr-visrec}

### Migration de sécurité conforme au RGPD (règlement général sur la protection des données)
{: #gdpr-visrec-update}

- Toutes les instances de service {{site.data.keyword.visualrecognitionfull}} créées avant le **22 mai 2018** ne conviennent pas aux clients exigeant la conformité au règlement général sur la protection des données (RGPD) de l'Union européenne (EU 2016/679).
- Les clients soumis au RGPD doivent [migrer vers une nouvelle instance de service {{site.data.keyword.visualrecognitionshort}}](/docs/services/visual-recognition?topic=visual-recognition-migrating#migrating) disponible à compter du **22 mai 2018** et accepter le nouveau contrat pour le service {{site.data.keyword.visualrecognitionshort}}.
- Les clients doivent fournir un nouveau service {{site.data.keyword.visualrecognitionshort}} et générer de *nouvelles clés d'authentification* afin d'utiliser le nouveau service {{site.data.keyword.visualrecognitionshort}}.
- Si un client ne fournit pas de nouveau service {{site.data.keyword.visualrecognitionshort}}, vous devez confirmer qu'IBM ne traite aucune donnée à caractère personnel pour le compte du client qui entre dans le cadre du RGPD.
- Les données des clients qui ne seront pas passés au nouveau service {{site.data.keyword.visualrecognitionshort}} entre le 22 mai et le 1er octobre 2018 seront supprimées.

### Etiquetage des données

Si vous devez retirer les données d'un client individuel d'une instance de service {{site.data.keyword.visualrecognitionshort}} comportant plusieurs clients, vous devez d'abord associer ces données à un client ID unique pour chaque individu qui pourrait avoir fourni des données.

Pour spécifier l'ID client de données envoyées avec la méthode **Create a classifier**, incluez la propriété **X-Watson-Metadata: customer_id** dans l'en-tête de demande. L'exemple suivant associe l'ID client `my_ID` à une demande : 

```bash
curl -X POST \
--header "X-Watson-Metadata: customer_id=my_ID" \
--form "apple_positive_examples=@apples.zip" \
"https://gateway.watsonplatform.net/visual-recognition/api/v3/classifiers?version=2018-03-19"
```
{: pre}

Les caractères multi-octet sont pris en charge pour la chaîne d'ID client. Les caractères doivent être codés dans l'URL, que ce soit dans l'en-tête lors de l'apprentissage, ou dans le paramètre de requête lors de la suppression. L'ID peut comporter des caractères alphanumériques et des traits de soulignement (``_``). Les caractères suivants ne sont pas pris en charge : ``\ | * { } $ - [ ] / ' ` " ~ ? ; < > ( ) ! & = % # ^ @ : . , + espace``.

Vous êtes responsable de la création des valeurs d'ID client et devez vous assurer qu'elles sont uniques.
{: important}

### Suppression de données libellées

Pour supprimer toutes les données associées à un ID client, utilisez la méthode de **suppression des données libellées**. Vous transmettez la chaîne `customer_id={id}` en tant que paramètre de requête avec la demande. L'exemple suivant supprime toutes les données de l'ID client `my_ID` :

```bash
curl -X DELETE -u "apikey:{apikey}" \
"https://gateway.watsonplatform.net/visual-recognition/api/v3/user_data?customer_id=my_ID&version=2018-03-19"
```
{: pre}

La méthode **Delete labeled data** supprime toutes les données associées à l'ID client spécifié, quelle que soit la méthode utilisée pour ajouter ces informations. La méthode est sans effet si aucune donnée n'est associée à l'ID client. 

Les demandes de suppression sont traitées par lots et leur exécution peut prendre jusqu'à 24 heures.
{: tip}

### Support
{: #gdpr-visrec-support}

Adressez vos questions à votre représentant de compte, ou contactez directement le support à l'adresse [https://ibm.biz/ibmcloudsupport ![Icône de lien externe](../../icons/launch-glyph.svg "Icône de lien externe")](https://ibm.biz/ibmcloudsupport){: new_window}.
