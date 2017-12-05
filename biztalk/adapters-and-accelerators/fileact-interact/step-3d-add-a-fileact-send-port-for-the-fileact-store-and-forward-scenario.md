---
title: "Étape 3D : ajouter un Port d’envoi FILEACT pour et le scénario de transfert de FileAct | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 7366140b-ab89-4bea-9cdb-aa27e8dea8a0
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: a3944c58aecda3d9ea984e0ef0ce9a2bf168ea80
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="step-3d-add-a-fileact-send-port-for-the-fileact-store-and-forward-scenario"></a>Étape 3D : ajouter un Port d’envoi FILEACT pour et le scénario de transfert de FileAct
Avant de commencer cette étape, vous devez effectuer [étape 3c : ajouter un Port d’envoi FILE pour capturer le Sw:HandleFileRequest et les Messages Sw:HandleSnFRequest et le scénario de transfert de FileAct](../../adapters-and-accelerators/fileact-interact/step-3c-add-file-send-port-to-get-sw-handlefilerequest-and-sw-handlesnfrequest.md).  
  
### <a name="to-add-a-fileact-send-port"></a>Pour ajouter un port d’envoi FILEACT  
  
1.  Démarrer **Administration de BizTalk Server**.  
  
2.  Dans l’arborescence de la console, développez le groupe BizTalk, puis développez l’application BizTalk pour laquelle vous souhaitez créer un port d’envoi.  
  
3.  Avec le bouton droit **Ports d’envoi**, pointez sur **nouveau**, puis cliquez sur **Port d’envoi statique avec sollicitation-réponse**.  
  
4.  Dans le **propriétés de Port d’envoi** fenêtre, le nom du port d’envoi Tutorial_FA_SendRequest_SnF.  
  
5.  Dans le **propriétés de Port d’envoi** fenêtre, à partir de la **type de Transport** la liste déroulante, sélectionnez **FILEACT**, puis cliquez sur **configurer**.  
  
6.  Dans le **propriétés du Transport FILEACT** boîte de dialogue zone, procédez comme suit :  
  
    |**Utilisez cette**|**Pour ce faire**|  
    |------------------|--------------------|  
    |**Mot de passe**|Définissez le mot de passe pour la connectivité des trous.|  
    |**Nom d'utilisateur**|Définissez le nom d’utilisateur pour la connectivité des trous.|  
    |**Mode de l’adaptateur**|Dans la liste déroulante, sélectionnez **stocker et transférer**.|  
    |**Indicateur de non répudiation**|Dans la liste déroulante, sélectionnez **FALSE**.|  
    |**Type de demande**|A la valeur approprié \<RequestType\> chaîne, en fonction de votre configuration avec SWIFT.|  
    |**ResponseCrypto**|Dans la liste déroulante, sélectionnez **FALSE**.|  
    |**Demandeur**|A la valeur approprié \<demandeur\> chaîne, en fonction de votre configuration avec SWIFT.|  
    |**Répondeur**|A la valeur approprié \<répondeur\> chaîne.|  
    |**Nom du service**|A la valeur approprié \<nom du service\>.|  
    |**Indicateur d’accusé de réception**|Dans la liste déroulante, sélectionnez **FALSE**.|  
    |**FileCompression**|Dans la liste déroulante, sélectionnez **aucun**.|  
    |**Fin de l’événement**|Tapez le point de terminaison trous approprié.|  
    |**Nom du dossier physique**|Tapez C:\SWIFTAdapterTutorial\Fileact\ClientLocation.|  
    |**Transfert de point de terminaison**|Tapez le point de terminaison approprié pour le jeu de routage trous. Cette valeur doit correspondre au point de terminaison SnL que vous avez configuré dans les trous.|  
    |**Profil_service**|Dans la liste déroulante, sélectionnez **nombre de transactions**.|  
    |**Accusé de réception**|Dans la liste déroulante, sélectionnez **FALSE**.|  
    |**File d’attente de notification**|Tapez le nom de la file d’attente, en fonction de votre configuration avec SWIFT.|  
  
    > [!WARNING]
    >  Si le message avec le nombre de transactions doit être transféré, définir le Mode de profil de Service pour « nombre de transactions » dans le FileAct port d’envoi.  
  
7.  Cliquez sur **OK**.  
  
8.  Dans le **propriétés de Port d’envoi** fenêtre, procédez comme suit :  
  
    |**Utilisez cette**|**Pour ce faire**|  
    |------------------|--------------------|  
    |**Gestionnaire d’envoi**|Dans la liste déroulante, sélectionnez l’hôte Fileact.|  
    |**Pipeline d’envoi**|Dans la liste déroulante, sélectionnez **XMLTransmit**.|  
    |**Pipeline de réception**|Dans la liste déroulante, sélectionnez **XMLReceive**.|  
  
9. Dans le **propriétés de Port d’envoi** fenêtre, dans le **filtres** onglet, procédez comme suit :  
  
    |**Utilisez cette**|**Pour ce faire**|  
    |------------------|--------------------|  
    |**Propriété**|Dans la liste déroulante, sélectionnez **BTS. ReceivePortName**.|  
    |**Opérateur**|Dans la liste déroulante, sélectionnez  **==** .|  
    |**Valeur**|Type Tutorial_FA_InputRequest_SnF.|  
    |**Regrouper par**|Laissez la valeur par défaut.|  
  
10. Cliquez sur **OK**.  
  
## <a name="see-also"></a>Voir aussi  
 [Étape 3 : Créer des Ports d’envoi et Ports de réception d’et le scénario de transfert de FileAct](../../adapters-and-accelerators/fileact-interact/step-3-create-send-ports-and-receive-ports-for-the-fileact-store-and-forward.md)   
 [Étape 3 a : ajouter un fichier emplacement de réception pour et le scénario de transfert de FileAct](../../adapters-and-accelerators/fileact-interact/step-3a-add-a-file-receive-location-for-the-fileact-store-and-forward-scenario.md)   
 [Étape 3 b : ajouter un FILEACT emplacement de réception pour et le scénario de transfert de FileAct](../../adapters-and-accelerators/fileact-interact/step-3b-add-a-fileact-receive-location-for-fileact-store-and-forward-scenario.md)   
 [Étape 3C : Ajouter un port d’envoi FILE pour capturer les messages Sw:HandleFileRequest et Sw:HandleSnFRequest pour le scénario de stockage et de redirection FileAct](../../adapters-and-accelerators/fileact-interact/step-3c-add-file-send-port-to-get-sw-handlefilerequest-and-sw-handlesnfrequest.md)