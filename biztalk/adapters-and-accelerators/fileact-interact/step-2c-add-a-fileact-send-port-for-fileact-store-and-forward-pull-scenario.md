---
title: "Étape 2c : ajouter un Port d’envoi FILEACT pour et le scénario de transfert (Pull) de FileAct | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 8743a868-9625-477b-a7da-673bfa262723
caps.latest.revision: "4"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 55db4fcd1a6a65ac9058a69f9c315de593181a65
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="step-2c-add-a-fileact-send-port-for-the-fileact-store-and-forward-pull-scenario"></a>Étape 2c : ajouter un Port d’envoi FILEACT pour et le scénario de transfert (Pull) de FileAct
Avant de commencer cette étape, vous devez effectuer [étape 2 b : ajouter des Ports d’envoi FILE pour capturer le Sw:HandleFileRequest et les Messages Sw:HandleSnFRequest et le scénario de (extraits) avant de FileAct](../../adapters-and-accelerators/fileact-interact/step-2b-add-file-send-ports--get-sw-handlefilerequest-and-sw-handlesnfrequest.md).  
  
### <a name="to-add-a-fileact-send-port"></a>Pour ajouter un port d’envoi FileACT  
  
1.  Démarrer **Administration de BizTalk Server**.  
  
2.  Dans l’arborescence de la console, développez le groupe BizTalk, puis développez l’application BizTalk pour laquelle vous souhaitez créer un port d’envoi.  
  
3.  Avec le bouton droit **Ports d’envoi**, pointez sur **nouveau**, puis cliquez sur **Port d’envoi statique avec sollicitation-réponse**.  
  
4.  Dans le **propriétés de Port d’envoi** fenêtre, le nom du port d’envoi **Tutorial_FA_SendRequest_SnF**.  
  
5.  Dans le **propriétés de Port d’envoi** fenêtre, à partir de la **type de Transport** la liste déroulante, sélectionnez **FILEACT**, puis cliquez sur **configurer**.  
  
6.  Dans le **propriétés du Transport FILEACT** boîte de dialogue zone, procédez comme suit :  
  
    |**Utilisez cette**|**Pour ce faire**|  
    |------------------|--------------------|  
    |**Mot de passe**|Définissez le mot de passe pour la connectivité des trous.|  
    |**Nom d'utilisateur**|Définissez le nom d’utilisateur pour la connectivité des trous.|  
    |**Mode de l’adaptateur**|Dans la liste déroulante, sélectionnez **stocker et transférer**.|  
    |**Indicateur de non répudiation**|Dans la liste déroulante, sélectionnez **FALSE**.|  
    |**Type de demande**|A la valeur approprié \<RequestType > chaîne, en fonction de votre configuration avec SWIFT.|  
    |**RequestCrypto**|Dans la liste déroulante, sélectionnez **FALSE**.|  
    |**Demandeur**|A la valeur approprié \<demandeur > chaîne, en fonction de votre configuration avec SWIFT.|  
    |**Répondeur**|A la valeur approprié \<répondeur > chaîne.|  
    |**Nom du service**|A la valeur approprié  **\<nom service >**.|  
    |**Indicateur d’accusé de réception**|Dans la liste déroulante, sélectionnez **FALSE**.|  
    |**Fin de l’événement**|Dans la liste déroulante, sélectionnez **FALSE**.|  
    |**Compression de fichiers**|Dans la liste déroulante, sélectionnez **aucun**.|  
    |**Nom du dossier physique**|Tapez C:\SWIFTAdapterTutorial\Fileact\ClientLocation.|  
    |**Transfert de point de terminaison**|Tapez le point de terminaison approprié pour le jeu de routage trous. Cette valeur doit correspondre au point de terminaison SNL que vous avez configuré dans les trous.|  
    |**Profil_service**|Dans la liste déroulante, sélectionnez **nombre de transactions**.|  
    |**Accusé de réception**|Dans la liste déroulante, sélectionnez **FALSE**.|  
    |**File d’attente de notification**|Tapez le nom de la file d’attente, en fonction de votre configuration avec SWIFT.|  
  
    > [!NOTE]
    >  Si le message avec le nombre de transactions doit être transféré, définir le Mode de profil de Service pour « nombre de transactions » dans le FileAct port d’envoi.  
  
7.  Cliquez sur **OK**.  
  
8.  Dans le **propriétés de Port d’envoi** fenêtre, procédez comme suit :  
  
    |**Utilisez cette**|**Pour ce faire**|  
    |------------------|--------------------|  
    |**Gestionnaire d’envoi**|Dans la liste déroulante, sélectionnez le **FileActHost**.|  
    |**Pipeline d’envoi**|Dans la liste déroulante, sélectionnez **XMLTransmit**.|  
    |**Pipeline de réception**|Dans la liste déroulante, sélectionnez **XMLReceive**.|  
  
9. Dans le **propriétés de Port d’envoi** fenêtre, dans le **filtres** onglet, procédez comme suit :  
  
    |**Utilisez cette**|**Pour ce faire**|  
    |------------------|--------------------|  
    |**Propriété**|Dans la liste déroulante, sélectionnez **BTS. ReceivePortName**.|  
    |**Opérateur**|Dans la liste déroulante, sélectionnez  **==** .|  
    |**Valeur**|Type **Tutorial_IA_InputRequest_SnF**.|  
    |**Regrouper par**|Laissez la valeur par défaut.|  
  
10. Cliquez sur **OK**.  
  
## <a name="see-also"></a>Voir aussi  
 [Étape 2 a : ajouter le fichier emplacements de réception pour le magasin de FileAct et d’un scénario de transfert (extraction de données)](../../adapters-and-accelerators/fileact-interact/step-2a-add-file-receive-locations-for-fileact-store-and-forward-scenario.md)   
 [Étape 2 b : ajouter des Ports d’envoi FILE pour capturer le Sw:HandleFileRequest et scénario Sw:HandleSnFRequest des Messages pour le magasin de FileAct et le transfert (Pull)](../../adapters-and-accelerators/fileact-interact/step-2b-add-file-send-ports--get-sw-handlefilerequest-and-sw-handlesnfrequest.md)