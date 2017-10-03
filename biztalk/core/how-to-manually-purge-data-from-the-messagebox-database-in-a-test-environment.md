---
title: "Purge manuelle des données à partir de la base de données MessageBox dans un environnement de Test | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 398991a9-344a-487a-a817-dfc97d48ebe6
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: d4a6d5f8b232e31a140ee4786b87d2bb270505f2
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-manually-purge-data-from-the-messagebox-database-in-a-test-environment"></a>Purge manuelle des données de la base de données MessageBox dans un environnement de test
Lors de l'exécution de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] dans un environnement de développement ou de test, les données stockées dans la base de données MessageBox ne sont généralement pas des données actives critiques et peuvent donc être supprimées. Dans ces scénarios, vous pouvez avoir besoin d'une méthode rapide pour purger les données de la base de données MessageBox. Suivez les procédures de cette rubrique pour purger manuellement les données de la base de données MessageBox à l'aide de la procédure stockée bts_CleanupMsgbox.  
  
> [!NOTE]
>  Vous devez uniquement effectuer ces opérations dans un environnement de test. La purge manuelle de la base de données MessageBox de BizTalk dans un environnement de production n'est pas prise en charge.  
  
### <a name="to-stop-biztalk-services"></a>Pour arrêter les services BizTalk  
  
1.  Arrêtez les instances du service BizTalk à partir de la console Services.  
  
2.  Si vous exécutez des adaptateurs dans des hôtes isolés (par exemple, HTTP, SOAP ou WCF), redémarrez IIS en exécutant IISRESET dans une invite de commandes.  
  
3.  Arrêtez les adaptateurs isolés personnalisés en cours d'exécution.  
  
### <a name="to-create-and-execute-the-btscleanupmsgbox-stored-procedure-using-sql-server-2008"></a>Pour créer et exécuter la procédure stockée bts_CleanupMsgbox à l'aide de SQL Server 2008  
  
1.  Cliquez sur **Démarrer**, cliquez sur **tous les programmes**, cliquez sur **Microsoft SQL Server 2008 R2**, puis cliquez sur **SQL Server Management Studio**.  
  
2.  Dans le **se connecter à SQL Server** boîte de dialogue, sélectionnez le serveur SQL server et la méthode d’authentification appropriée, puis cliquez sur **connexion**.  
  
3.  Dans le **bases de données disponibles** liste déroulante, sélectionnez la base de données BizTalk Messagebox (**BizTalkMsgBoxDB** par défaut).  
  
4.  Cliquez sur le **nouvelle requête** icône dans la barre d’outils.  
  
5.  Ouvrez le **msgbox_cleanup_logic.sql** fichier à partir de SQL Server Management Studio. Le fichier msgbox_cleanup_logic.sql est situé dans le répertoire [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]Schema\ de l'ordinateur BizTalk Server.  
  
6.  Cliquez sur le **exécuter la requête** icône dans la barre d’outils pour exécuter le script pour créer le bts_CleanupMsgbox de procédure stockée. La procédure stockée bts_CleanupMsgbox peut ensuite être affichée dans la liste des procédures stockées en tant que dbo.bts_CleanupMsgbox.  
  
7.  Cliquez sur le **nouvelle requête** icône dans la barre d’outils.  
  
8.  Collez la commande suivante dans la fenêtre de la nouvelle requête :  
  
    ```  
    exec bts_CleanupMsgbox  
    ```  
  
9. Cliquez sur le **exécuter la requête** icône dans la barre d’outils pour exécuter le bts_CleanupMsgbox de procédure stockée.  
  
    > [!IMPORTANT]
    >  N'exécutez pas la procédure stockée bts_CleanupMsgbox sur un serveur de production exécutant [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]. Vous devez uniquement exécuter la procédure stockée bts_CleanupMsgbox dans un environnement de test. L'exécution de la procédure stockée bts_CleanupMsgbox dans un environnement de production n'est pas prise en charge.  
  
10. Redémarrez les services BizTalk si nécessaire.  
  
## <a name="considerations-when-running-the-btscleanupmsgbox-stored-procedure"></a>Considérations relatives à l'exécution de la procédure stockée bts_CleanupMsgbox  
 Les considérations suivantes s'appliquent lors de l'exécution de la procédure stockée bts_CleanupMsgbox :  
  
1.  Si vous installez un correctif sur votre système de test qui met à jour les schémas de la base de données BizTalk, celui-ci peut remplacer la procédure stockée bts_CleanupMsgbox par une version vide de cette procédure stockée. Dans ce cas, vous devez suivre les procédures présentées dans cette rubrique pour la recréer.  
  
2.  Si vous créez une base de données MessageBox, la procédure stockée bts_CleanupMsgbox est vide. Vous devez suivre les procédures présentées dans cette rubrique pour la recréer.  
  
3.  Utilisation de la procédure stockée bts_CleanupMsgbox est **ne pas pris en charge** sur un système de production. Cette procédure stockée supprime toutes les données de votre base de données MessageBox.  
  
## <a name="see-also"></a>Voir aussi  
 [Purge des données de la base de données de suivi de BizTalk](../core/how-to-purge-data-from-the-biztalk-tracking-database.md)