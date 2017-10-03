---
title: "Étape 5 : Configurer les Pages Web du partenaire commercial | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 38c3054d-932a-42b6-a821-8b30604d8426
caps.latest.revision: "38"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 25be80ea28231ebf5e7b79ca9c087461dc8efb4c
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="step-5-configure-the-trading-partner-web-pages"></a>Étape 5 : Configurer les Pages Web du partenaire commercial
![L’étape 5 de 11](../core/media/tut-step5-of-11.gif "Tut_Step5_of_11")  
  
 Au cours de cette étape, vous allez effectuer les tâches suivantes pour configurer les pages Web d'un partenaire commercial :  
  
-   Activer le filtre ISAPI de réception HTTP BTS requis pour le transport HTTP.  
  
-   Configurer un dossier et une page aspx pour acheminer l'accusé de réception 997 vers l'organisation partenaire Fabrikam via le transport HTTP. Le répertoire virtuel Fabrikam dépose l’accusé de réception 997 dans le \\dossier _997ToFabrikam, qui est appelé dans le paramètre Destination_URL du port de 997 envoi.  
  
-   Configurer la page ASPX pour acheminer le message original vers l'organisation d'origine Contoso. Le répertoire virtuel Contoso utilise BTSHttpReceive.dll pour recevoir le message AS2 et l'envoyer à l'emplacement de réception.  
  
> [!NOTE]
>  Les procédures incluses dans cette rubrique s'appliquent à IIS 7.0.  
  
## <a name="prerequisites"></a>Conditions préalables  
 Vous devez ouvrir une session en tant que membre du groupe Administrateurs [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].  
  
### <a name="to-enable-the-bts-isapi-filter"></a>Pour activer le filtre ISAPI BTS  
  
1.  Cliquez sur **Démarrer**, pointez sur **Tous les programmes**, puis sur **Outils d'administration**, puis cliquez sur **Gestionnaire des services Internet (IIS)**.  
  
2.  Sélectionnez l’entrée de serveur Web racine et dans le **affichage des fonctionnalités**, double-cliquez sur **mappages de gestionnaires** puis, dans le **Actions** volet, cliquez sur **ajouter un mappage de scripts**.  
  
    > [!NOTE]
    >  La configuration du mappage de scripts au niveau du serveur Web entraîne l'application de ce mappage à tous les sites Web enfants. Si vous souhaitez limiter le mappage à un site Web ou un dossier virtuel spécifique, sélectionnez le site ou le dossier cible plutôt que le serveur Web.  
  
3.  Dans le **ajouter un mappage de scripts** boîte de dialogue, entrez `BtsHttpReceive.dll` dans les **chemin d’accès de la demande** champ.  
  
4.  Dans le **exécutable** , cliquez sur le **points de suspension (...)**  bouton et accédez à [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]HttpReceive. Sélectionnez **BtsHttpReceive.dll**, puis cliquez sur **OK**.  
  
5.  Entrez `BizTalk HTTP Receive` dans les `Name` champ, puis cliquez sur **Restrictions des demandes**.  
  
6.  Dans le **Restrictions des demandes** boîte de dialogue, sélectionnez le **verbes** onglet, puis sélectionnez **un des verbes suivants**. Entrez `POST` le verbe.  
  
7.  Sur le **accès** onglet, sélectionnez **Script**, puis cliquez sur **OK**.  
  
8.  Cliquez sur **OK** lorsque vous êtes invité à autoriser l’extension ISAPI, cliquez sur **Oui**.  
  
9. Cliquez sur l’entrée BTSHttpReceive.dll, puis sélectionnez **modifier les autorisations de fonction**.  
  
10. Vérifiez que **en lecture**, **Script** et **Execute** sont sélectionnées, puis cliquez sur **OK**.  
  
11. Cliquez sur **affichage des fonctionnalités**, puis double-cliquez sur **Restrictions ISAPI et CGI**.  
  
12. Assurez-vous qu’il existe une entrée pour BTSHTTPReceive.dll et qui **Restriction** a la valeur **autorisées**.  
  
    > [!NOTE]
    >  L'entrée Restrictions ISAPI et CGI pour BTSHTTPReceive.dll est définie automatiquement lors de la création du mappage de scripts.  
  
### <a name="to-configure-the-fabrikam-web-page"></a>Pour configurer la page Web Fabrikam  
  
1.  Avec le bouton droit dans le Gestionnaire des services Internet, **Pools d’applications** et sélectionnez **ajouter un Pool d’applications**.  
  
2.  Dans le **ajouter un Pool d’applications** boîte de dialogue, entrez **BizTalkAppPool** dans **nom**, puis sélectionnez **.NET Framework V4.0.30210** dans le **Version du .NET framework** liste déroulante. Cliquez sur **OK**.  
  
    > [!NOTE]
    >  Le numéro de version peut varier selon la version de [!INCLUDE[netfx40_short](../includes/netfx40-short-md.md)] installée sur l'ordinateur.  
  
3.  Sélectionnez **Pools d’applications**, dans le **affichage des fonctionnalités** sélectionnez **BizTalkAppPool**, puis cliquez sur **paramètres avancés** dans les  **Actions** volet.  
  
4.  Dans le **paramètres avancés** boîte de dialogue, définissez **Applications Enable 32 bits** à **True**.  
  
    > [!NOTE]
    >  Cette étape est uniquement requise sur un ordinateur 64 bits si vous souhaitez exécuter IIS en mode 32 bits.  
  
5.  Sélectionnez **identité** puis cliquez sur le **points de suspension (...)**  bouton.  
  
6.  Dans le **identité du Pool d’applications** boîte de dialogue, sélectionnez **compte personnalisé** puis cliquez sur **définir**.  
  
7.  Entrez le **nom d’utilisateur** et **mot de passe** pour un compte d’utilisateur qui est membre du groupe Administrateurs, entrez le mot de passe **confirmer le mot de passe** puis cliquez sur **OK** trois fois pour retourner le Gestionnaire des services Internet.  
  
8.  Dans le Gestionnaire des services Internet, ouvrez le **Sites** dossier. Cliquez sur le **Site Web par défaut**, puis sélectionnez **ajouter une Application**.  
  
9. Dans le **ajouter une Application** boîte de dialogue, entrez **Fabrikam** dans **Alias**, puis cliquez sur **sélectionnez**.  
  
10. Dans le **sélectionner un Pool d’applications** boîte de dialogue, sélectionnez **BizTalkAppPool** et cliquez sur **OK**.  
  
11. Cliquez sur le **points de suspension (...)**  bouton et accédez à [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]SDK\AS2 Tutorial\Fabrikam pour le **chemin d’accès physique**.  
  
12. Cliquez sur **des paramètres de Test** et vérifiez qu’il n’y a aucune erreur affiché dans le **tester la connexion** boîte de dialogue. Cliquez sur **Fermer**, puis sur **OK**.  
  
13. Dans le Gestionnaire des services Internet, sélectionnez le répertoire virtuel Fabrikam et dans **affichage des fonctionnalités**, double-cliquez sur **authentification**.  
  
14. Dans **authentification**, sélectionnez **l’authentification anonyme** et vérifiez que le **état** est **activé**. Si le **état** est **désactivé**, cliquez sur **activer** dans les **Actions** volet.  
  
### <a name="to-configure-the-contoso-web-page"></a>Pour configurer la page Web Contoso  
  
1.  Dans le Gestionnaire des services Internet, ouvrez le **Sites** dossier. Cliquez sur le **Site Web par défaut** , puis sélectionnez **ajouter une Application**.  
  
2.  Dans le **ajouter une Application** boîte de dialogue, entrez **Contoso** dans **Alias**, puis cliquez sur **sélectionnez**.  
  
3.  Dans le **sélectionner un Pool d’applications** boîte de dialogue, sélectionnez **BizTalkAppPool** et cliquez sur **OK**.  
  
    > [!NOTE]
    >  Le pool d'applications BizTalkAppPool, créé précédemment lors de la configuration de la page Web Fabrikam, doit être défini sur l'identité d'un utilisateur membre du groupe Administrateurs.  
  
4.  Cliquez sur le **points de suspension (...)**  bouton et accédez à [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]HttpReceive pour le **chemin d’accès physique**.  
  
5.  Cliquez sur **des paramètres de Test** et vérifiez qu’il n’y a aucune erreur affiché dans le **tester la connexion** boîte de dialogue. Cliquez sur **Fermer**, puis sur **OK**.  
  
6.  Dans le Gestionnaire des services Internet, sélectionnez le répertoire virtuel Contoso et dans le **affichage des fonctionnalités**, double-cliquez sur **authentification**.  
  
7.  Dans **authentification**, sélectionnez **l’authentification anonyme** et vérifiez que le **état** est **activé**. Si le **état** est **désactivé**, cliquez sur **activer** dans les **Actions** volet.  
  
## <a name="next-steps"></a>Étapes suivantes  
 Vous configurez l’emplacement de réception (**Receive_AS2**) pour recevoir le message AS2 de Fabrikam, comme décrit dans [étape 6 : configurer l’emplacement de réception EDI AS2](../core/step-6-configure-the-edi-as2-receive-location.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Didacticiel 3 : Didacticiel AS2](../core/tutorial-3-as2-tutorial.md)