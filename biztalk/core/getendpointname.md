---
title: GetEndpointName | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c5a06850-ff6d-4fe4-9834-61d14b117391
caps.latest.revision: "14"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 1567f0b4bceb756381c4033f3243ac7a58fda366
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="getendpointname"></a>GetEndpointName
Transmet le nom du point de terminaison d'interception en cours sur la pile.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
<wcf:Operation Name="GetEndpointName" />  
```  
  
#### <a name="parameters"></a>Paramètres  
 Aucun.  
  
## <a name="pushed-value"></a>Valeur transmise  
 Chaîne contenant le nom du point de terminaison d'interception en cours.  
  
## <a name="remarks"></a>Notes  
 Il est important de noter que les applications client et serveur renvoient des noms différents pour le point de terminaison spécifié dans les fichiers App.config.  
  
 Pour les applications clientes, le nom du point de terminaison extrait par l'opération GetEndPointName est au format suivant : nom de liaison, suivi d'un trait de soulignement et du nom du contrat.  
  
 Par exemple, si la propriété nom de ServiceEndpoint n’est pas définie, mais la liaison est définie, le nom défini \< *liaison*> _\<*contrat*>.  
  
 Si le nom et la liaison ne sont pas définies, la propriété Name est fixée \< *contrat*>.  
  
 Pour le service, le nom extrait correspond au nom du point de terminaison spécifié dans le fichier App.config.  
  
## <a name="example"></a>Exemple  
 L'exemple d'expression de filtre suivante définit une interception pour l'opération Réception pour le point d'appel de contrat ServiceRequest du point de terminaison PurchaseOrder_EP. La procédure à suivre est la suivante :  
  
1.  Comparez le nom de l'opération en cours à « Réception » et transmettez le résultat (True ou False) sur la pile.  
  
2.  Comparez le point d'appel de contrat de service en cours à « ServiceRequest » et transmettez le résultat (True ou False) sur la pile. La pile inclut désormais deux valeurs booléennes.  
  
3.  Comparez les résultats des étapes précédentes à l’aide d’une valeur booléenne **et** opération et transmettez le résultat dans la pile. La pile n'inclut désormais qu'une valeur booléenne.  
  
4.  Comparez le point de terminaison en cours à « PurchaseOrder_EP » et transmettez le résultat (True ou False) sur la pile. La pile inclut désormais deux valeurs booléennes.  
  
5.  Enfin, comparez les deux valeurs booléennes sur la pile à l’aide d’une valeur booléenne **et** opération et transmettez le résultat dans la pile. Ces opérations permettent de vérifier le résultat de la comparaison du point de terminaison par rapport à une valeur booléenne : True si le nom de l'opération et le point d'appel de contrat correspondent, False dans le cas contraire.  
  
```  
<ic:Filter>  
  <ic:Expression>  
    <wcf:Operation Name="GetOperationName" />  
    <ic:Operation Name="Constant">  
      <ic:Argument>Receive</ic:Argument>  
    </ic:Operation>  
    <ic:Operation Name="Equals" />  
    <wcf:Operation Name="GetServiceContractCallPoint" />  
    <ic:Operation Name="Constant">  
      <ic:Argument>ServiceRequest</ic:Argument>  
    </ic:Operation>  
    <ic:Operation Name="Equals" />  
    <ic:Operation Name="And" />  
    <wcf:Operation Name="GetEndpointName" />  
    <ic:Operation Name="Constant">  
      <ic:Argument>PurchaseOrder_EP</ic:Argument>  
    </ic:Operation>  
    <ic:Operation Name="Equals" />  
    <ic:Operation Name="And" />  
  </ic:Expression>  
</ic:Filter>  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Opérations dans Windows Communication Foundation](../core/operations-in-windows-communication-foundation.md)