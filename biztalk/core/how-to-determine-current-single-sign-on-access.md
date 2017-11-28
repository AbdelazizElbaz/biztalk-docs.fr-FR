---
title: "Comment déterminer l’accès d’authentification unique en cours | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: cab68dfc-27cd-4f7c-a0df-20c670306358
caps.latest.revision: "5"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: b16fc1d1677fa1a8859c75b43be36de9209dbac0
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-determine-current-single-sign-on-access"></a><span data-ttu-id="94236-102">Comment déterminer l’accès d’authentification unique en cours</span><span class="sxs-lookup"><span data-stu-id="94236-102">How to Determine Current Single Sign-On Access</span></span>
<span data-ttu-id="94236-103">L'une des premières tâches que vous pourrez être amené à effectuer pour le compte d'un utilisateur sera de déterminer quelles applications associées ont déjà été configurées pour l'utilisateur actuel.</span><span class="sxs-lookup"><span data-stu-id="94236-103">One of the first tasks you might need to perform for a user is to determine what affiliated applications have already been set up for the current user.</span></span> <span data-ttu-id="94236-104">Vous pouvez réaliser cette requête en appelant ISSOMapper.GetApplications.</span><span class="sxs-lookup"><span data-stu-id="94236-104">You can perform this query with a call to ISSOMapper.GetApplications.</span></span>  
  
### <a name="to-query-the-single-sign-on-database-for-the-applications-available-to-the-current-user"></a><span data-ttu-id="94236-105">Pour interroger la base de données de l'authentification unique à propos des applications à disposition de l'utilisateur actuel</span><span class="sxs-lookup"><span data-stu-id="94236-105">To query the Single Sign-On database for the applications available to the current user</span></span>  
  
1.  <span data-ttu-id="94236-106">Créez une nouvelle instance de `ISSOMapper`.</span><span class="sxs-lookup"><span data-stu-id="94236-106">Create a new instance of `ISSOMapper`.</span></span>  
  
     <span data-ttu-id="94236-107">Généralement, `ISSOMapper` est une interface conçue pour extraire des informations à partir de l'authentification unique.</span><span class="sxs-lookup"><span data-stu-id="94236-107">In general, `ISSOMapper` is an interface designed to retrieve information from Single Sign-On (SSO).</span></span> <span data-ttu-id="94236-108">Vous utiliserez très probablement `ISSOMapper` dans de nombreuses requêtes similaires.</span><span class="sxs-lookup"><span data-stu-id="94236-108">You will most likely use `ISSOMapper` in many similar queries.</span></span>  
  
2.  <span data-ttu-id="94236-109">Extrayez toutes les applications associées à l'utilisateur actuel en appelant GetApplications.</span><span class="sxs-lookup"><span data-stu-id="94236-109">Retrieve all applications that are affiliated with the current user by calling GetApplications.</span></span>  
  
     <span data-ttu-id="94236-110">GetApplications renvoie de manière automatique uniquement les applications associées à l'utilisateur actuel.</span><span class="sxs-lookup"><span data-stu-id="94236-110">GetApplications automatically returns only the affiliated applications of the current user.</span></span>  
  
 <span data-ttu-id="94236-111">L'exemple de code suivant démontre comment interroger la base de données de l'authentification unique.</span><span class="sxs-lookup"><span data-stu-id="94236-111">The following code example demonstrates how to query the Single Sign-On database.</span></span>  
  
```  
private static string[] Applications=null;  
. . .  
public static string[] GetCurrentUserApplications()  
{  
   if(Applications==null)  
   {  
      string[] descs;  
      string[] contacts;  
      ISSOMapper mapper=new ISSOMapper();  
      mapper.GetApplications(out Applications, out descs, out contacts);  
   }  
   return Applications;  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="94236-112">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="94236-112">See Also</span></span>  
 [<span data-ttu-id="94236-113">Programmation avec Enterprise Single Sign-On</span><span class="sxs-lookup"><span data-stu-id="94236-113">Programming with Enterprise Single Sign-On</span></span>](../core/programming-with-enterprise-single-sign-on.md)