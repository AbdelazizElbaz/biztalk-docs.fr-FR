---
title: "Mettre à jour les références à la base de données de suivi Analysis Server | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6a403325-1394-4668-946f-01b610cb686e
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 94ed784eeca992d32f431a7c6794b7051b7595e9
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="update-references-to-the-tracking-analysis-server-database"></a>Mettre à jour les références à la base de données de suivi Analysis Server
La base de données du serveur analyse des suivis est facultatif et contient les cubes de traitement analytique en ligne (OLAP). Ces cubes OLAP sont des agrégations de données contenues dans la base de données des suivis BizTalk.  
  
 Pour restaurer la base de données du serveur analyse des suivis, utilisez [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] Analysis Manager pour traiter les cubes MessageMetrics et ServiceMetrics. Pour obtenir des instructions, consultez [la gestion de la sauvegarde et restauration (Analysis Services)](http://go.microsoft.com/fwlink/?LinkId=130939) (http://go.microsoft.com/fwlink/?LinkId=130939) dans [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] la documentation en ligne.  
  
 Pour restaurer la base de données du serveur analyse des suivis à un autre ordinateur, vous devez également mettre à jour les références au nom de base de données dans la base de données de gestion BizTalk à l’aide de la procédure suivante.  
  
## <a name="prerequisites"></a>Conditions préalables  
 Vous devez être connecté en tant que membre de le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] groupe Administrateurs pour effectuer cette procédure.  
  
### <a name="to-update-references-to-the-tracking-analysis-server-database-name"></a>Pour mettre à jour les références au nom de base de données du serveur analyse des suivis  
  
1.  Dans le système de destination, cliquez sur **Démarrer**, cliquez sur **programmes**, cliquez sur **Microsoft SQL Server 2008**, puis cliquez sur **deSQLServerManagementStudio**.  
  
2.  Dans le **se connecter au serveur** boîte de dialogue, sélectionnez le **type de serveur** en tant que **moteur de base de données**, fournissez un nom de serveur, fournissez les informations d’identification pour se connecter ou le serveur, puis Cliquez sur **connexion**.  
  
3.  Ouvrez le serveur approprié en cliquant dessus, en double-cliquant sur **bases de données**, en double-cliquant sur **BizTalkMgmtDb**, puis en cliquant sur **Tables**.  
  
4.  Dans le volet détails, cliquez sur **adm_Group**, puis pointez sur **ouvrir la Table**.  
  
5.  Modifier les colonnes correspondant à la base de données d’origine pour référencer les valeurs appropriées pour la nouvelle base de données.  
  
    > [!NOTE]  
    >  *\<DBType >* NomServeurBD et  *\<DBType >* DBName indiquer l’emplacement de la base de données, où  *\<DBType >* correspond au type de la base de données, par exemple, TrackingAnalysis.  
  
6.  Fermez la table pour enregistrer les nouvelles valeurs.  
  
## <a name="see-also"></a>Voir aussi  
 [Mise à jour des références de base de données](../technical-guides/updating-database-references.md)