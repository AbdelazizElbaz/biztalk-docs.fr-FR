---
title: "Comment ajouter des comptes à un affichage | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Excel add-in [BAM], security
- Add-Account command [BAM]
- managing [BAM], adding accounts to views
ms.assetid: 0875796c-82a4-4165-9bed-88e8ba466548
caps.latest.revision: "18"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 808d5395452733d43337e0883b306b7757a7da08
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="how-to-add-accounts-to-a-view"></a>Ajout de comptes à une vue
Les administrateurs utilisent la **-ajouter un compte** commande pour associer des utilisateurs à des vues BAM et protéger les vues de la feuille de calcul Excel BAM à partir de tout accès non autorisé. Lorsque les vues BAM sont enregistrées par des utilisateurs, elles référencent une chaîne de connexion SQL masquée dans le classeur. Le classeur est protégé, mais vous devez vous assurer que le document est également protégé.  
  
 Lorsque vous associez des utilisateurs à des vues BAM, vous limitez l'accès de ces vues aux seuls utilisateurs et groupes auxquels vous avez accordé des autorisations d'accès.  
  
> [!IMPORTANT]
>  Si vous utilisez des agrégations en temps réel (RTA), les utilisateurs ajoutés à **-ajouter un compte** ne voient pas accorder automatiquement des droits d’ouverture de session à l’ordinateur exécutant SQL Server. Dans ce cas, prévoyez d'établir un groupe d'utilisateurs Windows contenant tous les utilisateurs qui ont besoin d'afficher des vues d'agrégations RTA. Accordez à ce groupe des droits de connexion SQL Server explicites au serveur SQL hébergeant la base de données d'importation principale BAM.  
  
 Pour plus d’informations sur l’affichage des vues BAM, consultez [comment répertorier les vues BAM](../core/how-to-list-bam-views.md).  
  
### <a name="to-add-an-account-to-a-view"></a>Pour ajouter des comptes à une vue  
  
1.  Ouvrez une invite de commandes comme suit : cliquez sur **Démarrer**, cliquez sur **exécuter**, type **cmd**, puis cliquez sur **OK**.  
  
2.  Accédez au dossier des suivis en tapant [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]\Tracking lorsque vous y êtes invité. Appuyez sur **Entrée**.  
  
3.  Type **bm ajouter-account - AccountName :\<nom de compte\> -View :\<nom de la vue\>**.  
  
    > [!NOTE]
    >  Sur les systèmes qui prennent en charge le contrôle de compte d'utilisateur, vous devrez peut-être exécuter l'outil avec des privilèges d'administrateur.  
  
4.  Appuyez sur **Entrée**.  
  
## <a name="see-also"></a>Voir aussi  
 [Gestion de l’Infrastructure dynamique BAM](../core/managing-the-bam-dynamic-infrastructure.md)   
 [Utilitaire de gestion de l’analyse BAM](../core/bam-management-utility.md)