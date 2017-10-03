---
title: "Le Service Web de résolution | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 236cff15-562a-41d5-bfdc-d250186fb616
caps.latest.revision: "4"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 916181431686ca729c0751d9362570afb7dddeee
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="the-resolver-web-service"></a>Le Service Web de résolution
Le service Web du programme de résolution est une passerelle dans le mécanisme de résolution dynamique ESB. [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)]inclut les deux versions de ce service : une version de ASP.NET (ASMX) et une version de Windows Communication Foundation (WCF). Les noms de service sont **ESB. ResolverServices** et **ESB. ResolverServices.WCF**, respectivement, et les services exposent des méthodes suivantes :  
  
-   **Résoudre.** Cette méthode prend comme unique paramètre un **chaîne** qui contient la chaîne de connexion de programme de résolution de la demande, qui est conforme pour les chaînes de connexion standard tels que des programmes de résolution des **statique, BRE, UDDI, XPATH, l’itinéraire, itinéraire statique, BRI,** ou **LDAP.**  
  
-   **ResolveMessage.** Cette méthode prend comme premier paramètre de chaîne qui contient la chaîne de connexion de programme de résolution de la demande, qui est conforme pour les chaînes de connexion standard tels que des programmes de résolution des **statique, BRE, UDDI, XPATH, feuille de route, ITINÉRAIRE statique, BRI,** ou **LDAP**. En outre, la méthode accepte un deuxième paramètre facultatif en tant qu’un **chaîne** qui contient un document de message XML que le service peut utiliser en tant que faits facultatif pour faciliter une résolution ; par exemple, le programme de résolution BRE peut nécessiter un corps de message qui encapsule des faits.  
  
 Pour plus d’informations sur les classes de programme de résolution et ResolverDictionary et leur utilisation, consultez [l’utilisation des Classes d’assistance](../esb-toolkit/using-the-helper-classes.md).  
  
## <a name="resolver-connection-strings"></a>Programme de résolution des chaînes de connexion  
 Le mécanisme de résolution dynamique ESB utilise une chaîne de connexion précédée d’un moniker qui indique le type de résolution à effectuer. Les monikers pris en charge incluent **statique, BRE, UDDI, UDDI3, XPATH, itinéraire, itinéraire statique, BRI,** et **LDAP**. La chaîne de connexion suivante montre un exemple d’un **UDDI** moniker :  
  
```  
  
//UDDI  
UDDI:\\serverUrl=http://localhost/uddi;serviceName=PurchaseOrder;serviceProvider=Microsoft.Practices.ESB  
```  
  
 Pour plus d’informations sur les types de chaînes de connexion pris en charge par le mécanisme de résolution dynamique, consultez [à l’aide de la résolution dynamique et routage](../esb-toolkit/using-dynamic-resolution-and-routing.md).  
  
> [!NOTE]
>  Vous devez configurer ce service pour utiliser la sécurité intégrée Windows et pour s’exécuter sous le compte SERVICE réseau intégré.  
>   
>  Par défaut, les services Web du programme de résolution ne sont pas configurés pour exiger SSL Secure Sockets Layer () lors de l’accès par les clients. Vous devez configurer le service afin qu’il exige SSL pour l’accès client et protéger la connexion entre l’ordinateur hôte du service Web des Internet Information Services (IIS) et votre serveur BizTalk Server à l’aide d’IPSec d’au niveau du réseau et l’accès approprié au niveau des fichiers contrôler les autorisations de liste (ACL). Pour éviter les risques de sécurité, il n’est pas recommandé pour exposer ce service en dehors de la limite du sous-système approuvé.