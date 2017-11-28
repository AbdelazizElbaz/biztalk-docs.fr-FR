---
title: "Comment configurer l’authentification unique sur | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 511edc1d-de82-4d17-88ea-6cacfccde10d
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 3203be74b21fa742e8e1ec2972e40f0212c4d1bf
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-configure-single-sign-on"></a><span data-ttu-id="7dac8-102">Comment configurer l’authentification unique</span><span class="sxs-lookup"><span data-stu-id="7dac8-102">How to Configure Single Sign-On</span></span>
<span data-ttu-id="7dac8-103">Avant d'accéder à l'authentification unique de l'entreprise, assurez-vous qu'elle est correctement définie pour l'utilisateur actuel.</span><span class="sxs-lookup"><span data-stu-id="7dac8-103">Before accessing Enterprise Single Sign-On, you should make sure that Enterprise Single Sign-On is set correctly for the current user.</span></span> <span data-ttu-id="7dac8-104">Pour la plupart des configurations, vous utilisez une des deux interfaces.</span><span class="sxs-lookup"><span data-stu-id="7dac8-104">For most configurations, you use one of two interfaces.</span></span> <span data-ttu-id="7dac8-105">`ISSOAdmin`est l’interface d’administration générale qui vous permet de créer des applications associées.</span><span class="sxs-lookup"><span data-stu-id="7dac8-105">`ISSOAdmin` is the general administration interface that enables you to create new affiliation applications.</span></span> <span data-ttu-id="7dac8-106">Mais avec ISSOAdmin.GetGlobalInfo et ISSOAdmin.UpdateGlobalInfo, vous pouvez définir une variété d'indicateurs et de valeurs d'administration.</span><span class="sxs-lookup"><span data-stu-id="7dac8-106">However, by using ISSOAdmin.GetGlobalInfo and ISSOAdmin.UpdateGlobalInfo, you can set a variety of flags and administration values.</span></span> <span data-ttu-id="7dac8-107">Une des tâches possibles est celle qui est décrite ci-dessous et qui consiste à s'assurer que la création de tickets d'authentification unique a été activée.</span><span class="sxs-lookup"><span data-stu-id="7dac8-107">One possible task, as described in the following procedure, is to ensure that SSO ticketing has been enabled.</span></span>  
  
### <a name="to-enable-ticketing"></a><span data-ttu-id="7dac8-108">Pour activer la création de tickets</span><span class="sxs-lookup"><span data-stu-id="7dac8-108">To enable ticketing</span></span>  
  
1.  <span data-ttu-id="7dac8-109">Créez une nouvelle instance de `ISSOAdmin`.</span><span class="sxs-lookup"><span data-stu-id="7dac8-109">Create a new instance of `ISSOAdmin`.</span></span>  
  
2.  <span data-ttu-id="7dac8-110">Récupérez les paramètres actuels via `ISSOAdmin.GetGlobalInfo`.</span><span class="sxs-lookup"><span data-stu-id="7dac8-110">Retrieve the current settings through `ISSOAdmin.GetGlobalInfo`.</span></span>  
  
     <span data-ttu-id="7dac8-111">Si nécessaire, vous pouvez vérifier que les indicateurs sont définis sur les valeurs appropriées à ce stade.</span><span class="sxs-lookup"><span data-stu-id="7dac8-111">If necessary, you may want to confirm that the flags are set to the correct values at this point.</span></span>  
  
3.  <span data-ttu-id="7dac8-112">Modifiez tous les indicateurs qui doivent l'être à l'aide d'`ISSOAdmin.UpdateGlobalInfo`.</span><span class="sxs-lookup"><span data-stu-id="7dac8-112">Change any relevant flags using `ISSOAdmin.UpdateGlobalInfo`.</span></span>  
  
     <span data-ttu-id="7dac8-113">Dans ce cas particulier, tous les indicateurs sont définis de manière à valider et à activer les tickets.</span><span class="sxs-lookup"><span data-stu-id="7dac8-113">In this particular case, all the flags are being set to validate and enable tickets.</span></span>  
  
 <span data-ttu-id="7dac8-114">L'exemple suivant montre comment activer la création de tickets à l'aide de l'authentification unique.</span><span class="sxs-lookup"><span data-stu-id="7dac8-114">The following example shows how to enable ticketing using Single Sign-On.</span></span>  
  
```  
public static bool EnableTickets()  
{  
   try  
   {  
      ISSOAdmin admin=new ISSOAdmin();  
      int flags=0;  
      int appDeleteMax=1000;  
      int mappingDeleteMax=1000;  
      int ntpLookupMax=-1000;  
      int xplLookupMax=-1000;  
      int ticketTimeout=2;  
      int cacheTimeout=60;  
      string secretServer=null;  
      string ssoAdminGroup=null;  
      string affiliateAppMgrGroup=null;  
      // Get current default settings.  
      admin.GetGlobalInfo(out flags, out appDeleteMax, out mappingDeleteMax, out ntpLookupMax, out xplLookupMax, out ticketTimeout, out cacheTimeout, out secretServer, out ssoAdminGroup, out affiliateAppMgrGroup);  
      // Update global settings.  
      admin.UpdateGlobalInfo(SSOFlag.SSO_FLAG_ALLOW_TICKETS | SSOFlag.SSO_FLAG_VALIDATE_TICKETS, SSOFlag.SSO_FLAG_ALLOW_TICKETS | SSOFlag.SSO_FLAG_VALIDATE_TICKETS, ref appDeleteMax, ref mappingDeleteMax, ref ntpLookupMax, ref xplLookupMax, ref ticketTimeout, ref cacheTimeout, null, null, null);   
   }  
   catch  
   {  
      return false;  
   }  
return true;  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="7dac8-115">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="7dac8-115">See Also</span></span>  
 [<span data-ttu-id="7dac8-116">Programmation avec Enterprise Single Sign-On</span><span class="sxs-lookup"><span data-stu-id="7dac8-116">Programming with Enterprise Single Sign-On</span></span>](../core/programming-with-enterprise-single-sign-on.md)