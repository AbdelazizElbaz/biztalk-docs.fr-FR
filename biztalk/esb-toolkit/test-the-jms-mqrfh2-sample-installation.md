---
title: "Testez l’Installation d’exemples de MQRFH2 JMS | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 965e985d-f0fe-4b0f-b01b-cf98d1e2f6a4
caps.latest.revision: "2"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 5970f12479cddfb6a635cbd00dd139495a2f6242
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="test-the-jms-mqrfh2-sample-installation"></a>Testez l’Installation d’exemples de MQRFH2 JMS
Vous pouvez vérifier pour la réussite de l’installation et du fonctionnement de la [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] exemple JMS MQRFH2 avant d’exécuter tous les scénarios d’exemple.  
  
 **Pour tester l’installation d’exemples JMS MQRFH2**  
  
1.  Utilisez le paramètre « RFHUtil » JMS test utilitaire pour écrire les messages de test dans le dossier \Source\Samples\JMS\Test\Data\Load à la file d’attente nommée ESB. JMS. EXEMPLE. SENDTOBIZTALK.  
  
2.  L’exemple envoie le message à la file d’attente de destination et une copie du message à la file d’attente de réponse.