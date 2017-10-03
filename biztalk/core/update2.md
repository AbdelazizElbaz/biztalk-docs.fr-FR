---
title: "Mise à jour2 | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 770c9ebb-df3a-428f-be18-b36535352f8d
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: a4376cae94e91f462974c626a57170b80b0117ba
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="update"></a>Update
L'élément `Update` permet d'extraire des données d'un événement et de les importer dans l'activité BAM associée.  
  
## <a name="format"></a>Format  
 Pour utiliser le `Update` élément, vous devez fournir un nom de colonne et le type et un **Expression** élément contenant un ou plusieurs **opération** les éléments qui correspondent à une valeur de chaîne unique.  
  
```  
<ic:Update DataItemName="Name" Type="Type">  
  <ic:Expression>  
    <!-- one or more Operation elements -->  
  </ic:Expression>  
</ic:Update>  
```  
  
### <a name="attributes"></a>Attributs  
  
|Nom de l'attribut| Description|  
|--------------------|-----------------|  
|ColumnName|Nom du point de contrôle de l'activité BAM. Il s'agit du point de contrôle qui est mis à jour avec les données extraites.|  
|Type|Type de données BAM du point de contrôle, qui doit être l'une des valeurs suivantes :<br /><br /> -NVARCHAR<br />-DATETIME<br />-INT<br />-FLOAT|  
  
## <a name="remarks"></a>Notes  
 Les opérations suivantes ne sont pas prises en charge dans l'expression `Update` :  
  
-   And  
  
-   Égal à  
  
## <a name="example"></a>Exemple  
 Dans l’exemple suivant, la **GetContextProperty** opération WF est utilisée pour récupérer le **EventTime** propriété. Cette valeur est stockée en tant qu’un **DATETIME** type pour l’élément de données « StartOrderProcessing » pour l’activité BAM.  
  
```  
<ic:Update DataItemName="StartOrderProcessing" Type="DATETIME">  
  <ic:Expression>  
    <wf:Operation Name="GetContextProperty">  
      <wf:Argument>EventTime</wf:Argument>  
    </wf:Operation>  
  </ic:Expression>  
</ic:Update>  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Élément OnEvent de l’intercepteur](../core/interceptor-onevent-element.md)