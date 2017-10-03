---
title: "Le mappage d’identification de connexion unique | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e847bde9-7a4c-4b81-8ad6-6a7cf23d19a1
caps.latest.revision: "5"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 1a2717a990cf6ac2bac92067354afd42931c9a75
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-map-single-sign-on-credentials"></a>Comment mapper des références d’authentification uniques
Lorsque vous savez que votre base de données d'authentification unique de l'entreprise contient des applications associées, vous pouvez mapper les informations d'identification sur cette application pour un utilisateur. Le mappage des informations d'identification de l'utilisateur actuel sur une application associée vous impose d'utiliser les interfaces `ISSOMapper` et `ISSOMapping`.  
  
### <a name="to-map-between-an-affiliated-application-and-user-credentials"></a>Pour réaliser un mappage entre une application associée et les informations d'identification d'un utilisateur  
  
1.  Créez de nouvelles instances de `ISSOMapper` et `ISSOMapping`.  
  
2.  Affectez les valeurs appropriées aux propriétés d'`ISSOMapping`.  
  
     Les propriétés appropriées d'`ISSOMapping` sont le nom de domaine Microsoft Windows de l'utilisateur, le nom de l'utilisateur Windows, le nom de l'application associée et le nom de l'utilisateur externe.  
  
3.  Créez le mappage à l'aide d'un appel SSOMapping.Create.  
  
     Appeler `ISSOMapping.Create` propage la copie locale du mappage vers le serveur d'authentification unique de l'entreprise.  
  
4.  Définissez les informations d'identification du mappage avec un appel `ISSOMapper.SetExternalCredentials`.  
  
5.  Activez le mappage avec un appel `ISSOMapping.Enable`.  
  
 L'exemple suivant indique comment ajouter un mappage entre une application et un utilisateur de l'authentification unique de l'entreprise donnés.  
  
```  
public static bool AddMapping(string application, string user, string XU, string XP)  
{  
   try  
   {  
      // Set mapping.  
      ISSOMapper mapper=new ISSOMapper();  
      ISSOMapping mapping=new ISSOMapping();  
     string username=user.Substring(user.IndexOf('\\')+1);  
      string userdomain=user.Substring(0, user.IndexOf('\\'));  
      mapping.WindowsDomainName=userdomain;  
      mapping.WindowsUserName=username;  
      mapping.ApplicationName=application;  
      mapping.ExternalUserName=XU;  
      mapping.Create(0);  
      // Set credentials.  
      string[] credentials=new string[]{XP};  
      mapper.SetExternalCredentials(application, XU, ref credentials);  
      mapping.Enable(0);  
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