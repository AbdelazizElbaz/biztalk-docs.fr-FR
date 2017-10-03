---
title: "Exécution de l’exemple d’enrichissement de Message | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 7015a2fe-3727-48f3-a2ed-c368e0630626
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: c4ed3b3ebc24a908dfefd70711db0d40638c2d3b
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="running-the-message-enrichment-sample"></a>L’exemple d’enrichissement de Message en cours d’exécution
L’exemple d’enrichissement de Message utilise une application de client Windows Forms test fournie avec l’exemple de feuille de route rampe d’entrée.  
  
 **Pour exécuter l’exemple d’enrichissement de Message**  
  
1.  Si l’application GlobalBank.ESB n’est pas déjà en cours d’exécution, utilisez la Console d’Administration Microsoft BizTalk pour le démarrer.  
  
2.  Dans l’Explorateur Windows, ouvrez le dossier \Source\Samples\Itinerary\Source\ESB. Itinerary.Test où vous avez installé le [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] exemples et démarrez l’application nommée Esb.Itinerary.Test.exe.  
  
3.  Désactivez le **utiliser le Service WCF** case à cocher afin qu’un itinéraire côté client peut être utilisé.  
  
4.  Cliquez sur le **charge itinéraire** bouton, puis sélectionnez parmi les itinéraires de l’exemple situés dans le dossier \Source\Samples\MessageEnrichment\Itineraries.  
  
5.  Cliquez sur le **LoadMessage** , puis l’exemple de message OrderDoc.xml à partir du dossier \Source\Samples\MessageEnrichment\Test\.  
  
6.  Cliquez sur le **SubmitRequest** bouton Envoyer la demande au service itinéraire rampe d’entrée.  
  
7.  Accédez à C:\Projects\Microsoft.Practices.ESB\Source\Samples\DynamicResolution\Test\Filedrop\Out\\%MessageID%.xml pour afficher le message de sortie.  
  
 Pour plus d’informations sur le fonctionne de l’exemple d’enrichissement de Message, consultez [Message enrichissement exemple fonctionnement](../esb-toolkit/how-the-message-enrichment-sample-works.md).