---
title: "Implémenter des modèles de conception dans les Orchestrations | Documents Microsoft"
description: "Aggregator, le routage basé sur le contenu, routeur dynamique, la gestion des erreurs, service broker de message et plusieurs modèles de conception dans BizTalk Server"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f62ba955-018a-40e7-b303-497acc906019
caps.latest.revision: "14"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 290b31e8d5494c7a00eb02517e910fc877da9124
ms.sourcegitcommit: dd7c54feab783ae2f8fe75873363fe9ffc77cd66
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/07/2017
---
# <a name="implement-design-patterns-in-orchestrations"></a>Implémenter des modèles de conception dans les Orchestrations
Cette rubrique décrit les modèles communs en matière de programmation BizTalk Server, ainsi que les modèles d'intégration d'entreprise. Vous pouvez utiliser un modèle unique ou associer plusieurs modèles afin de concevoir votre processus d'entreprise, puis d'implémenter cette conception à l'aide de formes dans le Concepteur d'orchestration BizTalk.  
  
## <a name="design-patterns"></a>Modèles de conception  
 Les entrées suivantes décrivent brièvement chaque modèle et pointent vers des rubriques ou des exemples qui expliquent comment implémenter ces modèles à l'aide du Concepteur d'orchestration BizTalk.  
  
### <a name="aggregator"></a>Aggregator  
 Le modèle d'agrégation est le modèle qui régit la réception des informations émanant de plusieurs sources et le regroupement de ces informations en un seul message. Pour obtenir un exemple de ce modèle, voir Aggregate.odx dans la rubrique [Aggregator (exemple BizTalk Server)](../core/aggregator-biztalk-server-sample.md).  
  
### <a name="calling-pipelines-from-an-orchestration"></a>Appel de pipelines à partir d'une orchestration  
 Vous pouvez appeler des pipelines d'envoi et de réception à partir de vos orchestrations. Ceci vous permet de réutiliser des pipelines et de préserver la dissociation entre une orchestration et les étapes du pipeline. Pour obtenir un exemple de ce modèle, voir Aggregate.odx dans la rubrique [Aggregator (exemple BizTalk Server)](../core/aggregator-biztalk-server-sample.md). Un autre exemple est CMP.odx dans la rubrique [processeur de messages composés (exemple BizTalk Server)](../core/composed-message-processor-biztalk-server-sample.md). Voir aussi [comment utiliser des Expressions pour exécuter des Pipelines](../core/how-to-use-expressions-to-execute-pipelines.md).  
  
### <a name="composed-message-processor"></a>Traitement des messages composés  
 Le traitement des messages composés est un modèle de traitement d'éléments individuels à partir d'un message d'échange agrégé ou par lot. Pour obtenir un exemple de ce modèle, voir CMP.odx dans la rubrique [processeur de messages composés (exemple BizTalk Server)](../core/composed-message-processor-biztalk-server-sample.md).  
  
### <a name="content-based-router"></a>Routeur basé sur le contenu  
 Le modèle de routeur basé sur le contenu est un modèle de détermination du destinataire d'un message basé sur une partie donnée du contenu du message. Pour obtenir un exemple de ce modèle, consultez [CBRSample (exemple BizTalk Server)](../core/cbrsample-biztalk-server-sample.md).  
  
### <a name="dynamic-router"></a>Routeur dynamique  
 Le modèle de routeur dynamique est un modèle de détermination de l'adresse de destination et du protocole de transport d'un message basé sur le résultat du traitement du message. Vous pouvez utiliser un port d’envoi dynamique ou un **lien de rôle** forme d’implémenter ce modèle. Pour obtenir un exemple de ce modèle, voir receivesend.odx dans la rubrique [SendMail](../core/sendmail.md). Un autre exemple est SupplierProcess.odx dans [PartyResolution (exemple BizTalk Server)](../core/partyresolution-biztalk-server-sample.md).  
  
### <a name="error-handling"></a>Gestion des erreurs  
 BizTalk Server vous permet de désigner la gestion automatique des échecs relatifs à la messagerie comme une alternative au comportement par défaut qui consiste à placer les messages ayant échoué dans la file d'attente des messages interrompus. Vous pouvez acheminer les messages ayant échoué vers un port d'abonnement pour les signaler dans un rapport ou les traiter. Pour obtenir un exemple de ce modèle, voir resubmitlogic.odx dans la rubrique [(dossier d’exemples BizTalk Server) de gestion des erreurs](../core/error-handling-biztalk-server-samples-folder.md).  
  
### <a name="exception-handling-and-compensation"></a>Gestion et compensation des exceptions  
 Vous pouvez utiliser un gestionnaire d’exceptions et un **lever Exception** forme ou un **Expression** forme pour la gestion des exceptions. Par exemple, vous pouvez placer le code suivant dans le **Expression** forme pour lever l’exception :,  
  
```  
excp = new System.Exception();  
throw(excp);  
```  
  
 Vous pouvez utiliser un bloc de compensation et un **compenser** shape pour effectuer la compensation sur les transactions qui ont été validées. Pour obtenir un exemple de ce modèle, voir updatecontact.odx dans la rubrique [Compensation (exemple BizTalk Server)](../core/compensation-biztalk-server-sample.md). Un autre exemple est en [personnalisé Exceptions](../core/custom-exceptions.md).  
  
### <a name="message-broker"></a>Courtier de messages  
 Le modèle de courtier de messages est un modèle de détermination de la destination d'un message tout en conservant le contrôle sur le flux de messages. Pour plus d’informations, consultez [du traitement de l’Orchestration OrderBroker](../core/processing-in-the-orderbroker-orchestration.md).  
  
### <a name="message-filter"></a>Filtre de message  
 Le modèle de filtre de message sélectionne les messages à traiter en fonction de critères particuliers. Vous pouvez implémenter ce modèle en ajoutant l’expression de filtre pour une activation **réception** forme. Pour plus d’informations, consultez [à l’aide de filtres avec le Message forme réception](../core/using-filters-with-the-receive-message-shape.md).  
  
### <a name="message-translator"></a>Convertisseur de messages  
 Le modèle de conversion de messages convertit un message d'une forme à une autre. Vous pouvez implémenter ce modèle à l’aide d’un mappage BizTalk avec un **transformer** forme dans une orchestration. Pour obtenir un exemple de ce modèle, voir helloorchestration.odx dans la rubrique [HelloWorld (exemple BizTalk Server)](../core/helloworld-biztalk-server-sample.md).  
  
### <a name="parallel-convoy"></a>Convoi parallèle  
 Le modèle de convoi parallèle permet à plusieurs éléments uniques d'être reliés de façon à obtenir une chose qu'un élément individuel ne peut pas accomplir seul. L'ensemble des éléments liés peut arriver dans n'importe quel ordre, mais BizTalk Server doit tous les recevoir avant de commencer le traitement. 
  
### <a name="scatter-and-gather"></a>Ventilation et regroupement  
 Le modèle de ventilation et de regroupement permet d'envoyer des messages à plusieurs destinataires et de recevoir des messages de la part de chaque destinataire. Vous pouvez implémenter ce modèle à l'aide des modèles de séparation et d'agrégation. Vous utilisez le modèle d’agrégation pour assembler les résultats obtenus à l’aide du modèle de séparation et de les placer dans un **Actions parallèles** forme. 
  
### <a name="sequential-convoy"></a>Convoi séquentiel  
 Le modèle de convoi séquentiel permet à plusieurs éléments uniques d'être reliés de façon à obtenir une chose qu'un élément individuel ne peut pas accomplir seul. Un convoi séquentiel est un ensemble d'éléments associés présentant un ordre prédéfini. Bien que ces éléments n'aient pas à être exactement identiques, BizTalk Server doit les recevoir dans un ordre séquentiel. 
  
### <a name="splitter"></a>Splitter  
 Le modèle de séparation fractionne un messages unique en plusieurs messages.  
  
### <a name="suspend-with-retry"></a>Suspension avec relance  
 Le modèle de suspension avec relance permet à l'orchestration de suspendre un message en cas d'erreur. La suspension se produit dans le cadre d'une boucle dans laquelle l'orchestration suspend le message, demande l'intervention, puis effectue un nombre de relances prédéfini de l'opération.  
  
## <a name="see-also"></a>Voir aussi  
 [Conception d’un flux d’orchestration](../core/designing-orchestration-flow.md)