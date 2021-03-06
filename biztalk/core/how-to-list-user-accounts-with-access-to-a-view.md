---
title: "Utilisateur de la liste des comptes ayant accès à une vue | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- user accounts, BAM
- managing [BAM], user accounts
- Get-Accounts utility [BAM]
ms.assetid: 690fb45a-6de0-489e-9ddd-e88e29413c16
caps.latest.revision: "20"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: c80a01aa9b4bd19581cb97f7fee127fc244322d4
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="how-to-list-user-accounts-with-access-to-a-view"></a>Affichage des comptes d'utilisateur ayant accès à une vue
Les administrateurs utilisent la **get-accounts** commande d’utilitaire de gestion BAM pour obtenir une liste de tous les comptes d’utilisateur pour un rôle de la vue, ce qui signifie que tous les comptes d’utilisateurs ayant accès à la vue spécifiée.  
  
 Pour plus d’informations sur l’affichage des vues BAM, consultez [comment répertorier les vues BAM](../core/how-to-list-bam-views.md).  
  
### <a name="to-list-user-accounts-with-access-to-a-view"></a>Pour afficher les comptes d'utilisateur ayant accès à une vue  
  
1.  Ouvrez une invite de commandes comme suit : cliquez sur **Démarrer**, cliquez sur **exécuter**, type **cmd**, puis cliquez sur **OK**.  
  
2.  Accédez à [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]de suivi  
  
3.  Type **bm get-accounts-View :\<nom de la vue\>**.  
  
    > [!NOTE]
    >  Sur les systèmes qui prennent en charge le contrôle de compte d'utilisateur, vous devrez peut-être exécuter l'outil avec des privilèges d'administrateur.  
  
4.  Appuyez sur **Entrée**.  
  
## <a name="see-also"></a>Voir aussi  
 [Gestion de l’Infrastructure dynamique BAM](../core/managing-the-bam-dynamic-infrastructure.md)   
 [Utilitaire de gestion de l’analyse BAM](../core/bam-management-utility.md)