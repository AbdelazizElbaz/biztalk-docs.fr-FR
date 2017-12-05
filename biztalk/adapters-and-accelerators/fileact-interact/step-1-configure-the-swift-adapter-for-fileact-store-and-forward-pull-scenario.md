---
title: "Étape 1 : Configurer l’adaptateur SWIFT pour le scénario d’extraction vers l’avant et de FileAct | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: fc271544-6bc8-4d62-aba0-3fe3295f2a2a
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 41e57df0f77718e3e36b5d0d68896def6a768be7
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="step-1-configure-the-swift-adapter-for-fileact-store-and-forward-pull-scenario"></a>Étape 1 : Configurer l’adaptateur SWIFT pour le scénario d’extraction avant d’et de FileAct
Complète [préparation à l’utilisation du didacticiel](../../adapters-and-accelerators/fileact-interact/preparing-to-use-the-tutorial1.md) avant de commencer cette étape.
  
## <a name="configure-the-swift-adapter"></a>Configurez la carte SWIFT  
  
1.  Démarrer **Administration de BizTalk Server**.  
  
2.  Dans l’arborescence de la console, développez **Administration de BizTalk Server**, développez le groupe BizTalk, **paramètres de plateforme**, développez **carte**, avec le bouton droit  **FILEACT**, pointez sur **nouveau**, puis cliquez sur **Gestionnaire d’envoi**.  
  
3.  Dans le **FILEACT – carte HandlerProperties** boîte de dialogue le **général** onglet, à partir de la **nom d’hôte** la liste déroulante, sélectionnez **FileActHost**, puis cliquez sur **propriétés**.  
  
4.  Dans le **propriétés du Transport FILEACT** boîte de dialogue le **propriétés** onglet, procédez comme suit :  
  
    |**Utilisez cette**|**Pour ce faire**|  
    |------------------|--------------------|  
    |**Arguments**|Type de l’argument suivant : - SagMessagePartner \<Fileact Client Message partenaire créé dans les trous\> **Remarque :** le client dans l’argument est le MessagePartner que vous avez configuré dans les trous.|  
    |**Mode de chiffrement**|Dans la liste déroulante, sélectionnez **avancé**.|  
    |**FACryptoMode**|Dans la liste déroulante, sélectionnez **avancé**.|  
    |**LogMessages**|Dans la liste déroulante, sélectionnez **TRUE**. Ainsi, les événements de message capturées et de suivi dans le portail BAM.|  
    |**Activer**|False|  
    |**Fin de l’événement**|Tapez le point de terminaison trous approprié.|  
    |**PhysicalFolderName**|Tapez le nom du dossier sur le serveur. Par exemple, C:\Fileact\ServerLocation.|  
    |**PollingInterval**|Tapez la valeur appropriée pour PollingInterval. Par exemple, 5. Cela indique l’intervalle (en secondes) après lequel l’adaptateur vérifie l’état d’un transfert de fichiers.|  
    |**Mot de passe**|Tapez le mot de passe que vous utilisez pour vous connecter à des trous. Pour plus d’informations, consultez l’aide d’anti-COULURE.|  
    |**Nom d'utilisateur**|Tapez le nom d’utilisateur que vous utilisez pour vous connecter à des trous.|  
  
5.  Cliquez sur **OK** pour fermer la boîte de dialogue Propriétés du Transport FILEACT.  
  
6.  Cliquez sur **OK** pour fermer la FILEACT – boîte de dialogue Propriétés de gestionnaire d’adaptateur.  
  
7.  Dans la boîte de Message, cliquez sur **OK**, puis redémarrez l’instance d’hôte FileAct.  
  
8.  Répétez l’étape 1.  
  
9. Dans l’arborescence de la console, développez **Administration de BizTalk Server**, développez le **BizTalk** de groupe, développez **paramètres de plateforme**, développez **carte**, sélectionnez **FILEACT**, ouvrez **BizTalkServerApplication** puis, cliquez sur **propriétés**.  
  
10. Dans le **propriétés du Transport FILEACT** boîte de dialogue le **propriétés** onglet, procédez comme suit :  
  
    |**Utilisez cette**|**Pour ce faire**|  
    |------------------|--------------------|  
    |**Arguments**|Type de l’argument suivant : – SagMessagePartner \<Fileact Client Message partenaire créé dans les trous\> **Remarque :** le client dans l’argument est le MessagePartner que vous avez configuré dans les trous.|  
    |**Mode de chiffrement**|Dans la liste déroulante, sélectionnez **avancé**.|  
    |**LogMessageBody**|Dans la liste déroulante, sélectionnez **TRUE**. Ainsi, les événements de message capturées et de suivi dans le portail BAM. **Remarque :** si vous affectez la valeur TRUE, il conserve le corps du message dans la base de données des suivis BizTalk. Toutefois, pour des raisons de sécurité, le corps du message ne peut jamais affiché dans le portail BAM.|  
    |**LogMessages**|Dans la liste déroulante, sélectionnez **TRUE**. Ainsi, les événements de message capturées et de suivi dans le portail BAM.|  
    |**Activer**|**True**|  
    |**Fin de l’événement**|Tapez le point de terminaison trous approprié.|  
    |**PhysicalFolderName**|Tapez le nom du dossier sur le serveur. Par exemple, C:\Fileact\ServerLocation.|  
    |**PollingInterval**|Tapez la valeur appropriée pour PollingInterval. Par exemple, 5. Cela indique l’intervalle (en secondes) après lequel l’adaptateur vérifie l’état d’un transfert de fichiers.|  
    |**Mot de passe**|Tapez le mot de passe que vous utilisez pour vous connecter à des trous. Pour plus d’informations, consultez l’aide d’anti-COULURE.|  
    |**Nom d’utilisateur**|Tapez le nom d’utilisateur que vous utilisez pour vous connecter à des trous.|  
  
11. Cliquez sur OK pour fermer la boîte de dialogue Propriétés du Transport FILEACT.  
  
12. Sélectionnez rendre cette option gestionnaire par défaut.  
  
13. Cliquez sur OK pour fermer la FILEACT – boîte de dialogue Propriétés de gestionnaire d’adaptateur.  
  
14. Dans la boîte de Message, cliquez sur OK et redémarrez l’instance de l’hôte BizTalkServerApplication.  
  
## <a name="see-also"></a>Voir aussi  
 [Étape 2 : Créer des Ports d’envoi et réception des Ports pour le magasin de FileAct et d’un scénario de transfert (extraction de données)](../../adapters-and-accelerators/fileact-interact/step-2-create-send-and-receive-ports-for-fileact-store-and-forward-scenario.md)   
 [Étape 3 : Créer et lier une orchestration avec un port d’envoi dynamique pour le magasin de fichiers Act et le scénario de (Pull) vers l’avant](../../adapters-and-accelerators/fileact-interact/step-3-create-and-bind-an-orchestration-with-dynamic-send-port-for-file-act.md)   
 [Étape 4 : Tester le scénario de stockage et de redirection (Pull) FileAct de bout en bout](../../adapters-and-accelerators/fileact-interact/step-4-test-fileact-store-and-forward-pull-end-to-end-scenario.md)