---
title: "Le déplacement de Notification BAM Services Databases2 | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Notification Services Application database [BAM]
- Notification Services Instance database [BAM]
- migrating, Notification Services database [BAM]
ms.assetid: 4b7f3397-65c9-4c71-8374-8764f4c2e2e3
caps.latest.revision: "14"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 639a326878cd425a951581711c08a0a53127035b
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-move-the-bam-notification-services-databases"></a>Déplacement des bases de données des services de notification BAM
Cette procédure vous permet de déplacer les bases de données des services de notification BAM vers un autre serveur.  
  
> [!NOTE]
>  Vous devez déplacer la base de données d'application (BAMAlertsApplication) et la base de données d'instance (BAMAlertsNSMain) des services de notification BAM ensemble.  
  
## <a name="prerequisites"></a>Conditions préalables  
 Pour exécuter cette procédure, vous devez être connecté avec un compte membre du rôle de serveur fixe sysadmin SQL Server.  
  
### <a name="to-move-the-bam-notification-services-databases"></a>Pour déplacer les bases de données des services de notification BAM  
  
1.  Obtenez une copie du fichier .xml utilisé pour restaurer BAM :  
  
    1.  Cliquez sur **Démarrer**, puis sur **Exécuter**, tapez **cmd**, puis cliquez sur **OK**.  
  
    2.  À l'invite de commandes, accédez au répertoire suivant :  
  
         **%SystemDrive%\Program Files\Microsoft** [!INCLUDE[btsBizTalkServer2006r3ui](../includes/btsbiztalkserver2006r3ui-md.md)] **\Tracking**   
  
    3.  À l'invite de commandes, tapez :  
  
        ```  
        Bm.exe get-config –filename:BAMConfiguration.xml  
        ```  
  
        > [!NOTE]
        >  Sur les systèmes qui prennent en charge le contrôle de compte d'utilisateur, vous devrez peut-être exécuter l'outil avec des privilèges d'administrateur.  
  
2.  À l'invite de commandes, tapez :  
  
    ```  
    Net stop NS$BamAlerts  
    ```  
  
3.  Suivez les instructions de la documentation en ligne de SQL Server pour sauvegarder la base de données sur l'ancien serveur.  
  
4.  Copiez les bases de données des services de notification BAM sur le nouveau serveur SQL Server.  
  
5.  Suivez les instructions de la documentation en ligne de SQL Server pour restaurer la base de données sur le nouveau serveur.  
  
6.  Modifiez le fichier BAMConfiguration.xml et définissez le nom du serveur dans la section Alert DeploymentUnit sur le nom du nouveau serveur.  
  
7.  Enregistrez le fichier BAMConfiguration.xml, puis fermez-le.  
  
8.  Cliquez sur **Démarrer**, puis sur **Exécuter**, tapez **cmd**, puis cliquez sur **OK**.  
  
9. À l'invite de commandes, accédez au répertoire suivant :  
  
     **%SystemDrive%\Program Files\Microsoft** [!INCLUDE[btsBizTalkServer2006r3ui](../includes/btsbiztalkserver2006r3ui-md.md)] **\Tracking**   
  
10. À l'invite de commandes, tapez :  
  
    ```  
    bm.exe update-config -FileName:BAMConfiguration.xml  
    ```  
  
    > [!NOTE]
    >  Sur les systèmes qui prennent en charge le contrôle de compte d'utilisateur, vous devrez peut-être exécuter l'outil avec des privilèges d'administrateur.  
  
11. Mettez à jour les références aux bases de données des services de notification BAM. Pour plus d’informations, consultez [comment la mise à jour des références aux bases de données Services de Notification BAM](../core/how-to-update-references-to-the-bam-notification-services-databases.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Déplacement de bases de données BizTalk Server](../core/moving-biztalk-server-databases.md)