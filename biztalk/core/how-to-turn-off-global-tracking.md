---
title: "Comment faire pour désactiver le suivi Global | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: eae3059a-cbdd-47c4-84cd-edfb5480b9fa
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: e98f793bb96ae8c74c8f375abda4dc87e580c63f
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-turn-off-global-tracking"></a>Désactivation du suivi global
Le suivi global est activé par défaut lorsque vous installez [!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)]. La taille de la base de données des suivis BizTalk (BizTalkDTADb) croît à mesure que [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] traite des données sur votre système. Si la taille de cette base de données affecte les performances du disque, vous pouvez en purger les données. Si vous rencontrez des problèmes de performances qui sont momentanément résolus par une purge de la base de données de suivi BizTalk, et que vous souhaitez configurer BizTalk de sorte que les informations de suivi ne soient plus collectées, vous pouvez envisager de désactiver le suivi global.  
  
 Il est important de comprendre que le fait de désactiver le suivi global entraîne également la désactivation des intercepteurs de suivi de l'ensemble du groupe [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]. Cela signifie que BizTalk ne suivra pas les événements dans les tables de suivi. Vous pouvez aussi désactiver le suivi des événements de manière individuelle.  
  
> [!NOTE]
>  Si vous utilisez l'analyse BAM, vous devez conserver un hôte de suivi dédié, même si vous désactivez le suivi global, car les événements BAM utilisent le service TDDS (Tracking Data Decode Service).  
  
## <a name="prerequisites"></a>Conditions préalables  
 Pour exécuter cette procédure, vous devez être connecté avec un compte membre du rôle de serveur fixe sysadmin SQL Server.  
  
### <a name="to-turn-off-global-tracking-sql-server-2008"></a>Pour désactiver le suivi global (SQL Server 2008)  
  
1.  Sur le serveur SQL qui héberge la base de données des suivis BizTalk (BizTalkDTADb), cliquez sur **Démarrer**, cliquez sur **programmes**, cliquez sur **Microsoft SQL Server 2008 R2**, puis cliquez sur  **SQL Server Management Studio**.  
  
2.  Dans le **se connecter au serveur** boîte de dialogue, vérifiez le nom du serveur et l’authentification, puis cliquez sur **connexion**.  
  
3.  Dans Microsoft SQL Server Management Studio, dans **l’Explorateur d’objets**, développez \< *nom de l’ordinateur*>, développez **bases de données**, développez  **BizTalkMgmtDb**, développez **Tables**, avec le bouton droit **adm_Group**, puis cliquez sur **ouvrir la Table**.  
  
4.  Dans la visionneuse de table, faites défiler horizontalement jusqu'à ce que vous trouviez **GlobalTrackingOption**.  
  
5.  Dans le **GlobalTrackingOption** colonne, modifiez la valeur 1 en 0 pour désactiver cette fonctionnalité et appuyez sur ENTRÉE.  
  
6.  Fermez Microsoft SQL Server Management Studio.  
  
    > [!NOTE]
    >  Vous devez redémarrer vos hôtes BizTalk pour que ce changement prenne effet.  
  
7.  Cliquez sur **Démarrer**, cliquez sur **programmes**, pointez sur **Microsoft** [!INCLUDE[btsBizTalkServer2006r3ui](../includes/btsbiztalkserver2006r3ui-md.md)], puis cliquez sur **Administration de BizTalk Server**.  
  
8.  Dans le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration de la console, développez **Administration de BizTalk Server**, développez **groupe BizTalk**, développez **paramètres de plateforme**, puis cliquez sur  **Instances de l’hôte**.  
  
9. Dans le volet de détails, cliquez sur chaque ordinateur hôte, puis cliquez sur **redémarrer**.  
  
## <a name="see-also"></a>Voir aussi  
 [Archivage et la purge de la base de données de suivi de BizTalk](../core/archiving-and-purging-the-biztalk-tracking-database.md)   
 [Purge des données de la base de données de suivi de BizTalk](../core/how-to-purge-data-from-the-biztalk-tracking-database.md)   
 [Purge manuelle des données à partir de la base de données de suivi BizTalk](../core/how-to-manually-purge-data-from-the-biztalk-tracking-database.md)