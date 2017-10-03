---
title: "Appel des règles d’entreprise dans les Orchestrations | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Call Rules shape [Orchestration Designer], business rules
- business rules, orchestrations
- Call Rules shape [Orchestration Designer], policies
- policies, Call Rules shape [Orchestration Designer]
- orchestrations, business rules
ms.assetid: ac3a3277-e9ea-4f40-9326-c63076c6b90e
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 77ecbb9738089dfa2d885f9aa45ac12e92ed27aa
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="invoking-business-rules-in-orchestrations"></a>Appel des règles d’entreprise dans les Orchestrations
Vous pouvez appeler une stratégie (ou un ensemble de règles) à partir d’une orchestration à l’aide de la **appeler règles** forme. La stratégie appelle le moteur des règles, qui agit sur les règles de la stratégie.  
  
 En plus des règles d’appel, les règles de moteur peut être appelé par programme à partir de l’expression de code, par exemple, dans un **Expression** ou **assignation du Message** forme. Pour plus d’informations sur l’exécution de stratégies par programme, consultez [comment exécuter les stratégies](../core/how-to-execute-policies.md).  
  
 Cette section décrit les informations de configuration et les procédures requises pour appeler et exécuter une stratégie commerciale à partir d'une orchestration BizTalk.  
  
## <a name="in-this-section"></a>Dans cette section  
  
-   [Informations de configuration](../core/configuration-information.md)  
  
-   [L’utilisation de la forme Appeler règles](../core/how-to-use-the-call-rules-shape.md)