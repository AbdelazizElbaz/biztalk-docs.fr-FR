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
# <a name="how-to-configure-single-sign-on"></a>Comment configurer l’authentification unique
Avant d'accéder à l'authentification unique de l'entreprise, assurez-vous qu'elle est correctement définie pour l'utilisateur actuel. Pour la plupart des configurations, vous utilisez une des deux interfaces. `ISSOAdmin`est l’interface d’administration générale qui vous permet de créer des applications associées. Mais avec ISSOAdmin.GetGlobalInfo et ISSOAdmin.UpdateGlobalInfo, vous pouvez définir une variété d'indicateurs et de valeurs d'administration. Une des tâches possibles est celle qui est décrite ci-dessous et qui consiste à s'assurer que la création de tickets d'authentification unique a été activée.  
  
### <a name="to-enable-ticketing"></a>Pour activer la création de tickets  
  
1.  Créez une nouvelle instance de `ISSOAdmin`.  
  
2.  Récupérez les paramètres actuels via `ISSOAdmin.GetGlobalInfo`.  
  
     Si nécessaire, vous pouvez vérifier que les indicateurs sont définis sur les valeurs appropriées à ce stade.  
  
3.  Modifiez tous les indicateurs qui doivent l'être à l'aide d'`ISSOAdmin.UpdateGlobalInfo`.  
  
     Dans ce cas particulier, tous les indicateurs sont définis de manière à valider et à activer les tickets.  
  
 L'exemple suivant montre comment activer la création de tickets à l'aide de l'authentification unique.  
  
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
  
## <a name="see-also"></a>Voir aussi  
 [Programmation avec Enterprise Single Sign-On](../core/programming-with-enterprise-single-sign-on.md)