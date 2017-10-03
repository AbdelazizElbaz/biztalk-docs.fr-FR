---
title: "L’exemple d’adaptateur SQL en cours d’exécution | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 13566d08-7a59-4065-b0d7-19ae2765555e
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: bf04c06a1ef96974912ce3affe278d5a98936325
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="running-the-sql-adapter-sample"></a>L’exemple d’adaptateur SQL en cours d’exécution
L’exemple d’adaptateur SQL utilise une application de client Windows Forms test fournie avec l’exemple de feuille de route rampe d’entrée.  
  
 **Pour exécuter l’exemple d’adaptateur SQL**  
  
1.  Si l’application GlobalBank.ESB n’est pas déjà en cours d’exécution, utilisez la Console d’Administration Microsoft BizTalk pour le démarrer.  
  
2.  Dans l’Explorateur Windows, ouvrez le dossier \Source\Samples\Itinerary\Source\ESB. Itinerary.Test où vous avez installé le [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] exemples et démarrez l’application nommée Esb.Itinerary.Test.exe.  
  
3.  Désactivez le **utiliser le Service WCF** case à cocher afin qu’un itinéraire côté client peut être utilisé.  
  
4.  Sélectionnez le **deux manière Service** option  
  
5.  Cliquez sur le **charge itinéraire** bouton, puis sélectionnez un des itinéraires de l’exemple situés dans le dossier \Source\Samples\SqlAdapter \Itineraries.  
  
6.  Cliquez sur le **LoadMessage** , puis l’exemple de message OrderDoc.xml dans le dossier \Source\Samples\SqlAdapter \Test.  
  
7.  Cliquez sur le **SubmitRequest** bouton Envoyer la demande au service itinéraire rampe d’entrée.  
  
8.  Assurez-vous d’une ligne est insérée dans la table Product de la base de données GlobalBankESB.  
  
 Pour plus d’informations sur le fonctionne de l’exemple d’adaptateur SQL, consultez [SQL adaptateur exemple fonctionnement](../esb-toolkit/how-the-sql-adapter-sample-works.md).