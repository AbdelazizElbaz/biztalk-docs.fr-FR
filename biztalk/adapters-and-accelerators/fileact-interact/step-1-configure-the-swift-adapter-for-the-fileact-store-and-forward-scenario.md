---
title: "Étape 1 : Configurer l’adaptateur SWIFT pour et le scénario de transfert de FileAct | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 18653322-b748-4954-93f7-9a7a39e406f8
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 3d2946bcd37e0e7641a2d3bf750f88cd3199fc74
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="step-1-configure-the-swift-adapter-for-the-fileact-store-and-forward-scenario"></a>Étape 1 : Configurer l’adaptateur SWIFT pour et le scénario de transfert de FileAct
Complète [préparation à l’utilisation du didacticiel](../../adapters-and-accelerators/fileact-interact/preparing-to-use-the-tutorial1.md) avant de commencer cette étape.
  
## <a name="configure-the-swift-adapter"></a>Configurez la carte SWIFT  
  
1.  Démarrer **Administration de BizTalk Server**.  
  
2.  Dans l’arborescence de la console, développez **Administration de BizTalk Server**, développez le groupe BizTalk, **paramètres de plateforme**, développez **carte**, avec le bouton droit  **FILEACT**, pointez sur **nouveau**, puis cliquez sur **Gestionnaire d’envoi**.  
  
3.  Dans le **FILEACT – carte HandlerProperties** boîte de dialogue le **général** onglet, à partir de la **nom d’hôte** la liste déroulante, sélectionnez **fileacthost**, puis cliquez sur **propriétés**.  
  
4.  Dans le **propriétés du Transport FILEACT** boîte de dialogue le **propriétés** onglet, procédez comme suit :  
  
    |**Utilisez cette**|**Pour ce faire**|  
    |------------------|--------------------|  
    |**Arguments**|Type de l’argument suivant : - SagMessagePartner \<Fileact Client Message partenaire créé dans les trous > **Remarque :** le client dans l’argument est le MessagePartner que vous avez configuré dans les trous.|  
    |**Mode de chiffrement**|Dans la liste déroulante, sélectionnez **avancé**.|  
    |**FACryptoMode**|Dans la liste déroulante, sélectionnez **avancé**.|  
    |**LogMessages**|Dans la liste déroulante, sélectionnez **TRUE**. Ainsi, les événements de message capturées et de suivi dans le portail BAM.|  
    |**Activer**|False|  
    |**Fin de l’événement**|Tapez le point de terminaison trous approprié.|  
    |**PhysicalFolderName**|Tapez le nom du dossier sur le serveur. Par exemple, C:\Fileact\ServerLocation.|  
    |**PollingInterval**|Tapez l’intervalle approprié (en secondes) après lequel l’adaptateur vérifie pour l’état du transfert de fichiers.|  
    |**Mot de passe**|Tapez le mot de passe que vous utilisez pour vous connecter à des trous. Pour plus d’informations, consultez l’aide d’anti-COULURE.|  
    |**Nom d'utilisateur**|Tapez le nom d’utilisateur que vous utilisez pour vous connecter à des trous.|  
  
5.  Cliquez sur **OK** pour fermer la boîte de dialogue Propriétés du Transport FILEACT.  
  
6.  Cliquez sur **OK** pour fermer la FILEACT – boîte de dialogue Propriétés de gestionnaire d’adaptateur.  
  
7.  Dans la boîte de Message, cliquez sur **OK**, puis redémarrez l’instance d’hôte FileAct.  
  
## <a name="complete-steps"></a>Étapes à suivre
 [Scénario de transfert et de FileAct](../../adapters-and-accelerators/fileact-interact/fileact-store-and-forward-scenario.md)   
 [Étape 2 : Ajouter SWIFTNet Configuration pour le Paramfile pour et le scénario de transfert de FileAct](../../adapters-and-accelerators/fileact-interact/step-2-add-swiftnet-configuration-to-paramfile-for-fileact-store-and-forward.md)   
 [Étape 3 : Créer des Ports d’envoi et Ports de réception d’et le scénario de transfert de FileAct](../../adapters-and-accelerators/fileact-interact/step-3-create-send-ports-and-receive-ports-for-the-fileact-store-and-forward.md)   
 [Étape 4 : Tester et de scénario de bout en bout avant de FileAct](../../adapters-and-accelerators/fileact-interact/step-4-test-fileact-store-and-forward-end-to-end-scenario.md)