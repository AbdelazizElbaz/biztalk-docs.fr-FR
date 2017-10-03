---
title: "Comment générer le Secret | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Master Secret server, generating
- managing [Master Secret server], generating
ms.assetid: 5512a8ee-bc5b-4fe4-90c7-41e3baaa723b
caps.latest.revision: "12"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: cfbe186aee99616fa35e8f1e98f67c6ac75593c9
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-generate-the-master-secret"></a>Comment générer le Secret principal
Vous devez disposer de droits d'administrateur sur le serveur de secret principal pour effectuer cette tâche. Par ailleurs, vous devez effectuer cette tâche depuis le serveur de secret principal.  
  
 Le premier serveur sur lequel vous installez l'authentification unique de l'entreprise (SSO) devient le serveur de secret principal.  
  
> [!IMPORTANT]
>  Il ne peut y avoir qu'un serveur de secret principal dans votre système SSO.  
  
> [!NOTE]
>  Lorsque l'authentification unique de l'entreprise est installée en même temps que [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], le secret principal est généré via l'Assistant Configuration. Vous ne devez effectuer cette tâche que si vous souhaitez générer un nouveau secret principal.  
  
### <a name="to-generate-the-master-secret-using-the-mmc-snap-in"></a>Pour générer le secret principal à l'aide du composant logiciel enfichable MMC  
  
1.  Dans le menu **Démarrer** , cliquez sur **Tous les programmes**, **Authentification unique de l'entreprise Microsoft**, puis sur **Administration SSO**.  
  
2.  Dans le volet d'étendue du composant logiciel enfichable MMC ENTSSO, développez le nœud **Authentification unique de l'entreprise** .  
  
3.  Avec le bouton droit **système**, puis cliquez sur **générer le Secret**.  
  
### <a name="to-generate-the-master-secret-using-the-command-line"></a>Pour générer le secret principal à l'aide de la ligne de commande  
  
1.  Sur le **Démarrer** menu, cliquez sur **exécuter**, puis tapez **cmd**.  
  
2.  Dans la ligne de commande, accédez au répertoire d'installation de l'authentification unique de l'entreprise. Le répertoire d’installation par défaut est  *\<lecteur >*: \Program Files\Enterprise Single Sign-On.  
  
3.  Type  **ssoconfig – generateSecret \<* fichier de sauvegarde*>**, où \<* le fichier de sauvegarde*> est le nom du fichier qui contient le secret principal.  
  
     Vous êtes ensuite invité à entrer un mot de passe pour protéger le fichier que vous venez de créer.  
  
    > [!NOTE]
    >  Sur les systèmes qui prennent en charge le contrôle de compte d'utilisateur, vous devrez peut-être exécuter l'outil avec des privilèges d'administrateur.  
  
## <a name="see-also"></a>Voir aussi  
 [Comment sauvegarder le Secret principal](../core/how-to-back-up-the-master-secret.md)   
 [Serveur de secret principal](../core/master-secret-server.md)   
 [Gestion du Secret](../core/managing-the-master-secret.md)