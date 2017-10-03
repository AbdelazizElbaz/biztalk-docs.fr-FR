---
title: "Référence | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b916c55a-c84c-4008-8927-f8e584c36fe9
caps.latest.revision: "14"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: f3e32145e2340a4d86a6893db3e9209b79c2b5e7
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="reference"></a>Référence
Le **référence** élément peut être utilisé pour ajouter une ou plusieurs relations à une activité BAM. Cela s'avère utile lorsque vous souhaitez associer un pointeur tel qu'une clé primaire, un ID ou une URL à un message lui correspondant. Par exemple, vous voulez peut-être stocker une référence à un lot d'expéditions d'une activité Purchase Order.  
  
## <a name="format"></a>Format  
 Le `Reference` élément prend en charge à la fois le **données** et **LongData** des éléments enfants qui contiennent une expression spécifiant les données à associer à l’activité BAM. Vous pouvez utiliser n’importe quelle combinaison de **données** et **LongData** pour répondre à vos exigences de suivi.  
  
### <a name="attributes"></a>Attributs  
  
|Nom de l'attribut| Description|  
|--------------------|-----------------|  
|Nom|Nom de la relation à associer à l'activité BAM.|  
|Type|Chaîne arbitraire spécifiant le type de relation à associer à l'activité BAM. Les chaînes arbitraires et les types BAM prédéfinis suivants sont pris en charge :<br /><br /> -BizTalkService<br />-MessageID<br />-Activité<br />-DocumentUrl<br />-InstanceID<br /><br /> Pour plus d’informations sur les types de référence BAM prédéfinis, consultez [propriétés de la référence](http://go.microsoft.com/fwlink/?LinkId=119601).|  
  
### <a name="child-elements"></a>Éléments enfants  
  
|État de l'exécution| Description|  
|----------------------|-----------------|  
|data|Indique le mode d'extraction des données de chaîne (jusqu'à 128 caractères) qui seront associées à l'activité BAM.|  
|LongData|Indique le mode d'extraction des données de chaîne longue arbitraire qui seront associées à l'activité BAM.|  
  
> [!NOTE]
>  A `Reference` élément peut combiner un ou plusieurs **données** et **LongData** des éléments enfants en fonction des besoins.  
  
## <a name="remarks"></a>Notes  
 Les opérations communes suivantes ne sont pas autorisées dans les expressions Reference :  
  
-   And  
  
-   Égal à  
  
## <a name="example"></a>Exemple  
 Dans l'exemple suivant, une référence intitulée « Related Document » du type « DocumentUrl » est créée à l'aide de l'opération `GetUserData` pour un workflow. Compte tenu que la longueur attendue des données utilisateur doit être inférieure à 1 024 caractères, l'élément `Data` est utilisé pour contenir l'élément `Expression`.  
  
```  
<ic:Reference Name="Related Document" Type="DocumentUrl">  
  <ic:Data>  
    <ic:Expression>  
      <wf:Operation Name="GetUserData" />  
    </ic:Expression>  
  </ic:Data>  
</ic:Reference>  
```  
  
 Le **référence** élément prend en charge un mélange de `Data` et `LongData` éléments. Dans l'exemple suivant, les champs relatifs au nom du pays et aux remarques d'un bon de commande sont récupérés à partir d'un service WCF, puis ils sont écrits dans la relation « Long and Short Data » comme le type « MyType ». Étant donné que la longueur prise en charge dans le champ de remarques est supérieure à 1 024 caractères, l'expression est intégrée à un élément `LongData`.  
  
```  
<ic:Reference Name="Long and Short Data" Type="MyType">  
  <ic:Data>  
    <ic:Expression>  
      <ic:Operation Name="Constant">  
        <ic:Argument>Country: </ic:Argument>  
      </ic:Operation>  
      <wcf:Operation Name="XPath">  
        <wcf:Argument>//s:Body//po:Country</wcf:Argument>  
      </wcf:Operation>  
       <ic:Operation Name="Concatenate" />  
    </ic:Expression>  
  </ic:Data>  
  <ic:LongData>  
    <ic:Expression>  
      <ic:Operation Name="Constant">  
        <ic:Argument>Note: </ic:Argument>  
      </ic:Operation>  
      <wcf:Operation Name="XPath">  
        <wcf:Argument>//s:Body//po:Note</wcf:Argument>  
      </wcf:Operation>  
      <ic:Operation Name="Concatenate" />  
    </ic:Expression>  
  </ic:LongData>  
</ic:Reference>  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Élément OnEvent de l’intercepteur](../core/interceptor-onevent-element.md)   
 [Méthode EventStream.AddRelatedActivity](http://go.microsoft.com/fwlink/?LinkId=119602)