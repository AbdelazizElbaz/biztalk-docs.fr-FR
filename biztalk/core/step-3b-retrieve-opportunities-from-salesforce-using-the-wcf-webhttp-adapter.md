---
title: "Étape 3 b : récupérer les détails d’opportunité de Salesforce à l’aide de l’adaptateur WCF-WebHttp | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 115c908f-777b-4c51-85ea-71d639b01775
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 05312890d7cd21810651e7e41a8418080912f72f
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="step-3b-retrieve-opportunity-details-from-salesforce-using-the-wcf-webhttp-adapter"></a>Étape 3 b : récupérer les détails d’opportunité de Salesforce à l’aide de l’adaptateur WCF-WebHttp
Dans cette section, nous allons améliorer l'orchestration pour traiter la notification d'opportunité entrante, extraire le nom d'opportunité à partir de la notification et utiliser cette information pour créer une requête à la demande à envoyer à Salesforce. Cela extrait des détails spécifiques sur les produits associés à l'opportunité. La réponse à la requête de Salesforce est reçue en retour dans [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]. Pour ce faire, nous allons effectuer les étapes suivantes :  
  
-   Créer un schéma et des variables de message pour envoyer un message de requête à Salesforce.  
  
-   Créer un mappage pour utiliser les valeurs de notification de l'opportunité pour créer une requête afin de récupérer des détails sur le produit associé à l'opportunité.  
  
-   Créer un schéma pour recevoir une réponse à la requête de Salesforce.  
  
-   Créer des variables de message pour les schémas associés aux requêtes et aux réponses.  
  
## <a name="create-schema-and-message-variables-to-send-query-messages-to-salesforce"></a>Créer un schéma et des variables de message pour envoyer des messages de requête à Salesforce  
 Pour extraire des détails sur le produit à partir de Salesforce en utilisant les informations disponibles par le biais d'une notification d'opportunité, nous devons envoyer une requête à Salesforce. La requête est envoyée à Salesforce sous forme de message XML. Ainsi, dans la procédure suivante, nous créons un schéma pour le message de requête. Dans la procédure suivante, nous allons mapper le schéma de notification d'opportunité avec ce schéma pour construire une requête afin de récupérer des détails sur le produit de l'opportunité.  
  
#### <a name="to-create-a-schema-for-sending-query-request"></a>Pour créer un schéma destiné à l'envoi d'une demande de requête  
  
1.  Ajoutez un nouveau schéma au projet [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]. Nommez-le `QueryRequest.xsd`.  
  
2.  Renommez le nœud racine à `QueryRequest`. Ajoutez un élément de champ enfant sous l’enregistrement QueryRequest et nommez-le `Query`.  
  
3.  Promouvoir le **requête** élément dans le schéma afin qu’il soit disponible pour utilisation dans l’orchestration. Dans les étapes ultérieures, nous allons utiliser cet élément promu pour affecter la chaîne de requête.  
  
     Cliquez sur le **requête** élément, pointez sur **promouvoir**, puis cliquez sur **Promotions rapides**. Cela entraîne la création d’un **PropertySchema.xsd** schéma avec un **requête** élément. Notez l'espace de noms pour PropertySchema. Vous en aurez besoin dans les étapes à venir lors de la configuration des ports physiques dans la console d'administration de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].  
  
4.  Enregistrez toutes les modifications effectuées.  
  
## <a name="map-the-opportunity-notification-schema-to-the-query-schema"></a>Mapper le schéma de notification d'opportunité au schéma de requête  
 Pour récupérer les détails sur le produit associés à l'opportunité, nous devons envoyer à Salesforce une requête similaire à la suivante :  
  
```  
SELECT Amount, Id, Name,(SELECT Quantity, ListPrice, PricebookEntry.UnitPrice, PricebookEntry.Name FROM OpportunityLineItems) FROM Opportunity Where Name = '<opportunity_name>'  
```  
  
 Dans la procédure précédente, nous avons déjà créé le schéma du message de requête. Dans cette procédure, nous mappons le schéma de notification de l'opportunité au schéma de demande de la requête et utilisons des fonctoids pour construire cette requête. Cette requête est passée en tant que valeur pour le **requête** élément dans le **QueryRequest.xsd** schéma.  
  
#### <a name="to-map-the-opportunity-notification"></a>Pour mapper la notification d'opportunité  
  
1.  Ajoutez un mappage au projet [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]. Nommez la carte `Notification_QueryRequest.btm`.  
  
2.  Définissez le schéma source **NotificationService_soap_sforce_com_2005_09_outbound.xsd**. Définissez le schéma de destination sur **QueryRequest**.xsd.  
  
3.  Ajouter un **concaténation de chaînes** fonctoid à la surface de mappage. Ouvrez le **fonctoid concaténation de chaînes configurer** boîte de dialogue zone, puis spécifiez les valeurs d’entrée comme suit :  
  
    |||  
    |-|-|  
    |Input[0]|SELECT Amount, Id, Name,(SELECT Quantity, ListPrice, PricebookEntry.UnitPrice, PricebookEntry.Name FROM OpportunityLineItems) FROM Opportunity Where Name = '|  
    |Input [1]|Connectez l'élément Name dans le schéma source au fonctoid pour utiliser la valeur de l'élément Name comme deuxième entrée.|  
    |Entrée [2]|' **Remarque :** pour la dernière valeur d’entrée, spécifiez uniquement un guillemet fermant (').|  
  
     La capture d’écran suivante illustre la configuration pour le **concaténation de chaînes** fonctoid.  
  
     ![Configurer le fonctoid concaténation de chaînes](../core/media/bts-sf-stringconcatenate.jpg "BTS_SF_StringConcatenate")  
  
     Lorsque les trois paramètres d'entrée sont concaténés, ils forment la requête nécessaire qui doit être envoyée à Salesforce.  
  
4.  Connectez le fonctoid Concaténation de chaînes à l'élément Query dans le schéma de destination, comme le montre la capture d'écran ci-dessous.  
  
     ![Mapper une réponse de notification pour interroger un schéma](../core/media/bts-sf-notification-query-mapping.jpg "BTS_SF_Notification_Query_Mapping")  
  
5.  Enregistrez les modifications apportées au mappage.  
  
## <a name="creating-schema-to-receive-the-query-response-message"></a>Création de schéma pour recevoir le message de réponse à la requête  
 Dans cette section, nous créons le schéma pour recevoir le message de réponse à la requête de Salesforce. Dans cette section, nous créons manuellement le schéma de réponse à la requête.  
  
#### <a name="to-create-a-schema-to-receive-the-query-response"></a>Pour créer un schéma afin de recevoir la réponse à la requête  
  
1.  Ajoutez un nouveau schéma à la [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] de projet et nommez-le `QueryResult.xsd`.  
  
2.  La force de vente [QueryResult](http://go.microsoft.com/fwlink/?LinkId=287017) objet représente la réponse à la requête reçue de Salesforce. Ainsi, nous allons construire un schéma pour illustrer ce qui suit :  
  
    ```  
    <?xml version="1.0" encoding="utf-16" ?>  
    - <xs:schema xmlns="http://BtsSalesforceIntegration.QueryResult" xmlns:b="http://schemas.microsoft.com/BizTalk/2003" targetNamespace="http://BtsSalesforceIntegration.QueryResult" xmlns:xs="http://www.w3.org/2001/XMLSchema">  
      - <xs:element name="QueryResult">  
        - <xs:complexType>  
          - <xs:sequence>  
            <xs:element name="done" type="xs:string" />  
            - <xs:sequence>  
              - <xs:element name="records">  
                - <xs:complexType>  
                  - <xs:sequence>  
                    <xs:element name="Id" type="xs:string" />  
                    <xs:element name="Amount" type="xs:string" />  
                    <xs:element name="Name" type="xs:string" />  
                    - <xs:sequence>  
                      - <xs:element name="OpportunityLineItems">  
                        - <xs:complexType>  
                          - <xs:sequence>  
                            <xs:element name="done" type="xs:string" />  
                            - <xs:sequence minOccurs="1" maxOccurs="unbounded">  
                              - <xs:element name="records">  
                                - <xs:complexType>  
                                  - <xs:sequence>  
                                    <xs:element name="Quantity" type="xs:string" />  
                                    <xs:element name="ListPrice" type="xs:string" />  
                                    - <xs:element name="PricebookEntry">  
                                      - <xs:complexType>  
                                        - <xs:sequence>  
                                          <xs:element name="UnitPrice" type="xs:string" />  
                                          <xs:element name="Name" type="xs:string" />  
                                        </xs:sequence>  
                                        <xs:attribute name="type" type="xs:string" />  
                                        <xs:attribute name="url" type="xs:string" />  
                                      </xs:complexType>  
                                    </xs:element>  
                                  </xs:sequence>  
                                  <xs:attribute name="type" type="xs:string" />  
                                  <xs:attribute name="url" type="xs:string" />  
                                </xs:complexType>  
                              </xs:element>  
                            </xs:sequence>  
                            <xs:element name="totalSize" type="xs:string" />  
                          </xs:sequence>  
                        </xs:complexType>  
                      </xs:element>  
                    </xs:sequence>  
                  </xs:sequence>  
                  <xs:attribute name="type" type="xs:string" />  
                  <xs:attribute name="url" type="xs:string" />  
                </xs:complexType>  
              </xs:element>  
            </xs:sequence>  
            <xs:element name="totalSize" type="xs:string" />  
          </xs:sequence>  
        </xs:complexType>  
      </xs:element>  
    </xs:schema>  
    ```  
  
     La structure de votre schéma doit présenter l'aspect suivant :  
  
     ![Schéma pour la réponse à la requête de Salesforce](../core/media/bts-sf-queryresult.jpg "BTS_SF_QueryResult")  
  
3.  Enregistrez les modifications apportées au schéma.  
  
## <a name="create-message-variables-for-queryrequest-and-queryresult-schemas"></a>Créer des variables de message pour les schémas QueryRequest et QueryResult  
 Après avoir créé les schémas QueryRequest et QueryResult, vous devez créer deux variables de message dans l'orchestration pour représenter les deux types de message.  
  
#### <a name="to-create-message-variables"></a>Pour créer des variables de message  
  
1.  Ouvrez le **NotificationService.odx** orchestration dans la vue orchestration, ajoutez deux nouveaux messages. Définir les noms de message `QueryRequestMsg` et `QueryResultMsg`.  
  
2.  Définir le type de message pour **QueryRequestMsg** en tant que **BtsSalesforceIntegration.QueryRequest**.  
  
3.  Définir le type de message pour **QueryResultMsg** en tant que **BtsSalesforceIntegration.QueryResult**.  
  
4.  Enregistrez les modifications apportées à l'orchestration.  
  
## <a name="update-the-orchestration-to-send-message-to-salesforce-and-receive-a-response"></a>Mettre à jour l'orchestration pour envoyer le message à Salesforce et recevoir une réponse  
 Dans la rubrique [étape 3 a : réception des notifications d’opportunité de Salesforce dans BizTalk Server](../core/step-3a-receive-salesforce-opportunity-notification-into-biztalk-server.md), nous avons créé l’orchestration qui reçoit des notifications d’opportunité de Salesforce et envoie un accusé de réception. Dans cette étape, nous nous appuyons sur cette orchestration pour envoyer une requête à la demande à Salesforce pour obtenir des détails sur le produit liés à l'opportunité et recevoir une réponse. Nous avons déjà créé des schémas (QueryRequest.xsd et QueryResult.xsd) et les variables de message (QueryRequestMsg et QueryResultMsg) que nous allons utiliser dans cette étape.  
  
#### <a name="to-send-a-query-request-to-salesforce-and-receive-a-response"></a>Pour envoyer une demande de requête à Salesforce et recevoir une réponse  
  
1.  Ajoutez une forme construire un Message après le **SendNotificationAck** forme. Définissez le nom de la forme à `ConstructQuery` et définir le **Messages construits** propriété **QueryRequestMsg**.  
  
2.  Dans le **ConstructQuery** mettre en forme, ajouter un **transformer** forme. Double-cliquez sur la forme Transformer pour ouvrir la boîte de dialogue Configuration de la forme Transformer. Dans la boîte de dialogue, sélectionnez le **mappage existant** option, puis, dans la liste déroulante, sélectionnez **BtsSalesforceIntegration.Notification_QueryRequest**. Définissez **Source** à **NotificaitonMessage**, **Destination** à **QueryRequestMsg**, puis cliquez sur **OK**.  
  
3.  Dans le **ConstructQuery** mettre en forme après la forme Transformer, ajoutez une forme assignation du Message. Double-cliquez sur la forme Assignation du message et ajoutez l'expression suivante :  
  
    ```  
    QueryRequestMsg(BtsSalesforceIntegration.PropertySchema.Query) = QueryRequestMsg.Query;  
    ```  
  
     Ce faisant, nous transmettons la valeur de la **requête** élément dans le **QueryRequestMsg** schéma à l’élément promu **requête** dans le schéma de propriété. Lors de la configuration du port WCF-WebHttp, nous allons utiliser cet élément pour passer dynamiquement ​​la valeur de requête au message de la demande.  
  
4.  Après le **ConstructQuery** mettre en forme, ajoutez une forme envoi. Nommez la forme `SendQueryRequest` et définissez le type de message **QueryRequestMsg**.  
  
5.  Après la forme envoi, ajoutez une forme réception et nommez-le `ReceiveQueryResult`. Définir le type de message de la forme à **QueryResultMsg**.  
  
6.  Ajoutez un port pour envoyer des demandes de requête à Salesforce et recevoir le résultat de la requête en réponse. Dans l'assistant Configuration du port, sélectionnez les options suivantes :  
  
    -   Spécifiez le nom de port `SalesforceRESTInterface`.  
  
    -   Sélectionnez l'option pour créer un nouveau type de port.  
  
    -   Définissez **modèle de Communication** à *demande-réponse*.  
  
    -   Définir **direction de communication du Port** à *puis-je envoyer une demande et recevoir une réponse* et **liaison de Port** à *spécifierultérieure*.  
  
     Connecter le **demande** opération du port à la forme envoi (*SendQueryRequest*) et le **réponse** opération du port sur la forme réception ( *ReceiveQueryResult*). La capture d'écran ci-dessous illustre la partie de l'orchestration qui représente le processus d'envoi de la demande de requête à Salesforce et la réception d'une réponse.  
  
     ![Envoyer une requête à Salesforce et recevoir la réponse](../core/media/bts-sf-sendqueryrequestorch.jpg "BTS_SF_SendQueryRequestOrch")  
  
 Dans cette rubrique, nous avons mis à jour l'orchestration pour envoyer une demande de requête à Salesforce et recevoir plus de détails (comme les produits, la quantité, etc) sur l'opportunité qui est créée dans Salesforce. Dans les rubriques suivantes, nous mettrons à jour cette solution pour entrer la réponse de Salesforce dans une base de données SQL Server sur site.  
  
## <a name="see-also"></a>Voir aussi  
 [Étape 3 : Créer la Solution BizTalk Server dans Visual Studio](../core/step-3-create-the-biztalk-server-solution-in-visual-studio.md)