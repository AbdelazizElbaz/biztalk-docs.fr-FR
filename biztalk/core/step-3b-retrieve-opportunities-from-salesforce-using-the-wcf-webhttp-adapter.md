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
# <a name="step-3b-retrieve-opportunity-details-from-salesforce-using-the-wcf-webhttp-adapter"></a><span data-ttu-id="c74a5-102">Étape 3 b : récupérer les détails d’opportunité de Salesforce à l’aide de l’adaptateur WCF-WebHttp</span><span class="sxs-lookup"><span data-stu-id="c74a5-102">Step 3b: Retrieve Opportunity Details from Salesforce using the WCF-WebHttp Adapter</span></span>
<span data-ttu-id="c74a5-103">Dans cette section, nous allons améliorer l'orchestration pour traiter la notification d'opportunité entrante, extraire le nom d'opportunité à partir de la notification et utiliser cette information pour créer une requête à la demande à envoyer à Salesforce.</span><span class="sxs-lookup"><span data-stu-id="c74a5-103">In this section, we’ll enhance the orchestration to process the incoming opportunity notification, extract the opportunity name from the notification, and use that to create a request query to send to Salesforce.</span></span> <span data-ttu-id="c74a5-104">Cela extrait des détails spécifiques sur les produits associés à l'opportunité.</span><span class="sxs-lookup"><span data-stu-id="c74a5-104">This retrieves specific details about the products associated with the opportunity.</span></span> <span data-ttu-id="c74a5-105">La réponse à la requête de Salesforce est reçue en retour dans [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="c74a5-105">The query response from Salesforce is received back into [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].</span></span> <span data-ttu-id="c74a5-106">Pour ce faire, nous allons effectuer les étapes suivantes :</span><span class="sxs-lookup"><span data-stu-id="c74a5-106">To achieve this, we’ll perform the following steps:</span></span>  
  
-   <span data-ttu-id="c74a5-107">Créer un schéma et des variables de message pour envoyer un message de requête à Salesforce.</span><span class="sxs-lookup"><span data-stu-id="c74a5-107">Create a schema and message variables to send a query message to Salesforce.</span></span>  
  
-   <span data-ttu-id="c74a5-108">Créer un mappage pour utiliser les valeurs de notification de l'opportunité pour créer une requête afin de récupérer des détails sur le produit associé à l'opportunité.</span><span class="sxs-lookup"><span data-stu-id="c74a5-108">Create a map to use the values from the opportunity notification for creating a query to retrieve product details associated with the opportunity.</span></span>  
  
-   <span data-ttu-id="c74a5-109">Créer un schéma pour recevoir une réponse à la requête de Salesforce.</span><span class="sxs-lookup"><span data-stu-id="c74a5-109">Create a schema to receive a query response from Salesforce.</span></span>  
  
-   <span data-ttu-id="c74a5-110">Créer des variables de message pour les schémas associés aux requêtes et aux réponses.</span><span class="sxs-lookup"><span data-stu-id="c74a5-110">Create message variables for the request and response schemas.</span></span>  
  
## <a name="create-schema-and-message-variables-to-send-query-messages-to-salesforce"></a><span data-ttu-id="c74a5-111">Créer un schéma et des variables de message pour envoyer des messages de requête à Salesforce</span><span class="sxs-lookup"><span data-stu-id="c74a5-111">Create Schema and Message Variables to Send Query Messages to Salesforce</span></span>  
 <span data-ttu-id="c74a5-112">Pour extraire des détails sur le produit à partir de Salesforce en utilisant les informations disponibles par le biais d'une notification d'opportunité, nous devons envoyer une requête à Salesforce.</span><span class="sxs-lookup"><span data-stu-id="c74a5-112">To retrieve product details from Salesforce by using the information available through an Opportunity notification, we need to send a query to Salesforce.</span></span> <span data-ttu-id="c74a5-113">La requête est envoyée à Salesforce sous forme de message XML.</span><span class="sxs-lookup"><span data-stu-id="c74a5-113">The query is sent to Salesforce as an XML message.</span></span> <span data-ttu-id="c74a5-114">Ainsi, dans la procédure suivante, nous créons un schéma pour le message de requête.</span><span class="sxs-lookup"><span data-stu-id="c74a5-114">So, in the following procedure we create a schema for the request message.</span></span> <span data-ttu-id="c74a5-115">Dans la procédure suivante, nous allons mapper le schéma de notification d'opportunité avec ce schéma pour construire une requête afin de récupérer des détails sur le produit de l'opportunité.</span><span class="sxs-lookup"><span data-stu-id="c74a5-115">In the subsequent procedure, we will map the opportunity notification schema with this schema to construct a query for retrieving product details for the opportunity.</span></span>  
  
#### <a name="to-create-a-schema-for-sending-query-request"></a><span data-ttu-id="c74a5-116">Pour créer un schéma destiné à l'envoi d'une demande de requête</span><span class="sxs-lookup"><span data-stu-id="c74a5-116">To create a schema for sending query request</span></span>  
  
1.  <span data-ttu-id="c74a5-117">Ajoutez un nouveau schéma au projet [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="c74a5-117">Add a new schema to the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] project.</span></span> <span data-ttu-id="c74a5-118">Nommez-le `QueryRequest.xsd`.</span><span class="sxs-lookup"><span data-stu-id="c74a5-118">Name it `QueryRequest.xsd`.</span></span>  
  
2.  <span data-ttu-id="c74a5-119">Renommez le nœud racine à `QueryRequest`.</span><span class="sxs-lookup"><span data-stu-id="c74a5-119">Rename the root node to `QueryRequest`.</span></span> <span data-ttu-id="c74a5-120">Ajoutez un élément de champ enfant sous l’enregistrement QueryRequest et nommez-le `Query`.</span><span class="sxs-lookup"><span data-stu-id="c74a5-120">Add a child field element under the QueryRequest record and name it `Query`.</span></span>  
  
3.  <span data-ttu-id="c74a5-121">Promouvoir le **requête** élément dans le schéma afin qu’il soit disponible pour utilisation dans l’orchestration.</span><span class="sxs-lookup"><span data-stu-id="c74a5-121">Promote the **Query** element in the schema so that it is available for use within the orchestration.</span></span> <span data-ttu-id="c74a5-122">Dans les étapes ultérieures, nous allons utiliser cet élément promu pour affecter la chaîne de requête.</span><span class="sxs-lookup"><span data-stu-id="c74a5-122">In the later steps we will use this promoted element to assign the query string.</span></span>  
  
     <span data-ttu-id="c74a5-123">Cliquez sur le **requête** élément, pointez sur **promouvoir**, puis cliquez sur **Promotions rapides**.</span><span class="sxs-lookup"><span data-stu-id="c74a5-123">Right-click the **Query** element, point to **Promote**, and then click **Quick Promotions**.</span></span> <span data-ttu-id="c74a5-124">Cela entraîne la création d’un **PropertySchema.xsd** schéma avec un **requête** élément.</span><span class="sxs-lookup"><span data-stu-id="c74a5-124">This results in creating a **PropertySchema.xsd** schema with a **Query** element.</span></span> <span data-ttu-id="c74a5-125">Notez l'espace de noms pour PropertySchema.</span><span class="sxs-lookup"><span data-stu-id="c74a5-125">Note the namespace for the PropertySchema.</span></span> <span data-ttu-id="c74a5-126">Vous en aurez besoin dans les étapes à venir lors de la configuration des ports physiques dans la console d'administration de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="c74a5-126">You will need this in the future steps while configuring the physical ports in [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration console.</span></span>  
  
4.  <span data-ttu-id="c74a5-127">Enregistrez toutes les modifications effectuées.</span><span class="sxs-lookup"><span data-stu-id="c74a5-127">Save all changes.</span></span>  
  
## <a name="map-the-opportunity-notification-schema-to-the-query-schema"></a><span data-ttu-id="c74a5-128">Mapper le schéma de notification d'opportunité au schéma de requête</span><span class="sxs-lookup"><span data-stu-id="c74a5-128">Map the Opportunity Notification Schema to the Query Schema</span></span>  
 <span data-ttu-id="c74a5-129">Pour récupérer les détails sur le produit associés à l'opportunité, nous devons envoyer à Salesforce une requête similaire à la suivante :</span><span class="sxs-lookup"><span data-stu-id="c74a5-129">To retrieve the product details associated with the opportunity, we need to send a query similar to the following to Salesforce:</span></span>  
  
```  
SELECT Amount, Id, Name,(SELECT Quantity, ListPrice, PricebookEntry.UnitPrice, PricebookEntry.Name FROM OpportunityLineItems) FROM Opportunity Where Name = '<opportunity_name>'  
```  
  
 <span data-ttu-id="c74a5-130">Dans la procédure précédente, nous avons déjà créé le schéma du message de requête.</span><span class="sxs-lookup"><span data-stu-id="c74a5-130">In the previous procedure we already created the schema of the query message.</span></span> <span data-ttu-id="c74a5-131">Dans cette procédure, nous mappons le schéma de notification de l'opportunité au schéma de demande de la requête et utilisons des fonctoids pour construire cette requête.</span><span class="sxs-lookup"><span data-stu-id="c74a5-131">In this procedure, we map the opportunity notification schema to the query request schema and use functoids to construct this query.</span></span> <span data-ttu-id="c74a5-132">Cette requête est passée en tant que valeur pour le **requête** élément dans le **QueryRequest.xsd** schéma.</span><span class="sxs-lookup"><span data-stu-id="c74a5-132">This query will be passed as a value to the **Query** element in the **QueryRequest.xsd** schema.</span></span>  
  
#### <a name="to-map-the-opportunity-notification"></a><span data-ttu-id="c74a5-133">Pour mapper la notification d'opportunité</span><span class="sxs-lookup"><span data-stu-id="c74a5-133">To map the opportunity notification</span></span>  
  
1.  <span data-ttu-id="c74a5-134">Ajoutez un mappage au projet [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="c74a5-134">Add a map to the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] project.</span></span> <span data-ttu-id="c74a5-135">Nommez la carte `Notification_QueryRequest.btm`.</span><span class="sxs-lookup"><span data-stu-id="c74a5-135">Name the map `Notification_QueryRequest.btm`.</span></span>  
  
2.  <span data-ttu-id="c74a5-136">Définissez le schéma source **NotificationService_soap_sforce_com_2005_09_outbound.xsd**.</span><span class="sxs-lookup"><span data-stu-id="c74a5-136">Set the source schema to **NotificationService_soap_sforce_com_2005_09_outbound.xsd**.</span></span> <span data-ttu-id="c74a5-137">Définissez le schéma de destination sur **QueryRequest**.xsd.</span><span class="sxs-lookup"><span data-stu-id="c74a5-137">Set the destination schema to **QueryRequest**.xsd.</span></span>  
  
3.  <span data-ttu-id="c74a5-138">Ajouter un **concaténation de chaînes** fonctoid à la surface de mappage.</span><span class="sxs-lookup"><span data-stu-id="c74a5-138">Add a **String Concatenate** functoid to the mapping surface.</span></span> <span data-ttu-id="c74a5-139">Ouvrez le **fonctoid concaténation de chaînes configurer** boîte de dialogue zone, puis spécifiez les valeurs d’entrée comme suit :</span><span class="sxs-lookup"><span data-stu-id="c74a5-139">Open the **Configure String Concatenate Functoid** dialog box and specify the input values as follows:</span></span>  
  
    |||  
    |-|-|  
    |<span data-ttu-id="c74a5-140">Input[0]</span><span class="sxs-lookup"><span data-stu-id="c74a5-140">Input[0]</span></span>|<span data-ttu-id="c74a5-141">SELECT Amount, Id, Name,(SELECT Quantity, ListPrice, PricebookEntry.UnitPrice, PricebookEntry.Name FROM OpportunityLineItems) FROM Opportunity Where Name = '</span><span class="sxs-lookup"><span data-stu-id="c74a5-141">SELECT Amount, Id, Name,(SELECT Quantity, ListPrice, PricebookEntry.UnitPrice, PricebookEntry.Name FROM OpportunityLineItems) FROM Opportunity Where Name = '</span></span>|  
    |<span data-ttu-id="c74a5-142">Input [1]</span><span class="sxs-lookup"><span data-stu-id="c74a5-142">Input[1]</span></span>|<span data-ttu-id="c74a5-143">Connectez l'élément Name dans le schéma source au fonctoid pour utiliser la valeur de l'élément Name comme deuxième entrée.</span><span class="sxs-lookup"><span data-stu-id="c74a5-143">Connect the Name element in the source schema to the functoid to use the value of the Name element as the second input.</span></span>|  
    |<span data-ttu-id="c74a5-144">Entrée [2]</span><span class="sxs-lookup"><span data-stu-id="c74a5-144">Input[2]</span></span>|<span data-ttu-id="c74a5-145">' **Remarque :** pour la dernière valeur d’entrée, spécifiez uniquement un guillemet fermant (').</span><span class="sxs-lookup"><span data-stu-id="c74a5-145">' **Note:**  For the last input value, specify only a closing single quote (').</span></span>|  
  
     <span data-ttu-id="c74a5-146">La capture d’écran suivante illustre la configuration pour le **concaténation de chaînes** fonctoid.</span><span class="sxs-lookup"><span data-stu-id="c74a5-146">The following screenshot depicts the configuration for the **String Concatenate** functoid.</span></span>  
  
     <span data-ttu-id="c74a5-147">![Configurer le fonctoid concaténation de chaînes](../core/media/bts-sf-stringconcatenate.jpg "BTS_SF_StringConcatenate")</span><span class="sxs-lookup"><span data-stu-id="c74a5-147">![Configure String Concatenate functoid](../core/media/bts-sf-stringconcatenate.jpg "BTS_SF_StringConcatenate")</span></span>  
  
     <span data-ttu-id="c74a5-148">Lorsque les trois paramètres d'entrée sont concaténés, ils forment la requête nécessaire qui doit être envoyée à Salesforce.</span><span class="sxs-lookup"><span data-stu-id="c74a5-148">When the three input parameters are concatenated, it will form the required query to be sent to Salesforce.</span></span>  
  
4.  <span data-ttu-id="c74a5-149">Connectez le fonctoid Concaténation de chaînes à l'élément Query dans le schéma de destination, comme le montre la capture d'écran ci-dessous.</span><span class="sxs-lookup"><span data-stu-id="c74a5-149">Connect the String Concatenate functoid to the Query element in the destination schema, as shown in the following screenshot.</span></span>  
  
     <span data-ttu-id="c74a5-150">![Mapper une réponse de notification pour interroger un schéma](../core/media/bts-sf-notification-query-mapping.jpg "BTS_SF_Notification_Query_Mapping")</span><span class="sxs-lookup"><span data-stu-id="c74a5-150">![Map notification response to query schema](../core/media/bts-sf-notification-query-mapping.jpg "BTS_SF_Notification_Query_Mapping")</span></span>  
  
5.  <span data-ttu-id="c74a5-151">Enregistrez les modifications apportées au mappage.</span><span class="sxs-lookup"><span data-stu-id="c74a5-151">Save changes to the map.</span></span>  
  
## <a name="creating-schema-to-receive-the-query-response-message"></a><span data-ttu-id="c74a5-152">Création de schéma pour recevoir le message de réponse à la requête</span><span class="sxs-lookup"><span data-stu-id="c74a5-152">Creating Schema to Receive the Query Response Message</span></span>  
 <span data-ttu-id="c74a5-153">Dans cette section, nous créons le schéma pour recevoir le message de réponse à la requête de Salesforce.</span><span class="sxs-lookup"><span data-stu-id="c74a5-153">In this section, we create the schema to receive the query response message from Salesforce.</span></span> <span data-ttu-id="c74a5-154">Dans cette section, nous créons manuellement le schéma de réponse à la requête.</span><span class="sxs-lookup"><span data-stu-id="c74a5-154">In this section, we manually create the schema for the query response.</span></span>  
  
#### <a name="to-create-a-schema-to-receive-the-query-response"></a><span data-ttu-id="c74a5-155">Pour créer un schéma afin de recevoir la réponse à la requête</span><span class="sxs-lookup"><span data-stu-id="c74a5-155">To create a schema to receive the query response</span></span>  
  
1.  <span data-ttu-id="c74a5-156">Ajoutez un nouveau schéma à la [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] de projet et nommez-le `QueryResult.xsd`.</span><span class="sxs-lookup"><span data-stu-id="c74a5-156">Add a new schema to the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] project and name it `QueryResult.xsd`.</span></span>  
  
2.  <span data-ttu-id="c74a5-157">La force de vente [QueryResult](http://go.microsoft.com/fwlink/?LinkId=287017) objet représente la réponse à la requête reçue de Salesforce.</span><span class="sxs-lookup"><span data-stu-id="c74a5-157">The Salesforce [QueryResult](http://go.microsoft.com/fwlink/?LinkId=287017) object depicts the query response received from Salesforce.</span></span> <span data-ttu-id="c74a5-158">Ainsi, nous allons construire un schéma pour illustrer ce qui suit :</span><span class="sxs-lookup"><span data-stu-id="c74a5-158">So, we’ll build a schema to depict the following:</span></span>  
  
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
  
     <span data-ttu-id="c74a5-159">La structure de votre schéma doit présenter l'aspect suivant :</span><span class="sxs-lookup"><span data-stu-id="c74a5-159">The schema structure should look like the following:</span></span>  
  
     <span data-ttu-id="c74a5-160">![Schéma pour la réponse à la requête de Salesforce](../core/media/bts-sf-queryresult.jpg "BTS_SF_QueryResult")</span><span class="sxs-lookup"><span data-stu-id="c74a5-160">![Schema for query response from Salesforce](../core/media/bts-sf-queryresult.jpg "BTS_SF_QueryResult")</span></span>  
  
3.  <span data-ttu-id="c74a5-161">Enregistrez les modifications apportées au schéma.</span><span class="sxs-lookup"><span data-stu-id="c74a5-161">Save changes to the schema.</span></span>  
  
## <a name="create-message-variables-for-queryrequest-and-queryresult-schemas"></a><span data-ttu-id="c74a5-162">Créer des variables de message pour les schémas QueryRequest et QueryResult</span><span class="sxs-lookup"><span data-stu-id="c74a5-162">Create Message Variables for QueryRequest and QueryResult Schemas</span></span>  
 <span data-ttu-id="c74a5-163">Après avoir créé les schémas QueryRequest et QueryResult, vous devez créer deux variables de message dans l'orchestration pour représenter les deux types de message.</span><span class="sxs-lookup"><span data-stu-id="c74a5-163">After you have created the QueryRequest and QueryResult schemas, you must create two message variables in the orchestration to represent the two message types.</span></span>  
  
#### <a name="to-create-message-variables"></a><span data-ttu-id="c74a5-164">Pour créer des variables de message</span><span class="sxs-lookup"><span data-stu-id="c74a5-164">To create message variables</span></span>  
  
1.  <span data-ttu-id="c74a5-165">Ouvrez le **NotificationService.odx** orchestration dans la vue orchestration, ajoutez deux nouveaux messages.</span><span class="sxs-lookup"><span data-stu-id="c74a5-165">Open the **NotificationService.odx** orchestration and in the orchestration view, add two new messages.</span></span> <span data-ttu-id="c74a5-166">Définir les noms de message `QueryRequestMsg` et `QueryResultMsg`.</span><span class="sxs-lookup"><span data-stu-id="c74a5-166">Set the message names as `QueryRequestMsg` and `QueryResultMsg`.</span></span>  
  
2.  <span data-ttu-id="c74a5-167">Définir le type de message pour **QueryRequestMsg** en tant que **BtsSalesforceIntegration.QueryRequest**.</span><span class="sxs-lookup"><span data-stu-id="c74a5-167">Set the message type for **QueryRequestMsg** as **BtsSalesforceIntegration.QueryRequest**.</span></span>  
  
3.  <span data-ttu-id="c74a5-168">Définir le type de message pour **QueryResultMsg** en tant que **BtsSalesforceIntegration.QueryResult**.</span><span class="sxs-lookup"><span data-stu-id="c74a5-168">Set the message type for **QueryResultMsg** as **BtsSalesforceIntegration.QueryResult**.</span></span>  
  
4.  <span data-ttu-id="c74a5-169">Enregistrez les modifications apportées à l'orchestration.</span><span class="sxs-lookup"><span data-stu-id="c74a5-169">Save changes to the orchestration.</span></span>  
  
## <a name="update-the-orchestration-to-send-message-to-salesforce-and-receive-a-response"></a><span data-ttu-id="c74a5-170">Mettre à jour l'orchestration pour envoyer le message à Salesforce et recevoir une réponse</span><span class="sxs-lookup"><span data-stu-id="c74a5-170">Update the Orchestration to Send Message to Salesforce and Receive a Response</span></span>  
 <span data-ttu-id="c74a5-171">Dans la rubrique [étape 3 a : réception des notifications d’opportunité de Salesforce dans BizTalk Server](../core/step-3a-receive-salesforce-opportunity-notification-into-biztalk-server.md), nous avons créé l’orchestration qui reçoit des notifications d’opportunité de Salesforce et envoie un accusé de réception.</span><span class="sxs-lookup"><span data-stu-id="c74a5-171">In the topic [Step 3a: Receive Salesforce Opportunity Notification into BizTalk Server](../core/step-3a-receive-salesforce-opportunity-notification-into-biztalk-server.md), we built the orchestration that receives opportunity notifications from Salesforce and sends an acknowledgement.</span></span> <span data-ttu-id="c74a5-172">Dans cette étape, nous nous appuyons sur cette orchestration pour envoyer une requête à la demande à Salesforce pour obtenir des détails sur le produit liés à l'opportunité et recevoir une réponse.</span><span class="sxs-lookup"><span data-stu-id="c74a5-172">In this step, we build on this orchestration to send a query request to Salesforce to get product details related to the opportunity and receive a response.</span></span> <span data-ttu-id="c74a5-173">Nous avons déjà créé des schémas (QueryRequest.xsd et QueryResult.xsd) et les variables de message (QueryRequestMsg et QueryResultMsg) que nous allons utiliser dans cette étape.</span><span class="sxs-lookup"><span data-stu-id="c74a5-173">We have already created the schemas (QueryRequest.xsd and QueryResult.xsd) and the message variables (QueryRequestMsg and QueryResultMsg) that we’ll use in this step.</span></span>  
  
#### <a name="to-send-a-query-request-to-salesforce-and-receive-a-response"></a><span data-ttu-id="c74a5-174">Pour envoyer une demande de requête à Salesforce et recevoir une réponse</span><span class="sxs-lookup"><span data-stu-id="c74a5-174">To send a query request to Salesforce and receive a response</span></span>  
  
1.  <span data-ttu-id="c74a5-175">Ajoutez une forme construire un Message après le **SendNotificationAck** forme.</span><span class="sxs-lookup"><span data-stu-id="c74a5-175">Add a Construct Message shape after the **SendNotificationAck** shape.</span></span> <span data-ttu-id="c74a5-176">Définissez le nom de la forme à `ConstructQuery` et définir le **Messages construits** propriété **QueryRequestMsg**.</span><span class="sxs-lookup"><span data-stu-id="c74a5-176">Set the name of the shape to `ConstructQuery` and set the **Messages Constructed** property to **QueryRequestMsg**.</span></span>  
  
2.  <span data-ttu-id="c74a5-177">Dans le **ConstructQuery** mettre en forme, ajouter un **transformer** forme.</span><span class="sxs-lookup"><span data-stu-id="c74a5-177">Within the **ConstructQuery** shape, add a **Transform** shape.</span></span> <span data-ttu-id="c74a5-178">Double-cliquez sur la forme Transformer pour ouvrir la boîte de dialogue Configuration de la forme Transformer.</span><span class="sxs-lookup"><span data-stu-id="c74a5-178">Double-click the Transform shape to open the Transform Configuration dialog box.</span></span> <span data-ttu-id="c74a5-179">Dans la boîte de dialogue, sélectionnez le **mappage existant** option, puis, dans la liste déroulante, sélectionnez **BtsSalesforceIntegration.Notification_QueryRequest**.</span><span class="sxs-lookup"><span data-stu-id="c74a5-179">In the dialog box, select the **Existing Map** option, and then from the drop-down select **BtsSalesforceIntegration.Notification_QueryRequest**.</span></span> <span data-ttu-id="c74a5-180">Définissez **Source** à **NotificaitonMessage**, **Destination** à **QueryRequestMsg**, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="c74a5-180">Set **Source** to **NotificaitonMessage**, **Destination** to **QueryRequestMsg**, and then click **OK**.</span></span>  
  
3.  <span data-ttu-id="c74a5-181">Dans le **ConstructQuery** mettre en forme après la forme Transformer, ajoutez une forme assignation du Message.</span><span class="sxs-lookup"><span data-stu-id="c74a5-181">Within the **ConstructQuery** shape, after the Transform shape, add a Message Assignment shape.</span></span> <span data-ttu-id="c74a5-182">Double-cliquez sur la forme Assignation du message et ajoutez l'expression suivante :</span><span class="sxs-lookup"><span data-stu-id="c74a5-182">Double-click the Message Assignment shape and add the following expression:</span></span>  
  
    ```  
    QueryRequestMsg(BtsSalesforceIntegration.PropertySchema.Query) = QueryRequestMsg.Query;  
    ```  
  
     <span data-ttu-id="c74a5-183">Ce faisant, nous transmettons la valeur de la **requête** élément dans le **QueryRequestMsg** schéma à l’élément promu **requête** dans le schéma de propriété.</span><span class="sxs-lookup"><span data-stu-id="c74a5-183">By doing this, we pass on the value of the **Query** element in the **QueryRequestMsg** schema to the promoted element **Query** in the property schema.</span></span> <span data-ttu-id="c74a5-184">Lors de la configuration du port WCF-WebHttp, nous allons utiliser cet élément pour passer dynamiquement ​​la valeur de requête au message de la demande.</span><span class="sxs-lookup"><span data-stu-id="c74a5-184">While configuring the WCF-WebHttp port, we’ll use this element to dynamically pass on the query value to the request message.</span></span>  
  
4.  <span data-ttu-id="c74a5-185">Après le **ConstructQuery** mettre en forme, ajoutez une forme envoi.</span><span class="sxs-lookup"><span data-stu-id="c74a5-185">After the **ConstructQuery** shape, add a Send shape.</span></span> <span data-ttu-id="c74a5-186">Nommez la forme `SendQueryRequest` et définissez le type de message **QueryRequestMsg**.</span><span class="sxs-lookup"><span data-stu-id="c74a5-186">Name the shape `SendQueryRequest` and set the message type as **QueryRequestMsg**.</span></span>  
  
5.  <span data-ttu-id="c74a5-187">Après la forme envoi, ajoutez une forme réception et nommez-le `ReceiveQueryResult`.</span><span class="sxs-lookup"><span data-stu-id="c74a5-187">After the Send shape, add a Receive shape and name it `ReceiveQueryResult`.</span></span> <span data-ttu-id="c74a5-188">Définir le type de message de la forme à **QueryResultMsg**.</span><span class="sxs-lookup"><span data-stu-id="c74a5-188">Set the message type of the shape to **QueryResultMsg**.</span></span>  
  
6.  <span data-ttu-id="c74a5-189">Ajoutez un port pour envoyer des demandes de requête à Salesforce et recevoir le résultat de la requête en réponse.</span><span class="sxs-lookup"><span data-stu-id="c74a5-189">Add a port to send query requests to Salesforce and receive the query result in response.</span></span> <span data-ttu-id="c74a5-190">Dans l'assistant Configuration du port, sélectionnez les options suivantes :</span><span class="sxs-lookup"><span data-stu-id="c74a5-190">In the Port Configuration wizard, select the following options:</span></span>  
  
    -   <span data-ttu-id="c74a5-191">Spécifiez le nom de port `SalesforceRESTInterface`.</span><span class="sxs-lookup"><span data-stu-id="c74a5-191">Specify the port name as `SalesforceRESTInterface`.</span></span>  
  
    -   <span data-ttu-id="c74a5-192">Sélectionnez l'option pour créer un nouveau type de port.</span><span class="sxs-lookup"><span data-stu-id="c74a5-192">Select the option to create a new port type.</span></span>  
  
    -   <span data-ttu-id="c74a5-193">Définissez **modèle de Communication** à *demande-réponse*.</span><span class="sxs-lookup"><span data-stu-id="c74a5-193">Set **Communication Pattern** to *Request-Response*.</span></span>  
  
    -   <span data-ttu-id="c74a5-194">Définir **direction de communication du Port** à *puis-je envoyer une demande et recevoir une réponse* et **liaison de Port** à *spécifierultérieure*.</span><span class="sxs-lookup"><span data-stu-id="c74a5-194">Set **Port direction of communication** to *I’ll be sending a request and receiving a response* and set **Port binding** to *Specify later*.</span></span>  
  
     <span data-ttu-id="c74a5-195">Connecter le **demande** opération du port à la forme envoi (*SendQueryRequest*) et le **réponse** opération du port sur la forme réception ( *ReceiveQueryResult*).</span><span class="sxs-lookup"><span data-stu-id="c74a5-195">Connect the **Request** operation of port to the Send shape (*SendQueryRequest*) and the **Response** operation of the port to the Receive shape (*ReceiveQueryResult*).</span></span> <span data-ttu-id="c74a5-196">La capture d'écran ci-dessous illustre la partie de l'orchestration qui représente le processus d'envoi de la demande de requête à Salesforce et la réception d'une réponse.</span><span class="sxs-lookup"><span data-stu-id="c74a5-196">The following screenshot depicts the part of the orchestration that represents the process of sending the query request to Salesforce and receiving a response.</span></span>  
  
     <span data-ttu-id="c74a5-197">![Envoyer une requête à Salesforce et recevoir la réponse](../core/media/bts-sf-sendqueryrequestorch.jpg "BTS_SF_SendQueryRequestOrch")</span><span class="sxs-lookup"><span data-stu-id="c74a5-197">![Send a query to Salesforce and receive response](../core/media/bts-sf-sendqueryrequestorch.jpg "BTS_SF_SendQueryRequestOrch")</span></span>  
  
 <span data-ttu-id="c74a5-198">Dans cette rubrique, nous avons mis à jour l'orchestration pour envoyer une demande de requête à Salesforce et recevoir plus de détails (comme les produits, la quantité, etc) sur l'opportunité qui est créée dans Salesforce.</span><span class="sxs-lookup"><span data-stu-id="c74a5-198">In this topic, we updated the orchestration to send a query request to Salesforce and receive more details (such as products, quantity, etc.) about the opportunity that is created in Salesforce.</span></span> <span data-ttu-id="c74a5-199">Dans les rubriques suivantes, nous mettrons à jour cette solution pour entrer la réponse de Salesforce dans une base de données SQL Server sur site.</span><span class="sxs-lookup"><span data-stu-id="c74a5-199">In the subsequent topics, we will update this solution to enter the Salesforce response into an on-premise SQL Server database.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c74a5-200">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c74a5-200">See Also</span></span>  
 [<span data-ttu-id="c74a5-201">Étape 3 : Créer la Solution BizTalk Server dans Visual Studio</span><span class="sxs-lookup"><span data-stu-id="c74a5-201">Step 3: Create the BizTalk Server Solution in Visual Studio</span></span>](../core/step-3-create-the-biztalk-server-solution-in-visual-studio.md)