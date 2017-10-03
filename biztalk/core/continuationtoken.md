---
title: ContinuationToken | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 2d4911fc-c6fb-4628-9177-bd723d4d8ebc
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 54cf9b9326661925f2d55bacd2fb22d02f565f89
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="continuationtoken"></a>ContinuationToken
Un jeton de liaison permet de corréler des informations hétérogènes au sein de l'infrastructure BAM. Prenons l'exemple d'un processus d'entreprise qui construit les types de messages suivants :  
  
-   bon de commande identifié par un numéro de bon de commande ;  
  
-   ordre d'achat identifié par un numéro d'ordre d'achat ;  
  
-   bordereau d'expédition identifié par un numéro de bordereau d'expédition.  
  
 Dans ce processus, il existe trois identificateurs importants : acheter order ID, ID de commande et d’expédition des ID de commande. Chacun de ces identificateurs signale un événement important dans la durée de vie de l’ordre d’origine, mais ils ne peuvent pas être corrélés directement. Pour suivre les événements associés à un bon de commande, les informations communes aux messages doivent être identifiées pour aider l'infrastructure de suivi BAM à corréler les événements avec précision.  
  
## <a name="format"></a>Format  
 Un jeton de liaison est constitué d'un élément d'expression et d'une ou plusieurs opérations :  
  
```  
<ic:ContinuationToken>  
  <ic:Expression>  
    <!-- Operations -->  
  </ic:Expression>  
</ic:ContinuationToken>  
```  
  
## <a name="remarks"></a>Notes  
 Les opérations communes suivantes ne sont pas autorisées dans les expressions ContinuationToken :  
  
-   And  
  
-   Égal à  
  
 [L'en-tête de section des opérations dans WF/WCF doit avoir un graphique similaire et d'autres graphiques au besoin]  
  
## <a name="example"></a>Exemple  
 Dans cet exemple, un jeton de liaison pour un processus WF est extrait du flux de travail à l'aide de `GetWorkflowProperty`. Ici le développeur a décidé de prendre en charge la continuation dans le flux de travail en utilisant du code personnalisé, probablement parce que le processus d'identification du jeton de liaison implique plusieurs expressions et peut reposer sur des données externes.  
  
```  
<ic:ContinuationToken>  
  <ic:Expression>  
    <wf:Operation Name="GetWorkflowProperty">  
      <wf:Argument>ContinuationToken</wf:Argument>  
    </wf:Operation>  
  </ic:Expression>  
</ic:ContinuationToken>  
```  
  
 Vous pouvez choisir d'inclure des fonctionnalités similaires dans vos nouvelles applications WF ou WCF ou, si le jeton est simple à établir à l'aide d'opérations d'expression, vous pouvez éviter d'écrire du code supplémentaire.  
  
 L’exemple suivant établit un jeton de liaison pour un processus WCF à l’aide un **XPath** opération à récupérer le numéro de carte de crédit dans le message actuel et le **constante** et  **concaténer** operations pour ajouter la chaîne « CID_ » au numéro récupéré :  
  
```  
<ic:ContinuationToken>  
  <ic:Expression>  
    <ic:Operation Name="Constant">  
      <ic:Argument>CID_</ic:Argument>  
    </ic:Operation>  
    <wcf:Operation Name="XPath">  
      <wcf:Argument>//Purchase/Payment/CreditCardNumber</wcf:Argument>  
    </wcf:Operation>  
    <ic:Operation Name="Concatenate" />  
  </ic:Expression>  
</ic:ContinuationToken>  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Élément OnEvent de l’intercepteur](../core/interceptor-onevent-element.md)