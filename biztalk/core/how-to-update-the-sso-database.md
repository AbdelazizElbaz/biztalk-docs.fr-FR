---
title: "Comment mettre à jour la base de données SSO | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- tickets [SSO], modifying
- managing [SSO], modifying Credential cache timeout
- tickets [SSO], timeouts
- modifying, SSO database
- managing [SSO], modifying ticket timeouts
- SSO database, modifying
ms.assetid: 45eb6a77-d91a-44a8-b26d-05508c288c36
caps.latest.revision: "15"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 1381ee4e5c2b90a96c52b59d125ec3121af02a4e
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-update-the-sso-database"></a>Comment mettre à jour la base de données SSO
Le composant logiciel enfichable MMC et la ligne de commande permettent de modifier les informations globales dans la base de données SSO, telles que l'identification du serveur de secret principal, les noms de compte, l'audit dans la base de données, le délai d'expiration du ticket et le délai d'expiration du cache des informations d'identification.  
  
## <a name="changing-timeouts-for-the-sso-system"></a>Modification des délais d'expiration du système d'authentification unique  
 Vous pouvez modifier deux délais d'expiration au niveau du système d'authentification unique de l'entreprise (SSO) :  
  
 **Délai d’expiration du ticket.** Cette propriété indique la durée de validité d’un ticket émis par le système d’authentification unique. Afin de répondre aux critères de la plupart des entreprises utilisant le système d'authentification unique, le délai d'expiration du ticket est défini sur 2 minutes par défaut. L'administrateur de l'authentification unique peut modifier ce délai selon les conditions requises par l'application.  
  
 **Délai d’expiration du Cache des informations d’identification.** Cette propriété indique le délai d’expiration du cache des informations d’identification pour tous les serveurs d’authentification unique (SSO). Les serveurs d'authentification unique mettent les informations d'identification en cache après la première recherche. Par défaut, le délai d'attente de ce cache est de 60 minutes. L'administrateur de l'authentification unique peut modifier ce délai selon les conditions de sécurité requises.  
  
 Vous devez modifier ces deux délais d'expiration en mettant à jour la base de données SSO.  
  
 Voici un exemple de fichier XML pour la mise à jour de la base de données SSO :  
  
```  
<sso>  
<globalInfo>  
<ssoAdminAccount>Domain\Accountname</ssoAdminAccount>  
<ssoAffiliateAdminAccount>Domain\Accountname</ssoAffiliateAdminAccount>  
<secretServer>ComputerA</secretServer>  
<auditDeletedApps>1000</auditDeletedApps>  
<auditDeletedMappings>1000</auditDeletedMappings>  
<auditCredentialLookups>1000</auditCredentialLookups>  
<ticketTimeout>2</ticketTimeout>  
<credCacheTimeout>60</credCacheTimeout>  
</globalInfo>  
</sso>  
  
```  
  
#### <a name="to-change-timeouts-using-the-mmc-snap-in"></a>Pour modifier les délais d'expiration à l'aide du composant logiciel enfichable MMC  
  
1.  Dans le menu **Démarrer** , cliquez sur **Tous les programmes**, **Authentification unique de l'entreprise Microsoft**, puis sur **Administration SSO**.  
  
2.  Dans le volet d'étendue du composant logiciel enfichable MMC ENTSSO, développez le nœud **Authentification unique de l'entreprise** .  
  
3.  Cliquez avec le bouton droit sur **Système**, puis cliquez sur **Propriétés**.  
  
4.  Dans la boîte de dialogue **Propriétés système** , cliquez sur l'onglet **Général** .  
  
5.  Entrez les paramètres appropriés, puis cliquez sur **OK**.  
  
#### <a name="to-update-the-sso-database-using-the-mmc-snap-in"></a>Pour mettre à jour la base de données SSO à l'aide du composant logiciel enfichable MMC  
  
1.  Dans le menu **Démarrer** , cliquez sur **Tous les programmes**, **Authentification unique de l'entreprise Microsoft**, puis sur **Administration SSO**.  
  
2.  Dans le volet d'étendue du composant logiciel enfichable MMC ENTSSO, développez le nœud **Authentification unique de l'entreprise** .  
  
3.  Cliquez avec le bouton droit sur **Système**, puis cliquez sur **Mettre à niveau la base de données**.  
  
#### <a name="to-update-the-sso-database-using-the-command-line"></a>Pour mettre à jour la base de données SSO à l'aide de la ligne de commande  
  
1.  Cliquez sur **Démarrer**, **Exécuter**, puis entrez **cmd**.  
  
2.  Dans l'invite de ligne de commande, accédez au répertoire d'installation de l'authentification unique de l'entreprise. Le répertoire d’installation par défaut est  *\<lecteur >*: \Program Files\Enterprise Single Sign-On.  
  
3.  Type **ssomanage-updatedb \<mise à jour de fichier >**, où  **\<mise à jour de fichier >** est le chemin d’accès et le nom du fichier.  
  
    > [!NOTE]
    >  Sur les systèmes qui prennent en charge le contrôle de compte d'utilisateur, vous devrez peut-être exécuter l'outil avec des privilèges d'administrateur.  
  
## <a name="see-also"></a>Voir aussi  
 [Comment configurer les Tickets d’authentification unique](../core/how-to-configure-the-sso-tickets.md)   
 [À l’aide de l’authentification unique](../core/using-sso.md)