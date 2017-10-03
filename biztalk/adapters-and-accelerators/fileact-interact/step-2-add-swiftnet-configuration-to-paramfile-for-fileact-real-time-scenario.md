---
title: "Étape 2 : Ajouter SWIFTNet Configuration pour le Paramfile pour le scénario en temps réel FileAct | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d4feec3f-4755-477e-b3d6-1dd6d075255e
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 793378e25c3ba92170e1da36b0c8276ab13357ae
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="step-2-add-swiftnet-configuration-to-the-paramfile-for-the-fileact-real-time-scenario"></a>Étape 2 : Ajouter SWIFTNet Configuration pour le Paramfile pour le scénario en temps réel FileAct
Les partenaires message créés dans les trous doivent être spécifiés dans le paramfile SWIFTNet pour activer les récepteurs initialiser avec ces valeurs.  
  
 Avant de commencer cette étape, vous devez effectuer [étape 1 : configurer l’adaptateur SWIFT pour le scénario en temps réel de FileAct](../../adapters-and-accelerators/fileact-interact/step-1-configure-the-swift-adapter-for-the-fileact-real-time-scenario.md).  
  
### <a name="to-add-swiftnet-configuration-to-the-paramfile"></a>Pour ajouter des SWIFTNet configuration à le paramfile  
  
1.  Ouvrez le paramfile dans un éditeur de texte, tel que le bloc-notes.  
  
    > [!NOTE]
    >  Le paramfile est généralement situé à : C:\SWIFTAlliance\RA\Ra1\cfg\paramfile  
  
2.  Dans la paramfile, apporter la modification en surbrillance pour spécifier le nom du Message du serveur partenaire :  
  
     username:snlowner  
  
     subsystem_name:FileactStub  
  
     \#subsystem_group:FileAct  
  
     \#subsystem_dependency:support, essaim  
  
     subsystem_nature : critique  
  
     subsystem_start :  
  
     **Création d’un « snlreceiver - SagMessagePartner \<MessagePartnerName de serveur pour fileact RT > - AdapterMode fileact »**  
  
     * FIN  
  
     subsystem_stop :  
  
     * KILL9:snlreceiver  
  
     * FIN  
  
     subsystem_status :  
  
     * NB:1:snlreceiver  
  
     * FIN  
  
     start_event:SNL001:Subsystem FileactStub est activé  
  
     stop_event:SNL002:Subsystem FileactStub est arrêté  
  
     \#subsystem_name:User  
  
     \##subsystem_group:user  
  
     \##subsystem_dependency :  
  
     \#subsystem_nature : critique  
  
     \#subsystem_start :  
  
     \#* FIN  
  
     \#subsystem_stop :  
  
     \#* FIN  
  
     \#subsystem_status :  
  
     #<a name="end"></a>* FIN  
  
     #<a name="starteventsnl001subsystem-user-is-up"></a>start_event:SNL001:Subsystem utilisateur est activé  
  
     #<a name="stopeventsnl002subsystem-user-is-down"></a>stop_event:SNL002:Subsystem utilisateur est arrêté  
  
## <a name="see-also"></a>Voir aussi  
 [Scénario en temps réel de FileAct](../../adapters-and-accelerators/fileact-interact/fileact-real-time-scenario.md)   
 [Étape 1 : Configurer l’adaptateur SWIFT pour le scénario en temps réel FileAct](../../adapters-and-accelerators/fileact-interact/step-1-configure-the-swift-adapter-for-the-fileact-real-time-scenario.md)   
 [Étape 3 : Créer les Ports d’envoi et Ports de réception pour le scénario en temps réel FileAct](../../adapters-and-accelerators/fileact-interact/step-3-create-the-send-ports-and-receive-ports-for-fileact-real-time-scenario.md)   
 [Étape 4 : Tester le scénario de bout en bout FileAct en temps réel](../../adapters-and-accelerators/fileact-interact/step-4-test-fileact-real-time-end-to-end-scenario.md)