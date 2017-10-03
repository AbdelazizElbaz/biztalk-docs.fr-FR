---
title: "Création d’applications associées à des Applications5 | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- applications, affiliate
- Single Sign-On, tickets
- affiliate applications
- creating affiliate applications
- tickets, SSO
- affiliate applications, enabling XML
- SSO tickets
ms.assetid: 191e5b56-dab9-4bf3-9f89-a900907d64e0
caps.latest.revision: "11"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: bc6b42a6f3251d9e897af21fcb4207b6790e91cf
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="creating-affiliate-applications"></a>Création d’Applications associées
Les procédures suivantes décrivent l'utilisation des applications associées et de l'authentification unique (SSO).  
  
> [!NOTE]
>  si vous recevez des erreurs liées à l'authentification unique, vérifiez que vous avez utilisé un compte de domaine lors de la configuration de BizTalk Server. En effet, cela affecte les fonctionnalités du service d'authentification unique de l'entreprise (compatible avec les comptes de domaine uniquement).  
  
### <a name="to-create-an-affiliate-application"></a>Pour créer une application associée  
  
1.  Dans le panneau de configuration, ouvrez **Services**et vérifiez que le service Enterprise Single Sign-On est en cours d’exécution.  
  
2.  Dans une invite de commandes, accédez au dossier Enterprise Single Sign-On.  
  
     Exemple :  
  
     **C:\Program Files\Common Files\Enterprise Single Sign-On >**  
  
3.  Utilisez les commandes du service de l'authentification unique de l'entreprise Pour obtenir la liste de commandes, utilisez la **-aide** basculer.  
  
4.  Pour créer l’application associée à l’aide de *. XML en tant qu’un démarrage, tapez la commande suivante :  
  
     `ssomanage.exe -createapps C:\SSOtest\AffiliateApplication.xml`  
  
     où :  
  
    -   C:\SSOtest est le dossier qui contient le fichier XML de votre application ;  
  
    -   AffiliateApplication.xml est l’application XML que vous avez créé et qui contient les informations d’authentification.  
  
     Exemple :  
  
    ```  
    <?xml version="1.0"?>  
    <SSO>  
        <application name="TIBCO EMS App">  
            <description>TIBCO EMS SSO Application</description>  
            <contact>someone@example.com</contact>  
            <appUserAccount>DomainName\AppUserGroup</appUserAccount>  
            <!—an existing group on the domain controller - >   
            <appAdminAccount>DomainName\AppAdminGroup</appAdminAccount>  
            <!-- an existing account in the domain group - >   
            <field ordinal="0" label="User ID" masked="no" />  
            <field ordinal="1" label="Password" masked="yes" />  
            <flags groupApp="no" allowTickets="yes" enableApp="yes"/>  
        </application>  
    </SSO>  
    ```  
  
 Si l'exemple de fichier XML est utilisé, l'application associée (TIBCO EMS App) contient les valeurs indiquées dans l'invite de commandes.  
  
### <a name="to-create-single-sign-on-tickets"></a>Pour créer des tickets d'authentification unique  
  
1.  Tapez la commande suivante pour contrôler le comportement des tickets d'authentification unique :  
  
     `ssomanage.exe -tickets yes yes`  
  
2.  Répondez aux questions :  
  
     `ssomanage -tickets <allowed yes | no> <validate yes | no>`  
  
     Une fois terminée, vous recevez une confirmation :  
  
     **Utilisation d'un serveur d'authentification unique sur cet ordinateur. L’opération s’est terminée correctement.**  
  
### <a name="to-enable-affiliate-application-xml"></a>Pour activer le fichier XML de l'application associée  
  
1.  Tapez la commande suivante :  
  
     `ssomanage -enableapp TIBCO EMSApp`  
  
2.  Tapez la commande suivante pour afficher la liste des applications et vérifier que l'application a été créée :  
  
     `ssoclient.exe –listapps`  
  
     Les applications associées utilisables apparaissent dans une liste :  
  
     **Applications disponibles pour IBI\YourID - TIBCO EMSApp**  
  
3.  Tapez la commande suivante pour définir des informations d’identification de l’application de la filiale :  
  
     `soclient.exe -setcredentials TIBCO EMSApp`  
  
4.  Lorsque vous y êtes invité, entrez les nom d'utilisateur et mot de passe. Entrez les informations d'identification de l'application associée TIBCO EMS App.  
  
     Par exemple, entrez les ID d'utilisateur et mot de passe suivants pour entrer dans le système via le serveur d'authentification unique.  
  
    -   ID d’utilisateur : **utilisateur**  
  
    -   Mot de passe :`******`  
  
    -   Confirmer ? Mot de passe :`******`  
  
     L’application associée apparaît dans l’adaptateur BizTalk pour TIBCO EMS **propriétés du Transport** boîte de dialogue.  
  
## <a name="see-also"></a>Voir aussi  
 [À l’aide de l’authentification unique](../core/using-single-sign-on4.md)