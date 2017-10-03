---
title: "Étape 4 : Créer un Port de réception pour accepter le Message de lot | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a37eb334-c4ae-40d1-a433-bf0ab39c0765
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 56d1aa54639263e6741c6df89c3888b9b4120515
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="step-4-create-a-receive-port-for-accepting-the-batch-message"></a>Étape 4 : Créer un Port de réception pour accepter le Message du lot
Dans cette étape, vous créez et configurez un port pour recevoir le traitement entrant.  
  
 Vous créez une requête-réponse (bidirectionnel) port de réception, car ce scénario inclut la génération d’application-accepter des accusés de réception pour les messages individuels dans le lot. En mode bidirectionnel, l’adaptateur de réception MLLP n’accepte pas un nouveau message entrant jusqu'à ce que le pipeline de réception a généré l’accusé de réception (ACK) pour le message précédent.  
  
## <a name="create-the-receive-port-for-accepting-the-batch-message"></a>Créer le port de réception pour accepter le message du lot  
  
1.  Ouvrez **Administration de BizTalk Server**, développez **Administration de BizTalk Server**, développez **groupe BizTalk**, développez **Applications**, puis développez **BizTalk Application 1**.  
  
    > [!NOTE]
    >  La Console Administration de BizTalk Server peut également être ouvert à partir de Visual Studio en cliquant sur **Administration de BizTalk Server** dans les **outils** menu.  
  
2.  Avec le bouton droit **Ports de réception**, sélectionnez **nouveau**, puis sélectionnez **Receive Port requête-réponse**.  

3.  Pour le **nom**, entrez **Tutorial_2WayReceive**.  

4.  Sélectionnez **appliquer** pour lier le port, puis sélectionnez **emplacements de réception**.  
  
5.  Sélectionnez **nouveau**.  

6.  Pour le **nom**, entrez **Tutorial_2WayReceive**.

7. Dans le **Transport** section, sélectionnez **Type**, puis sélectionnez **MLLP** dans la liste déroulante.  
  
8. Sélectionnez **Configurer**. Dans **propriétés du Transport MLLP**, configurez les éléments suivants, puis sélectionnez **OK**.  

    |Utiliser|Pour effectuer cette opération|  
    |---|---|  
    |**Temps de nouvelle tentative (s) de connexion**|Nouveau commençant par [!INCLUDE[bts2016_md](../../includes/bts2016-md.md)]. <br/><br/>La limite supérieure de durée à attendre avant d’essayer de se reconnecter à une connexion supprimée ou fermée. S’applique lorsque **connexion initiée par** a la valeur **Local**.<br/><br/>Valeur par défaut est 20 secondes.|
    |**Connexion initiée par**| Nouveau commençant par [!INCLUDE[bts2016_md](../../includes/bts2016-md.md)]. <br/><br/>Entrez **Local** pour la MLLP emplacement de réception pour la connexion à un serveur distant de LOB. Il s’agit de la nouvelle option.<br/><br/>Entrez **distant** pour la MLLP emplacement de réception pour continuer à écouter pour une connexion à partir du serveur LOB à distance. Il s’agit de l’option par défaut de compatibilité descendante.<br/><br/>Valeur par défaut est à distance.| 
    |**Nom de la connexion**|Entrez **2Way**.|  
    |**Nom d’hôte**|Spécifiques à [!INCLUDE[bts2013r2_md](../../includes/bts2013r2-md.md)] et les versions antérieures. <br/><br/>Entrez **localhost**.|  
    |**Nom d’hôte local**|Nouveau commençant par [!INCLUDE[bts2016_md](../../includes/bts2016-md.md)]. <br/><br/>Entrez le nom DNS ou l’adresse IP de l’ordinateur local [!INCLUDE[btsBizTalkServerNoVersion_md](../../includes/btsbiztalkservernoversion-md.md)]. Vous pouvez également entrer **localhost**.|  
    |**Port**|Spécifiques à [!INCLUDE[bts2013r2_md](../../includes/bts2013r2-md.md)] et les versions antérieures. <br/><br/>La valeur **21000**.|  
    |**Port local**|Nouveau commençant par [!INCLUDE[bts2016_md](../../includes/bts2016-md.md)]. <br/><br/>Entrez le numéro de port TCP pour la connexion à LocalHost. Applicable uniquement lorsque **connexion initiée par** est **distant**. <br/><br/>La valeur **21000**.|
    |**Hôte distant**|Nouveau commençant par [!INCLUDE[bts2016_md](../../includes/bts2016-md.md)]. <br/><br/>Entrez le nom DNS ou l’adresse IP du serveur distant LOB. S’applique lorsque **connexion initiée par** a la valeur **Local**.|  
    |**Port distant**|Nouveau commençant par [!INCLUDE[bts2016_md](../../includes/bts2016-md.md)]. <br/><br/>Entrez le numéro de port TCP pour la connexion d’hôte distant. S’applique lorsque **connexion initiée par** a la valeur **Local**.<br/><br/>La valeur **21000**.|  

9. Dans les propriétés de l’emplacement de réception, sélectionnez les éléments suivants :  
  
    |Utiliser|Pour effectuer cette opération|  
    |--------------|----------------|  
    |**Gestionnaire de réception**|Sélectionnez **BizTalkServerApplication** dans la liste déroulante|  
    |**Pipeline de réception**|Sélectionnez **BTAHL72XPipelines.BTAHL72XReceivePipeline**|  
    |**Pipeline d’envoi**|Sélectionnez **BTAHL72XPipelines.BTAHL72XSendPipeline**|  

11. Sélectionnez **OK** pour enregistrer vos modifications.  
  
12. Activer l’emplacement de réception que vous venez de créer par dessus, puis sélectionnez **activer**.  
  
## <a name="next-step"></a>Étape suivante
[Étape 5 : Créer un Port d’envoi pour remettre des Messages](../../adapters-and-accelerators/accelerator-hl7/step-5-create-a-send-port-to-deliver-messages.md)