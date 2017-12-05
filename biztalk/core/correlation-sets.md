---
title: "Ensembles de corrélations | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- correlation sets, inspecting
- correlation sets, about correlation sets
- correlation sets, passing as parameters
- messages, correlation sets
- correlation sets
- correlation sets, following correlation sets
- correlation sets, initializing
ms.assetid: 528dcd6c-d364-4bb8-8deb-cd4a0791867f
caps.latest.revision: "11"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 09bad0bf41f5b509f9a64e9484cac84f66a84e4b
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="correlation-sets"></a>Ensembles de corrélations
Vous pouvez réaliser une sorte de corrélation de messages avec des instances d'orchestration en définissant des ensembles de corrélations. Un ensemble de corrélations est un ensemble de propriétés *avec des valeurs spécifiques*. Il ne s'agit pas d'un type de corrélation, qui correspond à une simple liste de propriétés. Si un message entrant ne dispose pas de l'ensemble de ces propriétés, avec des valeurs correspondantes pour chacune d'elles, la corrélation échoue et l'instance d'orchestration ne reçoit pas le message.  
  
 Les types de corrélations définissent un jeu de propriétés sur lesquelles corréler les messages. Il peut s'agir de n'importe laquelle des propriétés précédemment définies dans un schéma de propriété et déployées dans le cadre d'un projet BizTalk, y compris des propriétés « système » déployées avec les schémas GlobalPropertySchemas installés en même temps que l'installation BizTalk de base. Un ensemble de corrélations définit un ensemble de propriétés et de valeurs attribuées à ces propriétés qu'un message doit contenir pour être traité par une orchestration particulière.  
  
 Par exemple, un type de corrélation pourrait se composer des propriétés suivantes :  
  
|Propriété d'un type de corrélation|Représentation XML possible|  
|-------------------------------|---------------------------------|  
|Social Security number|\<SSN\>\</SSN\>|  
|Date of Birth|\<DOB\>\</DOB\>|  
|Gender|\<Sexe\> \< /sexe\>|  
  
 Un ensemble de corrélations dérivé de ce type de corrélation pourrait se composer des propriétés et valeurs suivantes :  
  
|Propriété/valeur de l'ensemble de corrélations|Représentation XML possible|  
|-------------------------------------|---------------------------------|  
|Social Security number = 222112222|\<SSN\>222112222\</SSN\>|  
|Date of Birth = “1/1/1995”|\<DOB\>« 1/1/1995 »\</DOB\>|  
|Gender = Male|\<Sexe\>M \< /sexe\>|  
  
> [!NOTE]
>  Chaque ensemble de corrélations prend en charge un maximum de trois paramètres.  
  
## <a name="initializing-correlation-sets"></a>Propriété Initialisation des ensembles de corrélations  
  
-   **Ensembles de corrélations initialisés lors d’une action de réception**  
  
     Les ensembles de corrélations initialisés lors d'une action de réception définissent l'ensemble exact de propriétés devant figurer dans un message publié afin que ce dernier puisse être traité par les actions de réception correspondantes dans une orchestration. Un ensemble de corrélations initial crée un ensemble de corrélations à partir d'un type de corrélation en fonction des valeurs correspondantes d'un document.  
  
-   **Ensembles de corrélations initialisés lors d’une action d’envoi**  
  
     Les ensembles de corrélations initialisés lors d'une action d'envoi sont créés à partir d'un type de corrélation en fonction des valeurs correspondantes d'un document. Ils promeuvent les propriétés de corrélation dans le document sortant.  
  
## <a name="following-correlation-sets"></a>Propriété Ensembles de corrélations suivants  
 Les ensembles de corrélations suivants ne peuvent être liés qu'à une action d'envoi ou à une action de réception sans activation. Ils sont indiqués par deux avec des ensembles de corrélations précédemment initialisés.  
  
-   **Ensembles de corrélations suivants liés à une action de réception**  
  
     Les ensembles de corrélations suivants liés à une action Réception définissent le jeu de propriétés et de valeurs devant absolument figurer dans le document pour que ce dernier puisse être reçu.  Les actions de réception avec ensembles de corrélations suivants acceptent les documents contenant les propriétés d'un ensemble de corrélations précédemment initialisé.  
  
-   **Ensembles de corrélations suivants liés à une action d’envoi**  
  
     Les ensembles de corrélations suivants liés à une action Envoi indiquent que le jeu de propriétés figurant dans l'ensemble de corrélations est promu dans le document sortant.  
  
## <a name="inspecting-correlation-sets"></a>Inspection des ensembles de corrélations  
 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] permet d'inspecter les ensembles de corrélations. Vous pouvez inspecter un ensemble de corrélations dans une forme Expression à l'aide d'un code similaire à ce qui suit :  
  
```  
MsgLen = Correlation_1(BTS.MessageLength);  
```  
  
 L’exemple ci-dessus part du principe que vous avez créé une variable nommée **MsgLen** de type **System.Int16** et que votre orchestration contienne une corrélation définir nommée **Correlation_1**. Cette possibilité d'inspection des ensembles de corrélations peut se révéler utile lorsque vous avez besoin de vérifier la valeur d'une corrélation transmise entre orchestrations.  
  
## <a name="passing-correlation-sets-as-parameters-to-orchestrations"></a>Transmission d'ensembles de corrélations aux orchestrations en tant que paramètres  
 Vous pouvez transmettre des corrélations en tant que *dans* paramètres vers d’autres orchestrations.