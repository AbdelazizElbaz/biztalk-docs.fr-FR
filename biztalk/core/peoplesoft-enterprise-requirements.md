---
title: Configuration requise de PeopleSoft Enterprise | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- PeopleSoft Enterprise, requirements
- send handlers, PeopleSoft requirements
- CLASSPATH environment variable
- custom component interface object
- system requirements
- GET_CI_INFO.pc
ms.assetid: fabd808d-d9b6-43b0-a12a-727189f00a9d
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 45f267afce09e9c50d732d376fde43beaa1ef39a
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="peoplesoft-enterprise-requirements"></a>Configuration requise de PeopleSoft Enterprise
## <a name="send-handler-peoplesoft-requirements"></a>Configuration requise de PeopleSoft relative aux gestionnaires d'envoi  
 L'adaptateur Microsoft BizTalk pour PeopleSoft Enterprise inclut une interface de composant personnalisée accessible via une API Java. Un objet interface de composant personnalisée (`GET_CI_INFO`) est déployé dans le système PeopleSoft à l'aide des outils PeopleSoft pour fournir les informations de métadonnées requises par l'adaptateur BizTalk pour PeopleSoft Enterprise. Pour plus d’informations, consultez [préparation de l’utilisation de PeopleSoft Enterprise](../core/preparing-to-use-peoplesoft-enterprise.md).  
  
 Téléchargement de l’interface de composant personnalisée est une occurrence unique. Installé avec le produit, ce fichier (`GET_CI_INFO.pc`) doit être installé avant d'utiliser l'adaptateur pour explorer les interfaces de composant. Vous devez disposer d'un accès au Concepteur d'applications PeopleSoft. Il n'est toutefois pas nécessaire que l'application du Concepteur d'applications se trouve sur l'ordinateur BizTalk Server. Le Concepteur d'applications permet de télécharger l'interface de composant personnalisée sur l'ordinateur PeopleSoft que vous utilisez.  
  
 Vous devez avoir accès à l’ordinateur PeopleSoft, car vous devez définir la variable d’environnement CLASSPATH (ou définir les informations dans le **propriétés du Transport** écran) pour pointer vers de PeopleSoft `PSJOA/psjoa.jar` fichier.  
  
## <a name="see-also"></a>Voir aussi  
 [Prise en main](../core/getting-started-with-biztalk-adapter-for-peoplesoft-enterprise.md)   
 [Planification et Architecture](../core/planning-and-architecture13.md)