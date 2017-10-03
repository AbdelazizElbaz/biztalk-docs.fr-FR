---
title: "Comment déplacer la Database2 d’analyse BAM | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- migrating, Analysis database [BAM]
- Analysis database [BAM], migrating
ms.assetid: b0320273-4840-4573-bb82-bba95021535e
caps.latest.revision: "12"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 6f9ae627dffd36ceca78e7da0b9e8e516845691a
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-move-the-bam-analysis-database"></a>Déplacement de la base de données d'analyse BAM
Cette procédure vous permet de déplacer la base de données d'analyse BAM vers un autre serveur.  
  
## <a name="prerequisites"></a>Conditions préalables  
 Pour exécuter cette procédure, vous devez être connecté avec un compte membre du rôle de serveur fixe sysadmin SQL Server.  
  
### <a name="to-move-the-bam-analysis-database"></a>Pour déplacer la base de données d'analyse BAM  
  
1.  Obtenez une copie du fichier .xml utilisé pour restaurer BAM :  
  
    1.  Cliquez sur **Démarrer**, puis sur **Exécuter**, tapez **cmd**, puis cliquez sur **OK**.  
  
    2.  À l'invite de commandes, accédez au répertoire suivant :  
  
         [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]Tracking  
  
    3.  À l'invite de commandes, tapez :  
  
        ```  
        Bm.exe get-config –filename:BAMConfiguration.xml  
        ```  
  
        > [!NOTE]
        >  Sur les systèmes qui prennent en charge le contrôle de compte d'utilisateur, vous devrez peut-être exécuter l'outil avec des privilèges d'administrateur.  
  
2.  Suivez les instructions de la documentation en ligne de SQL Server pour sauvegarder la base de données sur l'ancien serveur.  
  
3.  Copiez la base de données d'analyse BAM sur le nouveau serveur SQL Server.  
  
4.  Suivez les instructions de la documentation en ligne de SQL Server pour restaurer la base de données sur le nouveau serveur.  
  
5.  Modifiez le fichier BAMConfiguration.xml et définissez le nom du serveur dans la section AnalysisDatabase DeploymentUnit sur le nom du nouveau serveur.  
  
6.  Enregistrez le fichier BAMConfiguration.xml, puis fermez-le.  
  
7.  Cliquez sur **Démarrer**, puis sur **Exécuter**, tapez **cmd**, puis cliquez sur **OK**.  
  
8.  À l'invite de commandes, accédez au répertoire suivant :  
  
     [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]Tracking  
  
9. À l'invite de commandes, tapez :  
  
    ```  
    bm.exe update-config -FileName:BAMConfiguration.xml  
    ```  
  
    > [!NOTE]
    >  Sur les systèmes qui prennent en charge le contrôle de compte d'utilisateur, vous devrez peut-être exécuter l'outil avec des privilèges d'administrateur.  
  
## <a name="see-also"></a>Voir aussi  
 [Déplacement de bases de données BizTalk Server](../core/moving-biztalk-server-databases.md)