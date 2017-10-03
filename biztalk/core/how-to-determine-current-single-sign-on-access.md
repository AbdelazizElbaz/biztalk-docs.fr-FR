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
# <a name="how-to-determine-current-single-sign-on-access"></a>Comment déterminer l’accès d’authentification unique en cours
L'une des premières tâches que vous pourrez être amené à effectuer pour le compte d'un utilisateur sera de déterminer quelles applications associées ont déjà été configurées pour l'utilisateur actuel. Vous pouvez réaliser cette requête en appelant ISSOMapper.GetApplications.  
  
### <a name="to-query-the-single-sign-on-database-for-the-applications-available-to-the-current-user"></a>Pour interroger la base de données de l'authentification unique à propos des applications à disposition de l'utilisateur actuel  
  
1.  Créez une nouvelle instance de `ISSOMapper`.  
  
     Généralement, `ISSOMapper` est une interface conçue pour extraire des informations à partir de l'authentification unique. Vous utiliserez très probablement `ISSOMapper` dans de nombreuses requêtes similaires.  
  
2.  Extrayez toutes les applications associées à l'utilisateur actuel en appelant GetApplications.  
  
     GetApplications renvoie de manière automatique uniquement les applications associées à l'utilisateur actuel.  
  
 L'exemple de code suivant démontre comment interroger la base de données de l'authentification unique.  
  
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
  
## <a name="see-also"></a>Voir aussi  
 [Programmation avec Enterprise Single Sign-On](../core/programming-with-enterprise-single-sign-on.md)