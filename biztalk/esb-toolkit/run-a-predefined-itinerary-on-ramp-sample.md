---
title: "Exécuter un exemple de rampe d’entrée d’itinéraire prédéfini | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b4400193-20ac-479a-8bf9-b1c99eb35231
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 38320cc6877815ccbf7b078190a3c2be1c6f74b0
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="run-a-predefined-itinerary-on-ramp-sample"></a>Exécuter un exemple de rampe d’entrée d’itinéraire prédéfini
La [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] inclut 20 cas d’usage itinéraire prédéfinis que vous pouvez exécuter. Pour obtenir la liste de ces cas d’usage, consultez [les exemples de scénarios de feuille de route](../esb-toolkit/the-sample-itinerary-scenarios.md).  
  
> [!NOTE]
>  Avant d’exécuter les exemples, vous devez importer manuellement le fichier de liaison d’itinéraire correspondant à partir du dossier \Source\Samples\Itinerary\Install\Binding dans l’application BizTalk de GlobalBank.ESB. Ce fichier de liaison réinitialise les propriétés sur les deux ports d’envoi dynamique. Importez le fichier de liaison nommé GlobalBank.ESB.Itinerary_Bindings.xml.  
  
### <a name="to-run-one-of-the-pre-defined-itinerary-on-ramp-samples"></a>Pour exécuter un des exemples de feuille de route rampe d’entrée prédéfinis  
  
1.  Si l’application GlobalBank.ESB n’est pas déjà en cours d’exécution, utilisez la Console Administration de BizTalk pour le démarrer.  
  
2.  Dans l’Explorateur Windows, ouvrez le sous-dossier \Source\Samples\Itinerary\Source\ESB. Itinerary.Test\bin\Debug où votre installé les exemples de BizTalk ESB Toolkit, puis démarrez l’application nommée Esb.Itinerary.Test.exe.  
  
3.  Cliquez sur le **LoadItinerary** , puis sur l’itinéraire d’exemple nommé TwoWay (bidirectionnel)-OrchTransform-OrchRoutingGroup-OrchTwoWayCustom.xml à partir du dossier \Source\Samples\Itinerary\Itineraries.  
  
4.  Dans le **Options du Service Web** section, sélectionnez le **bidirectionnel Service** case à cocher. Cela fait en sorte que le client de test pour effectuer une opération de service d’itinéraire de requête-réponse.  
  
5.  (Facultatif) Sélectionnez le **utiliser un Service WCF** case à cocher si vous souhaitez que l’application pour utiliser le OnRamp.Itinerary.Response.WCF l’emplacement de réception au lieu de la valeur par défaut OnRamp.Itinerary.Response.SOAP emplacement de réception.  
  
6.  Cliquez sur le **LoadMessage** , puis l’exemple de message NAOrderDoc.xml à partir du dossier \Source\Samples\Itinerary\Test\Data.  
  
7.  Cliquez sur le **SubmitRequest** bouton Envoyer la demande au service itinéraire rampe d’entrée. La figure 1 illustre le résultat.  
  
 ![Itinéraire sur rampe](../esb-toolkit/media/ch6-itineraryonramp.gif "§ 6-ItineraryOnRamp")  
  
 **Figure 1**  
  
 **L’application cliente de feuille de route rampe d’entrée en cours d’exécution un des exemples de la feuille de route rampe d’entrée**  
  
 Le nom du service spécifié dans la définition d’itinéraire correspond directement à la **ServiceName** propriété du service à laquelle s’abonne l’exemple. Dans l’exemple d’itinéraire exécutée dans la procédure précédente (TwoWay (bidirectionnel)-OrchTransform-OrchRoutingGroup-OrchTwoWayCustom.xml), le premier service exécuté est un service d’orchestration qui effectue une transformation. La section suivante de l’itinéraire spécifie ce service.  
  
```  
<Service uuid="" beginTime="" completeTime=""   
    name="Microsoft.Practices.ESB.Services.Transform"  
    type="Orchestration" state="Pending" isRequestResponse="false"  
    position="0" serviceInstanceId="" />  
```  
  
 Le service d’orchestration dans ce  **\<Service\>**  élément spécifie l’orchestration à liaison directe qui a les propriétés de filtre indiquées dans la Figure 2. Notez que l’orchestration s’abonne uniquement aux messages qui ont la valeur **Microsoft.Practices.ESB.Services.Transform** pour le **ServiceName** propriété de contexte, la valeur  **En attente** pour le **ServiceState** propriété de contexte et la valeur d’Orchestration pour les **ServiceType** propriété de contexte.  
  
 ![Expression de filtre](../esb-toolkit/media/ch6-filterexpression.gif "§ 6-FilterExpression")  
  
 **Figure 2**  
  
 **L’expression de filtre pour l’orchestration à liaison directe utilisée dans l’exemple de feuille de route rampe d’entrée**