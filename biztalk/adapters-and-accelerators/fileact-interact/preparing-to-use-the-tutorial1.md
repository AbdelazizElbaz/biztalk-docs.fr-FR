---
title: "Préparation à l’utilisation de la Tutorial1 | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d4a792b2-8351-4ae8-9d7c-75420c00af03
caps.latest.revision: "12"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: efedfeb184b8b0105b8622b6b3f068faffd6a906
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="preparing-to-use-the-tutorial"></a>Préparation à l’utilisation du didacticiel
Vous devez procédez comme suit avant d’utiliser le didacticiel de bout en bout pour l’adaptateur A4SWIFT.  
  
1.  Vous devez les artefacts SWIFT suivants pour ce didacticiel :  
  
    -   Alliance SWIFT passerelle (trous) 6.1  
  
    -   Accès à distance (RA) 6.1  
  
    -   SWIFT WebStation 6.0  
  
    -   Lien SWIFTNet (SNL) 6.1  
  
2.  Vous devez configurer des trous : créer les MessagePartners, les Points de terminaison et les règles de routage dans les trous et tester la connectivité des trous sur l’ordinateur sur lequel vous installez les adaptateurs. Pour plus d’informations, consultez la documentation de trous.  
  
3.  Suivez les instructions figurant dans la rubrique « Comment pour créer un nouvel hôte » dans l’aide de Microsoft BizTalk Server ([http://go.microsoft.com/fwlink/? LinkId = 100422](http://go.microsoft.com/fwlink/?LinkId=100422)) pour créer un hôte in-process pour l’adaptateur InterAct, nommé *interacthost*et un hôte in-process pour l’adaptateur FileAct, nommé *fileacthost*. Vous allez utiliser ces ordinateurs hôtes lors de la création de gestionnaires pour les adaptateurs.  
  
4.  Créez les dossiers suivants pour le didacticiel :  
  
    -   c:\SWIFTAdapterTutorial\Fileact\ClientLocation  
  
    -   c:\SWIFTAdapterTutorial\Fileact\FileRequestDropRealTime  
  
    -   c:\SWIFTAdapterTutorial\Fileact\ResponseClient  
  
    -   c:\SWIFTAdapterTutorial\Fileact\ResponseServer  
  
    -   c:\SWIFTAdapterTutorial\Fileact\ServerLocation  
  
    -   c:\SWIFTAdapterTutorial\Fileact\StatusEvents  
  
    -   c:\SWIFTAdapterTutorial\Fileact\PullRequest  
  
    -   c:\SWIFTAdapterTutorial\Fileact\PullResponse  
  
    -   c:\SWIFTAdapterTutorial\Interact\HandleRequest  
  
    -   c:\SWIFTAdapterTutorial\Interact\InputRequest_RealTime  
  
    -   c:\SWIFTAdapterTutorial\Interact\InputRequest_SnF  
  
    -   c:\SWIFTAdapterTutorial\Interact\Response  
  
    -   c:\SWIFTAdapterTutorial\Interact\PullRequest  
  
    -   c:\SWIFTAdapterTutorial\Interact\Pullresponse  
  
5.  Vous devez disposer d’une connexion à SWIFT ITB ou un environnement dynamique à l’adaptateur de test.  
  
## <a name="see-also"></a>Voir aussi  
 [BizTalk FileAct et interagir didacticiel de bout en bout pour les cartes](../../adapters-and-accelerators/fileact-interact/biztalk-fileact-and-interact-adapters-end-to-end-tutorial.md)   
 [Interagir scénario en temps réel](../../adapters-and-accelerators/fileact-interact/interact-real-time-scenario.md)   
 [Interagir Store et le scénario de transfert (Push)](../../adapters-and-accelerators/fileact-interact/interact-store-and-forward-push-scenario.md)   
 [Scénario en temps réel de FileAct](../../adapters-and-accelerators/fileact-interact/fileact-real-time-scenario.md)   
 [Scénario de transfert et de FileAct](../../adapters-and-accelerators/fileact-interact/fileact-store-and-forward-scenario.md)