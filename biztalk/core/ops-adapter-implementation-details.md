---
title: "Détails d’implémentation adaptateur OPS | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- batching, Ops adapters
- Ops adapters, batching
- Ops adapters, creating ports
- Ops adapters, implementing
- Ops adapters, transaction handling
- process management solution tutorial, Ops adapters
ms.assetid: dbca31ca-c3d8-4a25-9356-ef4bbab671e1
caps.latest.revision: "11"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 5d68a55ce0f6eba835313075e8ab3753ec825db2
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="ops-adapter-implementation-details"></a>Détails de l'implémentation de l'adaptateur Ops
La compréhension des aspects suivants de l'adaptateur Ops peut s'avérer utile lors de la modification de l'adaptateur ou de sa configuration par programme.  
  
> [!NOTE]
>  L'adaptateur Ops est créé à l'aide de l'infrastructure d'adaptateurs. Pour plus d’informations sur la création de cartes avec l’infrastructure, consultez [développement des adaptateurs personnalisés](../core/developing-custom-adapters.md).  
  
## <a name="batch-processing"></a>Traitement par lots  
 L'adaptateur traite un message à la fois de manière à ce que chaque message soit traité séparément, et les opérations de restauration sont effectuées sur une commande à la fois. Bien que l'adaptateur traite un message à la fois, il effectue cette opération à l'aide du traitement par lot avec une taille de lot égale à un. Cela simplifie la modification de l'adaptateur de manière à ce qu'il traite les messages par lots.  
  
## <a name="transaction-handling"></a>Gestion des transactions  
 L’adaptateur utilise les fonctionnalités de transaction fournies par Microsoft [!INCLUDE[btsDotNetFramework](../includes/btsdotnetframework-md.md)] **System.Transactions** installations. L’adaptateur crée un nouveau **CommittableTransaction** et l’utilise avec un **TransactionScope**. L’adaptateur appelle la **initialiser** et **Execute** méthodes dans le cadre de cette transaction. Code de l’assembly appelé peut participer à la transaction à l’aide de **Transaction.Current** une méthode statique pour obtenir le contexte de transaction. L'exemple de gestionnaire d'erreurs n'exploite pas cette fonction. Pour plus d’informations sur **System.Transactions**, consultez « System.Transactions Namespace » dans la version de la bibliothèque de classes .NET Framework.  
  
## <a name="handling-data-other-than-error-reports"></a>Traitement de données autres que des rapports d'erreurs  
 Dans la solution, l'adaptateur gère les messages des rapports d'erreurs grâce à la nouvelle fonctionnalité de signalement d'erreurs. Toutefois, étant donné que la **Execute** méthode prend un tableau d’octets comme seul argument, rien ne spécifiquement limite ce qui peut être passé à la **Execute** (méthode).  
  
## <a name="using-the-adapter-when-creating-ports-programmatically"></a>Utilisation de l'adaptateur lors de la création de ports par programme  
 Vous pouvez spécifier un adaptateur lors de la création de ports à partir d'un code. Le tableau suivant illustre les noms des propriétés personnalisées et la manière dont elles correspondent à leur nom complet.  
  
|Nom de la propriété personnalisée d'envoi|Nom complet|  
|-------------------------------|------------------|  
|**DotNetAssemblyStrongName**|**DotNetAssemblyStrongName**|  
|**DotNetClassName**|**DotNetClassName**|  
|**InitializationData**|**InitializationData**|  
|**TransportLocationUri**|Non applicable.|  
  
 Toutes les propriétés renvoient des valeurs de chaîne. Vous construisez la valeur de la propriété TransportLocationUri à partir du nom de l'assembly et du nom de la classe. L’URI a la valeur OPS : / /\<DotNetAssemblyStrongName > /\<DotNetClassName > où les espaces réservés sont remplacés par les valeurs de la propriété personnalisée correspondante.  
  
 Pour plus d’informations sur la création de ports à partir de code, consultez [comment créer des emplacements de réception MSMQ et les Ports d’envoi à partir de Code](../core/how-to-create-msmq-receive-locations-and-send-ports-from-code.md).  
  
## <a name="see-also"></a>Voir aussi  
 [L’adaptateur Ops](../core/the-ops-adapter.md)