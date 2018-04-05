---
title: Comment se connecter à un groupe existant | Documents Microsoft
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- bts10.admin.procedure.connecttogroup
helpviewer_keywords:
- groups, existing
- groups, connecting
- managing [groups], connecting
ms.assetid: 1eedbcd5-f3f1-4da5-b91c-67377131f889
caps.latest.revision: 24
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 942093faa4a556f31d090de97b3feff4eb7a9a45
ms.sourcegitcommit: 3fc338e52d5dbca2c3ea1685a2faafc7582fe23a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/01/2017
---
# <a name="how-to-connect-to-an-existing-group"></a>Connexion à un groupe existant
Vous pouvez utiliser la [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] console d’Administration sur n’importe quel ordinateur dans votre entreprise pour gérer à distance un ou plusieurs groupes BizTalk Server au sein de votre entreprise, tant que ces groupes se trouvent sur des ordinateurs au sein du même domaine ou dans des domaines approuvés.  
  
 Le nœud Administration de BizTalk Server dans la console Administration de BizTalk Server est le nœud de niveau supérieur pour tous les groupes BizTalk et le niveau que vous utilisez lors de l’ajout d’un groupe BizTalk Server existant dans la console Administration de BizTalk Server. Lorsque vous ajoutez un groupe, vous devez spécifier un serveur et une base de données de gestion BizTalk existants auxquels vous connecter.  
  
## <a name="prerequisites"></a>Conditions préalables  
 Pour exécuter cette procédure, vous devez avoir ouvert une session en tant que membre du groupe des opérateurs de BizTalk Server ou du groupe d'administrateurs de BizTalk Server.  
  
### <a name="to-connect-to-an-existing-group"></a>Pour se connecter à un groupe existant  
  
1.  Cliquez sur **Démarrer**, cliquez sur **tous les programmes**, cliquez sur [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], puis cliquez sur **Administration de BizTalk Server**.  
  
2.  Dans l’arborescence de la console, cliquez sur **Administration de BizTalk Server**, puis cliquez sur **se connecter au groupe existant**.  
  
3.  Dans le **se connecter à la base de Configuration BizTalk existante** boîte de dialogue le **nom SQL Server** liste déroulante, sélectionnez le nom de l’instance de Microsoft SQL Server qui héberge la BizTalk Base de données de gestion (également appelée la base de données de Configuration). Lorsque vous sélectionnez l'instance de SQL Server, BizTalk Server tente automatiquement de détecter les bases de données BizTalk Server sur l'ordinateur.  
  
4.  Dans le **nom de la base de données** liste déroulante, sélectionnez la base de données de gestion BizTalk Server (**BizTalkMgmtDb**) à laquelle vous souhaitez vous connecter, puis cliquez sur **OK**.  
  
     La console Administration de BizTalk Server ajoute le groupe BizTalk Server à l’arborescence de la console.  
  
    > [!NOTE]
    >  Si la base de données de gestion BizTalk Server est hébergée sur un cluster SQL Server et si ce cluster est en train de basculer, il se peut qu'une erreur similaire à l'erreur suivante se produise lorsque vous tentez de vous connecter à la base de données de gestion :  
    >   
    >  Échec du chargement du groupe [\<nom_serveur\>:\<base de données de gestion\>] fournisseurs de données.  
    >   
    >  And  
    >   
    >  INFORMATIONS SUPPLÉMENTAIRES :  
    >   
    >  Impossible de trouver l'instance de la classe WMI. (WinMgmt)  
    >   
    >  Cette erreur peut être due au fait que les bases de données BizTalk ne sont pas disponibles au moment où elles font l'objet d'un basculement. Pour contourner ce problème, patientez jusqu'à ce que l’instance en cluster de SQL Server est en ligne avant d’essayer de vous y connecter avec la console Administration de BizTalk Server.  
  
## <a name="see-also"></a>Voir aussi  
 [Gestion des groupes](../core/managing-groups.md)   
 [Groupes BizTalk](../core/biztalk-groups.md)