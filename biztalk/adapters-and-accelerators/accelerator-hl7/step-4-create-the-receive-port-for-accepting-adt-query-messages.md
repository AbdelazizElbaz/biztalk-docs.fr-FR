---
title: "Étape 4 : Créer le Port de réception pour accepter les Messages de requête ADT | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: interrogative tutorial, receive ports
ms.assetid: 8bef032f-5f43-4d36-b88f-ed81f27bb803
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 301215ea32b992516bfead3cd77ecdb009087bb8
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="step-4-create-the-receive-port-for-accepting-adt-query-messages"></a>Étape 4 : Créer le Port de réception pour accepter les Messages de requête ADT
Vous créez un port de réception pour spécifier l’emplacement des messages de requête entrant envoyé par l’admission, rejet et le système de transfert (ADT). Utilisez la procédure suivante pour créer le port de réception pour accepter les requêtes (Req ^ Q01 messages) à partir du système ADT à l’aide de l’adaptateur de protocole de couche inférieure minimale (MLLP).  
  
## <a name="create-the-adtreceiveport-receive-port"></a>Créer le ADT_ReceivePort port de réception  
  
1.  Ouvrez **Administration de BizTalk Server**, développez **Administration de BizTalk Server**, développez **groupe BizTalk**, développez **Applications**, puis développez **BizTalk Application 1**.  
  
2.  Avec le bouton droit **Ports de réception**, sélectionnez **nouveau**, puis sélectionnez **Receive Port requête-réponse**.  
  
3.  Pour le **nom**, entrez **ADT_ReceivePort**.  
  
4.  Sélectionnez **appliquer** pour lier le port, puis sélectionnez **emplacements de réception**.  
  
5.  Sélectionnez **nouveau**. 
  
6.  Pour le **nom**, entrez **ADT_Receive**.  

7. Dans le **Transport** section, sélectionnez **Type**, puis sélectionnez **MLLP** dans la liste déroulante.  
  
8. Sélectionnez **Configurer**. Dans **propriétés du Transport MLLP**, configurez les éléments suivants, puis sélectionnez **OK**.  
  
    |Utiliser|Pour effectuer cette opération|  
    |---|---|  
    |**Temps de nouvelle tentative (s) de connexion**|Nouveau commençant par [!INCLUDE[bts2016_md](../../includes/bts2016-md.md)]. <br/><br/>La limite supérieure de durée à attendre avant d’essayer de se reconnecter à une connexion supprimée ou fermée. S’applique lorsque **connexion initiée par** a la valeur **Local**.<br/><br/>Valeur par défaut est 20 secondes.|
    |**Connexion initiée par**| Nouveau commençant par [!INCLUDE[bts2016_md](../../includes/bts2016-md.md)]. <br/><br/>Entrez **Local** pour la MLLP emplacement de réception pour la connexion à un serveur distant de LOB. Il s’agit de la nouvelle option.<br/><br/>Entrez **distant** pour la MLLP emplacement de réception pour continuer à écouter pour une connexion à partir du serveur LOB à distance. Il s’agit de l’option par défaut de compatibilité descendante.<br/><br/>Valeur par défaut est à distance.| 
    |**Nom de la connexion**|Entrez **ADT_ReceiveMLLP**.|  
    |**Nom d’hôte**|Spécifiques à [!INCLUDE[bts2013r2_md](../../includes/bts2013r2-md.md)] et les versions antérieures. <br/><br/>Entrez **localhost**.|  
    |**Nom d’hôte local**|Nouveau commençant par [!INCLUDE[bts2016_md](../../includes/bts2016-md.md)]. <br/><br/>Entrez le nom DNS ou l’adresse IP de l’ordinateur local [!INCLUDE[btsBizTalkServerNoVersion_md](../../includes/btsbiztalkservernoversion-md.md)]. Vous pouvez également entrer **localhost**.|  
    |**Port**|Spécifiques à [!INCLUDE[bts2013r2_md](../../includes/bts2013r2-md.md)] et les versions antérieures. <br/><br/>La valeur **22000**.|  
    |**Port local**|Nouveau commençant par [!INCLUDE[bts2016_md](../../includes/bts2016-md.md)]. <br/><br/>Entrez le numéro de port TCP pour la connexion à LocalHost. Applicable uniquement lorsque **connexion initiée par** est **distant**. <br/><br/>La valeur **22000**.|
    |**Hôte distant**|Nouveau commençant par [!INCLUDE[bts2016_md](../../includes/bts2016-md.md)]. <br/><br/>Entrez le nom DNS ou l’adresse IP du serveur distant LOB. S’applique lorsque **connexion initiée par** a la valeur **Local**.|  
    |**Port distant**|Nouveau commençant par [!INCLUDE[bts2016_md](../../includes/bts2016-md.md)]. <br/><br/>Entrez le numéro de port TCP pour la connexion d’hôte distant. S’applique lorsque **connexion initiée par** a la valeur **Local**.<br/><br/>La valeur **22000**.|  

9. Définir le **Gestionnaire de réception** à **BizTalkServerApplication**.  
  
10. Définir le **Pipeline de réception** à **BTAHL72XPipelines.BTAHL72XReceivePipeline**.  

11. Définir le **pipeline d’envoi** à **PassThruTransmit**.
  
11. Sélectionnez **OK** pour enregistrer vos modifications.  
  
12. Activer l’emplacement de réception que vous venez de créer par dessus, puis sélectionnez **activer**.  

## <a name="next-step"></a>Étape suivante  
[Étape 5 : Créer le Port de réception pour l’acceptation de ses Messages](../../adapters-and-accelerators/accelerator-hl7/step-5-create-the-receive-port-for-accepting-his-messages.md)