---
title: "Étape 2 : Ajouter SWIFTNet Configuration pour le Paramfile pour et le scénario de transfert de FileAct | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 088ab41f-8325-4330-b6f2-0164aa1911b1
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 9b3048198747dd8d283ea9f7b329db27db615436
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="step-2-add-swiftnet-configuration-to-the-paramfile-for-the-fileact-store-and-forward-scenario"></a>Étape 2 : Ajouter SWIFTNet Configuration pour le Paramfile pour et le scénario de transfert de FileAct
Les partenaires message créés dans les trous doivent être spécifiés dans le paramfile SWIFTNet pour activer les récepteurs initialiser avec ces valeurs.  
  
Complète [étape 1 : configurer l’adaptateur SWIFT pour et le scénario de transfert de FileAct](../../adapters-and-accelerators/fileact-interact/step-1-configure-the-swift-adapter-for-the-fileact-store-and-forward-scenario.md) avant de commencer cette étape.
  
## <a name="add-swiftnet-configuration-to-the-paramfile"></a>Ajouter des configurations de SWIFTNet à la paramfile  
  
1.  Ouvrez le paramfile dans un éditeur de texte, tel que le bloc-notes.  
  
2.  Le paramfile est généralement situé à : C:\SWIFTAlliance\RA\Ra1\cfg\paramfile  
  
3.  Dans la paramfile, apporter la modification en surbrillance pour spécifier le nom du Message du serveur partenaire :  
    
     username:snlowner  
  
     subsystem_name:FileactStub  
  
     \#subsystem_group:fileactsnf  
  
     \#subsystem_dependency:support, essaim  
  
     subsystem_nature : critique  
  
     subsystem_start :  
  
     **Création d’un « snlreceiver - SagMessagePartner \<MessagePartnerName de serveur pour fileact MSNG > - AdapterMode fileact »**  
  
     * FIN  
  
     subsystem_stop :  
  
     * KILL9:snlreceiver  
  
     * FIN  
  
     subsystem_status :  
  
     * NB:1:snlreceiver  
  
     * FIN  
  
     start_event:SNL001:Subsystem FileactStubSnF est activé  
  
     stop_event:SNL002:Subsystem FileactStubSnF est arrêté  
  
     \#subsystem_name:User  
  
     \##subsystem_group:user  
  
     \##subsystem_dependency :  
  
     \#subsystem_nature : critique  
  
     \#subsystem_start :  
  
     \#* FIN  
  
     \#subsystem_stop :  
  
     \#* FIN  
  
     \#subsystem_status :  
  
     \#* FIN  
  
     #<a name="starteventsnl001subsystem-user-is-up"></a>start_event:SNL001:Subsystem utilisateur est activé  
  
     #<a name="stopeventsnl002subsystem-user-is-down"></a>stop_event:SNL002:Subsystem utilisateur est arrêté  
    
  
## <a name="complete-steps"></a>Étapes à suivre
 [Scénario de transfert et de FileAct](../../adapters-and-accelerators/fileact-interact/fileact-store-and-forward-scenario.md)   
 [Étape 1 : Configurer l’adaptateur SWIFT pour et le scénario de transfert de FileAct](../../adapters-and-accelerators/fileact-interact/step-1-configure-the-swift-adapter-for-the-fileact-store-and-forward-scenario.md)   
 [Étape 3 : Créer des Ports d’envoi et Ports de réception d’et le scénario de transfert de FileAct](../../adapters-and-accelerators/fileact-interact/step-3-create-send-ports-and-receive-ports-for-the-fileact-store-and-forward.md)   
 [Étape 4 : Tester et de scénario de bout en bout avant de FileAct](../../adapters-and-accelerators/fileact-interact/step-4-test-fileact-store-and-forward-end-to-end-scenario.md)