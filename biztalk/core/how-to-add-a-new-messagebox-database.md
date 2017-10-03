---
title: "Comment ajouter une nouvelle base de données MessageBox | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- adding, MessageBox database
- MessageBox database, adding
- managing [MessageBox database], adding
ms.assetid: 98d850dc-fe3e-43dd-8b5d-9b8c23c006ae
caps.latest.revision: "21"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: cab4fd370aab2d85519b3fd52e0dadcd9583275e
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-add-a-new-messagebox-database"></a>Ajout d'une nouvelle base de données MessageBox
Vous pouvez utiliser la console Administration de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] pour ajouter une nouvelle base de données MessageBox à votre déploiement BizTalk Server. Les bases de données MessageBox sont à la base de l'équilibrage de la charge des opérations entre les serveurs de traitement coopératif. Pour accroître le nombre de messages pouvant être traités par votre système, vous pouvez ajouter des bases de données MessageBox supplémentaires.  
  
 Vous ne pouvez pas créer une base de données MessageBox et, en même temps, avoir des orchestrations, des ports d'envoi ou des groupes de ports d'envoi inscrits. Les orchestrations, ports d'envoi ou groupes de ports d'envoi inscrits accèdent à des données que BizTalk Server doit copier dans la nouvelle base de données MessageBox. Tant que ces données font l'objet d'un accès, BizTalk Server ne peut pas les copier dans la nouvelle base de données MessageBox.  
  
 Vous pouvez désigner des bases de données locales et distantes comme bases de données MessageBox. Pour plus d’informations sur les bases de données BizTalk Server, consultez [bases de données BizTalk Server](../core/databases-in-biztalk-server.md).  
  
> [!IMPORTANT]
>  L'Agent SQL Server doit s'exécuter sur tous les serveurs SQL Server auxquels vous voulez ajouter une nouvelle base de données MessageBox.  
  
## <a name="prerequisites"></a>Conditions préalables  
 Les administrateurs qui gèrent les bases de données MessageBox doivent disposer des droits d'utilisateur nécessaires. Pour gérer ces bases de données et désactiver la publication des nouveaux messages, vous devez :  
  
-   Vous devez ouvrir une session en tant que membre du groupe Administrateurs BizTalk Server.  
  
-   être un administrateur SQL Server sur l'ordinateur sur lequel se trouve la base de données.  
  
### <a name="to-add-a-new-messagebox-database"></a>Pour ajouter une nouvelle base de données MessageBox  
  
1.  Cliquez sur **Démarrer**, cliquez sur **tous les programmes**, cliquez sur [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], puis cliquez sur **Administration de BizTalk Server**.  
  
2.  Dans l’arborescence de la console, développez [!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)], développez le groupe BizTalk, puis cliquez sur **paramètres de plateforme**.  
  
3.  Avec le bouton droit **boîtes de Message**, cliquez sur **nouveau**, puis cliquez sur **boîte de Message**.  
  
4.  Dans le **propriétés de MessageBox** boîte de dialogue, procédez comme suit, puis cliquez sur **OK**:  
  
    |Utiliser|Pour effectuer cette opération|  
    |--------------|----------------|  
    |**SQL Server**|Afficher le nom du serveur SQL Server hébergeant la base de données MessageBox.|  
    |**Base de données**|Afficher le nom de la base de données MessageBox.|  
    |**Boîte de message d’abonnement principal**|Indiquer si la base de données MessageBox sélectionnée est la base principale. Si la base de données MessageBox active est la base principale, cette case à cocher est activée et indisponible. Par défaut, la première base de données MessageBox créée quand vous exécutez l'Assistant Configuration est la base de données principale.|  
    |**Désactiver la publication des nouveaux messages**|Activer cette case à cocher pour indiquer que cette base de données MessageBox ne doit pas recevoir de messages d'activation.|  
  
## <a name="see-also"></a>Voir aussi  
 [Gestion des bases de données MessageBox](../core/managing-messagebox-databases.md)   
 [Comment désactiver la Publication des nouveaux messages](../core/how-to-disable-new-message-publication.md)   
 [Comment supprimer une base de données MessageBox](../core/how-to-delete-a-messagebox-database.md)   
 [Sauvegarde et restauration des bases de données BizTalk Server](../core/backing-up-and-restoring-biztalk-server-databases.md)   
 [La base de données MessageBox](../core/the-messagebox-database.md)