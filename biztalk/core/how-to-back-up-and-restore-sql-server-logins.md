---
title: Comment sauvegarder et restaurer les connexions SQL Server | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 847c3a3d-0d97-415b-893e-4ba173085bae
caps.latest.revision: "5"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 54fa6a51a27f82add8a96c613e36f5ed7ce88e87
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-back-up-and-restore-sql-server-logins"></a>Sauvegarde et restauration des comptes de connexion SQL Server
Sauvegarder et restaurer les connexions SQL Server associés à BizTalk Server.  
  
## <a name="biztalk-server-sql-server-security-logins"></a>Comptes de connexion de sécurité SQL Server de BizTalk Server  
 Les comptes de connexion de sécurité SQL Server répertoriés ci-dessous sont associés à BizTalk Server. D'autres comptes de connexion peuvent être associés aux applications BizTalk Server que vous avez créées. Vous devez sauvegarder les comptes de connexion et les restaurer lors du déplacement des bases de données BizTalk Server vers un nouveau serveur ou une nouvelle instance de SQL Server.  
  
-   Utilisateurs d'applications BizTalk  
  
-   Utilisateurs d'hôtes BizTalk isolés  
  
-   Administrateurs BizTalk Server  
  
-   Opérateurs BizTalk Server  
  
-   Administrateurs SSO  

## <a name="prerequisites"></a>Conditions préalables  
Vous devez être un membre de la **administrateurs** rôle de sécurité sur le serveur SQL où vous sauvegardez et restaurez les connexions.  
  
## <a name="back-up-a-login-using-a-script"></a>Sauvegarder un compte de connexion à l’aide d’un script  
  
1.  Ouvrez **SQL Server Management Studio**.  
  
2.  Développez **sécurité**, développez la liste des **connexions**.  
  
3.  Avec le bouton droit de la connexion que vous souhaitez créer un script de sauvegarde, puis **Script de la connexion en tant que**.  
  
4.  Sélectionnez **CREATE To**, puis sélectionnez une des **nouvelle fenêtre d’éditeur de requête**, **fichier**, ou **Presse-papiers** pour sélectionner une destination pour le script. En règle générale, la destination est un fichier avec un **.sql** extension.  
  
5.  Répétez cette procédure depuis l'étape 3 pour chaque compte de connexion pour lequel créer un script. Consultez la liste des comptes de connexion liés à BizTalk Server pour identifier ceux pour lesquels créer un script.  
  
## <a name="restore-a-login-from-a-script"></a>Restaurer un compte de connexion à partir d’un script  
  
1.  Ouvrez **SQL Server Management Studio**.  
  
2.  Sur le **fichier** menu, **ouvrir** le fichier qui contient la connexion sous forme de script.  
  
3.  Exécutez le script pour créer le compte de connexion.