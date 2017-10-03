---
title: "Spécification des Actions SOAP pour WCF des adaptateurs d’envoi | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- send adapters, mapping
- send adapters, WCF services
- mapping, send adapters
- mapping, WCF send adapters
ms.assetid: fa9878eb-65b5-4ccc-b727-ff7e09ba6302
caps.latest.revision: "14"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 385e92f7801dc2512fbd038bd0b005d95c503e57
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="specifying-soap-actions-for-wcf-send-adapters"></a>Spécification des actions SOAP pour les adaptateurs d'envoi WCF
Vous pouvez définir le **WCF. Action** propriété de contexte dans la boîte de dialogue Propriétés du transport WCF envoi carte ou dans l’orchestration **Expression** formes. Si vous définissez la **WCF. Action** propriété de contexte de l’orchestration, vous devez laisser la **Action** champ vide dans la boîte de dialogue Propriétés WCF adaptateur transport pour les ports d’envoi statiques. Si vous spécifiez également une action dans les ports d’envoi statiques, le **WCF. Action** propriété de contexte que vous définissez dans l’orchestration sera remplacée.  
  
 En outre, il existe deux façons de spécifier cette propriété : le format d’action unique et le format de mappage d’action. Si vous définissez cette propriété dans le format d'action unique (par exemple, http://MyService/IMyContract/MyAction1), l'action SOAP dans la boîte de dialogue Propriétés du transport de l'adaptateur WCF pour les messages sortants est toujours définie sur la valeur spécifiée dans cette propriété. Vous pouvez également définir le format d’action unique dans l’orchestration **Expression** forme. Par exemple :  
  
```  
OutboundMessage(WCF.Action)="http://MyService/IMyContract/MyAction1";  
```  
  
 Si vous définissez cette propriété dans le format de mappage d’action, l’action SOAP sortante est déterminée par le **BTS. Opération** propriété de contexte. Par exemple, si cette propriété est définie au format XML suivant dans WCF envoyer la boîte de dialogue Propriétés du transport adaptateur et le **BTS. Opération** est définie sur **Operation_1** du port d’envoi dans l’orchestration, l’adaptateur d’envoi WCF utilise http://MyService/IMyContract/MyAction1 pour l’action SOAP sortante.  
  
```  
BtsActionMapping xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:xsd="http://www.w3.org/2001/XMLSchema">  
<Operation Name="Operation_1" Action="http://MyService/IMyContract/MyAction1" />  
<Operation Name="Operation_2" Action="http://MyService/IMyContract/MyAction2" />  
<Operation Name="Operation_3" Action="http://MyService/IMyContract/MyAction3" />  
</BtsActionMapping>  
```  
  
 Spécification du mappage d’action pour **WCF. Action** dans un **Expression** forme n’est pas pris en charge. Vous devez spécifier le mappage d'action dans la boîte de dialogue Propriétés du transport WCF. Ensuite, l’adaptateur WCF recherche l’action SOAP à l’aide de la **BTS. Opération** la propriété de contexte, l’orchestration définit le nom de l’opération sur le port sur lequel le message est envoyé.  
  
 Si les messages sortants sont acheminés avec le routage basé sur le contenu (CBR) où le **http://schemas.microsoft.com/BizTalk/2003/system-properties#Operation** propriété n’est pas définie, les adaptateurs d’envoi WCF définira le mappage d’action entier chaîne à l’action des messages WCF sortants. Pour contourner ce problème, vous pouvez effectuer une des opérations suivantes :  
  
-   définir le champ Action sur le port d'envoi sur http://MyService/IMyContract/MyAction1 ;  
  
-   Définir le **BTS. Opération** propriété de contexte dans un pipeline. Par exemple, définir la valeur de **http://schemas.microsoft.com/BizTalk/2003/system-properties#Operation** sur Operation1.  
  
-   laisser vierge le champ Action et utiliser l'action du message entrant à la place.  
  
 Vous pouvez également utiliser l'Assistant Consommation de service WCF BizTalk pour utiliser les services WCF avec l'action unique ou le mappage d'action. Pour plus d’informations, consultez [l’utilisation de l’Assistant de consommation de Service WCF BizTalk pour utiliser un Service WCF](../core/how-to-use-the-biztalk-wcf-service-consuming-wizard-to-consume-a-wcf-service.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Configuration des Ports d’envoi dynamiques à l’aide des propriétés de contexte des adaptateurs WCF](../core/configuring-dynamic-send-ports-using-wcf-adapters-context-properties.md)