---
title: Comment modifier les comptes de Service et les mots de passe | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: dff53d6b-c262-4b66-b822-1c61f54ae105
caps.latest.revision: "20"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 77ce9dc143765f9db49c5880da4fa4202e26c0f3
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-change-service-accounts-and-passwords"></a>Modification des comptes de service et des mots de passe
Une fois BizTalk Server configuré, les organisations ont souvent besoin de modifier les comptes de service ou les mots de passe conformément aux stratégies concernant les mots de passe et le verrouillage des comptes. Pour plus d’informations sur les stratégies de compte, consultez le site Web Microsoft TechNet à l’adresse [http://go.microsoft.com/fwlink/?LinkId=62172](http://go.microsoft.com/fwlink/?LinkId=62172).  
  
 Lorsque vous modifiez les comptes de service ou les mots de passe, vous devez effectuer les opérations suivantes :  
  
1.  Créez un nouveau compte de service ou modifiez le mot de passe des comptes existants.  
  
2.  Assurez-vous que le compte de service est membre des groupes Windows nécessaires. Pour plus d’informations sur les groupes locaux ou de domaine auxquels vous devez ajouter le compte de service, consultez [groupes Windows et les comptes d’utilisateur de BizTalk Server](../core/windows-groups-and-user-accounts-in-biztalk-server.md).  
  
    > [!NOTE]
    >  Dans un environnement de groupe de domaine, vous utilisez la console Utilisateurs et ordinateurs Active Directory. Dans un environnement de groupe local, vous utilisez la console Gestion de l'ordinateur.  
  
3.  Effectuez les opérations suivantes en fonction du type de compte de service.  
  
    |Service ou compte|Comment modifier les comptes d’utilisateur|Tâches requises après la modification des comptes d'utilisateur|Modification des mots de passe|Tâches requises après la modification des mots de passe|  
    |------------------------|---------------------------------|-------------------------------------------------|-----------------------------|---------------------------------------------|  
    |Service d'authentification unique de l'entreprise sur le serveur de secret principal|1.  Vérifiez que vous disposez d'une sauvegarde du secret principal. Pour plus d’informations, consultez [comment revenir Up the Master Secret](../core/how-to-back-up-the-master-secret.md).<br />2.  Modifiez le compte du service à l'aide de la console Services.<br />3.  Restaurez le secret principal. Pour plus d’informations, consultez [comment restaurer le Secret principal](../core/how-to-restore-the-master-secret.md).|Redémarrez le service.|Modifiez le mot de passe du compte à l'aide de la console Services.|Redémarrez le service.|  
    |Service d'authentification unique de l'entreprise|Modifiez le compte du service à l'aide de la console Services.|Redémarrez le service.|Modifiez le mot de passe du compte à l'aide de la console Services.|Redémarrez le service.|  
    |Instance d'hôte BizTalk|Modifiez le compte de service à l'aide de la console Administration de BizTalk Server.|Redémarrez l’instance d’hôte BizTalk.|Modifiez le mot de passe du compte à l'aide de la console Administration de BizTalk Server ou de la console Services.|Redémarrez l'instance de l'hôte BizTalk.|  
    |Instance d'hôte isolée BizTalk et pool d'applications correspondant hébergeant l'adaptateur de réception SOAP.|1.  Modifiez le compte de service à l'aide de la console Administration de BizTalk Server.<br />2.  Modifier le compte du pool d’applications à l’aide de la console de gestion IIS **Remarque :** le compte de service pour le pool d’applications doit correspondre au compte de service pour un hôte isolé correspondant.|1.  Modifiez le compte de service du pool d'applications correspondant à l'aide de la console de gestion IIS.<br />2.  Redémarrez le pool d'applications à l'aide de la console de gestion IIS.|Modifier le mot de passe du compte sous lequel s’exécute le pool d’applications. à l’aide de la console de gestion IIS **Remarque :** vous n’avez pas besoin de modifier le mot de passe dans la console Administration de BizTalk Server après avoir modifié le mot de passe.|1.  Modifiez le mot de passe du compte sous lequel le pool d'applications correspondant s'exécute à l'aide de la console de gestion IIS.<br />2.  Redémarrez le pool d'applications à l'aide de la console de gestion IIS.|  
    |Service de mise à jour du moteur des règles|Modifiez le compte de service à l'aide de la console Gestionnaire de configuration ou Services.<br /><br /> Le Gestionnaire de configuration redémarre automatiquement le service.|Si vous utilisez la console Services, vous devez redémarrer manuellement le service.|Modifiez le mot de passe du compte à l'aide de la console Gestionnaire de configuration ou Services.<br /><br /> Le Gestionnaire de configuration redémarre automatiquement le service.|Si vous utilisez la console Services, vous devez redémarrer le service manuellement.|  
    |Service de notification BAM|1.  Ajoutez le nouveau compte sur le serveur SQL Server sur lequel le service de notification BAM a été installé.<br />2.  Octroyez les privilèges au nouveau compte. Pour plus d’informations sur les privilèges requis, consultez [groupes Windows et les comptes d’utilisateur de BizTalk Server](../core/windows-groups-and-user-accounts-in-biztalk-server.md)<br />3.  Modifiez le compte du service à l'aide de la console Services.|Redémarrez le service.|Modifier le mot de passe du compte à l’aide de la Console Services|Redémarrez le service.|  
    |Service Web de gestion BAM|1.  Ajoutez le nouveau compte pour le serveur SQL server approprié et accordez les privilèges dans [groupes Windows et les comptes d’utilisateur de BizTalk Server](../core/windows-groups-and-user-accounts-in-biztalk-server.md).<br />2.  Modifiez le compte d'utilisateur à l'aide du Gestionnaire de configuration.||Modifiez le mot de passe du compte d'utilisateur à l'aide du Gestionnaire de configuration.||  
    |Pool d'applications BAM|Modifiez le compte de service du pool d'applications à l'aide du Gestionnaire de configuration.<br /><br /> Le Gestionnaire de configuration redémarre automatiquement le pool d'applications.||Modifiez le mot de passe du compte à l'aide du Gestionnaire de configuration.<br /><br /> Le Gestionnaire de configuration redémarre automatiquement le pool d'applications.||  
  
 La procédure suivante décrit la modification des comptes de service et des mots de passe à l'aide du Gestionnaire de configuration.  
  
### <a name="to-change-service-accounts-and-passwords-using-configuration-manager"></a>Pour modifier les comptes de service et les mots de passe à l'aide du Gestionnaire de configuration  
  
1.  Cliquez sur **Démarrer**, cliquez sur **tous les programmes**, cliquez sur [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], puis cliquez sur **Configuration de BizTalk Server**.  
  
2.  Dans le **Configuration de Microsoft BizTalk Server**, cliquez sur **vue**, cliquez sur **les comptes de Service**, puis modifiez les comptes de service et les mots de passe dans le  **Les comptes de service** boîte de dialogue. Pour plus d’informations sur le Gestionnaire de Configuration, consultez [importer et exporter une Configuration de BizTalk Server](../install-and-config-guides/import-and-export-biztalk-server-configuration.md).  
  
    > [!NOTE]
    >  Le Gestionnaire de configuration ne fournit pas d'emplacement centralisé permettant de contrôler plusieurs ordinateurs. Si vous installez Microsoft BizTalk Server sur plusieurs ordinateurs, vous devez modifier les comptes de service et les mots de passe sur chaque ordinateur d'exécution.  
  
## <a name="see-also"></a>Voir aussi  
 [Groupes Windows et les comptes d’utilisateur dans BizTalk Server](../core/windows-groups-and-user-accounts-in-biztalk-server.md)   
 [Configuration de BizTalk Server](../install-and-config-guides/configure-biztalk-server.md)   
 [Gestion de la sécurité de BizTalk Server](../core/managing-biztalk-server-security.md)   
 [Meilleures pratiques pour la gestion des comptes d’utilisateurs et groupes Windows](../core/best-practices-for-managing-windows-groups-and-user-accounts.md)   
 [Gestion des hôtes et des comptes de Service](../core/managing-hosts-and-service-accounts.md)