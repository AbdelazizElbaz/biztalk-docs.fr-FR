---
title: "Comment mettre à jour les ordinateurs Runtime | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 576a7065-04b6-436c-acf9-28c8d6e40107
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: ca8edb4da6b59c33f87100ee3669bb2472d4350c
ms.sourcegitcommit: 3fc338e52d5dbca2c3ea1685a2faafc7582fe23a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/01/2017
---
# <a name="how-to-update-the-runtime-computers"></a>Comment mettre à jour les ordinateurs d’exécution
Le système de destination [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] runtime ordinateurs sont configurés avec le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Assistant de Configuration en tant que partie du groupe BizTalk de production en cours d’exécution dans l’environnement de production. Lorsque le groupe BizTalk de production est restauré dans l’environnement de récupération d’urgence, les paramètres doivent être mis à jour sur chaque [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] ordinateur d’exécution afin qu’il pointe vers la récupération d’urgence [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] instances lorsqu’il tente de se connecter à la restauration groupe BizTalk de production. Une fois le groupe BizTalk est restauré dans le système de destination, utilisez la procédure suivante pour mettre à jour le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] ordinateurs d’exécution.  
  
### <a name="to-update-the-biztalk-server-runtime-computers"></a>Pour mettre à jour les ordinateurs d’exécution BizTalk Server  
  
1.  Copiez le fichier SampleUpdateInfo.xml modifié pour le répertoire BizTalk Server\Schema\Restore sur chaque serveur BizTalk de 32 bits Program Files\Microsoft ou pour le répertoire \Program fichiers (x86) \Microsoft BizTalk Server\Bins32\Schema\Restore chaque 64 bits BizTalk serveur du système de destination.  
  
2.  Sur chaque serveur BizTalk server, ouvrez une invite de commandes. Cliquez sur **Démarrer**, puis sur **Exécuter**, tapez **cmd**, puis cliquez sur **OK**.  
  
    > [!NOTE]  
    >  Sur les ordinateurs 64 bits, vous devez ouvrir une invite de commandes 64 bits.  
  
3.  À l’invite de commandes, accédez à \Program Files\Microsoft BizTalk Server\Schema\Restore (sur les ordinateurs 32 bits) ou à \Program fichiers (x86) \Microsoft BizTalk Server\Bins32\Schema\Restore (sur les ordinateurs 64 bits) et tapez la commande suivante :  
  
    ```  
    cscript UpdateRegistry.vbs SampleUpdateInfo.xml  
    ```  
  
4.  Activer et redémarrer toutes les instances d’hôte BizTalk et tous les autres Services BizTalk sur les serveurs BizTalk Server dans le système de destination.  
  
5.  Redémarrez WMI sur chaque serveur BizTalk server dans le système de destination. Cliquez sur **Démarrer**, cliquez sur **exécuter**, type **services.msc**, puis cliquez sur **OK**. Dans le **Services** MMC enfichable, avec le bouton **Windows Management Instrumentation** et sélectionnez **redémarrer**.  
  
6.  Sur chaque serveur BizTalk server, ouvrez le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] console d’Administration, avec le bouton droit **groupe BizTalk**, puis sélectionnez **supprimer**.  
  
7.  Avec le bouton droit **Administration de BizTalk Server 2010**, sélectionnez **se connecter au groupe existant**, sélectionnez l’instance de base de données SQL Server et le nom qui correspond à la base de données de gestion BizTalk pour la base de données le groupe BizTalk, puis cliquez sur **OK**.  
  
    > [!NOTE]  
    >  Après la mise à jour la [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] ordinateurs d’exécution, vous devrez peut-être également mettre à jour le **nom du serveur SSO** tel qu’affiché dans le **propriétés du groupe** boîte de dialogue disponible dans le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Console d’administration. Pour mettre à jour le **nom du serveur SSO**, lancez le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] console d’Administration, développez [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration, avec le bouton droit le **groupe BizTalk** nœud et sélectionnez **Propriétés** pour afficher les **général** onglet du [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] console d’Administration. Puis, dans le **nom du serveur SSO** zone de texte, entrez le nom du serveur Enterprise Single Sign-On que cet ordinateur doit utiliser pour accéder aux informations de configuration pour les cartes réseau et cliquez sur **OK**. Il s'agit du nom du serveur d'authentification unique utilisé pour établir la connexion à la base de données d'authentification unique.  
  
8.  Redémarrez les services Windows suivants sur chaque serveur d’exécution de BizTalk server :  
  
    -   Service de l’authentification unique d’entreprise  
  
    -   Service de mise à jour du moteur des règles  
  
    -   Instances d’hôte BizTalk  
  
## <a name="see-also"></a>Voir aussi  
 [Récupération des ordinateurs d’exécution](../technical-guides/recovering-the-runtime-computers.md)