---
title: "Étape 1 : Configurer l’adaptateur SWIFT pour le magasin d’interagir et le scénario avant | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 03b81599-bd26-44dc-9cf3-73868248764c
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: e71525c74da0f7df0769c99d443c16cc672cfbcd
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="step-1-configure-the-swift-adapter-for-the-interact-store-and-forward-scenario"></a>Étape 1 : Configurer l’adaptateur SWIFT pour le magasin d’interagir et le scénario avant
Avant de commencer cette étape, vous devez effectuer [préparation à l’utilisation du didacticiel](../../adapters-and-accelerators/fileact-interact/preparing-to-use-the-tutorial1.md).  
  
### <a name="to-configure-the-swift-adapter"></a>Pour configurer l’adaptateur SWIFT  
  
1.  Démarrer **Administration de BizTalk Server**.  
  
2.  Dans l’arborescence de la console, développez Administration de BizTalk Server, développez le groupe BizTalk, **paramètres de plateforme**, développez **carte**, avec le bouton droit **interagir**, pointez sur **Nouveau**, puis cliquez sur **Gestionnaire d’envoi**.  
  
3.  Dans le **interagir – propriétés du Gestionnaire d’adaptateur** boîte de dialogue le **général** onglet, à partir de la **nom d’hôte** la liste déroulante, sélectionnez **interacthost**, puis cliquez sur **propriétés**.  
  
4.  Dans le **propriétés du Transport interagir** boîte de dialogue le **propriétés** onglet, procédez comme suit :  
  
    |**Utilisez cette**|**Pour ce faire**|  
    |------------------|--------------------|  
    |**Arguments**|Type de l’argument suivant : – SagMessagePartner \<interagir de partenaire de Message Client créé dans les trous > **Remarque :** le client dans l’argument est le MessagePartner que vous avez configuré dans les trous.|  
    |**Mode de chiffrement**|Dans la liste déroulante, sélectionnez **avancé**.|  
    |**LogMessageBody**|Dans la liste déroulante, sélectionnez **FALSE**. **Remarque :** si vous affectez la valeur TRUE, il conserve le corps du message dans la base de données des suivis BizTalk. Toutefois, pour des raisons de sécurité, le corps du message ne peut jamais affiché dans le portail BAM.|  
    |**LogMessages**|Dans la liste déroulante, sélectionnez **TRUE**. Ainsi, les événements de message capturées et de suivi dans le portail BAM.|  
    |**Activer**|False :|  
    |**Mot de passe**|Tapez le mot de passe que vous utilisez pour vous connecter à des trous. Pour plus d’informations, consultez l’aide d’anti-COULURE.|  
    |**Nom d’utilisateur**|Tapez le nom d’utilisateur que vous utilisez pour vous connecter à des trous.|  
  
5.  Cliquez sur **OK** pour fermer la boîte de dialogue Propriétés du Transport interagir.  
  
6.  Cliquez sur **OK** pour fermer l’interagir – boîte de dialogue Propriétés de gestionnaire d’adaptateur.  
  
7.  Dans la boîte de message, cliquez sur **OK**, puis redémarrez l’instance d’hôte interagir.  
  
## <a name="see-also"></a>Voir aussi  
 [Interagir Store et le scénario de transfert (Push)](../../adapters-and-accelerators/fileact-interact/interact-store-and-forward-push-scenario.md)   
 [Étape 2 : Ajouter SWIFTNet Configuration pour le Paramfile pour le magasin d’interagir et le scénario avant](../../adapters-and-accelerators/fileact-interact/step-2-add-swiftnet-configuration-to-paramfile-for-interact-store-and-forward.md)   
 [Étape 3 : Créer des Ports d’envoi et Ports de réception pour le magasin d’interagir et d’un scénario avant](../../adapters-and-accelerators/fileact-interact/step-3-create-send-and-receive-ports-for-interact-store-and-forward-scenario.md)   
 [Étape 4 : Tester le magasin d’interagir et le scénario de bout en bout avant](../../adapters-and-accelerators/fileact-interact/step-4-test-the-interact-store-and-forward-end-to-end-scenario.md)