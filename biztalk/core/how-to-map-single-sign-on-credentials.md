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
# <a name="how-to-map-single-sign-on-credentials"></a><span data-ttu-id="32820-102">Comment mapper des références d’authentification uniques</span><span class="sxs-lookup"><span data-stu-id="32820-102">How to Map Single Sign-On Credentials</span></span>
<span data-ttu-id="32820-103">Lorsque vous savez que votre base de données d'authentification unique de l'entreprise contient des applications associées, vous pouvez mapper les informations d'identification sur cette application pour un utilisateur.</span><span class="sxs-lookup"><span data-stu-id="32820-103">When you know that you have affiliated applications in your Enterprise Single Sign-On database, you can map the credentials for a user to that application.</span></span> <span data-ttu-id="32820-104">Le mappage des informations d'identification de l'utilisateur actuel sur une application associée vous impose d'utiliser les interfaces `ISSOMapper` et `ISSOMapping`.</span><span class="sxs-lookup"><span data-stu-id="32820-104">Mapping the credentials of the current user to an affiliated application requires that you use a combination of the `ISSOMapper` and `ISSOMapping` interfaces.</span></span>  
  
### <a name="to-map-between-an-affiliated-application-and-user-credentials"></a><span data-ttu-id="32820-105">Pour réaliser un mappage entre une application associée et les informations d'identification d'un utilisateur</span><span class="sxs-lookup"><span data-stu-id="32820-105">To map between an affiliated application and user credentials</span></span>  
  
1.  <span data-ttu-id="32820-106">Créez de nouvelles instances de `ISSOMapper` et `ISSOMapping`.</span><span class="sxs-lookup"><span data-stu-id="32820-106">Create new instances of `ISSOMapper` and `ISSOMapping`.</span></span>  
  
2.  <span data-ttu-id="32820-107">Affectez les valeurs appropriées aux propriétés d'`ISSOMapping`.</span><span class="sxs-lookup"><span data-stu-id="32820-107">Set the `ISSOMapping` properties to the relevant values.</span></span>  
  
     <span data-ttu-id="32820-108">Les propriétés appropriées d'`ISSOMapping` sont le nom de domaine Microsoft Windows de l'utilisateur, le nom de l'utilisateur Windows, le nom de l'application associée et le nom de l'utilisateur externe.</span><span class="sxs-lookup"><span data-stu-id="32820-108">The relevant properties for `ISSOMapping` are the Microsoft Windows domain name of the user, the Windows user name, the name of the affiliated application, and the external user name.</span></span>  
  
3.  <span data-ttu-id="32820-109">Créez le mappage à l'aide d'un appel SSOMapping.Create.</span><span class="sxs-lookup"><span data-stu-id="32820-109">Create the mapping with a call to ISSOMapping.Create.</span></span>  
  
     <span data-ttu-id="32820-110">Appeler `ISSOMapping.Create` propage la copie locale du mappage vers le serveur d'authentification unique de l'entreprise.</span><span class="sxs-lookup"><span data-stu-id="32820-110">Calling `ISSOMapping.Create` propagates the local copy of the mapping out to the Enterprise Single Sign-On server.</span></span>  
  
4.  <span data-ttu-id="32820-111">Définissez les informations d'identification du mappage avec un appel `ISSOMapper.SetExternalCredentials`.</span><span class="sxs-lookup"><span data-stu-id="32820-111">Set the credentials on the mapping with a call to `ISSOMapper.SetExternalCredentials`.</span></span>  
  
5.  <span data-ttu-id="32820-112">Activez le mappage avec un appel `ISSOMapping.Enable`.</span><span class="sxs-lookup"><span data-stu-id="32820-112">Enable the mapping with a call to `ISSOMapping.Enable`.</span></span>  
  
 <span data-ttu-id="32820-113">L'exemple suivant indique comment ajouter un mappage entre une application et un utilisateur de l'authentification unique de l'entreprise donnés.</span><span class="sxs-lookup"><span data-stu-id="32820-113">The following example shows how to add mapping between a specified Enterprise Single Sign-On application and a user.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="32820-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="32820-114">See Also</span></span>  
 [<span data-ttu-id="32820-115">Programmation avec Enterprise Single Sign-On</span><span class="sxs-lookup"><span data-stu-id="32820-115">Programming with Enterprise Single Sign-On</span></span>](../core/programming-with-enterprise-single-sign-on.md)