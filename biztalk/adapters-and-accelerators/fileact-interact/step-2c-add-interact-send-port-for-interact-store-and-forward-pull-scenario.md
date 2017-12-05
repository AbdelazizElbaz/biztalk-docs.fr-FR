---
title: "Étape 2c : ajouter un Port d’envoi interagissent pour le magasin d’interagir et le scénario de transfert (Pull) | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 57038f77-85c3-4811-ab3d-df6e2da8fbcf
caps.latest.revision: "5"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: fb46943b20676dbe98f79db8760043bb51606c56
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="step-2c-add-an-interact-send-port-for-the-interact-store-and-forward-pull-scenario"></a>Étape 2c : ajouter un Port d’envoi interagissent pour le magasin d’interagir et le scénario de transfert (Pull)
Avant de commencer cette étape, vous devez effectuer [étape 2 b : ajouter des Ports d’envoi FILE pour capturer le Message Sw:HandleRequest pour le magasin d’interagir et le scénario de (Pull) vers l’avant](../../adapters-and-accelerators/fileact-interact/step-2b-add-file-send-ports-to-get-sw-handlerequest-message-for-interact.md).  
  
### <a name="to-add-an-interact-send-port"></a>Pour ajouter un port d’envoi INTERACT  
  
1.  Démarrer **Administration de BizTalk Server**.  
  
2.  Dans l’arborescence de la console, développez le groupe BizTalk, puis développez l’application BizTalk pour laquelle vous souhaitez créer un port d’envoi.  
  
3.  Avec le bouton droit **Ports d’envoi**, pointez sur **nouveau**, puis cliquez sur **Port d’envoi statique avec sollicitation-réponse**.  
  
4.  Dans le **propriétés de Port d’envoi** fenêtre, le nom du port d’envoi **Tutorial_IA_SendRequest_SnF**.  
  
5.  Dans le **propriétés de Port d’envoi** fenêtre, à partir de la **type de Transport** la liste déroulante, sélectionnez **interagir**, puis cliquez sur **configurer**.  
  
6.  Dans le **propriétés du Transport interagir** boîte de dialogue zone, procédez comme suit :  
  
    |**Utilisez cette**|**Pour ce faire**|  
    |------------------|--------------------|  
    |**Mot de passe**|Définissez le mot de passe pour la connectivité des trous.|  
    |**Nom d'utilisateur**|Définissez le nom d’utilisateur pour la connectivité des trous.|  
    |**Format de message**|**InteractMessage**|  
    |**Indicateur de non répudiation**|**FALSE**|  
    |**Type de demande**|Tapez la commande appropriée \<RequestType\> chaîne, en fonction de votre configuration avec SWIFT.|  
    |**ResponseCrypto**|**FALSE**|  
    |**Demandeur**|Tapez la commande appropriée \<RequestorDN\> chaîne, en fonction de votre configuration avec SWIFT.|  
    |**Répondeur**|Tapez la commande appropriée \<ResponderDN\> chaîne, en fonction de votre configuration avec SWIFT.|  
    |**Nom du service**|Tapez la commande appropriée \<nom du service\>, en fonction de votre configuration avec SWIFT.|  
    |**Accusé de réception**|Dans la liste déroulante, sélectionnez **FALSE**.|  
    |**File d’attente de notification**|Tapez le nom de la file d’attente appropriée, en fonction de votre configuration avec SWIFT.|  
  
    > [!NOTE]
    >  Si une seule charge utile doit être transféré, jeu du MessageFormat à « Charge » dans l’interagir port de réception et port d’envoi interagir. Affectez les pipelines de réception et d’envoi PassThru.  
  
7.  Cliquez sur **OK**.  
  
8.  Dans le **propriétés de Port d’envoi** fenêtre, procédez comme suit :  
  
    |**Utilisez cette**|**Pour ce faire**|  
    |------------------|--------------------|  
    |**Gestionnaire d’envoi**|Dans la liste déroulante, sélectionnez l’hôte d’interagir.|  
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
 [Étape 2 a : ajouter le fichier emplacements de réception pour le magasin d’interagir et le scénario de transfert (Pull)](../../adapters-and-accelerators/fileact-interact/step-2a-add-file-receive-locations-for-interact-store-and-forward-scenario.md)   
 [Étape 2B : Ajouter des ports d’envoi FILE pour capturer le message Sw:HandleRequest pour le scénario de stockage et de redirection (Pull) InterAct](../../adapters-and-accelerators/fileact-interact/step-2b-add-file-send-ports-to-get-sw-handlerequest-message-for-interact.md)