---
title: Comment restaurer le Secret principal | Documents Microsoft
ms.custom: ''
ms.date: 11/30/2017
ms.prod: host-integration-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: b331c9c5-ca90-4a05-b3f6-59db88bf73dc
caps.latest.revision: ''
author: gplarsen
ms.author: hisdocs; plarsen
manager: anneta
ms.openlocfilehash: 5e640f2762ed9f9cc03a7795062c98a6aa76a59d
ms.sourcegitcommit: 8418b1a8f38b7f56979cd6e203f0b591e2f40fe1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/28/2018
---
# <a name="how-to-restore-the-master-secret"></a>Comment restaurer le Secret principal
Dans le cadre des procédures de récupération de données, vous devrez peut-être restaurer le secret pour réutiliser les données existantes. Pour effectuer cette tâche, vous devez vous connecter le serveur de secret principal en utilisant un compte qui est un administrateur Windows et un administrateur Single Sign-On (SSO).  
  
### <a name="to-restore-the-master-secret-using-the-mmc-snap-in"></a>Pour restaurer le secret principal à l'aide du composant logiciel enfichable MMC  
  
1.  Cliquez sur **Démarrer**, pointez sur **programmes**, cliquez sur **Microsoft Enterprise Single Sign-On**, puis cliquez sur **Administration SSO**.  
  
2.  Dans le volet d’étendue du composant logiciel enfichable ENTSSO Microsoft Management Console (MMC), développez le **Enterprise Single Sign-On** nœud.  
  
3.  Avec le bouton droit **système**, puis cliquez sur **restaurer le Secret**.  
  
### <a name="to-restore-the-master-secret-using-the-command-line"></a>Pour restaurer le secret principal à l'aide de la ligne de commande  
  
1.  Sur le **Démarrer** menu, cliquez sur **programmes**, puis cliquez sur **Accessoires**. Avec le bouton droit **invite de commandes**, puis cliquez sur **exécuter en tant que...** .  
  
2.  Sélectionnez l’administrateur approprié, puis cliquez sur **OK**.  
  
3.  À l’invite de commandes, accédez au répertoire d’installation Enterprise Single Sign-On.  
  
     Le répertoire d’installation par défaut est  *\<lecteur >*: \Program Files\Enterprise Single Sign-On.  
  
4.  Type `ssoconfig –restoresecret <restore file>`, où  *\<restaurer le fichier >* est le chemin d’accès et le nom du fichier dans lequel le secret est stocké.  
  
## <a name="see-also"></a>Voir aussi  
 [Comment générer le Secret principal](../esso/how-to-generate-the-master-secret.md)   
 [Comment sauvegarder le Secret principal](../esso/how-to-back-up-the-master-secret.md)   
 [Serveur de secret principal](../esso/master-secret-server.md)   
 [Gestion du secret principal](../esso/managing-the-master-secret.md)