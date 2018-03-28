---
title: Création d’applications associées à des Applications3 | Documents Microsoft
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- affiliate applications
- Single Sign-On, creating tickets
- tickets, creating Single Sign-On
- affiliate applications, creating
- SSO tickets
ms.assetid: 800644fd-2286-4e59-894b-260f584dd29f
caps.latest.revision: ''
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 857ee7edd623332e72176ac09082f0ec9fc460f4
ms.sourcegitcommit: 8418b1a8f38b7f56979cd6e203f0b591e2f40fe1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/28/2018
---
# <a name="creating-affiliate-applications"></a>Création d’Applications associées
Les procédures suivantes décrivent l'utilisation des applications associées à l'aide de l'authentification unique (SSO).  
  
> [!NOTE]
>  Si vous recevez des erreurs liées à l'authentification unique, vérifiez que vous avez utilisé un compte de domaine lors de la configuration de BizTalk Server. En effet, cela affecte les fonctionnalités du service d'authentification unique de l'entreprise (SSO n'est compatible qu'avec les comptes de domaine).  
  
## <a name="creating-an-affiliate-application"></a>Création d'une application associée  
  
#### <a name="to-create-an-affiliate-application"></a>Pour créer une application associée  
  
1.  Dans **le panneau de configuration**, ouvrez **Services**et vérifiez que le service Enterprise Single Sign-On est en cours d’exécution.  
  
2.  Dans une invite de commandes, accédez au dossier Enterprise Single Sign-On.  
  
     Par exemple :  
  
     **C:\Program Files\Common Files\Enterprise Single Sign-On>**  
  
3.  Utilisez les commandes du service de l'authentification unique de l'entreprise Pour obtenir la liste des commandes, utilisez le commutateur -help.  
  
     ![](../core/media/siebeladapter-23-sso-commands.gif "SiebelAdapter_23_SSO_Commands")  
  
4.  Pour créer l’application associée à l’aide la *. XML en tant qu’un début, tapez la commande suivante :  
  
     **ssomanage.exe -createapps C:\SSOtest\AffiliateApplication.xml**  
  
     où :  
  
     C:\SSOtest est le dossier contenant le XML de votre application.  
  
     AffiliateApplication.xml est l’application XML que vous avez créé contenant les informations de connexion.  
  
     Par exemple :  
  
    ```  
    <?xml version="1.0"?>  
    <SSO>  
         <application name="JDEdwardsApp">  
              <description>JDEdwards SSO Application</description>  
              <contact>someone@microsoft.com</contact>  
              <userGroup>ibi\Domain Users</userGroup>  
              <!—-an existing group on the domain controller - >   
              <appAdminGroup>ibi\YourID</appAdminGroup>  
              <!-- an existing account within the domain group - >   
              <field ordinal="0" label="User ID" masked="no" />  
              <field ordinal="1" label="Password" masked="yes" />  
              <flags groupApp="no" allowTickets="yes" enableApp="yes"/>  
         </application>  
    </SSO>  
    ```  
  
## <a name="creating-single-sign-on-tickets"></a>Création de tickets d'authentification unique  
  
#### <a name="to-create-sso-tickets"></a>Pour créer des tickets SSO  
  
1.  Tapez la commande suivante pour contrôler le comportement de ticket d’authentification unique :  
  
     `ssomanage.exe -tickets yes yes`  
  
2.  Répondez aux questions :  
  
     `ssomanage -tickets <allowed yes | no> <validate yes | no>`  
  
     Lorsque vous avez terminé, vous recevez une confirmation :  
  
     **Utilisation d'un serveur d'authentification unique sur cet ordinateur. L’opération s’est terminée correctement.**  
  
## <a name="enabling-the-affiliate-application-xml"></a>Activation du fichier XML de l'application associée  
  
#### <a name="to-enable-affiliate-application-xml"></a>Pour activer le fichier XML de l'application associée  
  
1.  Tapez la commande suivante :  
  
     `ssomanage -enableapp JDEdwardsApp`  
  
2.  Tapez la commande suivante pour répertorier les applications et pour vérifier que l’application a été créée :  
  
     `ssoclient.exe –listapps`  
  
     Les Applications associées utilisables apparaissent dans une liste.  
  
     **Applications disponibles pour IBI\YourID - JDEdwardsApp**  
  
3.  Tapez la commande suivante pour définir les informations d'identification de l'application associée :  
  
     `ssoclient.exe -setcredentials JDEdwardsApp`  
  
4.  Lorsque vous y êtes invité, entrez les nom d'utilisateur et mot de passe. Entrez les informations d'identification de l'application associée JDEdwardsApp. Par exemple, entrez les ID d'utilisateur et mot de passe suivants pour entrer dans le système via le serveur d'authentification unique.  
  
    -   **ID d’utilisateur :** utilisateur  
  
    -   **Mot de passe :** ******  
  
    -   **Confirmer ? Mot de passe :** ******  
  
5.  L'application associée s'affiche dans la liste déroulante de la boîte de dialogue Propriétés du transport de l'adaptateur BizTalk pour JD Edwards OneWorld.  
  
## <a name="see-also"></a>Voir aussi  
 [Sécurité de la carte](../core/security-in-biztalk-adapter-for-jd-edwards-oneworld.md)