---
title: "Étape 1 : Configurer l’adaptateur SWIFT pour le scénario en temps réel d’interagir | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6f4d3e08-611a-4af1-a3e3-957ace3b74e6
caps.latest.revision: "11"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 3ab7f1c75baf5a974fdbc10deb1651fcce1c7d51
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="step-1-configure-the-swift-adapter-for-the-interact-real-time-scenario"></a>Étape 1 : Configurer l’adaptateur SWIFT pour l’interaction du scénario en temps réel
Les étapes suivantes expliquent comment configurer le Gestionnaire d’envoi pour l’adaptateur Interact. Avant de commencer la procédure, vous devez effectuer la configuration requise figurant dans [préparation à l’utilisation du didacticiel](../../adapters-and-accelerators/fileact-interact/preparing-to-use-the-tutorial1.md).  
  
### <a name="to-configure-the-swift-adapter"></a>Pour configurer l’adaptateur SWIFT  
  
1.  Démarrer **Administration de BizTalk Server**.  
  
2.  Dans l’arborescence de la console, développez **Administration de BizTalk Server**, développez le groupe BizTalk, **paramètres de plateforme**, développez **carte**, avec le bouton droit  **INTERAGIR**, pointez sur **nouveau**, puis cliquez sur **Gestionnaire d’envoi**.  
  
3.  Dans le **interagir – propriétés du Gestionnaire d’adaptateur** boîte de dialogue le **général** onglet, à partir de la **nom d’hôte** la liste déroulante, sélectionnez **interacthost**, puis cliquez sur **propriétés**.  
  
4.  Dans le **INTERACTTransport propriétés** boîte de dialogue le **propriétés** onglet, procédez comme suit :  
  
    |**Utilisez cette**|**Pour ce faire**|  
    |------------------|--------------------|  
    |**Arguments**|Type de l’argument suivant : **SagMessagePartner**\<interagir de partenaire de Message Client créé dans les trous > **Remarque :** le client dans l’argument est le MessagePartner que vous avez configuré dans les trous.|  
    |**Mode de chiffrement**|Dans la liste déroulante, sélectionnez **avancé**.|  
    |**LogMessageBody**|Dans la liste déroulante, sélectionnez `FALSE`. **Remarque :** si vous définissez sur `TRUE`, il conserve le corps du message dans la base de données de suivi. Toutefois, pour des raisons de sécurité, le corps du message ne peut jamais affiché dans le portail BAM.|  
    |**LogMessages**|Dans la liste déroulante, sélectionnez `TRUE`. Ainsi, les événements de message capturées et de suivi dans le portail BAM.|  
    |**Activer**|False|  
    |**Mot de passe**|Tapez le mot de passe que vous utilisez pour vous connecter à des trous. Pour plus d’informations, consultez l’aide d’anti-COULURE.|  
    |**Nom d'utilisateur**|Tapez le nom d’utilisateur que vous utilisez pour vous connecter à des trous.|  
  
5.  Cliquez sur **OK** pour fermer la boîte de dialogue Propriétés du Transport interagir.  
  
6.  Cliquez sur **OK** pour fermer l’interagir – boîte de dialogue Propriétés de gestionnaire d’adaptateur.  
  
7.  Dans la boîte de message, cliquez sur **OK**, puis redémarrez l’instance d’hôte interagir.  
  
## <a name="see-also"></a>Voir aussi  
 [Interagir scénario en temps réel](../../adapters-and-accelerators/fileact-interact/interact-real-time-scenario.md)   
 [Étape 1 : Configurer l’adaptateur SWIFT pour l’interaction du scénario en temps réel](../../adapters-and-accelerators/fileact-interact/step-1-configure-the-swift-adapter-for-the-interact-real-time-scenario.md)   
 [Étape 2 : Ajouter SWIFTNet Configuration pour le Paramfile pour l’interaction du scénario en temps réel](../../adapters-and-accelerators/fileact-interact/step-2-add-swiftnet-configuration-to-paramfile-for-interact-real-time-scenario.md)   
 [Étape 3 : Créer l’envoi et Ports de réception l’interaction du scénario en temps réel](../../adapters-and-accelerators/fileact-interact/step-3-create-send-and-receive-ports-for-the-interact-real-time-scenario.md)   
 [Étape 4 : Tester l’interaction du scénario de bout en bout en temps réel](../../adapters-and-accelerators/fileact-interact/step-4-test-the-interact-real-time-end-to-end-scenario.md)