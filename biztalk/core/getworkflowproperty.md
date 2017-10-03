---
title: GetWorkflowProperty | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c9d3029e-3267-46bc-ba2e-1c6fa1f2e931
caps.latest.revision: "11"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 505fc41ce544cdf16e3826116514ba1991ba012e
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="getworkflowproperty"></a>GetWorkflowProperty
Transmet la propriété extraite de l'activité racine du workflow sur la pile.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
<wf:Operation Name="GetWorkflowProperty">  
      <wf:Argument>Arg1</wf:Argument>  
</wf:Operation>  
```  
  
#### <a name="parameters"></a>Paramètres  
 Nom de la propriété.  
  
## <a name="pushed-value"></a>Valeur transmise  
 Chaîne contenant la valeur de la propriété.  
  
## <a name="remarks"></a>Notes  
 L'opération est uniquement valide dans les mises à jour.  
  
 Vous pouvez utiliser la notation ponctuée pour qualifier le nom de propriété que vous souhaitez extraire. Vous aurez ainsi accès aux objets situés dans d'autres objets exposés via les propriétés. Par exemple, pour accéder à la propriété City d'une instance Address d'un bon de commande, utilisez « purchaseOrder.Address.City ».  
  
 Les noms de propriété respectent d'abord la casse, puis ne la respectent pas. Ce point est important lorsque plusieurs propriétés d'activité de votre application WF varient uniquement au niveau de la casse. Par exemple, si votre application de flux de travail possède les propriétés « myWorkflow » et « MyWorkflow » et que vous recherchez « MyWorkflow », vous obtiendrez comme résultat la deuxième propriété car la casse correspond. Si vous spécifiez « MYWORKFLOW », vous obtiendrez comme résultat la propriété « myWorkflow », qui respecte la casse étant donné que la tentative de non-respect de la casse a échoué.  
  
> [!NOTE]
>  Les valeurs de propriété NULL génèreront le renvoi d'une exception NullReferenceException dans l'instance de flux de travail.  
  
## <a name="example"></a>Exemple  
 Dans l'exemple suivant, une expression de mise à jour permet de rendre la propriété de workflow « City » persistante dans un bon de commande à l'aide de `GetWorkflowProperty`.  
  
```  
<ic:Update DataItemName="City" Type="NVARCHAR">  
  <ic:Expression>  
    <wf:Operation Name="GetWorkflowProperty">  
      <wf:Argument>po.Info.City</wf:Argument>  
    </wf:Operation>  
  </ic:Expression>  
</ic:Update>  
```