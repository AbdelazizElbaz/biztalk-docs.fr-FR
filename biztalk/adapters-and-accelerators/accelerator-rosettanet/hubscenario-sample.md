---
title: Exemple HubScenario | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: eb6990ec-aea2-4362-8573-7f737a4fc7f1
caps.latest.revision: "15"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 5b9b2770f1d14d716149025ac44cb3cdffbbb23b
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="hubscenario-sample"></a>Exemple HubScenario
L'exemple HubScenario montre comment gérer la transmission des messages dans un scénario basé sur un hub. Il convertit un message envoyé à un hub intermédiaire en message à envoyer au destinataire final.  
  
 HubScenario extrait le numéro DUNS du destinataire final à partir du contenu du service. Il gère les certificats de signature et de chiffrement, ainsi que l'URL de destination. Il génère un nouveau message pour le destinataire final.  
  
 Cet exemple gère les messages de requête et de réponse 3A4, ainsi que les messages de requête 0C1. Quand vous utilisez HubScenario pour créer une application répondant à vos besoins, vous devez générer des routines pour chaque message PIP (Partner Interface Process).  
  
 L'exemple HubScenario inclut les projets HubHelper.cs et HubScenario.odx.  
  
 L'exemple HubScenario inclut également un fichier de liaison qui vous permet d'importer des liaisons pour un port de réception (MessagesToLOB_Receive_Port) et un emplacement de réception (MessagesToLOB_Receive_Location) à utiliser avec l'orchestration HubScenario.odx. Ce fichier de liaison (HubScenarioBinding.xml) se trouve dans  *\<lecteur >*: \Program Files\\ [!INCLUDE[btsCoName](../../includes/btsconame-md.md)] Microsoft BizTalk \<version > Accelerator for RosettaNet \SDK\ HubScenario. Utilisez la commande BTSTask pour importer les liaisons. Pour plus d’informations, consultez la rubrique « Commande ImportBindings » dans [!INCLUDE[btsBizTalkServer2006r3](../../includes/btsbiztalkserver2006r3-md.md)] aide.  
  
### <a name="to-build-and-initialize-this-sample"></a>Pour créer et initialiser l'exemple  
  
1.  Dans Visual Studio, ouvrez \<lecteur > : \Program Files\Microsoft Microsoft BizTalk \<version > Accelerator pour RosettaNet\SDK\HubScenario\HubScenario.btproj. Dans l'Explorateur de solutions, cliquez avec le bouton droit sur le projet HubScenario, puis cliquez sur Propriétés. Dans la page de propriétés du projet HubScenario, sous l'onglet Signature, cochez la case **Signer l'assembly** , sélectionnez **HubScenario.snk** dans **Choisir un fichier de clé de nom fort** , puis cliquez sur **OK**.  
  
2.  Dans l'Explorateur de solutions, cliquez avec le bouton droit sur le projet HubHelper, puis cliquez sur Propriétés. Dans la page de propriétés du projet HubHelper, sous l'onglet Signature, cochez la case Signer l'assembly. Dans le champ Choisir un fichier de clé de nom fort, sélectionnez le nouveau type **HubHelper.snk** en tant que nom de fichier de clé, puis cliquez sur **OK**.  
  
    > [!NOTE]
    >  Si vous n'entrez pas manuellement le fichier de clé d'assembly dans les projets HubScenario et HubHelper, les assemblys ne seront pas déployés.  
  
3.  À l’invite de commandes, passez à  *\<lecteur >*: \Program Files\\ [!INCLUDE[btsCoName](../../includes/btsconame-md.md)] Microsoft BizTalk \<version > Accelerator pour RosettaNet\SDK\HubScenario dossier. Exécutez le fichier Setup.bat (ou sur un ordinateur 64 bits, exécutez Setupx64.bat).  
  
## <a name="demonstrates"></a>Montre  
 L'orchestration HubScenario.ods montre comment effectuer les tâches suivantes :  
  
1.  Reçoit le message de l'application métier.  
  
2.  Supprime l'élément `CDATA` du contenu du service, en retournant la chaîne XML.  
  
3.  Récupère le nom du tiers de destination, ainsi que le PIPCode, le PIPInstanceID et le PIPVersion pour le message final.  
  
4.  Récupère le numéro DUNS du destinataire final.  
  
5.  Détermine la catégorie du message, puis ajoute l'élément DOCTYPE contenant une référence au schéma approprié pour le contenu du service.  
  
6.  Construit un message avec le nouveau nom du tiers de destination, ainsi que le numéro DUNS, les informations de code PIP et le contenu du service.  
  
7.  Envoie le message de traitement par [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)]. Il s'agit d'un appel à `SubmitRNIF.SubmitMessage`.  
  
## <a name="see-also"></a>Voir aussi  
 [Exemple de scénario basé sur un concentrateur](../../adapters-and-accelerators/accelerator-rosettanet/sample-hub-based-scenario.md)   
 [Exemples d’orchestration](../../adapters-and-accelerators/accelerator-rosettanet/orchestration-samples.md)