---
title: Création d’applications associées à des Applications4 | Documents Microsoft
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- tickets, Single Sign-On
- affiliate applications, setting credentials
- affiliate applications
- Single Sign-On, creating tickets
- SSO tickets
ms.assetid: 790fbe21-8081-4d57-803f-23014c8a3135
caps.latest.revision: ''
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 87aa9be716e437e80c0e85bd9e462713e48090ad
ms.sourcegitcommit: 8418b1a8f38b7f56979cd6e203f0b591e2f40fe1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/28/2018
---
# <a name="creating-affiliate-applications"></a>Création d’Applications associées
Les étapes suivantes décrivent la mise en route des applications associées à l'aide de l'authentification unique (SSO).  
  
> [!NOTE]
>  Si vous obtenez des erreurs de l’authentification unique, vérifiez que vous avez utilisé un compte de domaine lors de la configuration de BizTalk Server, comme cela affecte les fonctionnalités du service SSO de l’entreprise. (SSO n'est compatible qu'avec les comptes de domaine).  
  
### <a name="to-create-an-affiliate-application"></a>Pour créer une application associée  
  
1.  Dans le panneau de configuration, ouvrez **Services**et vérifiez que le service Enterprise Single Sign-On est en cours d’exécution.  
  
2.  Ouvrez une invite de commandes, puis accédez au dossier de l'authentification unique de l'entreprise.  
  
     Par exemple :  
  
     **C:\Program Files\Common Files\Enterprise Single Sign-On>**  
  
3.  Utilisez les commandes du service de l'authentification unique de l'entreprise Pour obtenir la liste de commandes, utilisez la **-aide** basculer.  
  
4.  Pour créer l'application associée à l'aide d'un fichier .XML, tapez la commande suivante :  
  
     `ssomanage.exe -createapps C:\SSOtest\AffiliateApplication.xml`  
  
     où :  
  
    -   C:\SSOtest est le dossier qui contient le fichier XML de votre application ;  
  
    -   AffiliateApplication.xml est l’application XML que vous avez créé et qui contient les informations d’authentification.  
  
     Par exemple :  
  
    ```  
    <?xml version="1.0"?>  
    <SSO>  
        <application name="JDEdwardsApp">  
            <description>JDEdwards SSO Application</description>  
            <contact>someone@microsoft.com</contact>  
            <userGroup>ibi\Domain Users</userGroup>  
            <!—an existing group on the domain controller - >   
            <appAdminGroup>ibi\YourID</appAdminGroup>  
            <!-- an existing account within the domain group - >   
  
            <field ordinal="0" label="User ID" masked="no" />  
            <field ordinal="1" label="Password" masked="yes" />  
            <flags groupApp="no" allowTickets="yes" enableApp="yes"/>  
  
        </application>  
    </SSO>  
    ```  
  
### <a name="to-create-single-sign-on-tickets"></a>Pour créer des tickets d'authentification unique  
  
1.  Tapez la commande suivante pour contrôler le comportement des tickets d'authentification unique :  
  
     `ssomanage.exe -tickets yes yes`  
  
2.  Répondez aux questions comme suit :  
  
     `ssomanage -tickets <allowed yes | no> <validate yes | no>`  
  
     Lorsque vous avez terminé, vous recevez la confirmation suivante :  
  
     **Utilisation d'un serveur d'authentification unique sur cet ordinateur. L’opération s’est terminée correctement.**  
  
### <a name="to-enable-affiliate-application-xml"></a>Pour activer le fichier XML de l'application associée  
  
1.  Tapez la commande suivante :  
  
     `ssomanage -enableapp JDEdwardsApp`  
  
2.  Tapez la commande suivante pour afficher la liste des applications et vérifier que l'application a été créée :  
  
     `ssoclient.exe –listapps`  
  
     Les applications associées qui sont disponibles pour utilisent l’affichage dans une liste :  
  
     **Applications disponibles pour IBI\YourID - JDEdwardsApp**  
  
3.  Tapez la commande suivante pour définir des informations d’identification de l’application de la filiale :  
  
     `ssoclient.exe -setcredentials JDEdwardsApp`  
  
4.  Lorsque vous y êtes invité, entrez les nom d'utilisateur et mot de passe. Entrez les informations d'identification de l'application associée JDEdwardsApp.  
  
     Par exemple, entrez les ID d'utilisateur et mot de passe suivants pour entrer dans le système via le serveur d'authentification unique.  
  
    -   ID d’utilisateur : **utilisateur**  
  
    -   Mot de passe : `******`  
  
    -   Confirmer ? Mot de passe : `******`  
  
     L’application associée apparaît dans l’adaptateur BizTalk pour JD Edwards EnterpriseOne **propriétés du Transport** boîte de dialogue.  
  
## <a name="see-also"></a>Voir aussi  
 [Sécurité de l’adaptateur BizTalk pour JD Edwards EnterpriseOne](../core/security-in-biztalk-adapter-for-jd-edwards-enterpriseone.md)