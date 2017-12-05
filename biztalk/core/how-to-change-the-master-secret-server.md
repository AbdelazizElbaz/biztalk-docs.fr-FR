---
title: Comment modifier le serveur de secret principal | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Master Secret server, promoting
- managing [Master Secret server], promoting servers
- managing [SSO], promoting servers
- SSO, Master Secret server
- modifying, Master Secret server
- Master Secret server, changing
ms.assetid: 44a786ca-4645-44a8-b33e-d0019f0aeca9
caps.latest.revision: "14"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 2a1e30f1703f554792ce5243414a95965da93670
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="how-to-change-the-master-secret-server"></a>Comment modifier le serveur de secret principal
Après avoir installé le serveur de secret principal et configuré la base de données SSO, vous pouvez modifier le serveur de secret principal d'origine en cas d'échec sans possibilité de le récupérer. Pour modifier le serveur de secret principal, vous devez promouvoir un serveur SSO au rang de serveur de secret principal.  
  
### <a name="to-change-the-master-secret-server-using-the-mmc-snap-in"></a>Pour modifier le serveur de secret principal à l'aide du composant logiciel enfichable MMC  
  
1.  Dans le menu **Démarrer** , cliquez sur **Tous les programmes**, **Authentification unique de l'entreprise Microsoft**, puis sur **Administration SSO**.  
  
2.  Dans le volet de la portée, avec le bouton droit sur **système**, puis cliquez sur **propriétés**. Le contrôleur de serveur de secret principal s’affiche sur le **général** onglet de la **propriétés système** boîte de dialogue.  
  
3.  Cliquez sur **modification** pour sélectionner un nouveau serveur de secret principal.  
  
    > [!IMPORTANT]
    >  Lorsque vous utilisez le composant logiciel enfichable MMC pour modifier le serveur de secret principal, l'opération doit être effectuée sur le serveur de secret principal. Il n'est pas possible de modifier le serveur de secret principal à l'aide du composant logiciel enfichable MMC à partir d'un ordinateur qui n'est pas le serveur de secret principal.  
  
4.  Connectez-vous au nouveau serveur de secret principal pour restaurer le secret principal dans le Registre du nouveau serveur de secret principal.  
  
5.  Sur le **Démarrer** menu, cliquez sur **exécuter**, puis tapez **cmd**.  
  
6.  Dans l'invite de ligne de commande, accédez au répertoire d'installation de l'authentification unique de l'entreprise. Le répertoire d’installation par défaut est  *\<lecteur\>*: \Program Files\Enterprise Single Sign-On.  
  
7.  Redémarrez le nouveau serveur de secret principal.  
  
8.  Type **ssoconfig – restoreSecret \<restaurer le fichier\>**, où  **\<restaurer le fichier\>**  est le chemin d’accès et le nom du fichier où le secret principal stockées.  
  
     Le serveur principal est stocké dans le Registre à l'emplacement suivant :  
  
     HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\ENTSSO\SSOSS  
  
    > [!NOTE]
    >  Sur les systèmes qui prennent en charge le contrôle de compte d'utilisateur, vous devrez peut-être exécuter l'outil avec des privilèges d'administrateur.  
  
### <a name="to-promote-a-single-sign-on-server-to-master-secret-server-using-the-command-line"></a>Pour promouvoir un serveur de l'authentification unique au rang de serveur de secret principal à l'aide de la ligne de commande  
  
1.  Créez un fichier XML contenant le nom du serveur SSO à promouvoir au rang de serveur de secret principal. Par exemple :  
  
    ```  
    <sso>  
      <globalInfo>  
         <secretServer>SSO Server name</secretServer>  
      </globalInfo>  
    </sso>  
    ```  
  
    > [!IMPORTANT]
    >  Pour modifier le serveur de secret principal à partir d'un ordinateur qui n'est pas le serveur de secret principal, assurez-vous que le fichier XML spécifié contient uniquement le nom du serveur de secret principal. Plus précisément, il ne doit pas contenir la balise XML administrateurs SSO ou **ssomanage - updatedb** échoue.  
  
2.  Sur le **Démarrer** menu, cliquez sur **exécuter**, puis tapez **cmd**.  
  
3.  Dans l'invite de ligne de commande, accédez au répertoire d'installation de l'authentification unique de l'entreprise. Le répertoire d’installation par défaut est  *\<lecteur\>*: \Program Files\Enterprise Single Sign-On.  
  
4.  Type **ssomanage-updatedb** \< **fichier de mise à jour**\>, où \< **fichier de mise à jour** \> est le nom du fichier XML vous créez à l’étape 1.  
  
    > [!NOTE]
    >  Sur les systèmes qui prennent en charge le contrôle de compte d'utilisateur, vous devrez peut-être exécuter l'outil avec des privilèges d'administrateur.  
  
5.  Redémarrez le serveur de secret principal.  
  
6.  Type **ssoconfig – restoresecret \<restaurer le fichier\>**, où  **\<restaurer le fichier\>**  est le chemin d’accès et le nom du fichier où le secret principal stockées.  
  
     Le serveur principal est stocké dans le Registre à l'emplacement suivant :  
  
     HKEY_LOCAL_MACHINESOFTWAREMicrosoftENTSSOSSOSS  
  
    > [!NOTE]
    >  Sur les systèmes qui prennent en charge le contrôle de compte d'utilisateur, vous devrez peut-être exécuter l'outil avec des privilèges d'administrateur.  
  
## <a name="see-also"></a>Voir aussi  
 [Serveur de secret principal](../core/master-secret-server.md)   
 [Mise en Cluster du serveur de secret principal](../core/how-to-cluster-the-master-secret-server1.md)   
 [Comment mettre à jour la base de données SSO](../core/how-to-update-the-sso-database.md)   
 [Utilisation de l’authentification unique](../core/using-sso.md)