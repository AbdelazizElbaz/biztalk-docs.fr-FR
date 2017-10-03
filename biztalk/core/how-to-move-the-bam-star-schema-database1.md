---
title: "Comment déplacer la Database1 de schéma en étoile BAM | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Star Schema database [BAM], migrating
- migrating, Star Schema database [BAM]
ms.assetid: b4a5f8fc-0dc4-4987-b96f-ecd49bd4dba3
caps.latest.revision: "12"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 6661a9ae315988a5348198fa463e24ea508cf50f
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-move-the-bam-star-schema-database"></a>Déplacement de la base de données de schémas en étoile BAM
Cette procédure vous permet de déplacer la base de données de schémas en étoile BAM vers un autre serveur.  
  
## <a name="prerequisites"></a>Conditions préalables  
 Pour exécuter cette procédure, vous devez être connecté avec un compte membre du rôle de serveur fixe sysadmin SQL Server.  
  
### <a name="to-move-the-bam-star-schema-database"></a>Pour déplacer la base de données de schémas en étoile BAM  
  
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
  
3.  Copiez la base de données de schémas en étoile BAM sur le nouveau serveur SQL Server.  
  
4.  Suivez les instructions de la documentation en ligne de SQL Server pour restaurer la base de données sur le nouveau serveur.  
  
5.  Modifiez le fichier BAMConfiguration.xml et définissez le nom du serveur dans la section StarSchemaDatabase DeploymentUnit sur le nom du nouveau serveur.  
  
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
  
10. Mettez à jour la connexion SQL 2 en modifiant le nom du serveur et celui de la base de données dans tous les lots DTS de l'analyse BAM dotés du préfixe « BAM_AN_ ». Pour cela, suivez la procédure ci-dessous :  
  
    1.  Ouvrez le serveur hébergeant l'analyse BAM à l'aide de SQL Server Management Studio.  
  
    2.  Ouvrez le **Data Transformation Services** dossier.  
  
    3.  Ouvrez le **lots locaux** dossier.  
  
    4.  Ouvrez le lot DTS, puis double-cliquez sur **connexion 2** pour ouvrir la connexion.  
  
    5.  Dans la zone de liste déroulante, sélectionnez les nouveaux noms de serveur et de base de données.  
  
11. Mettez à jour la source de données dans la base de données d'analyse BAM comme indiqué ci-dessous :  
  
    1.  À l'aide de SQL Server Analysis Manager, ouvrez le serveur hébergeant la base de données d'analyse BAM.  
  
    2.  Ouvrez le **des Sources de données** dossier.  
  
    3.  Avec le bouton droit de la source de données pour le cube, puis cliquez sur **modifier**.  
  
    4.  Sur le **connexion** onglet, tapez le nouveau nom du serveur et le nom de base de données pour la base de données de schémas en étoile BAM, puis cliquez sur **OK**.  
  
## <a name="see-also"></a>Voir aussi  
 [Déplacement de bases de données BizTalk Server](../core/moving-biztalk-server-databases.md)