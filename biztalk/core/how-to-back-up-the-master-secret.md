---
title: Comment sauvegarder le Secret principal | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- managing [Master Secret server], backing up
- backing up, Master Secret server
- Master Secret server, backing up
ms.assetid: 22c23f66-b7df-4379-8a9f-065406ba8aa8
caps.latest.revision: "14"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: d5bd6cdecda9ca2456a770d4cf885fcd420fc18e
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-back-up-the-master-secret"></a>Comment sauvegarder le Secret principal
Vous pouvez sauvegarder le secret principal du serveur de secret principal dans un système de fichiers NTFS ou sur un média amovible, tel qu'une disquette.  
  
 Pour effectuer cette tâche, vous devez être un administrateur SSO (authentification unique) et un administrateur Windows. Le système SSO vous invitera à entrer un mot de passe. Vous devrez spécifier celui-ci pour restaurer le secret ultérieurement.  
  
> [!CAUTION]
>  Si le serveur de secret principal échoue et que vous perdez la clé, ou si celle-ci est endommagée, vous ne serez plus en mesure de récupérer les données stockées dans la base de données SSO. Vous devez sauvegarder le secret principal, sans quoi vous risquez de perdre les données figurant dans la base de données SSO.  
  
### <a name="to-back-up-the-master-secret-using-the-mmc-snap-in"></a>Pour sauvegarder le secret principal à l'aide du composant logiciel enfichable MMC  
  
1.  Dans le menu **Démarrer** , cliquez sur **Tous les programmes**, **Authentification unique de l'entreprise Microsoft**, puis sur **Administration SSO**.  
  
2.  Dans le volet d'étendue du composant logiciel enfichable MMC ENTSSO, développez le nœud **Authentification unique de l'entreprise** .  
  
3.  Avec le bouton droit **système**, puis cliquez sur **sauvegarde Secret**.  
  
### <a name="to-back-up-the-master-secret-using-the-command-line"></a>Pour sauvegarder le secret principal à l'aide de la ligne de commande  
  
1.  Sur le **Démarrer** menu, cliquez sur **tous les programmes**, puis cliquez sur **Accessoires**. Avec le bouton droit **invite de commandes**, puis cliquez sur **exécuter en tant que...** .  
  
2.  Sélectionnez l’administrateur approprié, puis cliquez sur **OK**.  
  
3.  Dans la ligne de commande, accédez au répertoire d'installation de l'authentification unique de l'entreprise. Le répertoire d’installation par défaut est  *\<lecteur >*: \Program Files\Enterprise Single Sign-On.  
  
4.  Type **ssoconfig – backupSecret  *\<fichier de sauvegarde >***, où  *\<fichier de sauvegarde >* est le chemin d’accès et le nom du fichier où le maître clé secrète est sauvegardé. Par exemple, A:\ssobackup.bak  
  
    > [!NOTE]
    >  Sur les systèmes qui prennent en charge le contrôle de compte d'utilisateur, vous devrez peut-être exécuter l'outil avec des privilèges d'administrateur.  
  
5.  Fournissez un mot de passe pour protéger ce fichier. Vous serez invité à confirmer le mot de passe, ainsi qu'à fournir une indication de mot de passe pour mémoriser celui-ci.  
  
> [!IMPORTANT]
>  Vous devez enregistrer et stocker le fichier de sauvegarde dans un emplacement sécurisé.  
  
## <a name="see-also"></a>Voir aussi  
 [Comment générer le Secret principal](../core/how-to-generate-the-master-secret.md)   
 [Comment restaurer le Secret principal](../core/how-to-restore-the-master-secret.md)   
 [Serveur de secret principal](../core/master-secret-server.md)   
 [Gestion du Secret](../core/managing-the-master-secret.md)