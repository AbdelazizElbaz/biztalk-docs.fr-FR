---
title: "Désactiver la Publication des nouveaux messages | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 9099ecaa-31ed-4880-a0f6-8dbfaf783f7a
caps.latest.revision: "17"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 478cf89ac4677d60e9a5b5a855998e0b0e5120c8
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="disable-new-message-publication"></a>Désactiver la Publication des nouveaux messages

## <a name="overview"></a>Vue d'ensemble
Vous pouvez utiliser la console Administration de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] ou Windows Management Instrumentation (WMI) pour désactiver la publication des nouveaux messages. Cette désactivation dans la base de données MessageBox permet d'arrêter la réception de nouveaux messages par cette base de données. Dans certains environnements BizTalk Server, la désactivation de la publication des nouveaux messages pour la base de données principale MessageBox permet d'améliorer les performances. Cette désactivation n'affecte pas les messages existants de la base de données MessageBox ni les instances de service en cours.  
  
 Pour plus d’informations sur l’utilisation de WMI pour désactiver la publication des nouveaux messages, consultez le **propriété MSBTS_MsgBoxSetting.DisableNewMessagePublication (WMI)** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)].
  
> [!IMPORTANT]
>  Pour pouvoir supprimer une base de données MessageBox, vous devez désactiver la publication des nouveaux messages. Pour plus d’informations sur la suppression d’une base de données MessageBox, consultez [comment supprimer une base de données MessageBox](../core/how-to-delete-a-messagebox-database.md).  
  
## <a name="prerequisites"></a>Conditions préalables  
 Les administrateurs qui gèrent les bases de données MessageBox doivent disposer des droits d'utilisateur nécessaires. Pour gérer ces bases de données et désactiver la publication des nouveaux messages, vous devez :  
  
-   Vous devez ouvrir une session en tant que membre du groupe Administrateurs BizTalk Server.  
  
-   être un administrateur SQL Server sur l'ordinateur sur lequel se trouve la base de données.  
  
## <a name="disable-steps"></a>Désactiver des étapes
  
1.  Cliquez sur **Démarrer**, cliquez sur **tous les programmes**, cliquez sur [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], puis cliquez sur **Administration de BizTalk Server**.  
  
2.  Dans l’arborescence de la console, développez [!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)], développez le groupe BizTalk, cliquez sur **paramètres de plateforme**, puis cliquez sur **boîtes de Message**.  
  
3.  Dans le volet de détails, cliquez sur la base de données MessageBox que vous voulez désactiver, puis cliquez sur **propriétés**.  
  
4.  Dans le **propriétés de MessageBox** boîte de dialogue, sélectionnez le **désactiver la publication des nouveaux messages** case à cocher, puis cliquez sur **OK**.  
  
## <a name="see-also"></a>Voir aussi  
 [Gestion des bases de données MessageBox](../core/managing-messagebox-databases.md)   
 [Ajouter une nouvelle base de données MessageBox](../core/how-to-add-a-new-messagebox-database.md)   
 [Supprimer une base de données MessageBox](../core/how-to-delete-a-messagebox-database.md)   
 [La base de données MessageBox](../core/the-messagebox-database.md)