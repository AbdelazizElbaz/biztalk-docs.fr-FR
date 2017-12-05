---
title: "Étape 1 : Configurer l’adaptateur SWIFT pour le magasin d’interagir et le scénario de transfert (Pull) | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 4182021c-36c9-4c96-b2fa-e23c87862cfe
caps.latest.revision: "5"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: d9de8c569744c5bbf750ef2aa804efbc456cd74a
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="step-1-configure-the-swift-adapter-for-the-interact-store-and-forward-pull-scenario"></a>Étape 1 : Configurer l’adaptateur SWIFT pour le magasin d’interagir et le scénario de transfert (Pull)
Avant de commencer cette étape, vous devez effectuer [préparation à l’utilisation du didacticiel](../../adapters-and-accelerators/fileact-interact/preparing-to-use-the-tutorial1.md).  
  
### <a name="to-configure-the-swift-adapter"></a>Pour configurer l’adaptateur SWIFT  
  
1.  Démarrer **Administration de BizTalk Server**.  
  
2.  Dans l’arborescence de la console, développez Administration de BizTalk Server, développez le groupe BizTalk, **paramètres de plateforme**, développez **carte**, avec le bouton droit **interagir**, pointez sur **Nouveau**, puis cliquez sur **Gestionnaire d’envoi**.  
  
3.  Dans le **interagir – propriétés du Gestionnaire d’adaptateur** boîte de dialogue le **général** onglet, à partir de la **nom d’hôte** la liste déroulante, sélectionnez **interacthost**, puis cliquez sur **propriétés**.  
  
4.  Dans le **propriétés du Transport interagir** boîte de dialogue le **propriétés** onglet, procédez comme suit :  
  
    |**Utilisez cette**|**Pour ce faire**|  
    |------------------|--------------------|  
    |**Arguments**|Type de l’argument suivant : – SagMessagePartner \<interagir de partenaire de Message Client créé dans les trous\> **Remarque :** le client dans l’argument est le MessagePartner que vous avez configuré dans les trous.|  
    |**Mode de chiffrement**|Dans la liste déroulante, sélectionnez **avancé**.|  
    |**LogMessageBody**|Dans la liste déroulante, sélectionnez **FALSE**. **Remarque :** si vous affectez la valeur TRUE, il conserve le corps du message dans la base de données des suivis BizTalk. Toutefois, pour des raisons de sécurité, le corps du message ne peut jamais affiché dans le portail BAM.|  
    |**LogMessages**|Dans la liste déroulante, sélectionnez **TRUE**. Ainsi, les événements de message capturées et de suivi dans le portail BAM.|  
    |**Activer**|False :|  
    |**Mot de passe**|Tapez le mot de passe que vous utilisez pour vous connecter à des trous. Pour plus d’informations, consultez l’aide d’anti-COULURE.|  
    |**Nom d’utilisateur**|Tapez le nom d’utilisateur que vous utilisez pour vous connecter à des trous.|  
  
5.  Cliquez sur **OK** pour fermer la boîte de dialogue Propriétés du Transport interagir.  
  
6.  Cliquez sur **OK** pour fermer l’interagir – boîte de dialogue Propriétés de gestionnaire d’adaptateur.  
  
7.  Dans la boîte de message, cliquez sur **OK**, puis redémarrez l’instance d’hôte interagir.  
  
8.  Répétez l’étape 1.  
  
9. Dans l’arborescence de la console, développez successivement Administration de BizTalk Server, le **BizTalk** de groupe, développez **paramètres de plateforme**, développez **adaptateur**, sélectionnez interagir, ouvrez  **BizTalkServerApplication** puis, cliquez sur **propriétés**.  
  
10. Dans le **propriétés du Transport interagir** boîte de dialogue le **propriétés** onglet, procédez comme suit :  
  
    |**Utilisez cette**|**Pour ce faire**|  
    |------------------|--------------------|  
    |**Arguments**|Type de l’argument suivant : – SagMessagePartner \<interagir de partenaire de Message Client créé dans les trous\> **Remarque :** le client dans l’argument est le MessagePartner que vous avez configuré dans les trous.|  
    |**Mode de chiffrement**|Dans la liste déroulante, sélectionnez **avancé**.|  
    |**LogMessageBody**|Dans la liste déroulante, sélectionnez **FALSE**. **Remarque :** si vous affectez la valeur TRUE, il conserve le corps du message dans la base de données des suivis BizTalk. Toutefois, pour des raisons de sécurité, le corps du message ne peut jamais affiché dans le portail BAM.|  
    |**LogMessages**|Dans la liste déroulante, sélectionnez **TRUE**. Ainsi, les événements de message capturées et de suivi dans le portail BAM.|  
    |**Activer**|True|  
    |**Mot de passe**|Tapez le mot de passe que vous utilisez pour vous connecter à des trous. Pour plus d’informations, consultez l’aide d’anti-COULURE.|  
    |**Nom d’utilisateur**|Tapez le nom d’utilisateur que vous utilisez pour vous connecter à des trous.|  
  
11. Cliquez sur **OK** pour fermer la boîte de dialogue Propriétés du Transport interagir.  
  
12. Sélectionnez **transformer en gestionnaire par défaut** option.  
  
13. Cliquez sur **OK** pour fermer la boîte de dialogue Propriétés du gestionnaire interagir – carte.  
  
14. Dans la boîte de Message, cliquez sur **OK**, puis redémarrez le **BizTalkServerApplication** instance d’hôte.  
  
## <a name="see-also"></a>Voir aussi  
 [Étape 2 : Créer des Ports d’envoi et Ports de réception pour le magasin d’interagir et le scénario de transfert (Pull)](../../adapters-and-accelerators/fileact-interact/step-2-create-send-ports-and-receive-ports-for-the-interact-store-and-forward.md)   
 [Étape 3 : Créer une orchestration avec un port d’envoi dynamique pour le magasin d’interagir et le scénario de (Pull) vers l’avant](../../adapters-and-accelerators/fileact-interact/step-3-create-orchestration-with-dynamic-send-for-interact-store-and-forward.md)   
 [Étape 4 : Tester le scénario de stockage et de redirection (Pull) InterAct de bout en bout](../../adapters-and-accelerators/fileact-interact/step-4-test-the-interact-store-and-forward-pull-end-to-end-scenario.md)