---
title: "Création d’applications associées à des Applications1 | Documents Microsoft"
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
- tickets, SSO
- affiliate applications, enabling XML
- SSO tickets
ms.assetid: f3603fcb-3594-460b-b74a-618e22d9c4e0
caps.latest.revision: "11"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: f52c59caf451a2e0b55c775bf70a36a9a05ae9c3
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="creating-affiliate-applications"></a>Création d’Applications associées
Les procédures suivantes décrivent comment travailler avec des applications associées et de l'authentification unique (SSO). Pour obtenir des informations exhaustives sur l'utilisation de l'authentification unique de l'entreprise, consultez la documentation de Microsoft.  
  
> [!NOTE]
>  Si vous recevez des erreurs de l’authentification unique, vérifiez que vous avez utilisé un compte de domaine lors de la configuration de BizTalk Server, comme cela affecte les fonctionnalités du service SSO de l’entreprise. (SSO n'est compatible qu'avec les comptes de domaine).  
  
### <a name="to-create-an-affiliate-application"></a>Pour créer une application associée  
  
1.  Dans le panneau de configuration, ouvrez **Services**et vérifiez que le service Enterprise Single Sign-On est en cours d’exécution.  
  
2.  Dans une invite de commandes, accédez au dossier Enterprise Single Sign-On. Exemple :  
  
     **C:\Program Files\Common Files\Enterprise Single Sign-On >**  
  
3.  Utilisez les commandes du service de l'authentification unique de l'entreprise Pour obtenir la liste de commandes, utilisez la **-aide** basculer.  
  
4.  Pour créer l’application associée à l’aide de *. XML en tant qu’un démarrage, tapez la commande suivante :  
  
     `ssomanage.exe -createapps C:\SSOtest\AffiliateApplication.xml`  
  
     Où :  
  
     C:\SSOtest est le dossier qui contient le fichier XML de votre application ;  
  
     AffiliateApplication.xml est l’application XML que vous avez créé et qui contient les informations d’authentification.  
  
     Exemple :  
  
    ```  
    <?xml version="1.0"?>  
    <SSO>  
        <application name="TIBCO RendezvousApp">  
            <description> TIBCO Rendezvous SSO Application</description>  
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
  
3.  Lorsque vous avez terminé, vous recevez la confirmation suivante :  
  
     **Utilisation d'un serveur d'authentification unique sur cet ordinateur. L’opération s’est terminée correctement.**  
  
### <a name="to-enable-affiliate-application-xml"></a>Pour activer le fichier XML de l'application associée  
  
1.  Tapez la commande suivante :  
  
     `ssomanage -enableapp TIBCO RendezvousApp`  
  
2.  Tapez la commande suivante pour afficher la liste des applications et vérifier que l'application a été créée :  
  
     `ssoclient.exe –listapps`  
  
     Les applications associées utilisables apparaissent dans une liste.  
  
     **Applications disponibles pour IBI\YourID - TIBCO RendezvousApp**  
  
3.  Tapez la commande suivante pour définir des informations d’identification de l’application de la filiale :  
  
     `ssoclient.exe -setcredentials TIBCO RendezvousApp`  
  
4.  Entrez le nom d’utilisateur et un mot de passe à la demande.  
  
5.  Entrez les informations d'identification de l'application associée TIBCO RendezvousApp.  
  
     Par exemple, entrez l'ID d'utilisateur et le mot de passe pour entrer dans le système via le serveur d'authentification unique.  
  
    -   ID d'utilisateur : utilisateur  
  
    -   Mot de passe : ******  
  
    -   Confirmer le mot de passe : ******  
  
6.  L’application associée apparaît dans l’adaptateur BizTalk pour TIBCO Rendezvous **propriétés du Transport** boîte de dialogue.  
  
## <a name="see-also"></a>Voir aussi  
 [Sécurité de l’adaptateur BizTalk pour TIBCO Rendezvous](../core/security-in-biztalk-adapter-for-tibco-rendezvous.md)   
 [À l’aide de l’authentification unique](../core/using-single-sign-on5.md)