---
title: "Étape 3 b : ajouter un interagir emplacement de réception pour le scénario en temps réel d’interagir | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 59780635-e1b6-4e74-a89a-73ec26d6c670
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: fa1a98f97cba9f46b43b92128a6585ad18afb894
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="step-3b-add-an-interact-receive-location-for-the-interact-real-time-scenario"></a>Étape 3 b : ajouter un interagir emplacement de réception pour l’interaction scénario en temps réel
Complète [étape 3 a : ajouter un emplacement de réception de fichier pour le scénario en temps réel interagir](../../adapters-and-accelerators/fileact-interact/step-3a-add-a-file-receive-location-for-the-interact-real-time-scenario.md) avant de commencer cette étape.
  
## <a name="add-an-interact-receive-location"></a>Ajouter l’emplacement de réception un INTERACT  
  
1.  Démarrer **Administration de BizTalk Server**.  
  
2.  Dans l’arborescence de la console, développez le groupe BizTalk, puis développez l’application BizTalk pour laquelle vous souhaitez créer un port de réception.  
  
3.  Avec le bouton droit **Ports de réception**, pointez sur **nouveau**, puis cliquez sur **Port de réception unidirectionnel.**  
  
4.  Dans le **propriétés du Port de réception** fenêtre, le nom du port de réception, **Tutorial_IA_HandleRequestOneWay_RealTime**.  
  
5.  Dans le **propriétés du Port de réception** fenêtre, dans le **emplacements de réception** , cliquez sur **nouveau**.  
  
6.  Dans le **propriétés de l’emplacement de réception** fenêtre, dans le **général** onglet, à partir de la **type de Transport** la liste déroulante, sélectionnez **interagir**, puis cliquez sur **configurer**.  
  
7.  Dans le **propriétés du Transport interagir** boîte de dialogue zone, procédez comme suit :  
  
    |**Utilisez cette**|**Pour ce faire**|  
    |------------------|--------------------|  
    |**Mot de passe**|Tapez le mot de passe que vous utilisez pour vous connecter à des trous. Pour plus d’informations, consultez l’aide d’anti-COULURE.|  
    |**Nom d'utilisateur**|Tapez le nom d’utilisateur que vous utilisez pour vous connecter à des trous.|  
    |**Nom de l’application**|Le serveur de type \< *nom de l’Interface* \> pour les trous zone jeu de routage.|  
    |**Mode de chiffrement**|Dans la liste déroulante, sélectionnez **avancé**.|  
    |**LogMessageBody**|Dans la liste déroulante, sélectionnez **FALSE**. **Remarque :** si vous affectez la valeur TRUE, il conserve le corps du message dans la base de données de suivi. Toutefois, pour des raisons de sécurité, le corps du message ne peut jamais affiché dans le portail BAM.|  
    |**LogMessages**|Dans la liste déroulante, sélectionnez **TRUE**. Ainsi, les événements de message capturées et de suivi dans le portail BAM.|  
    |**Format de message**|Dans la liste déroulante, sélectionnez **InterActMessage**.|  
    |**MemberRef**|Dans la liste déroulante, sélectionnez **ResponseHeader**.|  
    |**Indicateur de non répudiation**|Dans la liste déroulante, sélectionnez **FALSE**.|  
    |**Répondeur**|Tapez la commande appropriée \< *ResponderDN* \> chaîne, en fonction de votre configuration avec SWIFT.|  
    |**ResponseCrypto**|Dans la liste déroulante, sélectionnez **FALSE**.|  
    |**Délai d'expiration**|Type d’un nombre approprié de secondes avant le délai de connexion doit se produire.|  
    |**Acquisition de file d’attente**|Laissez la valeur par défaut de cette propriété. Cette propriété est utilisée pour les scénarios de stockage et de transfert.|  
    |**ForceAcquire**|Laissez la valeur par défaut de cette propriété. Cette propriété est utilisée pour les scénarios de stockage et de transfert.|  
    |**Trier par**|Laissez la valeur par défaut de cette propriété. Cette propriété est utilisée pour les scénarios de stockage et de transfert.|  
    |**Session push**|Laissez la valeur par défaut de cette propriété. Cette propriété est utilisée pour les scénarios de stockage et de transfert.|  
    |**En mode de récupération**|Laissez la valeur par défaut de cette propriété. Cette propriété est utilisée pour les scénarios de stockage et de transfert.|  
    |**Point d’arrêt SNL**|Laissez la valeur par défaut de cette propriété. Cette propriété est utilisée pour les scénarios de stockage et de transfert.|  
  
8.  Cliquez sur **OK**.  
  
9. Dans le **propriétés de l’emplacement de réception** fenêtre, dans le **général** onglet, procédez comme suit :  
  
    |**Utilisez cette**|**Pour ce faire**|  
    |------------------|--------------------|  
    |**Gestionnaire de réception**|Dans la liste déroulante, sélectionnez **BizTalkServerIsolatedHost**.|  
    |**Pipeline de réception**|Dans la liste déroulante, sélectionnez **XMLReceive**.|  
  
10. Cliquez sur **OK**.  
  
## <a name="see-also"></a>Voir aussi  
 [Étape 3 : Créer l’envoi et Ports de réception l’interaction du scénario en temps réel](../../adapters-and-accelerators/fileact-interact/step-3-create-send-and-receive-ports-for-the-interact-real-time-scenario.md)   
 [Étape 3 a : ajouter un fichier emplacement de réception pour l’interaction du scénario en temps réel](../../adapters-and-accelerators/fileact-interact/step-3a-add-a-file-receive-location-for-the-interact-real-time-scenario.md)   
 [Étape 3c : ajouter un Port d’envoi FILE pour capturer le Message Sw:HandleRequest pour l’interaction du scénario en temps réel](../../adapters-and-accelerators/fileact-interact/step-3c-add-file-send-port-to-get-sw-handlerequest-interact-real-time-scenario.md)   
 [Étape 3D : ajouter un Port d’envoi FILE pour capturer le Message Sw:HandleResponse pour l’interaction du scénario en temps réel](../../adapters-and-accelerators/fileact-interact/step-3d-add-file-send-port-to-get-sw-handleresponse-message-for-interact.md)   
 [Étape 3E : Ajouter un port d’envoi INTERACT pour le scénario en temps réel InterAct](../../adapters-and-accelerators/fileact-interact/step-3e-add-an-interact-send-port-for-the-interact-real-time-scenario.md)