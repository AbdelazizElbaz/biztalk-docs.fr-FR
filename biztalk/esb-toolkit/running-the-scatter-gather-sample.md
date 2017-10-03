---
title: "Exécution de l’exemple de ventilation-regroupement | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 53676974-ea1f-4c95-9dbb-98fff92286fa
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 7dcafa519aac074ccb339373a591b590846c9341
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="running-the-scatter-gather-sample"></a>Exécution de l’exemple de ventilation-regroupement
L’exemple de ventilation-regroupement utilise une application cliente fournie avec l’exemple de feuille de route rampe d’entrée pour illustrer comment ce modèle applique les fonctionnalités du service itinéraire de test de Windows Forms.  
  
 **Pour exécuter l’exemple de ventilation-regroupement**  
  
1.  Si l’application GlobalBank.ESB n’est pas déjà en cours d’exécution, utilisez la Console d’Administration Microsoft BizTalk pour le démarrer.  
  
2.  Dans l’Explorateur Windows, ouvrez le dossier \Source\Samples\Itinerary\Source\ESB. Itinerary.Test où vous avez installé le [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] exemples et démarrez l’application nommée Esb.Itinerary.Test.exe.  
  
3.  Cliquez sur le **LoadItinerary** , puis sur l’itinéraire d’exemple nommé ScatterGatherItinerary.xml à partir du dossier \Source\Samples\ScatterGather\Itineraries.  
  
4.  Désactivez le **réponse à la demande est** case à cocher afin de l’application effectue un itinéraire à sens unique de services d’exploitation.  
  
5.  (Facultatif) Définir le **utiliser un Service WCF** case à cocher si vous souhaitez que l’application pour utiliser le OnRamp.Itinerary.Response.WCF l’emplacement de réception au lieu de la valeur par défaut OnRamp.Itinerary.Response.SOAP emplacement de réception.  
  
6.  Cliquez sur le **LoadMessage** , puis l’exemple de message NAOrderDoc.xml à partir du dossier \Source\Samples\Itinerary\Test\Data.  
  
7.  Cliquez sur le **SubmitRequest** bouton Envoyer la demande au service itinéraire rampe d’entrée. Ouvrez le dossier \Source\Samples\DynamicResolution\Test\FileDrop\Out pour afficher le message de réponse.  
  
 Pour savoir comment l’exemple de nuage de points de rassembler utilise le service de l’itinéraire d’ESB, consultez [ventilation-regroupement exemple fonctionnement](../esb-toolkit/how-the-scatter-gather-sample-works.md).