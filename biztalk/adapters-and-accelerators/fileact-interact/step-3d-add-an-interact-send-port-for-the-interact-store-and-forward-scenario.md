---
title: "Étape 3D : ajouter un Port d’envoi interagissent pour le magasin d’interagir et le scénario avant | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: cd126d9a-f4e4-429e-bab0-8b4c9c555e36
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 7ac1d379f2e68431f197f2db339cd0ac9f50c92e
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="step-3d-add-an-interact-send-port-for-the-interact-store-and-forward-scenario"></a>Étape 3D : ajouter un Port d’envoi interagissent pour le magasin d’interagir et le scénario avant
Complète [étape 3c : ajouter un Port d’envoi FILE pour capturer le Message Sw:HandleRequest pour le magasin d’interagir et le scénario par progression](../../adapters-and-accelerators/fileact-interact/step-3c-add-file-send-port-to-get-sw-handlerequest-interact-store-and-forward.md) avant de commencer cette étape.
  
## <a name="add-an-interact-send-port"></a>Ajouter un port d’envoi INTERACT  
  
1.  Démarrer **Administration de BizTalk Server**.  
  
2.  Dans l’arborescence de la console, développez le groupe BizTalk, puis développez l’application BizTalk pour laquelle vous souhaitez créer un port d’envoi.  
  
3.  Avec le bouton droit **Ports d’envoi**, pointez sur **nouveau**, puis cliquez sur **Port d’envoi statique avec sollicitation-réponse**.  
  
4.  Dans le **propriétés de Port d’envoi** fenêtre, le nom du port d’envoi Tutorial_IA_SendRequest_SnF.  
  
5.  Dans le **propriétés de Port d’envoi** fenêtre, à partir de la **type de Transport** la liste déroulante, sélectionnez **interagir**, puis cliquez sur **configurer**.  
  
6.  Dans le **propriétés du Transport interagir** boîte de dialogue zone, procédez comme suit :  
  
    |**Utilisez cette**|**Pour ce faire**|  
    |------------------|--------------------|  
    |**Mot de passe**|Définissez le mot de passe pour la connectivité des trous.|  
    |**Nom d'utilisateur**|Définissez le nom d’utilisateur pour la connectivité des trous.|  
    |**Format de message**|**InteractMessage**|  
    |**Indicateur de non répudiation**|**FALSE**|  
    |**Type de demande**|Tapez la commande appropriée \<RequestType > chaîne, en fonction de votre configuration avec SWIFT.|  
    |**ResponseCrypto**|**FALSE**|  
    |**Demandeur**|Tapez la commande appropriée \<RequestorDN > chaîne, en fonction de votre configuration avec SWIFT.|  
    |**Répondeur**|Tapez la commande appropriée \<ResponderDN > chaîne, en fonction de votre configuration avec SWIFT.|  
    |**Nom du service**|Tapez la commande appropriée \<nom service >, en fonction de votre configuration avec SWIFT.|  
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
    |**Valeur**|Type Tutorial_IA_InputRequest_SnF.|  
    |**Regrouper par**|Laissez la valeur par défaut.|  
  
10. Cliquez sur **OK**.  
  
## <a name="complete-steps"></a>Étapes à suivre
 [Étape 3 : Créer des Ports d’envoi et Ports de réception pour le magasin d’interagir et d’un scénario avant](../../adapters-and-accelerators/fileact-interact/step-3-create-send-and-receive-ports-for-interact-store-and-forward-scenario.md)   
 [Étape 3 a : ajouter un fichier emplacement de réception pour le magasin d’interagir et d’un scénario avant](../../adapters-and-accelerators/fileact-interact/step-3a-add-a-file-receive-location-for-interact-store-and-forward-scenario.md)   
 [Étape 3 b : ajouter un interagir emplacement de réception pour le magasin d’interagir et d’un scénario avant](../../adapters-and-accelerators/fileact-interact/step-3b-add-interact-receive-location-for-interact-store-and-forward-scenario.md)   
 [Étape 3c : ajouter un Port d’envoi FILE pour capturer le Message Sw:HandleRequest pour le magasin d’interagir et le scénario avant](../../adapters-and-accelerators/fileact-interact/step-3c-add-file-send-port-to-get-sw-handlerequest-interact-store-and-forward.md)  