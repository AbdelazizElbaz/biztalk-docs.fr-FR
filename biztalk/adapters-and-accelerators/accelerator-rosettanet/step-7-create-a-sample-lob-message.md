---
title: "Étape 7 : Créer un exemple de Message LOB | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- messages, LOB
- loopback tutorial, creating LOB message
- creating, LOB messages
- LOBs, creating messages
ms.assetid: 3023bbc0-5bc4-4e5a-a345-c3253874f0d3
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: acc6b57a78d51d9c132115f387296c48c2e924c9
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="step-7-create-a-sample-lob-message"></a>Étape 7 : Créer un exemple de Message LOB
Dans cette étape, vous utilisez l’utilitaire de l’Application métier pour créer un exemple de message de métier (LOB).  
  
### <a name="to-create-a-sample-message-using-the-lob-application-utility"></a>Pour créer un exemple de message à l’aide de l’utilitaire d’Application métier  
  
1.  Dans [!INCLUDE[btsWinNoVersion](../../includes/btswinnoversion-md.md)] Explorer, accédez à \< *lecteur*> : \Program Files\Microsoft BizTalk \<version > Accelerator for RosettaNet\SDK dossier, puis double-cliquez sur  **LOBApplication.exe**.  
  
2.  Dans le **Application métier** boîte de dialogue zone, procédez comme suit :  
  
    |**Utilisez cette**|**Pour ce faire**|  
    |------------------|--------------------|  
    |**Nom du profil de base**|Type **accueil**.|  
    |**Nom du partenaire commercial**|Type **partenaire**.|  
    |**Nom du PIP**|Type **0c1**.|  
    |**Version PIP**|Tapez **R01.02**.|  
    |**Nom de fichier**|Cliquez sur le bouton de sélection (**...** ) et les déplacer vers \< *lecteur*: > \Program Files\Microsoft BizTalk \<version > Accelerator for RosettaNet\SDK\LOBApplication\SampleInstances. Sélectionnez **0C1_Request.xml** dans la liste des fichiers, puis cliquez sur **ouvrir**.|  
    |**Catégorie de message**|Sélectionnez **Action** dans la liste déroulante.|  
  
3.  Dans le **Application métier** boîte de dialogue, cliquez sur **envoyer un Message**.  
  
 L’application métier génère un message de Microsoft [!INCLUDE[BTARN_CurrentVersion_FirstRef](../../includes/btarn-currentversion-firstref-md.md)] en simulant un message d’origine généré par une application métier. Vous pouvez afficher l’état du message dans la fenêtre d’état.  
  
> [!NOTE]
>  Les exemples de messages supposent que les identificateurs entreprise Global (GBI) pour « HOME » et « Partenaire » 123456789 et 987654321, respectivement. Pour utiliser un autre GBI, vous devez modifier le contenu de ces fichiers.  
  
## <a name="see-also"></a>Voir aussi  
 [Étape 8 : Afficher les Messages dans les bases de données BTARN](../../adapters-and-accelerators/accelerator-rosettanet/step-8-view-messages-in-the-btarn-databases.md)