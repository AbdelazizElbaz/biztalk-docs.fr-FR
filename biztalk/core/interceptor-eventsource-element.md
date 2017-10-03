---
title: "Élément EventSource de l’intercepteur | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d78846c1-3984-43af-a13f-9d5c0a66d3b5
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 35b5cd6b2e872f689988f3d10d18df002f66d6a0
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="interceptor-eventsource-element"></a>Élément EventSource de l'intercepteur
Le **EventSource** élément fournit des informations sur la source d’un ou plusieurs des événements qui apparaissent dans le fichier de configuration de l’intercepteur. Outre un nom de source d'événements, vous devez indiquez la technologie ainsi qu'un manifeste pour la source.  
  
## <a name="format"></a>Format  
 L'élément `EventSource` dispose de trois attributs et peut comporter des éléments enfants selon l'élément incluant les schémas. Par exemple, le schéma WCF WcfInterceptorConfiguration.xsd propose l'élément `NamespaceMapping`.  
  
### <a name="attributes"></a>Attributs  
  
|Nom de l'attribut| Description|  
|--------------------|-----------------|  
|Nom|Nom de cette source d'événements. Ce nom est utilisé par **OnEvent** entrées pour faire référence à la source.|  
|Technologie|Type de technologie hébergeant la source d'événements indiquée dans le manifeste. Indiquez « WF » pour Windows Workflow Foundation et « WCF » pour Windows Communication Framework.|  
|Manifeste|Nom de classe qualifié pour les assemblys du type à utiliser comme source d'événements. Par exemple, `TopNamespace.SubNameSpace.ContainingClass+NestedClass, MyAssembly, Version=1.3.0.0, Culture=neutral, PublicKeyToken=b17a5c561934e08`<br /><br /> Si vous ne disposez pas de jeton de clé publique, utilisez `PublicKeyToken=null`.|  
  
## <a name="example"></a>Exemple  
 L’exemple suivant contient deux **EventSource** éléments, un ciblant WF et l’autre ciblant WCF.  
  
```  
<!-- WF -->  
<ic:EventSource Name="OrderWorkflow" Technology="WF" Manifest="SimpleWorkflow.OrderWorkflow, SimpleWorkflow, Version=0.0.0.0, Culture=neutral, PublicKeyToken=null"/>  
<!-- WCF -->  
<ic:EventSource Name="PurchaseService" Technology="WCF" Manifest="Service.IProcessPOContract, DuplexService, Version=1.0.0.0, Culture=neutral, PublicKeyToken=null"/>  
```