---
title: "Étape 4 : Créer le Port de réception pour l’acceptation de ADT ^ A03 des Messages à partir de systèmes ADT à l’aide de l’adaptateur MLLP | Documents Microsoft"
ms.custom: 
ms.date: 2015-12-09
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- receive ports
- end-to-end tutorial, receive ports
- creating, receive ports
ms.assetid: 3c4192d5-d011-48b0-a3f9-47c5225780ee
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 865675e12609beea4c909d19a74d3e0ec4f38715
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="step-4-create-the-receive-port-for-accepting-adta03-messages-from-adt-systems-using-the-mllp-adapter"></a>Étape 4 : Créer le Port de réception pour l’acceptation de ADT ^ A03 des Messages à partir de systèmes ADT à l’aide de l’adaptateur MLLP
Le port de réception vous permet de spécifier l’emplacement de réception pour les messages entrants. Utilisez la procédure suivante pour créer le port de réception pour l’acceptation de ADT ^ A03 des messages à partir du système ADT à l’aide de l’adaptateur MLLP.  
  
## <a name="create-the-receive-port"></a>Créer le port de réception  
  
1.  Ouvrez **Administration de BizTalk Server**, développez **Administration de BizTalk Server**, développez **groupe BizTalk**, développez **Applications**, puis développez **BizTalk Application 1**.  
  
    > [!NOTE]
    >  La Console Administration de BizTalk Server peut également être ouvert à partir de Visual Studio en cliquant sur **Administration de BizTalk Server** dans les **outils** menu.  
  
2.  Avec le bouton droit **Ports de réception**, sélectionnez **nouveau**, puis sélectionnez **Port de réception unidirectionnel**.  
  
3.  Pour le **nom**, entrez **Tutorial_1WayReceive**.  
  
4.  Sélectionnez **appliquer** pour lier le port, puis sélectionnez **emplacements de réception**.  
  
5.  Sélectionnez **nouveau**.  
  
6.  Pour le **nom**, entrez **Tutorial_MLLPReceive**.  
  
7. Dans le **Transport** section, sélectionnez **Type**, puis sélectionnez **MLLP** dans la liste déroulante.  
  
8. Sélectionnez **Configurer**. Dans **propriétés du Transport MLLP**, configurez les éléments suivants, puis sélectionnez **OK**.  
  
    |Utiliser|Pour effectuer cette opération|  
    |---|---|  
    |**Temps de nouvelle tentative (s) de connexion**|Nouveau commençant par [!INCLUDE[bts2016_md](../../includes/bts2016-md.md)]. <br/><br/>La limite supérieure de durée à attendre avant d’essayer de se reconnecter à une connexion supprimée ou fermée. S’applique lorsque **connexion initiée par** a la valeur **Local**.<br/><br/>Valeur par défaut est 20 secondes.|
    |**Connexion initiée par**| Nouveau commençant par [!INCLUDE[bts2016_md](../../includes/bts2016-md.md)]. <br/><br/>Entrez **Local** pour la MLLP emplacement de réception pour la connexion à un serveur distant de LOB. Il s’agit de la nouvelle option.<br/><br/>Entrez **distant** pour la MLLP emplacement de réception pour continuer à écouter pour une connexion à partir du serveur LOB à distance. Il s’agit de l’option par défaut de compatibilité descendante.<br/><br/>Valeur par défaut est à distance.| 
    |**Nom de la connexion**|Entrez **1Way**.|  
    |**Nom d’hôte**|Spécifiques à [!INCLUDE[bts2013r2_md](../../includes/bts2013r2-md.md)] et les versions antérieures. <br/><br/>Entrez **localhost**.|  
    |**Nom d’hôte local**|Nouveau commençant par [!INCLUDE[bts2016_md](../../includes/bts2016-md.md)]. <br/><br/>Entrez le nom DNS ou l’adresse IP de l’ordinateur local [!INCLUDE[btsBizTalkServerNoVersion_md](../../includes/btsbiztalkservernoversion-md.md)]. Vous pouvez également entrer **localhost**.|  
    |**Port**|Spécifiques à [!INCLUDE[bts2013r2_md](../../includes/bts2013r2-md.md)] et les versions antérieures. <br/><br/>Valeur par défaut est **11000**.|  
    |**Port local**|Nouveau commençant par [!INCLUDE[bts2016_md](../../includes/bts2016-md.md)]. <br/><br/>Entrez le numéro de port TCP pour la connexion à LocalHost. Applicable uniquement lorsque **connexion initiée par** est **distant**. <br/><br/>Valeur par défaut est **11000**.|
    |**Hôte distant**|Nouveau commençant par [!INCLUDE[bts2016_md](../../includes/bts2016-md.md)]. <br/><br/>Entrez le nom DNS ou l’adresse IP du serveur distant LOB. S’applique lorsque **connexion initiée par** a la valeur **Local**.|  
    |**Port distant**|Nouveau commençant par [!INCLUDE[bts2016_md](../../includes/bts2016-md.md)]. <br/><br/>Entrez le numéro de port TCP pour la connexion d’hôte distant. S’applique lorsque **connexion initiée par** a la valeur **Local**.|  

9. Définir le **Gestionnaire de réception** à **BizTalkServerApplication**.  
  
10. Définir le **Pipeline de réception** à **BTAHL72XPipelines.BTAHL72XReceivePipeline**.  
  
11. Sélectionnez **OK** pour enregistrer vos modifications.  
  
12. Activer l’emplacement de réception que vous venez de créer par dessus, puis sélectionnez **activer**.  

## <a name="next-step"></a>Étape suivante  
[Étape 5 : Créer un Port d’envoi pour remettre les accusés de réception au système ADT à l’aide de l’adaptateur de fichier](../../adapters-and-accelerators/accelerator-hl7/step-5-create-send-port-to-deliver-acknowledgments-to-adt-system-using-file.md)