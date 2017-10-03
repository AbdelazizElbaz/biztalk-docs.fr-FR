---
title: "Étape 2 : Ajouter SWIFTNet Configuration pour le Paramfile pour le magasin d’interagir et le scénario avant | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 2a18a43c-1dd9-4113-bf32-8bc7bf9338b0
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 78aa75762e40bfcdd033a057610cb34f38825dd8
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="step-2-add-swiftnet-configuration-to-the-paramfile-for-the-interact-store-and-forward-scenario"></a>Étape 2 : Ajouter SWIFTNet Configuration pour le Paramfile pour le magasin d’interagir et le scénario avant
Les partenaires message créés dans les trous doivent être spécifiés dans le paramfile SWIFTNet pour activer les récepteurs initialiser avec ces valeurs.  
  
 Avant de commencer cette étape, vous devez effectuer [étape 1 : configurer l’adaptateur SWIFT pour le magasin d’interagir et le scénario par progression](../../adapters-and-accelerators/fileact-interact/step-1-configure-the-swift-adapter-for-the-interact-store-and-forward-scenario.md).  
  
### <a name="to-add-swiftnet-configuration-to-the-paramfile"></a>Pour ajouter des SWIFTNet configuration à le paramfile  
  
1.  Ouvrez le paramfile dans un éditeur de texte, tel que le bloc-notes.  
  
    > [!NOTE]
    >  Le paramfile est généralement situé à : C:\SWIFTAlliance\RA\Ra1\cfg\paramfile.  
  
2.  Dans la paramfile, apporter la modification en surbrillance pour spécifier le nom du Message du serveur partenaire :  
  
     username:snlowner  
  
     subsystem_name:InteractStub  
  
     \#subsystem_group:Interactsnf  
  
     \#subsystem_dependency:support, essaim  
  
     subsystem_nature : critique  
  
     subsystem_start :  
  
     **Création d’un « snlreceiver - SagMessagePartner \<MessagePartnerName de serveur pour interagir MSNG > - AdapterMode interagir »**  
  
     * FIN  
  
     subsystem_stop :  
  
     * KILL9:snlreceiver  
  
     * FIN  
  
     subsystem_status :  
  
     * NB:1:snlreceiver  
  
     * FIN  
  
     start_event:SNL001:Subsystem InteractStubSnF est activé  
  
     stop_event:SNL002:Subsystem InteractStubSnF est arrêté  
  
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
  
## <a name="see-also"></a>Voir aussi  
 [Interagir Store et le scénario de transfert (Push)](../../adapters-and-accelerators/fileact-interact/interact-store-and-forward-push-scenario.md)   
 [Étape 1 : Configurer l’adaptateur SWIFT pour le magasin d’interagir et le scénario avant](../../adapters-and-accelerators/fileact-interact/step-1-configure-the-swift-adapter-for-the-interact-store-and-forward-scenario.md)   
 [Étape 3 : Créer des Ports d’envoi et Ports de réception pour le magasin d’interagir et d’un scénario avant](../../adapters-and-accelerators/fileact-interact/step-3-create-send-and-receive-ports-for-interact-store-and-forward-scenario.md)   
 [Étape 4 : Tester le magasin d’interagir et le scénario de bout en bout avant](../../adapters-and-accelerators/fileact-interact/step-4-test-the-interact-store-and-forward-end-to-end-scenario.md)