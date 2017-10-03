---
title: "En cours d’exécution SSO Projects1 | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- SSO projects
- running SSO projects
- samples, SSO projects
ms.assetid: f8da1874-7495-47cd-a3a3-881f722c80a2
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: ac9286dbaaced073dc7517bf5731fab3fa332d1c
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="running-sso-projects"></a>Exécution de projets SSO
Vous pouvez exécuter l'exemple sous Internet Explorer.  
  
## <a name="running-a-sample-from-internet-explorer"></a>Exécution de l'exemple sous Internet Explorer  
  
#### <a name="to-run-the-sample-from-the-internet-explorer"></a>Pour exécuter l'exemple sous Internet Explorer  
  
1.  Ouvrez votre navigateur.  
  
2.  Utilisez la syntaxe suivante :  
  
    ```  
    http://localhost/SSODemo/BTSHTTPReceive.dll?[Insert XML Instance body]   
    ```  
  
     Exemple :  
  
     http://localhost/SSODemo/BTSHTTPReceive.dll? \<ns0:method_list_method % 20xmlns : ns0 = « http://microsoft.com/exposed/object/object1 » >\<ns0:method_list_method >\<ns1:method_list % 20xmlns : ns1 = « http://microsoft.com/exposed/object » >\<ns1:comp_code >\</ns1:comp_code >\<ns1:comp_name >\</ns1:comp_name >\< /ns1:object_1 >\</ns0:method_list >\</ns0 : method_list_method >  
  
     Dans ce cas, il n'est pas nécessaire de fournir des informations d'identification.  
  
## <a name="see-also"></a>Voir aussi  
 [À l’aide de l’authentification unique](../core/using-single-sign-on2.md)