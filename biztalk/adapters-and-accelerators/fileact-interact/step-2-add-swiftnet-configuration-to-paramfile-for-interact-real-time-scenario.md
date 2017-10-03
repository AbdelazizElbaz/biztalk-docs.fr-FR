---
title: "Étape 2 : Ajouter SWIFTNet Configuration pour le Paramfile pour le scénario en temps réel d’interagir | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6a900a6e-3e08-430a-8766-4a7192adba5e
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 249bfb8120a7b7d44ee0f73e7b5e5cef34126670
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="step-2-add-swiftnet-configuration-to-the-paramfile-for-the-interact-real-time-scenario"></a>Étape 2 : Ajouter SWIFTNet Configuration pour le Paramfile pour l’interaction du scénario en temps réel
Les partenaires message créés dans les trous doivent être spécifiés dans le paramfile SWIFTNet pour activer les récepteurs initialiser avec ces valeurs. Avant de commencer la procédure, vous devez effectuer les instructions de [étape 1 : configurer l’adaptateur SWIFT pour le scénario en temps réel interagir](../../adapters-and-accelerators/fileact-interact/step-1-configure-the-swift-adapter-for-the-interact-real-time-scenario.md).  
  
### <a name="to-add-swiftnet-configuration-to-the-paramfile"></a>Pour ajouter des SWIFTNet configuration à le paramfile  
  
1.  Ouvrez le paramfile dans un éditeur de texte, tel que le bloc-notes.  
  
     Le paramfile est généralement situé à : C:\SWIFTAlliance\RA\Ra1\cfg\paramfile  
  
2.  Dans la paramfile, apporter la modification en surbrillance pour spécifier le nom du Message du serveur partenaire :  
  
     username:snlowner  
  
     subsystem_name:InteractStub  
  
     \#subsystem_group:InteractRT  
  
     \#subsystem_dependency:support, essaim  
  
     subsystem_nature : critique  
  
     subsystem_start :  
  
     **Création d’un « snlreceiver - SagMessagePartner \<MessagePartnerName de serveur pour interagir RT > - AdapterMode interagir »**  
  
     * FIN  
  
     subsystem_stop :  
  
     * KILL9:snlreceiver  
  
     * FIN  
  
     subsystem_status :  
  
     * NB:1:snlreceiver  
  
     * FIN  
  
     start_event:SNL001:Subsystem InteractStub est activé  
  
     stop_event:SNL002:Subsystem InteractStub est arrêté  
  
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
 [Interagir scénario en temps réel](../../adapters-and-accelerators/fileact-interact/interact-real-time-scenario.md)   
 [Étape 1 : Configurer l’adaptateur SWIFT pour l’interaction du scénario en temps réel](../../adapters-and-accelerators/fileact-interact/step-1-configure-the-swift-adapter-for-the-interact-real-time-scenario.md)   
 [Étape 3 : Créer l’envoi et Ports de réception l’interaction du scénario en temps réel](../../adapters-and-accelerators/fileact-interact/step-3-create-send-and-receive-ports-for-the-interact-real-time-scenario.md)   
 [Étape 4 : Tester l’interaction du scénario de bout en bout en temps réel](../../adapters-and-accelerators/fileact-interact/step-4-test-the-interact-real-time-end-to-end-scenario.md)