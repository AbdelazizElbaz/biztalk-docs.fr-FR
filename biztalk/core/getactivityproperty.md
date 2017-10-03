---
title: GetActivityProperty | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 2321f1ec-d98d-478f-bb1d-a11a98e60fa5
caps.latest.revision: "12"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: a55f0d24da85088fb8f13693c8c71d32bee1bef7
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="getactivityproperty"></a>GetActivityProperty
Transmet la propriété extraite de l'activité associée à l'événement de suivi dans la pile.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
<wf:Operation Name="GetActivityProperty">  
      <wf:Argument>Arg1</wf:Argument>  
</wf:Operation>  
```  
  
#### <a name="parameters"></a>Paramètres  
 Nom de la propriété.  
  
## <a name="return-value"></a>Valeur retournée  
 Chaîne contenant la valeur de la propriété.  
  
## <a name="remarks"></a>Notes  
 Vous pouvez utiliser la notation ponctuée pour qualifier le nom de propriété que vous souhaitez extraire. Vous aurez ainsi accès aux objets situés dans d'autres objets exposés via les propriétés. Par exemple, pour accéder à la propriété City d'une instance Address d'un bon de commande, utilisez « purchaseOrder.Address.City ».  
  
 Les noms de propriété respectent d'abord la casse, puis ne la respectent pas. Ce point est important lorsque plusieurs propriétés d'activité de votre application WF varient uniquement au niveau de la casse. Par exemple, si votre application de flux de travail possède les propriétés « myWorkflow » et « MyWorkflow » et que vous recherchez « MyWorkflow », vous obtiendrez comme résultat la deuxième propriété car la casse correspond. Si vous recherchez « MYWORKFLOW », la recherche avec distinction de casse ne donnera aucun résultat, mais si vous relancez la recherche sans distinction de casse, le résultat « myWorkflow » s'affichera.  
  
 Par exemple, si vous avez deux propriétés de l’activité qui varient uniquement par la casse : « myProperty » et « MyProperty ».  
  
> [!NOTE]
>  Les valeurs de propriété NULL génèreront le renvoi d'une exception NullReferenceException dans l'instance de flux de travail.  
  
## <a name="example"></a>Exemple  
 Dans l'exemple suivant, une expression de mise à jour permet de rendre la propriété d'activité « MyProperty » persistante à l'aide de `GetActivityProperty`.  
  
```  
<ic:Update DataItemName="TextData" Type="NVARCHAR">  
  <ic:Expression>  
    <wf:Operation Name="GetActivityProperty">  
      <wf:Argument>MyProperty</wf:Argument>  
    </wf:Operation>  
  </ic:Expression>  
</ic:Update>  
```