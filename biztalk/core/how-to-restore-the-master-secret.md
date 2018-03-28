---
title: Comment restaurer le Secret principal | Documents Microsoft
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- managing [Master Secret server], restoring
- Master Secret server, restoring
- restoring, Master Secret server
ms.assetid: 68e133c5-4591-4d76-9a3b-c9564ff1aa60
caps.latest.revision: ''
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 9241c8d9c5f6e41f47199211d0215c16526951d6
ms.sourcegitcommit: 8418b1a8f38b7f56979cd6e203f0b591e2f40fe1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/28/2018
---
# <a name="how-to-restore-the-master-secret"></a>Comment restaurer le Secret principal
Dans le cadre des procédures de récupération des données, vous devrez peut-être restaurer le secret principal afin de réutiliser les données existantes. À cette fin, vous devez ouvrir une session sur le serveur de secret principal à l'aide d'un compte à la fois Administrateur Windows et Administrateur SSO.  
  
### <a name="to-restore-the-master-secret-using-the-mmc-snap-in"></a>Pour restaurer le secret principal à l'aide du composant logiciel enfichable MMC  
  
1.  Dans le menu **Démarrer** , cliquez sur **Tous les programmes**, **Authentification unique de l'entreprise Microsoft**, puis sur **Administration SSO**.  
  
2.  Dans le volet d'étendue du composant logiciel enfichable MMC ENTSSO, développez le nœud **Authentification unique de l'entreprise** .  
  
3.  Avec le bouton droit **système**, puis cliquez sur **restaurer le Secret**.  
  
### <a name="to-restore-the-master-secret-using-the-command-line"></a>Pour restaurer le secret principal à l'aide de la ligne de commande  
  
1.  Sur le **Démarrer** menu, cliquez sur **tous les programmes**, puis cliquez sur **Accessoires**. Avec le bouton droit **invite de commandes**, puis cliquez sur **exécuter en tant que...** .  
  
2.  Sélectionnez l’administrateur approprié, puis cliquez sur **OK**.  
  
3.  Dans la ligne de commande, accédez au répertoire d'installation de l'authentification unique de l'entreprise. Le répertoire d’installation par défaut est  *\<lecteur\>*: \Program Files\Enterprise Single Sign-On.  
  
4.  Type **ssoconfig – restoreSecret \<restaurer le fichier\>**, où **\<restaurer le fichier\>** est le chemin d’accès et le nom du fichier où le secret principal stockées.  
  
    > [!NOTE]
    >  Sur les systèmes qui prennent en charge le contrôle de compte d'utilisateur, vous devrez peut-être exécuter l'outil avec des privilèges d'administrateur.  
  
## <a name="see-also"></a>Voir aussi  
 [Comment générer le Secret principal](../core/how-to-generate-the-master-secret.md)   
 [Comment sauvegarder le Secret principal](../core/how-to-back-up-the-master-secret.md)   
 [Serveur de secret principal](../core/master-secret-server.md)   
 [Gestion du secret principal](../core/managing-the-master-secret.md)