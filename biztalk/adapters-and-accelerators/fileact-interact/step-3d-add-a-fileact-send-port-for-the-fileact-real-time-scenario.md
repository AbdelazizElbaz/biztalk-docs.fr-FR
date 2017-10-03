---
title: "Étape 3D : ajouter un Port d’envoi FILEACT pour le scénario en temps réel FileAct | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 8a22ba41-4f43-4fbb-92f7-a0fd7558d2ce
caps.latest.revision: "11"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: f3ab2de6dabd581cb36d23ce218fb1b902ac04e5
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="step-3d-add-a-fileact-send-port-for-the-fileact-real-time-scenario"></a>Étape 3D : ajouter un Port d’envoi FILEACT pour le scénario en temps réel FileAct
Avant de commencer cette étape, vous devez effectuer [étape 3c : ajouter un Port d’envoi FILE à capturer le Message Sw:HandleRequest pour le scénario en temps réel de FileAct](../../adapters-and-accelerators/fileact-interact/step-3c-add-file-send-port-to-get-sw-handlerequest-message-for-fileact.md).  
  
### <a name="to-add-a-fileact-send-port"></a>Pour ajouter un port d’envoi FILEACT  
  
1.  Démarrer **Administration de BizTalk Server**.  
  
2.  Dans l’arborescence de la console, développez le groupe BizTalk, puis développez l’application BizTalk pour laquelle vous souhaitez créer un port d’envoi.  
  
3.  Avec le bouton droit **Ports d’envoi**, pointez sur **nouveau**, puis cliquez sur **Port d’envoi statique avec sollicitation-réponse**.  
  
4.  Dans le **propriétés de Port d’envoi** fenêtre, le nom du port d’envoi Tutorial_FA_SendRequest_RealTime.  
  
5.  Dans le **propriétés de Port d’envoi** fenêtre, à partir de la **type de Transport** la liste déroulante, sélectionnez **FILEACT**, puis cliquez sur **configurer**.  
  
6.  Dans le **propriétés du Transport FILEACT** boîte de dialogue zone, procédez comme suit :  
  
    |**Utilisez cette**|**Pour ce faire**|  
    |------------------|--------------------|  
    |**Mot de passe**|Définissez le mot de passe pour la connectivité des trous.|  
    |**Nom d'utilisateur**|Définissez le nom d’utilisateur pour la connectivité des trous.|  
    |**Mode de l’adaptateur**|Dans la liste déroulante, sélectionnez **stocker et transférer**.|  
    |**Indicateur de non répudiation**|Dans la liste déroulante, sélectionnez **FALSE**.|  
    |**Type de demande**|A la valeur approprié \<RequestType > chaîne, en fonction de votre configuration avec SWIFT.|  
    |**ResponseCrypto**|Dans la liste déroulante, sélectionnez **FALSE**.|  
    |**Demandeur**|A la valeur approprié \<demandeur > chaîne, en fonction de votre configuration avec SWIFT.|  
    |**Répondeur**|A la valeur approprié \<répondeur > chaîne selon votre configuration avec SWIFT.|  
    |**Nom du service**|A la valeur approprié \<nom service > en fonction de votre configuration avec SWIFT.|  
    |**Indicateur d’accusé de réception**|Dans la liste déroulante, sélectionnez **FALSE**.|  
    |**Fin de l’événement**|Dans la liste déroulante, sélectionnez **FALSE**.|  
    |**Compression de fichiers**|Dans la liste déroulante, sélectionnez **aucun**.|  
    |**Nom du dossier physique**|Tapez C:\SWIFTAdapterTutorial\Fileact\ClientLocation.|  
    |**Transfert de point de terminaison**|Tapez le point de terminaison approprié pour le jeu de routage trous. Cette valeur doit correspondre au point de terminaison SnL que vous avez configuré dans les trous.|  
    |**Profil_service**|Dans la liste déroulante, sélectionnez **nombre de transactions**.|  
    |**Accusé de réception**|Dans la liste déroulante, sélectionnez **FALSE**.|  
    |**File d’attente de notification**|Tapez le nom de la file d’attente, en fonction de votre configuration avec SWIFT.|  
  
    > [!NOTE]
    >  Si le message avec le nombre de transactions doit être transféré, définir le Mode de profil de Service pour « nombre de transactions » dans le FileAct port d’envoi.  
  
7.  Cliquez sur **OK**.  
  
8.  Dans le **propriétés de Port d’envoi** fenêtre, procédez comme suit :  
  
    |**Utilisez cette**|**Pour ce faire**|  
    |------------------|--------------------|  
    |**Gestionnaire d’envoi**|Dans la liste déroulante, sélectionnez l’hôte Fileact.|  
    |**Pipeline d’envoi**|Dans la liste déroulante, sélectionnez **XMLTransmit**.|  
    |**Pipeline de réception**|Dans la liste déroulante, sélectionnez **XMLReceive**.|  
  
9. Dans la fenêtre Propriétés de Port d’envoi, sur le **filtres** onglet, procédez comme suit :  
  
    |**Utilisez cette**|**Pour ce faire**|  
    |------------------|--------------------|  
    |**Propriété**|Dans la liste déroulante, sélectionnez **BTS. ReceivePortName**.|  
    |**Opérateur**|Dans la liste déroulante, sélectionnez  **==** .|  
    |**Valeur**|Type Tutorial_FA_InputRequest_RealTime.|  
    |**Regrouper par**|Laissez la valeur par défaut.|  
  
10. Cliquez sur **OK**.  
  
## <a name="see-also"></a>Voir aussi  
 [Étape 3 : Créer les Ports d’envoi et Ports de réception pour le scénario en temps réel FileAct](../../adapters-and-accelerators/fileact-interact/step-3-create-the-send-ports-and-receive-ports-for-fileact-real-time-scenario.md)   
 [Étape 3 a : ajouter un fichier emplacement de réception pour le scénario en temps réel FileAct](../../adapters-and-accelerators/fileact-interact/step-3a-add-a-file-receive-location-for-the-fileact-real-time-scenario.md)   
 [Étape 3 b : ajouter un FILEACT emplacement de réception pour le scénario en temps réel FileAct](../../adapters-and-accelerators/fileact-interact/step-3b-add-a-fileact-receive-location-for-the-fileact-real-time-scenario.md)   
 [Étape 3c : ajouter un Port d’envoi FILE pour capturer les messages Sw:HandleRequest pour le scénario en temps réel FileAct](../../adapters-and-accelerators/fileact-interact/step-3c-add-file-send-port-to-get-sw-handlerequest-message-for-fileact.md)   
 [Étape 3E : ajouter un Port d’envoi FILE pour capturer les messages Sw:ExchangeFileResponse pour le scénario en temps réel FileAct](../../adapters-and-accelerators/fileact-interact/step-3e-add-file-send-port-to-get-sw-exchangefileresponse-message-for-fileact.md)