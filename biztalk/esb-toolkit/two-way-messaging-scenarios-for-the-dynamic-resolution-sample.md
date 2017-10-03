---
title: "Les scénarios de messagerie bidirectionnelles pour l’exemple de résolution dynamique | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e89792f1-c725-46c4-946c-23211e2f892a
caps.latest.revision: "4"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 852b1f203b693c7783c7eb461c521f3fbe0ceffe
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="two-way-messaging-scenarios-for-the-dynamic-resolution-sample"></a>Scénarios de messagerie bidirectionnelles pour l’exemple de résolution dynamique
Cette rubrique montre comment vous pouvez exécuter les scénarios de messagerie bidirectionnelles pour la [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] exemple de résolution dynamique.  
  
 **Pour exécuter les scénarios de messagerie bidirectionnelles pour l’exemple de résolution dynamique**  
  
1.  Avant d’exécuter cet exemple pour la première fois, assurez-vous que l’URL d’emplacement de réception pointe vers le service Web approprié. Spécifiez le service Web /ESB d’URL. Emplacement de réception NorthAmericanServices/CustomerOrder.asmx pour la DynamicResolutionReqResp_SOAP. En outre, assurez-vous que le port d’envoi dynamique nommé DynamicResolutionSolicitResp existe.  
  
    > [!NOTE]
    >  L’exemple de résolution dynamique utilise la résolution dynamique pour envoyer des messages à et recevoir des réponses à partir, le service Web canadien (http://localhost/ESB.CanadianServices/SubmitPOService.asmx). C’est pourquoi un port d’envoi statique n’est pas défini pour cet exemple. Le composant résolution dynamique récupère l’URL sortante à partir de la résolution et l’infrastructure d’adaptateurs fournisseur appelé par le pipeline ESBReceiveXml, qui est configuré dans le DynamicResolutionReqResp_SOAP l’emplacement de réception. Dans certains des exemples de messagerie bidirectionnelles, le pipeline ESBMapSend résout et exécute des mappages BizTalk de Microsoft.  
  
2.  Si l’application GlobalBank.ESB n’est pas déjà en cours d’exécution, utilisez la Console Administration de BizTalk pour le démarrer.  
  
3.  Décider quel exemple que vous souhaitez exécuter. Tous les scénarios de messagerie bidirectionnelles utilisent l’architecture ESB. Service Web de NorthAmericanServices situé dans http://localhost/ESB.NorthAmericanServices/CustomerOrder.asmx pour publier le message de demande à BizTalk Server, qui utilise l’emplacement de réception nommé DynamicResolutionReqResp_SOAP. Il existe des exemples de messagerie bidirectionnelles 10, chacun représenté par un fichier de liaison unique. Les tableaux suivants répertorient ces exemples, avec leurs fichiers de liaison associés et leurs descriptions.  
  
    |Entrant SOAP à SOAP sortant (submitOrder Action) à l’aide de l’outil de résolution BRE|  
    |---------------------------------------------------------------------------------|  
    |Utilise le fichier de liaison nommé GlobalBank.ESB.DynamicResolution_SubmitOrder_To_SubmitOrder_BRE_Bindings.xml pour définir l’emplacement de réception et les propriétés de port d’envoi.|  
    |Utilise le répartiteur ESB à l’emplacement de réception pour la résolution de point de terminaison.|  
  
    |Entrant SOAP à SOAP sortant (submitOrder Action) à l’aide de l’outil de résolution BRE pour le point de terminaison et la résolution de la Transformation|  
    |----------------------------------------------------------------------------------------------------------------------------|  
    |Utilise le fichier de liaison nommé GlobalBank.ESB.DynamicResolution_SubmitOrder_To_SubmitOrder_BRE_Routing_AND_ Transform_Bindings.xml pour définir l’emplacement de réception et les propriétés de port d’envoi.|  
    |Utilise le composant ESB répartiteur sur le port d’envoi sortante de pipeline et sortant emplacement le pipeline de réception pour résoudre dynamiquement et d’exécuter le mappage.|  
    |Utilise le répartiteur ESB à l’emplacement de réception pour la résolution de point de terminaison.|  
  
    |Entrant SOAP à SOAP sortant (submitOrder Action) à l’aide de l’outil de résolution statique|  
    |------------------------------------------------------------------------------------|  
    |Utilise le fichier de liaison nommé GlobalBank.ESB.DynamicResolution_SubmitOrder_To_SubmitOrder_STATIC_Bindings.xml pour définir l’emplacement de réception et les propriétés de port d’envoi.|  
    |Définit les mappages statiquement au niveau du port de réception.|  
    |Utilise le répartiteur ESB à l’emplacement de réception pour la résolution de point de terminaison.|  
  
    |Entrant SOAP à SOAP sortant (submitOrder Action) à l’aide de l’UDDI programme de résolution par rapport à Microsoft UDDI Server|  
    |--------------------------------------------------------------------------------------------------------------------|  
    |Utilise le fichier de liaison nommé GlobalBank.ESB.DynamicResolution_SubmitOrder_To_SubmitOrder_UDDI_MSFTREGISTRY_ Bindings.xml pour définir l’emplacement de réception et les propriétés de port d’envoi.|  
    |Définit les mappages statiquement au niveau du port de réception.|  
    |Utilise le répartiteur ESB à l’emplacement de réception pour la résolution de point de terminaison.|  
  
    > [!NOTE]
    >  Pour l’exemple précédent, vous devez modifier la clé de service dans le fichier de liaison à un qui existe sur le serveur UDDI cible.  
  
    |Entrant SOAP à SOAP sortant (submitOrder Action) à l’aide du programme de résolution par rapport à la SOA logiciel UDDI serveur UDDI|  
    |-----------------------------------------------------------------------------------------------------------------------|  
    |Utilise le fichier de liaison nommé GlobalBank.ESB.DynamicResolution_SubmitOrder_To_SubmitOrder_UDDI_SOAREGISTRY_ Bindings.xml pour définir l’emplacement de réception et les propriétés de port d’envoi.|  
    |Définit les mappages statiquement au niveau du port de réception.|  
    |Utilise le répartiteur ESB à l’emplacement de réception pour la résolution de point de terminaison.|  
  
    |Entrant SOAP à SOAP sortant (submitOrder Action) à l’aide de l’outil de résolution de XPATH|  
    |-----------------------------------------------------------------------------------|  
    |Utilise le fichier de liaison nommé GlobalBank.ESB.DynamicResolution_SubmitOrder_To_SubmitOrder_XPATH_Bindings.xml pour définir l’emplacement de réception et les propriétés de port d’envoi.|  
    |Définit les mappages statiquement au niveau du port de réception.|  
    |Utilise le répartiteur ESB à l’emplacement de réception pour la résolution de point de terminaison.|  
    |Le message contient l’ID de configuration de point de terminaison = http://localhost/ESB.CanadianServices/SubmitPOService.asmx et customerName = http://globalbank.esb.dynamicresolution.com/canadianservices/.|  
  
    |Entrant SOAP à SOAP sortant (submitPurchase Action) à l’aide du point de terminaison de programme de résolution BRE et résolution de Transformation|  
    |---------------------------------------------------------------------------------------------------------------------------|  
    |Utilise le fichier de liaison nommé GlobalBank.ESB.DynamicResolution_SubmitOrder_To_SubmitPurchaseOrder_BRE_Routing_ AND_Transform_Bindings.xml pour définir l’emplacement de réception et les propriétés de port d’envoi.|  
    |Utilise le composant ESB répartiteur sur le port d’envoi sortante de pipeline et sortant emplacement le pipeline de réception pour résoudre dynamiquement et d’exécuter le mappage.|  
    |Utilise le répartiteur ESB à l’emplacement de réception pour la résolution de point de terminaison.|  
    |Les modifications du programme de résolution BRE le **Action** de **submitOrder** à **submitPurchase**.|  
  
    |Entrant SOAP à SOAP sortant (submitPurchase Action) à l’aide de l’outil de résolution statique|  
    |---------------------------------------------------------------------------------------|  
    |Utilise le fichier de liaison nommé GlobalBank.ESB.DynamicResolution_SubmitOrder_To_SubmitPurchaseOrder_STATIC_ Bindings.xml pour définir l’emplacement de réception et les propriétés de port d’envoi.|  
    |Définit les mappages statiquement au niveau du port de réception.|  
    |Utilise le répartiteur ESB à l’emplacement de réception pour la résolution de point de terminaison.|  
    |Les modifications du programme de résolution statique le **Action** de **submitOrder** à **submitPurchase**.|  
  
4.  Importez le fichier de liaison pour l’exemple de messagerie que vous souhaitez exécuter dans l’application GlobalBank.ESB.  
  
5.  Appeler le service Web de NorthAmerican à l’aide de Microsoft InfoPath, le Studio de Service Web .NET ou tout autre mécanisme approprié. Assurez-vous que vous incluez tous les paramètres requis par l’opération.  
  
6.  Recherchez la réponse de message retourné. Si vous avez spécifié le **submitOrder** action, le texte « Envoyer la commande » doit précéder la valeur de la **ID** champ dans le message retourné. Si vous avez spécifié le **submitPurchase** action, le texte « Achat soumettre » doit précéder la valeur de la **ID** champ dans le message retourné.  
  
 Pour comprendre comment l’exemple utilise le répartiteur d’ESB et les composants de pipeline désassembleur de répartiteur ESB, consultez [dynamique résolution exemple fonctionnement](../esb-toolkit/how-the-dynamic-resolution-sample-works.md).