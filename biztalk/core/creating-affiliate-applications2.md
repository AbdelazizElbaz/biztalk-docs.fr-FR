---
title: "Création d’applications associées pour PeopleSoft Enterprise | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 95151163-5aaf-4683-afb7-02949ccda3e1
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 4a77926fa9d98606770ad2fe7715a3b0ff66ea5c
ms.sourcegitcommit: dd7c54feab783ae2f8fe75873363fe9ffc77cd66
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/07/2017
---
# <a name="creating-affiliate-applications"></a>Création d’Applications associées
Les étapes suivantes montrent comment commencer à utiliser les applications associées et Single Sign-On (SSO).  
  
> [!NOTE]
>  Si vous recevez des erreurs de l’authentification unique, vérifiez que vous avez utilisé un compte de domaine lorsque vous avez configuré BizTalk Server, comme cela affecte les fonctionnalités du service SSO de l’entreprise. (SSO n'est compatible qu'avec les comptes de domaine).  
  
## <a name="create-an-affiliate-application"></a>Créer une application associée  
  
1.  Dans le panneau de configuration, ouvrez **Services**et vérifiez que le service Enterprise Single Sign-On est en cours d’exécution.  
  
2.  Dans une invite de commandes, accédez au dossier Enterprise Single Sign-On.  
  
     Exemple :  
  
     **C:\Program Files\Common Files\Enterprise Single Sign-On >**  
  
3.  Utilisez les commandes du service de l'authentification unique de l'entreprise Pour obtenir la liste de commandes, utilisez la **-aide** basculer.  
  
     ![](../core/media/siebeladapter-23-sso-commands.gif "SiebelAdapter_23_SSO_Commands")  
  
4.  Pour créer l’application associée à l’aide de *. XML en tant qu’un démarrage, tapez la commande suivante :  
  
     `ssomanage.exe -createapps C:\SSOtest\AffiliateApplication.xml`  
  
     où :  
  
    -   C:\SSOtest est le dossier qui contient le fichier XML de votre application ;  
  
    -   AffiliateApplication.xml est le fichier XML de l'application que vous avez créée qui contient les informations de l'authentification unique.  
  
     Exemple :  
  
    ```  
    <?xml version="1.0"?>  
    <SSO>  
         <application name="PeopleSoftApp">  
              <description>PeopleSoft SSO Application</description>  
              <contact>someone@microsoft.com</contact>  
             <appUserAccount>DomainName\AppUserGroup</appUserAccount>  
              <!—-an existing group on the domain controller - >   
              <appAdminAccount>DomainName\AppAdminGroup<appAdminAccount>   
              <!-- an existing account in the domain group - >   
              <field ordinal="0" label="User ID" masked="no" />  
              <field ordinal="1" label="Password" masked="yes" />  
              <flags groupApp="no" allowTickets="yes" enableApp="yes"/>  
         </application>  
    </SSO>  
    ```  
  
## <a name="create-single-sign-on-tickets"></a>Créer des Tickets d’authentification uniques  
  
1.  Tapez la commande suivante pour contrôler le comportement des tickets d'authentification unique :  
  
     `ssomanage.exe -tickets yes yes`  
  
2.  Répondez aux questions :  
  
     `ssomanage -tickets <allowed yes | no> <validate yes | no>`  
  
     Une fois terminée, vous recevez une confirmation :  
  
     **Utilisation d'un serveur d'authentification unique sur cet ordinateur. L’opération s’est terminée correctement.**  
  
## <a name="enable-the-affiliate-application-xml"></a>Activer l’Application associée XML  
  
1.  Tapez la commande suivante :  
  
     `ssomanage -enableapp PeopleSoftApp`  
  
2.  Tapez la commande suivante pour afficher la liste des applications et vérifier que l'application a été créée :  
  
     `ssoclient.exe –listapps`  
  
     Les applications associées utilisables apparaissent dans une liste.  
  
     **Applications disponibles pour IBI\YourID - PeopleSoftApp**  
  
3.  Tapez la commande suivante pour définir des informations d’identification de l’application de la filiale :  
  
     `ssoclient.exe -setcredentials PeopleSoftApp`  
  
4.  Lorsque vous y êtes invité, entrez les nom d'utilisateur et mot de passe. Entrez les informations d'identification de l'application associée PeopleSoftApp.  
  
     Par exemple, entrez les ID d'utilisateur et mot de passe suivants pour entrer dans le système via le serveur d'authentification unique.  
  
    -   **ID d’utilisateur :**`user`  
  
    -   **Mot de passe :**`******`  
  
    -   **Confirmer ? Mot de passe :**`******`  
  
5.  L'application associée apparaît dans la boîte de dialogue Propriétés du transport de l'adaptateur BizTalk pour PeopleSoft Enterprise.  
  
## <a name="see-also"></a>Voir aussi  
 [Sécuriser l’adaptateur](../core/security-in-biztalk-adapter-for-peoplesoft-enterprise.md)