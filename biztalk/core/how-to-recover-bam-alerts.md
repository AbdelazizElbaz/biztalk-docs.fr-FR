---
title: "Comment récupérer les alertes BAM | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 56c477b4-4605-4763-b20a-3baf4529f13f
caps.latest.revision: "15"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 37c18265712fa2f0dd1bb2d83d756cc9a9bd1505
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-recover-bam-alerts"></a>Récupération des alertes BAM
Si vous utilisez l'analyse BAM, vous devez récupérer les alertes BAM dans le cadre de la récupération de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].  
  
## <a name="prerequisites"></a>Conditions préalables  
 Vous devez être connecté en tant que membre de le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] groupe Administrateurs pour effectuer cette procédure.  
  
### <a name="to-recover-bam-alerts-sql-server-2008"></a>Pour récupérer les alertes d’analyse BAM (SQL Server 2008)  
  
1.  Cliquez sur **Démarrer**, cliquez sur **tous les programmes**, cliquez sur **Microsoft SQL Server 2008**, cliquez sur **outils de Configuration**, puis cliquez sur **Invite de commandes des Services de notification**.  
  
2.  À l'invite de commandes, tapez :  
  
     **NSControl register - name BamAlerts-server***\<nom_serveur >***-service - serviceusername «**  *\<ServiceUserName >* **« - servicepassword »**  *\<ServicePassword >* **»**   
  
     Cette commande permet à Notification Services de se connecter à la base de données appropriée (ces informations sont conservées par nscontrol dans le Registre de l'ordinateur du service).  
  
    > [!IMPORTANT]
    >  N’oubliez pas d’utiliser le nouveau serveur de bases de données des Services de Notification dans le **-server** option lors de la réinscription du service. Par ailleurs, vous devez conserver le même nom d'utilisateur pour le nouveau service Notification Services.  
  
3.  Cliquez sur **Démarrer**, puis sur **Exécuter**, tapez **cmd**, puis cliquez sur **OK**.  
  
4.  À l’invite de commandes, tapez : **net start NS$ BamAlerts**.  
  
## <a name="see-also"></a>Voir aussi  
 [Récupération d’un ordinateur exécutant BizTalk Server](../core/recovering-a-computer-running-biztalk-server.md)