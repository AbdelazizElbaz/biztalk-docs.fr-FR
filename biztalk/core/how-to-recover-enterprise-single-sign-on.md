---
title: "Comment récupérer Enterprise Single Sign-On | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 845e6ff7-88a8-4ab4-b307-f9275d44600e
caps.latest.revision: "14"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 0fa0c0b5435e235a07046f311a971a0036dc8346
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-recover-enterprise-single-sign-on"></a>Récupération de l'authentification unique de l'entreprise
Avant de restaurer BizTalk Server, vous devez restaurer l'authentification unique de l'entreprise (SSO).  
  
## <a name="prerequisites"></a>Conditions préalables  
  
-   Pour effectuer cette tâche, vous devez ouvrir une session en tant que membre du groupe Administrateurs de l'authentification unique et du groupe Administrateurs.  
  
-   Vous devez disposer du mot de passe utilisé lors de la configuration de l'authentification unique de l'entreprise.  
  
-   Toutes les bases de données sont intactes sur le serveur distant.  
  
-   Le fichier de sauvegarde du secret principal est intact et stocké dans un emplacement sûr.  
  
### <a name="to-recover-enterprise-single-sign-on"></a>Pour restaurer l'authentification unique de l'entreprise  
  
1.  Cliquez sur **Démarrer**, cliquez sur **tous les programmes**, cliquez sur [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], puis cliquez sur **Configuration de BizTalk Server**.  
  
2.  Dans la Configuration de Microsoft BizTalk Server, dans l’arborescence de la console, cliquez sur **Enterprise SSO**.  
  
3.  Dans le volet détails, sélectionnez **activer Enterprise Single Sign-On sur cet ordinateur**, puis cliquez sur **joindre un système SSO existant**.  
  
4.  Dans **banques de données**, entrez le nom du serveur SQL qui héberge la base de données SSO et le nom de la base de données SSO.  
  
5.  Dans **service Windows**, entrez le nom d’utilisateur et un mot de passe pour le compte de service d’authentification unique que vous avez utilisé lors de l’installation et configuration de BizTalk Server.  
  
    > [!NOTE]
    >  Vous pouvez utiliser un autre compte, mais celui-ci doit être membre du groupe Administrateurs de l'authentification unique.  
  
6.  Cliquez sur **Appliquer la configuration**.  
  
     L'avertissement qui s'affiche indique qu'aucun secret principal n'a été récupéré. Vous pouvez utiliser l'Observateur d'événements pour vérifier que le service d'authentification unique de l'entreprise est démarré et exécuté sur l'ordinateur.  
  
7.  Cliquez sur **fichier**, puis cliquez sur **Exit**.  
  
8.  Cliquez sur **Démarrer**, puis sur **Exécuter**, tapez **cmd**, puis cliquez sur **OK**.  
  
9. À l'invite de commandes, tapez :  
  
     **CD programme Files\Common Files\Enterprise Single Sign-On**  
  
10. À l'invite de commandes, tapez :  
  
     **ssoconfig - restoreSecret***\<backupfile >*   
  
     où  *\<backupfile >* est le nom du fichier de secret principal que vous avez sauvegardé.  
  
     Lorsque **ssoconfig** vous demande le mot de passe du fichier de sauvegarde, entrez le mot de passe qui a été spécifié lors de la configuration de l’authentification unique. Si le mot de passe est correct, **ssoconfig** affiche le message suivant :  
  
     **L’opération s’est terminée avec succès**  
  
## <a name="see-also"></a>Voir aussi  
 [Récupération d’un ordinateur exécutant BizTalk Server](../core/recovering-a-computer-running-biztalk-server.md)   
 [Configuration d’Enterprise SSO à l’aide de la Configuration de BizTalk Server](http://msdn.microsoft.com/library/f63d1aec-a8c7-4e76-a67f-19af69e252f0)