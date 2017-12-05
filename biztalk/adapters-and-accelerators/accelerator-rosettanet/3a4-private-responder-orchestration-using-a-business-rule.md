---
title: "Orchestration de répondeur de 3 a 4 à l’aide d’une règle d’entreprise | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 33d87952-def6-4202-b535-3d80171332eb
caps.latest.revision: "11"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 130349d707c8e4382c50cd7b65d01d346bf0a7fc
ms.sourcegitcommit: 3fc338e52d5dbca2c3ea1685a2faafc7582fe23a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/01/2017
---
# <a name="3a4-private-responder-orchestration-using-a-business-rule"></a>Orchestration de répondeur de 3 a 4 à l’aide d’une règle d’entreprise
L’exemple de PIP3A4PrivateResponder.odx est une orchestration de processus privé qui montre comment implémenter un processus PIP (Partner Interface)-processus privé de répondeur spécifiques incorporant une règle d’entreprise. Pour plus d’informations sur ce processus, consultez [définition d’une règle d’entreprise pour une Orchestration de processus privé](../../adapters-and-accelerators/accelerator-rosettanet/defining-a-business-rule-for-a-private-process-orchestration.md).  
  
 Par défaut, le [!INCLUDE[btsCoName](../../includes/btsconame-md.md)]® [!INCLUDE[BTARN_CurrentVersion_FirstRef](../../includes/btarn-currentversion-firstref-md.md)] programme d’installation installe l’exemple dans \< *lecteur*\>: \Program Files\Microsoft BizTalk \<version\> Accelerator for RosettaNet\SDK\PipAutomation\3A4.  
  
## <a name="procedures"></a>Procédures  
  
#### <a name="to-build-and-initialize-this-sample"></a>Pour créer et initialiser l'exemple  
  
1.  À l’invite de commandes, recherchez le  *\<lecteur\>*: \Program Files\ Microsoft BizTalk Accelerator for RosettaNet \<version\>\SDK\PIPAutomation\3A4 dossier.  
  
2.  Exécutez le fichier Setup.bat, qui utilise le fichier de liaison Binding.xml pour effectuer les actions suivantes :  
  
    -   Compile le projet d’assistance et inscrit l’assembly dans le global assembly cache.  
  
    -   Compile le projet PIP3APrivateResponder et inscrit l’assembly dans le global assembly cache.  
  
    -   Crée le LOB_To_PrivateResponder port de réception.  
  
    -   Crée le LOB_To_PrivateResponder emplacement de réception.  
  
    -   Crée et démarre le port d’envoi PrivateResponder_To_LOB.  
  
    -   Compilation et déploiement de l’orchestration PIP3A4PrivateResponderProcess.  
  
    > [!NOTE]
    >  Vous devez effectuer la configuration de liaison de port de l’orchestration PIP3A4PrivateResponderProcess à l’aide de l’Explorateur BizTalk.  
  
    > [!NOTE]
    >  Pour annuler les modifications apportées par setup.bat, manuellement désinscrivez l’orchestration PIP3A4PrivateResponder.odx, annuler le déploiement des assemblys du programme d’assistance et PIP3A4PrivateResponder et annuler le déploiement, puis supprimez la stratégie de règles samplebtarnpolicy. Vous ne pouvez pas utiliser Cleanup.bat dans le  *\<lecteur\>*: \Program Files\ Microsoft BizTalk Accelerator for RosettaNet \<version\>dossier \SDK\PIPAutomation\3A4 pour annuler les modifications apportées par setup.bat.  
  
## <a name="demonstrates"></a>Montre  
 Cet exemple s’abonne des messages d’action et de signal demande 3 a 4. Elle fonctionne dans les deux processus synchrones et asynchrones de 3 a 4. Tous les autres messages PIP repositionner toujours générique [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] processus privé. Cet exemple appelle la [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] moteur des règles d’entreprise et passe à la règle de moteur de message de demande entrant 3 a 4.  
  
> [!NOTE]
>  [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)]fournit un exemple de stratégie de règle d’entreprise nommé samplebtarnpolicy.xml dans \< *lecteur*\>: \Program Files\ Microsoft BizTalk Accelerator for RosettaNet \<version\>\SDK\ PipAutomation\3A4. Pour plus d’informations, consultez [stratégie d’entreprise BTARN exemple](../../adapters-and-accelerators/accelerator-rosettanet/sample-btarn-business-policy.md).  
  
 Pour utiliser l’exemple, configurez une règle d’entreprise. Si le message répond à la règle d’entreprise, le processus enregistre le message d’action entrant dans la table MessagesToLOB, définit l’état de remise à 2. La valeur de colonne remis doit être différent de zéro, afin que l’application métier-sait qu’il ne dispose pas de générer une confirmation pour cette demande. Le processus mappe le message de demande de 3 a 4 à un message de confirmation de 3 a 4, puis envoie la réponse à la table MessageStorageIn à l’aide du `SubmitRNIF` (méthode).  
  
 Si le message ne répond pas à la règle d’entreprise, le processus enregistre le message d’action entrant dans la table MessageStorageOut et définit l’état de remise à 0.  
  
 Cet exemple inclut un fichier de liaison (Binding.xml) que vous pouvez utiliser pour configurer un port d’envoi (PrivateResponder_To_LOB), un port de réception (LOB_To_PrivateResponder) et un emplacement de réception (LOB_To_PrivateResponder) pour une utilisation avec la PIP3A4PrivateResponder.odx orchestration. Utilisez la commande BTSTask pour importer les liaisons dans le fichier Binding.xml. Pour plus d’informations, consultez la rubrique « Commande ImportBindings » dans l’aide de BizTalk Server.  
  
## <a name="see-also"></a>Voir aussi  
 [Orchestration Action PIPAutomation double](../../adapters-and-accelerators/accelerator-rosettanet/double-action-pipautomation-orchestration.md)   
 [Stratégie d’entreprise BTARN exemple](../../adapters-and-accelerators/accelerator-rosettanet/sample-btarn-business-policy.md)   
 [Exemples d’orchestration](../../adapters-and-accelerators/accelerator-rosettanet/orchestration-samples.md)