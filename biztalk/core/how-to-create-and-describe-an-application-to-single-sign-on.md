---
title: "La création et la description d’une Application pour l’authentification unique sur | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 7d717885-b132-4ba0-a93b-03377ac5eb97
caps.latest.revision: "5"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 423439795d9a3822427edbee2e062c3c0aa6bb80
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-create-and-describe-an-application-to-single-sign-on"></a>La création et la description d’une Application pour l’authentification unique
L’ajout d’une application associée à la base de données de l’authentification unique de l’entreprise est une tâche administrative commune que vous serez peut-être amené à effectuer. Le fait d’ajouter une application associée à la base de données d’authentification unique de l’entreprise vous permet d’associer des utilisateurs et des données d’identification à l’application associée.  
  
> [!NOTE]
>  La création d'une application associée nécessite l'appartenance au compte « Administrateur d'applications associées à authentification unique » ou plus.  
  
### <a name="to-create-and-describe-an-application-in-the-sso-database"></a>Pour créer et décrire une application dans la base de données d’authentification unique  
  
1.  Créez un nouvel objet `ISSOAdmin`.  
  
2.  Créer une nouvelle application avec un appel vers `ISSOAdmin.CreateApplication`.  
  
3.  Ajoutez les champs appropriés décrivant l’application avec un appel vers `ISSOAdmin.CreateFieldInfo`.  
  
     Au cours de cette étape, vous indiquez à la base de données qu’une application est associée à des utilisateurs et à des mots de passe.  
  
4.  Transmettez la description que vous avez créée au serveur avec un appel vers `ISSOAdmin.UpdateApplication` ou `ISSOAdmin2.UpdateApplication2`.  
  
     La différence entre les deux méthodes réside dans le fait que `UpdateApplication2` utilise un `IPropertyBag` pour décrire les mises à jour de l'application, tandis que `UpdateApplication` comporte plusieurs paramètres.  
  
5.  Videz la mémoire cache locale pour les modifications que vous avez apportées en appelant `ISSOAdmin.PurgeCacheForApplication`.  
  
     Il s'agit d'une mesure de sécurité qui permet d'éviter que les noms et mots de passe que vous avez décrits à l'étape 3 figurent dans un emplacement non sécurisé.  
  
 L’exemple suivant décrit comment créer une application et ajouter des informations de champs.  
  
```  
public static bool AddApplication(string name, string admins, string users)  
    {  
       try  
       {  
          ISSOAdmin admin=new ISSOAdmin();  
          // Create application.  
          admin.CreateApplication(name, "SSO Sample Application", "administrator@ssoaffiliateapplication.com", users, admins, SSOFlag.SSO_WINDOWS_TO_EXTERNAL | SSOFlag.SSO_FLAG_ALLOW_TICKETS | SSOFlag.SSO_FLAG_VALIDATE_TICKETS, 2);  
          // Add fields.  
          admin.CreateFieldInfo(name, "User Id", SSOFlag.SSO_FLAG_NONE);  
          admin.CreateFieldInfo(name, "Password", SSOFlag.SSO_FLAG_FIELD_INFO_MASK);  
          // Enable application.  
          admin.UpdateApplication(name, null, null, null, null, SSOFlag.SSO_FLAG_ENABLED, SSOFlag.SSO_FLAG_ENABLED);  
          // Purge changes.  
          admin.PurgeCacheForApplication(name);  
       }  
       catch  
       {  
          return false;  
       }  
       return true;  
    }  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Programmation avec Enterprise Single Sign-On](../core/programming-with-enterprise-single-sign-on.md)