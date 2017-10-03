---
title: "Étape 3E : ajouter un Port d’envoi interagir pour l’interaction scénario en temps réel | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d9522386-e980-4ab1-b65a-939ca7936ad9
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: fcb78fd556e72e4ca19e1d5172826a813f23eb24
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="step-3e-add-an-interact-send-port-for-the-interact-real-time-scenario"></a>Étape 3E : ajouter un Port d’envoi interagir pour l’interaction scénario en temps réel
Complète [étape 3D : ajouter un Port d’envoi FILE pour capturer le Message Sw:HandleResponse pour le scénario en temps réel interagir](../../adapters-and-accelerators/fileact-interact/step-3d-add-file-send-port-to-get-sw-handleresponse-message-for-interact.md) avant de commencer cette étape.
  
## <a name="add-an-interact-send-port"></a>Ajouter un port d’envoi INTERACT  
  
1.  Démarrer **Administration de BizTalk Server**.  
  
2.  Dans l’arborescence de la console, développez le groupe BizTalk, puis développez l’application BizTalk pour laquelle vous souhaitez créer un port d’envoi.  
  
3.  Avec le bouton droit **Ports d’envoi**, pointez sur **nouveau**, puis cliquez sur **Port d’envoi statique avec sollicitation-réponse**.  
  
4.  Dans le **propriétés de Port d’envoi** fenêtre, le nom du port d’envoi **Tutorial_IA_SendRequest_RealTime**.  
  
5.  Dans le **propriétés de Port d’envoi** fenêtre, à partir de la **type de Transport** la liste déroulante, sélectionnez **interagir**, puis cliquez sur **configurer**.  
  
6.  Dans le **propriétés du Transport interagir** boîte de dialogue zone, procédez comme suit :  
  
    |**Utilisez cette**|**Pour ce faire**|  
    |------------------|--------------------|  
    |**Mot de passe**|Définissez le mot de passe pour la connectivité des trous.|  
    |**Nom d'utilisateur**|Définissez le nom d’utilisateur pour la connectivité des trous.|  
    |**Mode de l’adaptateur**|Dans la liste déroulante, sélectionnez **en temps réel**.|  
    |**Format de message**|**InteractMessage**.|  
    |**Indicateur de non répudiation**|**FALSE**.|  
    |**Type de demande**|Tapez la commande appropriée \<RequestType > chaîne, en fonction de votre configuration avec SWIFT.|  
    |**ResponseCrypto**|**FALSE**.|  
    |**Demandeur**|Affectez-lui la valeur approprié \<demandeur > chaîne, en fonction de votre configuration avec SWIFT.|  
    |**Répondeur**|Affectez-lui la valeur approprié \<répondeur > chaîne, en fonction de votre configuration avec SWIFT.|  
    |**Nom du service**|Affectez-lui la valeur approprié \<nom service >, en fonction de votre configuration avec SWIFT.|  
    |**Accusé de réception**|Dans la liste déroulante, sélectionnez **FALSE**.|  
    |**File d’attente de notification**|Tapez le nom de la file d’attente appropriée, en fonction de votre configuration avec SWIFT.|  
  
    > [!NOTE]
    >  Si une seule charge utile doit être transféré, jeu du MessageFormat à « Payloadonly » dans l’interagir port de réception et port d’envoi interagir. Définir la réception et pipelines d’envoi à PassThru.  
  
7.  Cliquez sur **OK**.  
  
8.  Dans le **propriétés de Port d’envoi** fenêtre, procédez comme suit :  
  
    |**Utilisez cette**|**Pour ce faire**|  
    |------------------|--------------------|  
    |**Gestionnaire d’envoi**|Dans la liste déroulante, sélectionnez l’hôte d’interagir.|  
    |**Pipeline d’envoi**|Dans la liste déroulante, sélectionnez **XMLTransmit**.|  
    |**Pipeline de réception**|**XMLReceive**|  
  
9. Dans le **propriétés de Port d’envoi** fenêtre, dans le **filtres** onglet, procédez comme suit :  
  
    |**Utilisez cette**|**Pour ce faire**|  
    |------------------|--------------------|  
    |**Propriété**|Dans la liste déroulante, sélectionnez **BTS. ReceivePortName**.|  
    |**Opérateur**|Dans la liste déroulante, sélectionnez  **==** .|  
    |**Valeur**|Type **Tutorial_IA_InputRequest_RealTime**.|  
    |**Regrouper par**|Laissez la valeur par défaut.|  
  
10. Cliquez sur **OK**.  
  
## <a name="see-also"></a>Voir aussi  
 [Étape 3 : Créer l’envoi et Ports de réception l’interaction du scénario en temps réel](../../adapters-and-accelerators/fileact-interact/step-3-create-send-and-receive-ports-for-the-interact-real-time-scenario.md)   
 [Étape 3 a : ajouter un fichier emplacement de réception pour l’interaction du scénario en temps réel](../../adapters-and-accelerators/fileact-interact/step-3a-add-a-file-receive-location-for-the-interact-real-time-scenario.md)   
 [Étape 3 b : ajouter un interagir emplacement de réception pour l’interaction scénario en temps réel](../../adapters-and-accelerators/fileact-interact/step-3b-add-an-interact-receive-location-for-the-interact-real-time-scenario.md)   
 [Étape 3c : ajouter un Port d’envoi FILE pour capturer le Message Sw:HandleRequest pour l’interaction du scénario en temps réel](../../adapters-and-accelerators/fileact-interact/step-3c-add-file-send-port-to-get-sw-handlerequest-interact-real-time-scenario.md)   
 [Étape 3D : ajouter un Port d’envoi FILE pour capturer le Message Sw:HandleResponse pour l’interaction du scénario en temps réel](../../adapters-and-accelerators/fileact-interact/step-3d-add-file-send-port-to-get-sw-handleresponse-message-for-interact.md)