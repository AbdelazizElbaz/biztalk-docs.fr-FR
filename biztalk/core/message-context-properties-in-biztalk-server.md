---
title: "Utilisez les propriétés de contexte de message TIBCO EMS | Documents Microsoft"
description: Utilisez les champs de descripteur de message TIBCO Enterprise Message System dans une orchestration BizTalk Server
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 163ac2cf-0e2d-4780-b398-baa825f92b00
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 5433e454d161c77ac140167e9af082eaee7c2032
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="message-context-properties-in-tibco-ems"></a>Propriétés de contexte de message TIBCO EMS

## <a name="tibcoemspropertiesdll"></a>TibcoEMSProperties.dll
Pour accéder aux champs de descripteur de message TIBCO Enterprise Message System à partir d’une orchestration BizTalk Server, vous devez ajouter une référence à **Microsoft.BizTalk.Adapters.TibcoEMSProperties.dll** à votre projet. Cet assembly se trouve dans  **\<TIBCO EMS_Adapter_installation_directory\>\bin**. Après avoir référencé ce schéma de propriété TIBCO EMS, vous pouvez accéder à des propriétés de contexte supplémentaires à l'aide de différents outils de développement BizTalk Server (par exemple, la forme Assignation de message dans le Concepteur d'orchestration).  
  
## <a name="access-context-properties"></a>Accéder aux propriétés de contexte  
 Pour accéder à une propriété de contexte, spécifiez une des propriétés de contexte disponibles dans l'espace de noms TIBCO EMS. Pour lire la propriété de contexte d'un message reçu à partir d'un port lié à l'adaptateur BizTalk pour TIBCO EMS, utilisez la syntaxe suivante dans une expression :  
  
```  
Message(TibcoEMS.Property)  
```  
  
 Pour plus d’informations, consultez [propriétés de descripteur de Message TIBCO Enterprise Message Service](../core/tibco-enterprise-message-service-message-descriptor-properties.md).  
  
 Dans BizTalk Server, les messages sont immuables. C'est pourquoi, pour affecter une valeur de propriété de contexte à un message, créez un message, définissez son contenu (par exemple, en lui affectant un message existant) puis les propriétés dont vous avez besoin.  
  
 Pour affecter des propriétés de contexte TIBCO EMS à un message destiné à un port d'envoi lié à l'adaptateur BizTalk pour TIBCO EMS, utilisez l'opérateur d'affectation du message et spécifiez l'une des propriétés de contexte disponibles dans l'espace de noms TIBCO EMS. La syntaxe de base est la suivante :  
  
```  
Message(TibcoEMS.Property) = value;  
```  
  
## <a name="next-steps"></a>Étapes suivantes
-   [Les valeurs et les propriétés du descripteur de Message TIBCO EMS](../core/tibco-enterprise-message-service-message-descriptor-properties.md)  
  
-   [Didacticiel : Utiliser les propriétés du contexte de message](../core/tutorial-using-message-context-properties.md)