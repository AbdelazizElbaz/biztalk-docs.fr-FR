---
title: AutoGenerateCorrelationToken | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a24357c9-34e5-4caa-b41c-19551cfe81f9
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 2e396fd0b2c6153a5252d336b9af9c22bf9421fd
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="autogeneratecorrelationtoken"></a>AutoGenerateCorrelationToken
Génère automatiquement un jeton de corrélation et le place sur la pile.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
<wcf:Operation Name="AutoGenerateCorrelationToken" />  
```  
  
#### <a name="parameters"></a>Paramètres  
 Aucun.  
  
## <a name="pushed-value"></a>Valeur transmise  
 Chaîne contenant le jeton de corrélation.  
  
## <a name="remarks"></a>Notes  
 Vous pouvez utiliser cette opération quand le message ne contient aucun jeton de corrélation, mais que vous voulez néanmoins corréler les informations d'une demande et d'une réponse. Vous pouvez les utiliser pour corréler une requête-réponse particulière du côté client ou service.  
  
> [!NOTE]
>  Si vous voulez corréler les données collectées par la requête et la réponse pour le client et le service (continuation), vous devez utiliser un ou plusieurs éléments de données de votre message.  
  
## <a name="example"></a> Exemple  
 L'exemple suivant d'expression de corrélation dépend de `AutoGenerateCorrelationToken` pour générer un jeton de corrélation.  
  
```  
<ic:CorrelationID>  
  <ic:Expression>            
    <wcf:Operation Name="AutoGenerateCorrelationToken"/>  
  </ic:Expression>  
</ic:CorrelationID>  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Opérations dans Windows Communication Foundation](../core/operations-in-windows-communication-foundation.md)