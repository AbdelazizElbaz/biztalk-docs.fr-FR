---
title: "Continuation d’activités | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- continuation tokens
- activities [BAM], code samples
- activities [BAM], continuation tokens
- continuations, activities [BAM]
- code samples, activities [BAM]
ms.assetid: 47d91ae6-77c1-4efb-940f-a7b3a325e5bd
caps.latest.revision: "14"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: c7568da0647ae9847c3de2d060d75a53466b9709
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="activity-continuation"></a>Continuation d'activités
L'activité d'analyse BAM (également appelée activité d'entreprise) peut englober plusieurs applications hétérogènes (par exemple un pipeline, deux orchestrations, une application sectorielle et un autre pipeline). L’infrastructure BAM peut mettre en corrélation les événements à partir de plusieurs applications avec un peu d’aide du développeur – un concept appelé «*Continuation*, » qui est indiqué dans l’illustration suivante.  
  
 ![](../core/media/ebiz-prog-bam-fig4-app-scopes-cont-tokens.gif "ebiz_prog_bam_fig4_app_scopes_cont_tokens")  

## <a name="applications"></a>Applications  
 La première partie de l'activité se produit dans l'application des ventes, la deuxième dans l'application d'emballage et d'assemblage en palettes et la troisième, traitant le suivi de la livraison, est disponible dans l'application d'expédition. Chaque application utilise différents des ID de l’unité de travail actuelle : fournisseur numéro de commande (PO), le numéro de commande (ainsi) et le numéro de commande d’expédition (UPS). Pour mettre des événements en corrélation entre deux applications différentes, vous devez :  
  
-   identifier le jeton de continuation, donnée unique disponible pour les deux applications (par exemple, la partie du message échangé) ;  
  
-   appeler l'événement EnableContinuation dans la première application et transmettre le jeton de continuation en même temps que l'ID d'activité actuel ;  
  
-   éviter absolument d'appeler l'événement BeginActivity dans la deuxième application ;  
  
-   déclencher tous les événements suivants dans la deuxième application en utilisant le jeton de continuation au lieu de l'ID d'activité.  
  
 Le code ci-dessous est un exemple de l'utilisation d'une continuation d'activités entre trois applications :  
  
 **Application de bon de commande**  
  
```  
string oID="PO#123";  
string soID="SO#265";  
es.BeginActivity("PurchaseOrder",poID);  
es.UpdateActivity("PurchaseOrder",poID,  
    "POReceived",DateTime.UtcNow,  
    "POAmount",100,  
"CustomerCity","Seattle");  
es.EnableContinuation(  
   "PurchaseOrder",poId,soID);  
es.EndActivity("PurchaseOrder",poID);  
```  
  
 **Application de traitement**  
  
```  
string soID="SO#265";  
string upsID="UPS#97892";  
es.UpdateActivity("PurchaseOrder",soID,  
    "POApproved",DateTime.UtcNow,  
    "ProductName","ProductA");  
es.EnableContinuation(  
   "PurchaseOrder",soID,upsID);  
es.EndActivity("PurchaseOrder",soID);  
```  
  
 **Application d’expédition**  
  
```  
string upsID="UPS#97892"  
es.UpdateActivity("PurchaseOrder", upsID,  
"POShipped",DateTime.UtcNow);  
es.EndActivity("PurchaseOrder",upsID)  
  
```  
  
 Tenez compte des instructions suivantes pour intégrer la continuation d'activités dans votre code :  
  
-   Utilisez la continuation uniquement quand l'utilisateur final doit traiter le travail d'applications différentes dans une seule activité. Utilisez des activités distinctes pour chaque application et créez une relation d'activité si l'utilisateur final considère le travail de chaque application comme des activités suffisamment significatives.  
  
-   Si les unités de travail des applications n'utilisent pas une relation de type un-à-un, vous pouvez leur appliquer des relations d'activité au lieu d'une continuation, dans le cas où plusieurs expéditions sont prévues pour une même commande par exemple.  
  
-   Lorsque vous envoyez de manière synchrone des données à l'analyse BAM (à l'aide de la classe DirectEventStream) et que l'ID d'activité est propagé à tous les composants concernés, vous n'avez pas besoin d'utiliser la continuation.  
  
-   Si vous envoyez des données de façon asynchrone à l'analyse BAM (à l'aide de la classe BufferedEventStream ou depuis des orchestrations), vous devez utiliser la continuation, même si l'ID d'activité est propagé à tous les composants. Dans ce cas, utilisez un ID d'activité différent dans chaque application en lui ajoutant un préfixe sous la forme d'une chaîne unique (le nom de l'application, par exemple). Cette opération est nécessaire dans la mesure où les données des différentes applications sont susceptibles d'arriver au composant BAM dans un ordre aléatoire et que ce dernier doit masquer les événements arrivant dans le désordre pour garantir des résultats d'interrogation et d'agrégation corrects.  
  
-   La continuation ne vous oblige pas à réécrire vos applications pour qu'elles puissent échanger des données supplémentaires.  
  
## <a name="see-also"></a>Voir aussi  
  
 [Infrastructure dynamique BAM](../core/bam-dynamic-infrastructure.md)   
 [API BAM (exemple BizTalk Server)](../core/bam-api-biztalk-server-sample.md)   
 [BAM de bout en bout (exemple BizTalk Server)](../core/bam-end-to-end-biztalk-server-sample.md)