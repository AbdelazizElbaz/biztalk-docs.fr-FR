---
title: "Fonctionnement de l’exemple de Namespace supprimer | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: bf5834b4-e0fd-4180-9d15-4cdd99f0f353
caps.latest.revision: "2"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: e82e4f369d8db2230b44586cbb928ea57b27f462
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-the-remove-namespace-sample-works"></a>Fonctionnement de l’exemple de Namespace supprimer
Les tests de la deuxième et troisième utilisent le **supprimer le Namespace** composant se trouve dans le **NamespaceSampleSendPipeline** pipeline. Il prend comme entrée un document avec un espace de noms sur le nœud racine, telle que la suivante :  
  
```  
<ns0:CanonicalOrder OrderID="OrderID_0" OrderDate="OrderDate_1"   
    Status="Status_2"   
    xmlns:ns0="http://schemas.microsoft.biztalk.esb.test.com/test">  
```  
  
 Le **supprimer le Namespace** composant simplement supprime cet espace de noms et renvoie un document qui ne dispose pas d’un espace de noms de nœud racine, comme illustré ici :  
  
```  
<CanonicalOrder OrderID="OrderID_0" OrderDate="OrderDate_1" Status="Status_2">  
```