---
title: "Étape 3 b : ajouter un interagir emplacement de réception pour le magasin d’interagir et scénario avant | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: da077518-b2ee-4b5f-88d0-fe73af2baa7a
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 5f6f0ffd20dba192a038981469164f63cdd7593f
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="step-3b-add-an-interact-receive-location-for-the-interact-store-and-forward-scenario"></a>Étape 3 b : ajouter un interagir emplacement de réception pour le magasin d’interagir et d’un scénario avant
Complète [étape 3 a : ajouter un emplacement de réception de fichier pour le magasin d’interagir et le scénario par progression](../../adapters-and-accelerators/fileact-interact/step-3a-add-a-file-receive-location-for-interact-store-and-forward-scenario.md) avant de commencer cette étape.
  
## <a name="add-an-interact-receive-location"></a>Ajouter l’emplacement de réception un INTERACT  
  
1.  Démarrer **Administration de BizTalk Server**.  
  
2.  Dans l’arborescence de la console, développez le groupe BizTalk, puis développez l’application BizTalk pour laquelle vous souhaitez créer un port de réception.  
  
3.  Avec le bouton droit **Ports de réception**, pointez sur **nouveau**, puis cliquez sur **Port de réception unidirectionnel.**  
  
4.  Dans le **propriétés du Port de réception** fenêtre, nom du port de réception, Tutorial_IA_HandleRequestOneWay_SnF.  
  
5.  Dans le **propriétés du Port de réception** fenêtre, dans le **emplacements de réception** , cliquez sur **nouveau**.  
  
6.  Dans le **propriétés de l’emplacement de réception** fenêtre, dans le **général** onglet, à partir de la **type de Transport** la liste déroulante, sélectionnez **interagir**, puis cliquez sur **configurer**.  
  
7.  Dans le **propriétés du Transport interagir** boîte de dialogue zone, procédez comme suit :  
  
    |**Utilisez cette**|**Pour ce faire**|  
    |------------------|--------------------|  
    |**Mot de passe**|Tapez le mot de passe que vous utilisez pour vous connecter à des trous. Pour plus d’informations, consultez l’aide d’anti-COULURE.|  
    |**Nom d'utilisateur**|Tapez le nom d’utilisateur que vous utilisez pour vous connecter à des trous.|  
    |**Nom de l’application**|Le serveur de type \<Interface nom_application > pour les trous zone jeu de routage.|  
    |**Mode de chiffrement**|Dans la liste déroulante, sélectionnez **avancé**.|  
    |**LogMessageBody**|Dans la liste déroulante, sélectionnez **FALSE**. **Remarque :** si vous affectez la valeur TRUE, il conserve le corps du message dans la base de données des suivis BizTalk. Toutefois, pour des raisons de sécurité, le corps du message ne peut jamais affiché dans le portail BAM.|  
    |**LogMessages**|Dans la liste déroulante, sélectionnez **TRUE**. Ainsi, les événements de message capturées et de suivi dans le portail BAM.|  
    |**Format de message**|Dans la liste déroulante, sélectionnez **InterActMessage**.|  
    |**MemberRef**|Dans la liste déroulante, sélectionnez **ResponseHeader**.|  
    |**Indicateur de non répudiation**|Dans la liste déroulante, sélectionnez **FALSE**.|  
    |**Répondeur**|Tapez la commande appropriée \<répondeur > chaîne, en fonction de votre configuration avec SWIFT.|  
    |**ResponseCrypto**|Dans la liste déroulante, sélectionnez **FALSE**.|  
    |**Délai d'expiration**|Tapez un nombre approprié de secondes avant le délai d’expiration doit se produire.|  
    |**Acquisition de file d’attente**|Tapez le nom de la file d’attente, en fonction de votre configuration avec SWIFT.|  
    |**ForceAcquire**|Dans la liste déroulante, sélectionnez **TRUE**.|  
    |**Trier par**|Dans la liste déroulante, sélectionnez **interagir**.|  
    |**Session push**|Dans la liste déroulante, sélectionnez **TRUE**.|  
    |**En mode de récupération**|Dans la liste déroulante, sélectionnez **TRUE**.|  
    |**Point d’arrêt SNL**|Tapez le point de terminaison approprié pour le jeu de routage trous. Cette valeur doit correspondre au point de terminaison SnL que vous avez configuré dans les trous.|  
  
8.  Cliquez sur **OK**.  
  
9. Dans le **propriétés de l’emplacement de réception** fenêtre, dans le **général** onglet, procédez comme suit :  
  
    |**Utilisez cette**|**Pour ce faire**|  
    |------------------|--------------------|  
    |**Gestionnaire de réception**|Dans la liste déroulante, sélectionnez **BizTalkServerIsolatedHost**.|  
    |**Pipeline de réception**|Dans la liste déroulante, sélectionnez **XMLReceive**.|  
  
10. Cliquez sur **OK**.  
  
## <a name="complete-steps"></a>Étapes à suivre
 [Étape 3 : Créer des Ports d’envoi et Ports de réception pour le magasin d’interagir et d’un scénario avant](../../adapters-and-accelerators/fileact-interact/step-3-create-send-and-receive-ports-for-interact-store-and-forward-scenario.md)   
 [Étape 3 a : ajouter un fichier emplacement de réception pour le magasin d’interagir et d’un scénario avant](../../adapters-and-accelerators/fileact-interact/step-3a-add-a-file-receive-location-for-interact-store-and-forward-scenario.md)   
 [Étape 3c : ajouter un Port d’envoi FILE pour capturer le Message Sw:HandleRequest pour le magasin d’interagir et le scénario avant](../../adapters-and-accelerators/fileact-interact/step-3c-add-file-send-port-to-get-sw-handlerequest-interact-store-and-forward.md)  
 [Étape 3D : ajouter un Port d’envoi interagissent pour le magasin d’interagir et le scénario avant](../../adapters-and-accelerators/fileact-interact/step-3d-add-an-interact-send-port-for-the-interact-store-and-forward-scenario.md)