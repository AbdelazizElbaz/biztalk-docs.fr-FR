---
title: "Considérations sur la sécurité des messages et le suivi des instances de données | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- permissions, HAT
- MessageBox database, HAT
- Tracking database, HAT
- security, HAT
- HAT, permissions
- HAT, security
- Management database, HAT
ms.assetid: 83e47dc2-c8e2-42a2-9c85-d511e7dae83f
caps.latest.revision: "21"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 7c342a62470fa26365f439cda242eeb119689737
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="security-considerations-for-message-and-instance-data-tracking"></a>Considérations de sécurité pour le suivi des données de message et d'instance
Pour des raisons de sécurité, le suivi des messages et des instances de service n'utilise pas de navigateurs ou d'URL, comme dans les versions précédentes de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]. Cette option de surveillance est incluse en tant que page Présentation du groupe dans la console Administration de BizTalk Server.  Pour la compatibilité avec des versions antérieures, [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] héberge toujours Microsoft Internet Explorer dans un shell pour des raisons de sécurité.  
  
 À l'aide des données de suivi des messages et des instances de service, vous pouvez accéder aux détails techniques nécessaires pour dépanner et optimiser votre environnement [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]. L'outil de données de suivi étant très puissant, nous vous conseillons d'en restreindre l'accès dans votre environnement de production pour éviter que des utilisateurs malveillants ou non autorisés causent des dommages. Il est conseillé de suivre les recommandations suivantes pour sécuriser et utiliser la console Administration de BizTalk Server dans votre environnement.  
  
-   Pour afficher des données à l'aide de la console Administration de BizTalk Server, vous devez ouvrir une session en tant que membre du groupe Opérateurs [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]. Pour pouvoir accéder aux corps des messages dans la section Présentation du groupe de la console Administration de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], vous devez ouvrir une session en tant que membre du groupe Administrateurs [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].  
  
     Lorsque vous utilisez le suivi des messages et des instances de service, vous pouvez accéder aux bases de données suivantes :  
  
    |Base de données|Groupe d'utilisateurs/Autorisations|  
    |--------------|-----------------------------|  
    |gestion BizTalk (BizTalkMgmtDb) ;|Administrateurs [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], Opérateurs [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
    |MessageBox BizTalk (BizTalkMsgBoxDb)|Administrateurs [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], Opérateurs [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] ou autorisations de lecture/écriture|  
    |Suivi BizTalk (BizTalkDTADb)|Administrateurs [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], Opérateurs [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] ou autorisations de lecture seule|  
  
-   Le suivi des messages et des instances de service génère des rapports sur tous les hôtes de l'environnement [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] en se basant sur les paramètres d'une requête. Pour minimiser les risques de divulgation d'informations, seuls les membres du groupe Administrateurs [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] peuvent utiliser la console Administrateur de BizTalk Server pour exécuter ces requêtes. Toutefois, si vous ne voulez pas que tous les Administrateurs [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] aient accès aux données produites par ce processus de suivi, vous pouvez limiter leur accès aux données en ajoutant/supprimant des utilisateurs dans les rôles du serveur SQL Server HM_EVENT_WRITER et BAM_EVENT_WRITER dans la base de données des suivis BizTalk (BizTalkDTADb).  
  
-   BizTalk utilise ces rôles pour accorder ou refuser à leurs membres l'accès en écriture et en lecture aux données de suivi dans la base de données correspondante, sans l'aide de l'appartenance au rôle. Ne supprimez pas ces rôles du serveur SQL Server. Lorsqu'un hôte qui héberge le suivi ne l'héberge plus (ou inversement), la procédure stockée adm_ChangeHostTrackingPrivilege est appelée. Cette procédure lit la définition des rôles de serveur SQL Server BAM_EVENT_WRITER et HM_EVENT_WRITER et applique l'instruction d'autorisation ou de refus correspondante au groupe Windows de l'hôte. Cela revient à ajouter le groupe Windows de l'hôte à ces rôles SQL.  
  
-   Lorsque vous configurez les préférences de la console Administration de BizTalk Server pour afficher les données d'une base de données archivée, les requêtes de suivi se connectent aux bases de données qui contiennent les données archivées, et pas à la base de données des suivis BizTalk (BizTalkDTADb) active.  
  
-   Le débogage des orchestrations actives ne peut pas être effectué dans les pare-feu de traduction d'adresse réseau (NAT, &lt;localizedText&gt;Network Address Translation&lt;/localizedText&gt;). Pour effectuer cette opération, vous devez disposer d'un ordinateur d'administration dans le domaine de traitement.  
  
-   Suivant la façon dont vous configurez le suivi ainsi que les pipelines, il se peut que [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] stocke des informations personnelles contenues dans le contexte du message. Si vous utilisez WMI ou le suivi pour enregistrer les corps de messages à l'emplacement d'un fichier, assurez-vous que l'emplacement est associé à une liste de contrôle d'accès discrétionnaire renforcée autorisant les seuls administrateurs [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] à lire ces corps de messages. Appliquez la même liste de contrôle d'accès discrétionnaire à tous les emplacements où vous enregistrez les corps de messages, y compris les bases de données autres que BizTalk dans lesquelles vous pouvez archiver et restaurer ces corps de messages.  
  
-   Vous devez accorder des autorisations manuellement au groupe Administrateurs [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] pour l'accès à la base de données du serveur d'analyse des suivis (BizTalkAnalysisDb) ; par défaut, seuls les administrateurs OLAP disposent d'autorisations sur cette base.  
  
## <a name="see-also"></a>Voir aussi  
 [Planification de Message et le suivi des instances](../core/planning-for-message-and-instance-tracking.md)   
 [Affichage des messages suivis et les données d’Instance](../core/viewing-tracked-message-and-instance-data.md)