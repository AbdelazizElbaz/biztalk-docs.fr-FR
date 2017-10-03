---
title: "Nœuds de référence d’URL de document | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Document Reference URL nodes [Tracking Profile Editor]
- Tracking Profile Editor, node descriptions
- definition files [BAM], related documents
ms.assetid: 38c8ae50-ed56-451c-9549-db852d4770e5
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: c7939a7e74483b8df192530fd9da2deafeda0681
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="document-reference-url-nodes"></a>Nœuds Document Reference URL
Il existe, dans le fichier de définition de l'activité, des nœuds Document Reference URL qu'un développeur importe du modèle d'observation créé par le travailleur du savoir. Les nœuds Document Reference URL contiennent des références pour un emplacement où se trouve un document associé à la présente activité. Ce document peut être de n'importe quel type. Par exemple, pour une activité qui représente un flux de travail d'acceptation d'un bon de commande, le nœud Document Reference URL peut pointer vers le document du bon de commande concerné.  
  
## <a name="working-with-document-reference-url-nodes"></a>Utilisation des nœuds Document Reference URL  
 La source de données pour le nœud Document Reference URL est généralement le **MessageRefURL** propriété système BizTalk Server. Vous pouvez également utiliser des schémas personnalisés pour stocker les URL et effectuer un mappage de la propriété vers le nœud Document Reference URL.  
  
 Éléments à prendre en compte pour les nœuds Document Reference URL :  
  
-   Vous pouvez ajouter un ou plusieurs nœuds Document Reference URL, mais chacun d'entre eux doit être doté d'un nom unique dans l'activité.  
  
-   Le **MessageRefURL** propriété requis pour remplir un nœud Document Reference URL n’est remplie avec une valeur dans le cas des adaptateurs de transport WSS, le fichier et FTP.  
  
-   Alors que les utilisateurs finaux peuvent afficher cette référence dans le portail BAM, l’objectif principal de l’URL de référence est de permettre aux développeurs d’interface utilisateur personnalisée accéder à des informations de document associé afin qu’ils peuvent présenter à l’utilisateur final.  Pour plus d’informations sur l’affichage de la référence de document dans le portail BAM, consultez [Documents associés](../core/related-documents.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Nœuds de l’activité TPE](../core/tpe-activity-view-nodes.md)