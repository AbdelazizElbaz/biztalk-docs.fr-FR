---
title: "Exécute le site Web de plusieurs Services exemple | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b201c7c3-213a-4009-8872-5a4c1cbb8195
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 4ec54fabb7ed140fd88b5a2d5a07d788805c741e
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="running-the-multiple-web-services-sample"></a>Exécution de l’exemple de Services Web multiples
L’exemple de plusieurs Services Web utilise l’application de client Windows Forms test fournie avec l’exemple de feuille de route rampe d’entrée.  
  
 **Pour exécuter l’exemple de plusieurs Services Web**  
  
1.  Si l’application GlobalBank.ESB n’est pas déjà en cours d’exécution, utilisez la Console d’Administration Microsoft BizTalk pour le démarrer.  
  
2.  Dans l’Explorateur Windows, ouvrez le dossier \Source\Samples\Itinerary\Source\ESB. Itinerary.Test où vous avez installé le [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] exemples et démarrez l’application nommée Esb.Itinerary.Test.exe.  
  
3.  Désactivez le **utiliser le Service WCF** case, afin qu’un itinéraire côté client peut être utilisé.  
  
4.  Cliquez sur le **charge itinéraire** bouton, puis sélectionnez parmi les itinéraires de l’exemple situés dans le dossier \Source\Samples\MultipleWebServices\Itineraries.  
  
5.  Sélectionnez le **deux manière Service** case à cocher afin de l’application effectue un itinéraire bidirectionnels services l’opération.  
  
6.  Cliquez sur le **LoadMessage** , puis l’exemple de message NAOrderDoc.xml à partir du dossier \Source\Samples\Itinerary\Test\Data.  
  
7.  Cliquez sur le **SubmitRequest** bouton Envoyer la demande au service itinéraire rampe d’entrée. Attendre un message de réponse s’affichent dans le **résultat** boîte.  
  
 Pour savoir comment l’exemple de plusieurs Services Web utilise le service de l’itinéraire d’ESB, consultez [plusieurs Web Services exemple fonctionnement](../esb-toolkit/how-the-multiple-web-services-sample-works.md).