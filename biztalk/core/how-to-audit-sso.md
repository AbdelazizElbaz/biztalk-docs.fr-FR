---
title: "Comment auditer l’authentification unique | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- managing [SSO], auditing
- SSO, auditing
- auditing [SSO]
- SSO database, auditing
ms.assetid: dc6d0726-fc31-4af2-9a23-8df9e3fc5836
caps.latest.revision: "13"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 27528cf6da53c69db4b2bc6c9e1d296472b24186
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="how-to-audit-sso"></a>Comment auditer l’authentification unique
Le composant logiciel enfichable MMC ou la ligne de commande permet de définir les niveaux d'audit positif et négatif. Les résultats de l'audit sont stockés dans les journaux des événements et des audits de la base de données.  
  
 Les administrateurs SSO peuvent définir les niveaux d'audit positifs et négatifs selon leurs stratégies d'entreprise. Vous pouvez définir des audits positifs et négatifs sur l'un des niveaux suivants :  
  
 0 = Aucun  
  
 1 = Faible  
  
 2 = Moyen  
  
 3 = Élevé. Ce niveau émet plusieurs messages d’audit que possible.  
  
 La valeur par défaut pour l’audit positif est 0 (aucun), et la valeur par défaut pour l’audit négatif est 1(low).  
  
 Pour modifier le niveau d'audit de la base de données, vous devez mettre à jour la base de données SSO à l'aide d'un fichier XML. Voici un exemple de fichier XML pour la mise à jour de la base de données SSO :  
  
```  
<sso>  
<globalnfo>  
<auditDeletedApps>1000</auditDeletedApps>  
<auditDeletedMappings>1000</auditDeletedMappings>  
<auditCredentialLookups>1000</auditCredentialLookups>  
</globalInfo>  
</sso>  
  
```  
  
### <a name="to-audit-single-sign-on-using-the-mmc-snap-in"></a>Pour activer l'audit de l'authentification unique de l'entreprise à l'aide du composant logiciel enfichable MMC  
  
1.  Dans le menu **Démarrer** , cliquez sur **Tous les programmes**, **Authentification unique de l'entreprise Microsoft**, puis sur **Administration SSO**.  
  
2.  Dans le volet d'étendue du composant logiciel enfichable MMC ENTSSO, développez le nœud **Authentification unique de l'entreprise** .  
  
3.  Cliquez avec le bouton droit sur **Système**, puis cliquez sur **Propriétés**.  
  
4.  Sur le **propriétés système** boîte de dialogue, cliquez sur le **Audits** onglet.  
  
5.  Entrez les paramètres appropriés, puis cliquez sur **OK**.  
  
### <a name="to-audit-single-sign-on-using-the-command-line"></a>Pour activer l'audit de l'authentification unique de l'entreprise à l'aide de la ligne de commande  
  
1.  Sur le **Démarrer** menu, cliquez sur **exécuter**, puis tapez **cmd**.  
  
2.  Dans l'invite de ligne de commande, accédez au répertoire d'installation de l'authentification unique de l'entreprise. Le répertoire d’installation par défaut est  **\<lecteur\>**: \Program Files\Enterprise Single Sign-On.  
  
3.  Type **ssoconfig-auditlevel \<positif\>\<négatif\>**, où  **\<positif\>**  est le niveau de l’audit lorsque actions réussissent, et  **\<négatif\>**  est le niveau de cas d’échouent des actions d’audit.  
  
    > [!NOTE]
    >  Sur les systèmes qui prennent en charge le contrôle de compte d'utilisateur, vous devrez peut-être exécuter l'outil avec des privilèges d'administrateur.  
  
### <a name="to-audit-the-sso-database"></a>Pour activer l'audit de la base de données SSO  
  
1.  Cliquez sur **Démarrer**, **Exécuter**, puis entrez **cmd**.  
  
2.  Dans l'invite de ligne de commande, accédez au répertoire d'installation de l'authentification unique de l'entreprise. Le répertoire d’installation par défaut est  **\<lecteur\>**: \Program Files\Enterprise Single Sign-On.  
  
3.  Type **ssomanage-updatedb \<fichier de mise à jour\>**, où  **\<fichier de mise à jour\>**est le chemin d’accès et le nom du fichier.  
  
    > [!NOTE]
    >  Sur les systèmes qui prennent en charge le contrôle de compte d'utilisateur, vous devrez peut-être exécuter l'outil avec des privilèges d'administrateur.  
  
## <a name="see-also"></a>Voir aussi  
 [Comment mettre à jour la base de données SSO](../core/how-to-update-the-sso-database.md)   
 [Utilisation de l’authentification unique](../core/using-sso.md)