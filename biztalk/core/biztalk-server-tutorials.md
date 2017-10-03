---
title: Didacticiels de BizTalk Server | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- tutorials, getting started
- getting started, tutorials
ms.assetid: 58019f98-e91a-4705-b689-c269174d6bae
caps.latest.revision: "42"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: f13a5d74d0957a208600653823e7604680296f4d
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="biztalk-server-tutorials"></a>Didacticiels de BizTalk Server
Didacticiels pour apprendre à utiliser [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].

Il s'agit de scénarios simples permettant aux nouveaux utilisateurs de prendre en main divers outils que propose BizTalk dans le cadre de la création de solutions d'intégration compilées pouvant être testées. Pour les utilisateurs plus expérimentés, ou les utilisateurs concevez des solutions BizTalk, consultez [scénarios pour les Solutions](../core/scenarios-for-business-solutions.md).  
  
## <a name="enterprise-application-integration"></a>IAE (Intégration des applications de l'entreprise)
  
[Didacticiel : Intégration d’Application d’entreprise](../core/tutorial-1-enterprise-application-integration.md) 

Implémenter une solution BizTalk qui reçoit les messages de demande de réapprovisionnement de stock d’un entrepôt et évalue les messages de demande. Si la solution refuse une requête, il envoie un message de refus à l’entrepôt. Si la demande est acceptée par la solution, puis il transmet le message à un système de planification ERP (Enterprise Resource).  

## <a name="create-a-hybrid-application"></a>Créer une Application hybride
[Didacticiel : Création d’une Application hybride à l’aide de BizTalk Server](../core/tutorial-4-creating-a-hybrid-application-using-biztalk-server-2013.md)  

Configurer une application de bout en bout qui utilise l’EDI pour générer des accusés de réception, Service Bus pour recevoir des messages, et puis insérez des données dans SQL. 

## <a name="invoke-a-rest-interface"></a>Appeler une Interface REST
[Didacticiel : Appel d’une Interface REST à l’aide de BizTalk Server](../core/tutorial-5-invoking-a-rest-interface-using-biztalk-server.md)  

Utilise l’adaptateur WCF-WebHttp pour utiliser une URL de REST, puis envoyer un message de réponse. 

## <a name="integrate-biztalk-with-salesforce"></a>Intégration de BizTalk avec Salesforce
[Didacticiel : Intégration de BizTalk Server auprès de Salesforce](Tutorial:%20Integrating%20BizTalk%20Server%202013%20with%20Salesforce.md)  

Chaque fois qu’une opportunité de vente est créée dans le système Salesforce, Northwind veut que ses systèmes sur site, tels que BizTalk Server, pour être averti afin que les autres systèmes en aval puissent collecter les données et démarrer d’autres processus pertinents. 

## <a name="process-json-messages"></a>Traiter les messages JSON
[Traitement des messages JSON à l’aide de BizTalk Server](../core/processing-json-messages-using-biztalk-server.md)  

Configurer une application BizTalk qui reçoit un bon de commande JSON. Dans le pipeline de réception, un composant du décodeur JSON transforme le message JSON en message XML. Puis, utilise un mappage pour transformer le bon de commande XML en facture XML. Le pipeline d’envoi utilise un encodeur JSON pour transformer la facture XML en une facture JSON, puis envoie le message.

## <a name="edi-interface-developer"></a>Développeur d’Interface EDI
  [Didacticiel : EDI Interface Developer Tutorial.](../core/tutorial-2-edi-interface-developer-tutorial.md)
  
Un partenaire commercial envoie des bons de commande à l’aide de l’ANSI X12 4010 850 du document informatisé (message 850). Un processus de système de commande interne bons de commande.

En tant que développeur d’interface chargé de concevoir l’interface entre le message 850, vous recevez de votre partenaire commercial et système de commande interne de votre entreprise. Votre partenaire commercial requiert un accusé de réception fonctionnel (997) pour chaque message 850 qu'il envoie.


## <a name="as2"></a>AS2  
[Didacticiel : Didacticiel AS2](../core/tutorial-3-as2-tutorial.md)

Configurer une solution qui reçoit et envoie les messages codés EDIINT/AS2 via un transport HTTP.    


## <a name="do-more"></a>Faire plus  
 Pour plus d’informations sur l’architecture et les concepts de BizTalk Server, procédez comme suit :  
  
[Prise en main](../core/getting-started-with-biztalk-server.md)
  
[Planifier et concevoir votre solution BizTalk Server](../core/plan-and-architect-your-biztalk-server-solution.md)