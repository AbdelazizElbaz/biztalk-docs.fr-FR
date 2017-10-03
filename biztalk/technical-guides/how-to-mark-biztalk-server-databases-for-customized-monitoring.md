---
title: "Bases de données BizTalk Server de marque pour une analyse personnalisée | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: cfbdc73d-a108-42ee-a5d8-401d5bfe5e7d
caps.latest.revision: "4"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 08807b1a365b84765221e3a71cb131d8c037fcf0
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-mark-biztalk-server-databases-for-customized-monitoring"></a>Comment marquer les bases de données BizTalk Server pour une analyse personnalisée
Si vous avez installé Microsoft [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] Pack d’administration, vous pouvez personnaliser la façon dont [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] bases de données sont analysées. Cela garantit que le [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] Pack d’administration analyse les éléments suivants [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] bases de données :  
  
-   Base de données des archives BAM (BAMArchive)  
  
-   Base de données d'importation principale BAM (BAMPrimaryImport)  
  
-   Base de données de schémas en étoile BAM (BAMStarSchema)  
  
-   Base de données des suivis (BizTalkDTADb)  
  
-   Base de données de gestion BizTalk (BizTalkMgmtDb)  
  
-   Base de données MessageBox BizTalk (BizTalkMsgBoxDb)  
  
-   Base de données du moteur de règles (BizTalkRuleEngineDb)  
  
-   Base de données de l'authentification unique de l'entreprise (SSODB)  
  
> [!NOTE]  
>  Vous devez être connecté en tant que membre du rôle opérateur avancé Operations Manager ou [!INCLUDE[opsmgr_short](../includes/opsmgr-short-md.md)] groupe d’administration.  
  
### <a name="to-mark-biztalk-server-databases-for-customized-monitoring"></a>Pour marquer les bases de données BizTalk Server pour personnaliser l’analyse  
  
1.  Cliquez sur **Démarrer**, cliquez sur **tous les programmes**, cliquez sur **System Center Operations Manager 2007**, puis cliquez sur **Console opérateur**.  
  
2.  Dans la console Opérateur, cliquez sur le **création** bouton.  
  
3.  Dans le **création** volet, développez **objets du Pack d’administration**, puis cliquez sur **détections**.  
  
4.  Pour localiser une détection pour SQL Server, dans la barre d’outils de la console Opérateur, cliquez sur **trouver**et dans le **recherchez** zone de texte Entrez **SQL 2008** à rechercher pour SQL Server 2008.  
  
5.  Sous le **Type découvert : base de données SQL 2008** catégorie, sélectionnez **découvrir de bases de données pour un moteur de base de données**.  
  
6.  Dans la barre d’outils de la console Opérateur, cliquez sur **substitue** , puis pointez sur **remplacer la détection d’objets**. Vous pouvez choisir de remplacer la détection des objets d’un type spécifique ou pour tous les objets au sein d’un groupe. Après avoir choisi le groupe du type d’objet à substituer, mais le **propriétés du remplacement** boîte de dialogue s’ouvre.  
  
    > [!NOTE]  
    >  Si le **substitue** bouton n’est pas disponible, assurez-vous que vous avez sélectionné un moniteur et non un objet conteneur dans le volet analyses.  
  
7.  Activez la case à cocher dans la **remplacer** colonne suivant pour le **liste d’exclusion** paramètre, puis, dans le **remplacer par la valeur** colonne, tapez le nom de la base de données que vous souhaitez exclure à partir de l’analyse. Assurez-vous que le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] que vous souhaitez surveiller les bases de données ne sont pas répertoriées dans le **remplacer par la valeur** colonne.  
  
    > [!TIP]  
    >  Vous pouvez utiliser les détections d’objets modifiés pour créer un pack d’administration. En bas du volet, le **sélectionnez Pack d’administration de destination** liste déroulante affiche la valeur par défaut **Pack d’administration par défaut**. Cliquez sur **nouveau** pour créer un nouveau pack d’administration dans les détections d’objet modifié.  
  
## <a name="see-also"></a>Voir aussi  
 [Analyse des serveurs SQL](../technical-guides/monitoring-sql-servers.md)