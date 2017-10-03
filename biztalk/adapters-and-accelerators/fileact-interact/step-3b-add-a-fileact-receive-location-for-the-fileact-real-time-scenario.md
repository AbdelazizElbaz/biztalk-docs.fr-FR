---
title: "Étape 3 b : ajouter un FILEACT emplacement de réception pour le scénario en temps réel FileAct | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 7e086c86-1525-4cef-b7e5-a66e14bd8d4f
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: d97c2f58639814bda45a23c115fea0c3708c2579
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="step-3b-add-a-fileact-receive-location-for-the-fileact-real-time-scenario"></a>Étape 3 b : ajouter un FILEACT emplacement de réception pour le scénario en temps réel FileAct
Avant de commencer cette étape, vous devez effectuer [étape 3 a : ajouter un emplacement de réception de fichier pour le scénario en temps réel de FileAct](../../adapters-and-accelerators/fileact-interact/step-3a-add-a-file-receive-location-for-the-fileact-real-time-scenario.md).  
  
### <a name="to-add-a-fileact-receive-location"></a>Pour ajouter l’emplacement de réception un FILEACT  
  
1.  Démarrer **Administration de BizTalk Server**.  
  
2.  Dans l’arborescence de la console, développez le groupe BizTalk, puis développez l’application BizTalk pour laquelle vous souhaitez créer un port de réception.  
  
3.  Avec le bouton droit **Ports de réception**, pointez sur **nouveau**, puis cliquez sur **Port de réception unidirectionnel.**  
  
4.  Dans le **propriétés du Port de réception** fenêtre, nom du port de réception, Tutorial_FA_HandleRequestOneWay_RealTime.  
  
5.  Dans le **propriétés du Port de réception** fenêtre, dans le **emplacements de réception** , cliquez sur **nouveau**.  
  
6.  Dans le **propriétés de l’emplacement de réception** fenêtre, dans le **général** onglet, à partir de la **type de Transport** la liste déroulante, sélectionnez **FILEACT**, et puis cliquez sur **configurer**.  
  
7.  Dans le **propriétés du Transport FILEACT** boîte de dialogue zone, procédez comme suit :  
  
    |**Utilisez cette**|**Pour ce faire**|  
    |------------------|--------------------|  
    |**Mot de passe**|Tapez le mot de passe que vous utilisez pour vous connecter à des trous. Pour plus d’informations, consultez l’aide d’anti-COULURE.|  
    |**Nom d'utilisateur**|Tapez le nom d’utilisateur que vous utilisez pour vous connecter à des trous.|  
    |**Nom de l’application**|Le serveur de type \<Interface nom_application > pour les trous zone jeu de routage.|  
    |**Mode de chiffrement**|Dans la liste déroulante, sélectionnez **avancé**.|  
    |**Mode FACrypto**|Dans la liste déroulante, sélectionnez **avancé**.|  
    |**LogMessages**|Dans la liste déroulante, sélectionnez **TRUE**. Ainsi, les événements de message capturées et de suivi dans le portail BAM.|  
    |**MemberRef**|Dans la liste déroulante, sélectionnez **ResponsePayload**.|  
    |**Indicateur de non répudiation**|Dans la liste déroulante, sélectionnez **FALSE**.|  
    |**Répondeur**|Tapez la commande appropriée \<répondeur > chaîne, en fonction de votre configuration avec SWIFT.|  
    |**ResponseCrypto**|Dans la liste déroulante, sélectionnez **FALSE**.|  
    |**Indicateur d’accusé de réception**|Dans la liste déroulante, sélectionnez **ResponsePayload**.|  
    |**FileCompression**|Dans la liste déroulante, sélectionnez **aucun**.|  
    |**PhysicalFolderName**|Tapez le nom du dossier sur le serveur. Par exemple, C:\Fileact\ServerLocation.|  
    |**SubscribeFileEvents**|Dans la liste déroulante, sélectionnez **FALSE**.|  
    |**TransferAnswer**|Dans la liste déroulante, sélectionnez **accepté**.|  
    |**AllFileEvents**|Dans la liste déroulante, sélectionnez **TRUE**.|  
    |**Fin de l’événement**|Tapez le point de terminaison approprié pour le jeu de routage trous. Cette valeur doit correspondre au point de terminaison SnL que vous avez configuré dans les trous.|  
    |**FullFileStatus**|Dans la liste déroulante, sélectionnez **TRUE**.|  
    |**Délai d'expiration**|Tapez un nombre approprié de secondes avant le délai d’expiration doit se produire.|  
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
 [Étape 3 : Créer les Ports d’envoi et Ports de réception pour le scénario en temps réel FileAct](../../adapters-and-accelerators/fileact-interact/step-3-create-the-send-ports-and-receive-ports-for-fileact-real-time-scenario.md)   
 [Étape 3 a : ajouter un fichier emplacement de réception pour le scénario en temps réel FileAct](../../adapters-and-accelerators/fileact-interact/step-3a-add-a-file-receive-location-for-the-fileact-real-time-scenario.md)   
 [Étape 3c : ajouter un Port d’envoi FILE pour capturer les messages Sw:HandleRequest pour le scénario en temps réel FileAct](../../adapters-and-accelerators/fileact-interact/step-3c-add-file-send-port-to-get-sw-handlerequest-message-for-fileact.md)   
 [Étape 3D : ajouter un Port d’envoi FILEACT pour le scénario en temps réel FileAct](../../adapters-and-accelerators/fileact-interact/step-3d-add-a-fileact-send-port-for-the-fileact-real-time-scenario.md)   
 [Étape 3E : ajouter un Port d’envoi FILE pour capturer les messages Sw:ExchangeFileResponse pour le scénario en temps réel FileAct](../../adapters-and-accelerators/fileact-interact/step-3e-add-file-send-port-to-get-sw-exchangefileresponse-message-for-fileact.md)