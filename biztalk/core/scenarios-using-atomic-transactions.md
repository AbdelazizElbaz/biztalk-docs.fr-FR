---
title: "Scénarios à l’aide de Transactions atomiques | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Scope shape [Orchestration Designer], examples
- Scope shape [Orchestration Designer], atomic transactions
- transactions, examples
- transactions, atomic
- atomic transactions, examples
- examples, atomic transactions
ms.assetid: f3481b4e-7e7e-47f0-b8f4-6012a2fc5310
caps.latest.revision: "4"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: e73cfea7a99e2fafbf115a367dbf0840de3369c3
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="scenarios-using-atomic-transactions"></a>Utilisation de transactions atomiques
Les scénarios suivants décrivent l'utilisation des transactions atomiques.  
  
## <a name="scenario-1-an-atomic-transaction-with-com-servicedcomponent"></a>Scénario 1 : Une Transaction atomique avec COM + ServicedComponent  
 L’orchestration suivante montre comment utiliser le **RetryTransactionException** avec des transactions atomiques. Bien qu'il ne soit pas possible d'inclure directement des gestionnaires d'exceptions dans une étendue atomique, cette étendue peut comporter une étendue non transactionnelle possédant un gestionnaire d'exceptions. Le **ServicedComponent** s’inscrit dans la même transaction DTC et toute exception générée par le composant est interceptée et levée à nouveau en tant que **RetryTransactionException**. (Cela suppose que le **réessayer** est définie sur **True** pour l’étendue atomique).  
  
 Notez que l’orchestration aurait été suspendue et l’action de la forme MessageAssignment aurait ont été restaurée même si le **RetryTransactionException** n’est pas levée. Ce modèle, toutefois, permet de renforcer la faculté de récupération de l'application dans laquelle les nouvelles tentatives ont lieu de façon automatique.  
  
 **Une transaction atomique avec COM + ServicedComponent**  
  
 ![Une transaction atomique avec COM &#43; ServicedComponent](../core/media/bts-trans-orch-fig5.gif "BTS_Trans_Orch_Fig5")  
  
## <a name="scenario-2-using-transacted-adapters-with-atomic-transactions"></a>Scénario 2 : Utilisation d’adaptateurs traités avec des Transactions atomiques  
 L'orchestration suivante montre comment utiliser les transactions atomiques avec l'adaptateur SQL. L’ensemble de l’orchestration est marqué comme à long terme avec transactions atomiques individuelles pour les deux éléments de travail logiques : insertion d’un nouveau client et le même ordre d’insertion des détails pour le client.  
  
 Si, pour une raison ou pour une autre, l'insertion de la commande (Order Insert) échoue, l'insertion du client (Customer Insert) doit être annulée. L'exemple utilise l'adaptateur SQL pour faire le travail de la base de données. Comme nous l'avons déjà vu, l'étendue associée à une transaction atomique se termine lorsque le message est envoyé à la base de données MessageBox. Cela implique qu'une fois que le moteur a réussi à envoyer le message dans les étendues Scope_InsertCustomer et Scope_InsertOrder, chaque étendue est validée. L'adaptateur SQL crée une transaction pour l'insertion du client ou la commande.  
  
 Les ports présentent une propriété « Notification d'envoi » pour valider l'envoi du message par le biais du port d'envoi. Lorsque la propriété Notification d'envoi est définie sur « Transmis », un abonnement de réception est placé avant le point de validation transactionnel de l'opération d'envoi. Cependant, dans le cas d'étendues atomiques, l'abonnement de réception est placé dans l'étendue parente englobante.  
  
 Si la transaction SQL InsertOrder échoue, un accusé de réception négatif (ou nack) est renvoyé et la « Scope_InsertOrder » est validée. Une fois que le port d'envoi a épuisé toutes les tentatives configurées, une exception DeliveryFailureException est générée. Cette exception est détectée par le gestionnaire d'exceptions par défaut, qui exécute le processus de compensation par défaut. Les gestionnaires de compensation associés à Scope_InsertCustomer et Scope_InsertOrder sont alors appelés, ce qui annule l'insertion des informations sur le client.  
  
> [!NOTE]
>  L'imbrication des deux étendues en une étendue à long terme et l'appel de la forme Compenser (qui cible la transaction à long terme) à partir du gestionnaire d'exceptions pour l'étendue à long terme aboutissent au résultat décrit ci-dessus. L'ensemble de l'orchestration ne peut pas être indiqué comme étant atomique car les transactions atomiques n'autorisent pas les transactions imbriquées.  
  
 **Adaptateurs traités avec des transactions atomiques**  
  
 ![Transactionnel des cartes avec des transactions atomiques](../core/media/bts-trans-orch-fig6.gif "BTS_Trans_Orch_Fig6")