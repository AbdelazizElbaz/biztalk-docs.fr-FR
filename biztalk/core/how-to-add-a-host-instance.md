---
title: "Ajouter une Instance d’hôte | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 98ba10a6-c5e7-4dec-98f1-4e6ba44c2851
caps.latest.revision: "27"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 6a446f5527bf06164d14079c0bb40f2f41942f38
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="add-a-host-instance"></a>Ajouter une Instance d’hôte

## <a name="overview"></a>Vue d'ensemble
La console Administration de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] ou Windows Management Instrumentation (WMI) permet d'ajouter des instances d'hôte. En revanche, dans [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], vous ne pouvez ajouter une instance d'hôte qu'à un seul serveur à la fois. Pour plus d’informations sur les instances d’hôte, consultez [Instances d’hôte](../core/host-instances.md). Pour plus d’informations sur l’utilisation de WMI pour ajouter une instance d’hôte, consultez **MSBTS_HostInstance (WMI)** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)].
  
 L'ajout d'une instance d'hôte mappe l'instance d'un hôte donné sur une instance de BizTalk Server.  Lorsqu'une instance d'hôte existante doit être réparée, vous pouvez mettre à jour ses propriétés. Avant d'ajouter à nouveau une instance d'hôte existante, vous devez l'arrêter. Pour plus d’informations sur l’arrêt d’une instance d’hôte, consultez [comment arrêter une Instance d’hôte](../core/how-to-stop-a-host-instance.md).  
  
> [!NOTE]
>  Si vous souhaitez créer plus de 26 instances d’hôte, vous devez suivre les instructions dans l’article suivant de la Base de connaissances 184802, « User32.dll ou Kernel32.dll ne parvient pas à initialiser, » qui est disponible à l’adresse [http://go.microsoft.com/fwlink/?LinkId=26176](http://go.microsoft.com/fwlink/?LinkId=26176). Si vous avez besoin d'instances d'hôte supplémentaires après avoir appliqué les recommandations de cet article de la Base de connaissances, vous pouvez essayer de réduire la quantité de mémoire disponible pour chaque instance du service BTSNTSvc. Cette opération fournira la mémoire supplémentaire requise pour créer plus d'instances.  
  
> [!NOTE]
>  Le compte de service disposera automatiquement de l'autorisation « Ouvrir une session en tant que service » sur le serveur où l'instance d'hôte est installée.  
  
## <a name="prerequisites"></a>Conditions préalables  
 Pour exécuter cette procédure, vous devez avoir ouvert une session en tant que membre du groupe des administrateurs BizTalk Server ou du groupe des administrateurs Windows.  
  
 Vous devez également être un membre du rôle de la base de données SQL Server db_securityadmin et du rôle SQL Server securityadmin sur les serveurs sur lesquels se trouvent les bases de données suivantes :  
  
-   importation principale BAM (BAMPrimaryImport).  
  
-   gestion BizTalk (BizTalkMgmtDb) ;  
  
-   MessageBox BizTalk (BizTalkMsgBoxDb) (tout) ;  
  
-   suivis BizTalk (BizTalkDTADb) ;  
  
-   moteur des règles (BizTalkRuleEngineDb) ;  
  
> [!CAUTION]
>  Nous vous recommandons de mettre à jour les informations de compte des instances d'hôte à l'aide de la console Administration de BizTalk Server ou d'un script WMI (Windows Management Instrumentation). De cette manière, BizTalk Server peut mettre à jour les informations de compte dans les bases de données BizTalk Server et peut synchroniser la configuration de sécurité entre les bases de données et l'instance d'hôte.  
  
## <a name="steps"></a>Étapes
  
1.  Cliquez sur **Démarrer**, cliquez sur **tous les programmes**, cliquez sur [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], puis cliquez sur **Administration de BizTalk Server**.  
  
2.  Dans l’arborescence de la console, développez [!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)], développez le groupe BizTalk, puis cliquez sur **paramètres de plateforme**.  
  
3.  Avec le bouton droit **Instances d’hôte**, cliquez sur **nouveau**, puis cliquez sur **Instance d’hôte**.  
  
4.  Dans le **propriétés de l’Instance hôte** boîte de dialogue, procédez comme suit, puis cliquez sur **OK**:  
  
    |Utiliser|Pour effectuer cette opération|  
    |--------------|----------------|  
    |**Nom d’hôte**|Afficher le nom de l'hôte associé au serveur sélectionné.|  
    |**Server**|Afficher le serveur associé à l'hôte sélectionné.|  
    |**Ouverture de session**|Afficher le nom de compte du nouveau service sous lequel l'instance de l'hôte doit s'exécuter.|  
    |**Configurer**|Cliquez pour afficher les **informations d’identification d’ouverture de session** boîte de dialogue, dans lequel vous pouvez entrer le nom de compte et le mot de passe du compte sous lequel s’exécute l’instance d’hôte.|  
    |**Désactiver l’instance de l’hôte de démarrer**|Activer cette case à cocher pour faire passer l'état de l'hôte sélectionné de « Activé » à « Désactivé ». La désactivation d'une instance de l'hôte est utile lorsque vous ne souhaitez pas que l'instance démarre, mais que vous voulez tout de même conserver sa configuration.|  
  
 Après avoir installé une instance d'hôte, vous devez la démarrer pour qu'elle puisse acheminer des messages vers la base de données MessageBox. Pour plus d’informations sur le démarrage d’une instance d’hôte, consultez [comment démarrer une Instance d’hôte](../core/how-to-start-a-host-instance.md).  
  
## <a name="known-issues"></a>Problèmes connus  
  
#### <a name="a-biztalk-host-instance-is-created-with-a-status-of-uninstall-failed-if-the-designated-biztalk-server-runtime-computer-is-not-available-during-host-instance-creation"></a>Une instance d'hôte BizTalk Host est créée avec l'état « Échec de la désinstallation » si l'ordinateur d'exécution BizTalk Server désigné n'est pas disponible lors de sa création.  
  
##### <a name="problem"></a>Problème  
 Si la console Administration de BizTalk est installée sur une ordinateur distant d'un ordinateur d'exécution [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], il est possible de tenter de créer une instance d'hôte sur l'ordinateur [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] distant, même si l'ordinateur [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] n'est pas disponible.  
  
 Si vous essayez de créer une instance d'un hôte BizTalk sur un ordinateur [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] non disponible, une boîte de dialogue s'affiche avec le message d'erreur suivant :  
  
 Installation de l’instance d’hôte \< *nom d’hôte*> sur le serveur \< *nom du serveur*> a échoué.  
  
 Informations supplémentaires :  
  
 Le serveur RPC n'est pas disponible. (WinMgmt)  
  
 Lorsque vous cliquez sur OK pour refermer la boîte de dialogue, une autre s'affiche avec le message d'erreur suivant :  
  
 Nettoyage abandonné l’installation de l’hôte \< *nom d’hôte*> sur le serveur \< *nom du serveur*> a échoué.  
  
 Informations supplémentaires :  
  
 Une erreur s’est produite lors de la suppression du service Windows NT BTSSvc {*\<GUID >*}. (WinMgmt)  
  
 Lorsque vous cliquez sur **OK** pour fermer cette boîte de dialogue, l’instance de l’hôte BizTalk seront visible dans la Console Administration de BizTalk avec un **état** de **échouée de la désinstallation** .  
  
##### <a name="cause"></a>Cause  
 Lors de la création d'une instance d'hôte, une entrée est effectuée dans la base de données de gestion BizTalk avant que l'instance d'hôte ne soit installée sur l'ordinateur [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] désigné. Si l'installation de l'instance d'hôte sur l'ordinateur [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] désigné échoue, le programme Administration de BizTalk tente de la désinstaller mais l'ordinateur [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] désigné étant non disponible, la désinstallation échoue également.  
  
##### <a name="resolution"></a>Résolution  
 Si une instance d’hôte BizTalk est créée dans la Console Administration de BizTalk avec l’état **échouée de la désinstallation**, de supprimer l’instance d’hôte et recréer l’instance d’hôte, une fois que l’ordinateur BizTalk Server désigné est disponible.  
  
> [!NOTE]
>  Si une instance d’hôte BizTalk est créée dans la Console Administration de BizTalk avec un **état** de **échouée de la désinstallation** l’instance d’hôte ne sera pas fonctionnelle même après désigné [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] ordinateur redevient disponible.  
  
## <a name="see-also"></a>Voir aussi  
 [La gestion des hôtes BizTalk et les Instances d’hôte](../core/managing-biztalk-hosts-and-host-instances.md)   
 [Démarrer une Instance d’hôte](../core/how-to-start-a-host-instance.md)   
 [Arrêter une Instance d’hôte](../core/how-to-stop-a-host-instance.md)   
 [Supprimer une Instance d’hôte](../core/how-to-delete-a-host-instance.md)   
 [Modifier les propriétés de l’Instance hôte](../core/how-to-modify-host-instance-properties.md)