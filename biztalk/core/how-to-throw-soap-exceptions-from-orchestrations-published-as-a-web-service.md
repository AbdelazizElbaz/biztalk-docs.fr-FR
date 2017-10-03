---
title: "Levée des Exceptions SOAP à partir d’Orchestrations publiées en tant qu’un Service Web | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- errors, SOAP exceptions
- orchestrations, SOAP errors
- Web services, orchestrations
ms.assetid: e1c7cd74-d1c8-4b9d-a418-4601b1f040d7
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: d4ef3d975632b6230cf1e3df299d0d9455f39da0
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-throw-soap-exceptions-from-orchestrations-published-as-a-web-service"></a>Levée des Exceptions SOAP à partir d’Orchestrations publiées en tant qu’un Service Web
Vous pouvez renvoyer une exception SOAP à partir d'une orchestration publiée en tant que service Web. Vous ajoutez un message d'erreur à votre port SOAP et l'envoyez à la place de la réponse.  
  
### <a name="to-throw-a-soap-exception-from-an-orchestration-published-as-a-web-service"></a>Pour lever une exception SOAP à partir d'une orchestration publiée en tant que service Web  
  
1.  Ajoutez un message d'erreur au type de port SOAP. Le type du message d'erreur peut être tout type simple ou de schéma compatible XDS (XML Schema).  
  
    > [!NOTE]
    >  Pour retourner une chaîne comme un **SoapException** avec les informations d’erreur, vous pouvez utiliser la chaîne de type simple en tant que le type de message d’erreur.  
  
2.  Dans votre orchestration, créez le message d'erreur.  
  
3.  Utilisez le **envoyer** forme à lier à l’opération d’erreur dans le port SOAP qui correspond au message d’erreur. Une exception SOAP enveloppe le message d'erreur renvoyé.  
  
 Si votre orchestration ne retourne pas d’erreur, utilisez une autre **envoyer** forme pour envoyer le message de réponse SOAP standard à l’aide de l’opération de réponse habituel.  
  
## <a name="see-also"></a>Voir aussi  
 [Messages d’erreur](../core/fault-messages.md)   
 [Publication d’une Orchestration en tant que Service Web](../core/publishing-an-orchestration-as-a-web-service.md)