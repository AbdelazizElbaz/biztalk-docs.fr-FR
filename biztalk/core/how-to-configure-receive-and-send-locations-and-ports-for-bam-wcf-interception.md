---
title: "La configuration de réception et emplacements et les Ports d’envoi pour l’Interception WCF BAM | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 501194dc-427a-4910-88c9-19cf47daeaad
caps.latest.revision: "18"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: aa77f39e8320c0d6598caaf5ea547592078774ba
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-configure-receive-and-send-locations-and-ports-for-bam-wcf-interception"></a>Configuration des emplacements et ports de réception et d'envoi pour l'interception WCF de l'analyse BAM
Cette procédure permet de configurer les emplacements de réception et d'envoi dans un scénario de routage basé sur le contenu afin d'illustrer les principaux concepts d'une manière simple. Les concepts présentés dans cette rubrique peuvent être appliqués à une orchestration exposée en tant que service [!INCLUDE[firstref_btsWinCommFoundation](../includes/firstref-btswincommfoundation-md.md)].  
  
## <a name="prerequisites"></a>Conditions préalables  
 Cette procédure implique que vous ayez :  
  
-   Modifié votre fichier machine.config comme dans [comment ajouter le comportement de l’intercepteur BAM au fichier Machine.config](../core/how-to-add-the-bam-interceptor-behavior-to-the-machine-config-file.md).  
  
-   Créé un adaptateur WCF pour BizTalk Server, comme dans [la création d’un adaptateur WCF pour BizTalk Server](../core/how-to-create-a-wcf-adapter-for-biztalk-server.md).  
  
### <a name="to-configure-the-receive-and-send-locations"></a>Pour configurer les emplacements de réception et d'envoi  
  
1.  Ouvrez la console Administration de BizTalk. Pour ce faire, cliquez sur **Démarrer**, pointez sur **tous les programmes**, pointez sur [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], puis cliquez sur **Administration de BizTalk Server**.  
  
2.  Développez l'arborescence de la console pour localiser le nœud des emplacements de réception de votre application BizTalk. Cliquez sur [!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)], cliquez sur **Applications**, cliquez sur l’application que vous avez sélectionné dans le [!INCLUDE[nextref_btsWinCommFoundation](../includes/nextref-btswincommfoundation-md.md)] boîte de dialogue Type de Service, puis cliquez sur **emplacements de réception**. Un nouvel emplacement de réception correspondant à celui que vous avez créé est affiché. Son état est Désactivé.  
  
3.  Double-cliquez sur l’emplacement de réception pour ouvrir la **propriétés de l’emplacement de réception** boîte de dialogue zone, puis choisissez le type de transport WCF-Custom.  
  
4.  Cliquez sur le **configurer** bouton pour ouvrir la **propriétés du Transport WCF-Custom** boîte de dialogue.  
  
5.  Cliquez sur le **liaison** onglet et sélectionnez la liaison que vous souhaitez utiliser.  
  
6.  Cliquez sur le **comportement** onglet, cliquez sur le **EndpointBehavior** nœud et sélectionnez **Ajout d’une Extension**.  
  
7.  Sélectionnez l’extension BAMEndPointExtension (il s’agit de l’extension que vous avez ajouté au fichier machine.config), puis cliquez sur **Ok**.  
  
     ![Écran d’Extension de comportement SELECT](../core/media/fe830d29-504e-465a-9316-b3f0db2dbc24.gif "fe830d29-504e-465a-9316-b3f0db2dbc24")  
  
8.  Sélectionnez l’extension que vous venez de créer, entrez les valeurs suivantes, puis cliquez sur **OK**:  
  
    |Propriété|Valeur|  
    |--------------|-----------|  
    |PollingIntervalSec|10|  
    |ConnectionString|ConnectionString : Integrated Security = SSPI ; Persist Security Info = False ; catalogue Initial = BAMPrimaryImport ; Source de données =|  
  
9. Dans le **propriétés de l’emplacement de réception** boîte de dialogue, sélectionnez **PassThruReceive** à partir de la **pipeline de réception** liste déroulante, puis cliquez sur **OK**.  
  
10. Activez l'emplacement de réception et actualisez la console Administration. L'état Démarré indique que l'installation a réussi.  
  
## <a name="see-also"></a>Voir aussi  
 [Configuration de l’adaptateur WCF pour intercepter les données BAM](../core/configuring-the-wcf-adapter-to-intercept-bam-data.md)