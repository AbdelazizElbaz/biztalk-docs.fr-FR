---
title: Comment sauvegarder le Secret principal | Documents Microsoft
ms.custom: ''
ms.date: 11/30/2017
ms.prod: host-integration-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 0841c52a-7b15-45f8-9900-f5c9e3abd90b
caps.latest.revision: ''
author: gplarsen
ms.author: hisdocs; plarsen
manager: anneta
ms.openlocfilehash: 124c077d7a15a4938f94239518ad02c8268074a4
ms.sourcegitcommit: 8418b1a8f38b7f56979cd6e203f0b591e2f40fe1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/28/2018
---
# <a name="how-to-back-up-the-master-secret"></a>Comment sauvegarder le Secret principal
Vous pouvez sauvegarder le secret principal du serveur de secret principal dans un système de fichiers NTFS ou sur un média amovible, tel qu'une disquette.  
  
 Vous devez être un administrateur de l’authentification unique et un administrateur Windows pour effectuer cette tâche. Le système Single Sign-On (SSO) vous demandera un mot de passe. Vous devrez spécifier celui-ci pour restaurer le secret ultérieurement.  
  
> [!CAUTION]
>  Si le serveur de secret principal tombe en panne et vous perdez la clé, ou si la clé est endommagée, vous ne serez pas en mesure de récupérer les données stockées dans la base de données d’informations d’identification. Vous devez sauvegarder le secret principal, ou vous risquez de perdre des données à partir de la base de données d’informations d’identification.  
  
### <a name="to-back-up-the-master-secret-using-the-mmc-snap-in"></a>Pour sauvegarder le secret principal à l'aide du composant logiciel enfichable MMC  
  
1.  Cliquez sur **Démarrer**, pointez sur **programmes**, cliquez sur **Microsoft Enterprise Single Sign-On**, puis cliquez sur **Administration SSO**.  
  
2.  Dans le volet d’étendue du composant logiciel enfichable ENTSSO Microsoft Management Console (MMC), développez le **Enterprise Single Sign-On** nœud.  
  
3.  Avec le bouton droit **système**, puis cliquez sur **sauvegarder le Secret principal**.  
  
### <a name="to-back-up-the-master-secret-using-the-command-line"></a>Pour sauvegarder le secret principal à l'aide de la ligne de commande  
  
1.  Sur le **Démarrer** menu, cliquez sur **programmes**, puis cliquez sur **Accessoires**. Avec le bouton droit **invite de commandes**, puis cliquez sur **exécuter en tant que...** .  
  
2.  Sélectionnez l’administrateur approprié, puis cliquez sur **OK**.  
  
3.  À l’invite de commandes, accédez au répertoire d’installation Enterprise Single Sign-On.  
  
     Le répertoire d’installation par défaut est  *\<lecteur >*: \Program Files\Enterprise Single Sign-On.  
  
4.  Type `ssoconfig –backupsecret <backup file>`, où  *\<fichier de sauvegarde >* est le chemin d’accès et le nom du fichier où le secret principal sera sauvegardé, par exemple, `A:\ssobackup.bak`.  
  
5.  Fournir un mot de passe pour protéger ce fichier.  
  
     Vous serez invité à confirmer le mot de passe, ainsi qu'à fournir une indication de mot de passe pour mémoriser celui-ci.  
  
> [!IMPORTANT]
>  Vous devez enregistrer et stocker le fichier de sauvegarde dans un emplacement sécurisé.  
  
## <a name="see-also"></a>Voir aussi  
 [Comment générer le Secret principal](../esso/how-to-generate-the-master-secret.md)   
 [Comment restaurer le Secret principal](../esso/how-to-restore-the-master-secret.md)   
 [Serveur de secret principal](../esso/master-secret-server.md)   
 [Gestion du secret principal](../esso/managing-the-master-secret.md)