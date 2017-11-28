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
# <a name="how-to-create-and-describe-an-application-to-single-sign-on"></a><span data-ttu-id="55da7-102">La création et la description d’une Application pour l’authentification unique</span><span class="sxs-lookup"><span data-stu-id="55da7-102">How to Create and Describe an Application to Single Sign-On</span></span>
<span data-ttu-id="55da7-103">L’ajout d’une application associée à la base de données de l’authentification unique de l’entreprise est une tâche administrative commune que vous serez peut-être amené à effectuer.</span><span class="sxs-lookup"><span data-stu-id="55da7-103">A common administrative task that you might need to perform is adding an affiliate application into the Enterprise Single Sign-On (SSO) database.</span></span> <span data-ttu-id="55da7-104">Le fait d’ajouter une application associée à la base de données d’authentification unique de l’entreprise vous permet d’associer des utilisateurs et des données d’identification à l’application associée.</span><span class="sxs-lookup"><span data-stu-id="55da7-104">Adding an affiliate application to the Enterprise SSO database enables you to associate users and credentials with the affiliated application.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="55da7-105">La création d'une application associée nécessite l'appartenance au compte « Administrateur d'applications associées à authentification unique » ou plus.</span><span class="sxs-lookup"><span data-stu-id="55da7-105">Creating an affiliated application requires membership in the "SSO Affiliate Administrator" account or above.</span></span>  
  
### <a name="to-create-and-describe-an-application-in-the-sso-database"></a><span data-ttu-id="55da7-106">Pour créer et décrire une application dans la base de données d’authentification unique</span><span class="sxs-lookup"><span data-stu-id="55da7-106">To create and describe an application in the SSO database</span></span>  
  
1.  <span data-ttu-id="55da7-107">Créez un nouvel objet `ISSOAdmin`.</span><span class="sxs-lookup"><span data-stu-id="55da7-107">Create a new `ISSOAdmin` object.</span></span>  
  
2.  <span data-ttu-id="55da7-108">Créer une nouvelle application avec un appel vers `ISSOAdmin.CreateApplication`.</span><span class="sxs-lookup"><span data-stu-id="55da7-108">Create a new application with a call to `ISSOAdmin.CreateApplication`.</span></span>  
  
3.  <span data-ttu-id="55da7-109">Ajoutez les champs appropriés décrivant l’application avec un appel vers `ISSOAdmin.CreateFieldInfo`.</span><span class="sxs-lookup"><span data-stu-id="55da7-109">Add the relevant fields describing the application with a call to `ISSOAdmin.CreateFieldInfo`.</span></span>  
  
     <span data-ttu-id="55da7-110">Au cours de cette étape, vous indiquez à la base de données qu’une application est associée à des utilisateurs et à des mots de passe.</span><span class="sxs-lookup"><span data-stu-id="55da7-110">During this step, you tell the database that an application has users and associated passwords.</span></span>  
  
4.  <span data-ttu-id="55da7-111">Transmettez la description que vous avez créée au serveur avec un appel vers `ISSOAdmin.UpdateApplication` ou `ISSOAdmin2.UpdateApplication2`.</span><span class="sxs-lookup"><span data-stu-id="55da7-111">Push the newly created description out to the server with a call to `ISSOAdmin.UpdateApplication` or `ISSOAdmin2.UpdateApplication2`.</span></span>  
  
     <span data-ttu-id="55da7-112">La différence entre les deux méthodes réside dans le fait que `UpdateApplication2` utilise un `IPropertyBag` pour décrire les mises à jour de l'application, tandis que `UpdateApplication` comporte plusieurs paramètres.</span><span class="sxs-lookup"><span data-stu-id="55da7-112">The difference between the two methods is that `UpdateApplication2` uses an `IPropertyBag` as the way to describe the application updates, while `UpdateApplication` has multiple parameters.</span></span>  
  
5.  <span data-ttu-id="55da7-113">Videz la mémoire cache locale pour les modifications que vous avez apportées en appelant `ISSOAdmin.PurgeCacheForApplication`.</span><span class="sxs-lookup"><span data-stu-id="55da7-113">Purge the local cache for the changes you made by calling `ISSOAdmin.PurgeCacheForApplication`.</span></span>  
  
     <span data-ttu-id="55da7-114">Il s'agit d'une mesure de sécurité qui permet d'éviter que les noms et mots de passe que vous avez décrits à l'étape 3 figurent dans un emplacement non sécurisé.</span><span class="sxs-lookup"><span data-stu-id="55da7-114">Purging the local cache is a security measure that prevents having the names and passwords that you describe in step 3 to exist in an unsecured location.</span></span>  
  
 <span data-ttu-id="55da7-115">L’exemple suivant décrit comment créer une application et ajouter des informations de champs.</span><span class="sxs-lookup"><span data-stu-id="55da7-115">The following example shows how to create an application and add field information.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="55da7-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="55da7-116">See Also</span></span>  
 [<span data-ttu-id="55da7-117">Programmation avec Enterprise Single Sign-On</span><span class="sxs-lookup"><span data-stu-id="55da7-117">Programming with Enterprise Single Sign-On</span></span>](../core/programming-with-enterprise-single-sign-on.md)