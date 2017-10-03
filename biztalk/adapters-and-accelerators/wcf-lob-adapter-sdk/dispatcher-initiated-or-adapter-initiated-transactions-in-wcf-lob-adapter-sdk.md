---
title: "Configurer les transactions initiée par le répartiteur ou initiée par l’adaptateur avec WCF LOB Adapter SDK | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 85b9ef8d-3922-4838-a41a-32db5e005dc0
caps.latest.revision: "11"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: aa8105b4b6f8eb77d68471faf9b702419f6a1f90
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="configure-dispatcher-initiated-or-adapter-initiated-transactions-with-the-wcf-lob-adapter-sdk"></a>Configurer les transactions initiée par le répartiteur ou initiée par l’adaptateur avec WCF LOB Adapter SDK
## <a name="inbound-transactions"></a>Transactions entrantes  
 Il existe deux méthodes d’implémentation des transactions avec les opérations entrantes : initiée par le répartiteur ou initiée par l’adaptateur. La configuration requise de la carte détermine quelle méthode doit être utilisée. La valeur de la `SupportsTransactedInbound` propriété indique le type de transaction implémentera votre adaptateur.  
  
 Le tableau suivant compare initiée par le répartiteur avec des transactions initiée par l’adaptateur.  
  
|SupportsTransactedInbound|Comportement transactionnel|  
|-------------------------------|----------------------------|  
|True (exécutée par le répartiteur)|-TryReceive est toujours appelée dans le contexte d’une transaction.<br />-La transaction est validée après que le message est renvoyé à l’implémentation de service.<br />-Une nouvelle transaction est créée pour chaque appel de IInputChannel.Receive. Fractionnement d’une transaction entre plusieurs reçoit est dépendante de l’hôte de service et non le développeur d’adaptateur. **Remarque :** si l’hôte n’utilise pas le distributeur WCF (hôte de service) et utilise à la place de programmation de niveau canal, l’hôte doit respecter la **TransactedReceiveEnabled** propriété de la liaison WCF et vous devez effectuer tous les appels à IInputChannel.Receive dans une transaction. **Remarque :** si l’adaptateur utilise des transactions initiée par le répartiteur et est utilisé avec Biztalk Server, définissez la `SupportedInboundChannels` propriété `SupportedInboundChannels.IInputChannel` pour indiquer que l’adaptateur prend en charge les canaux unidirectionnels. Si cela n’est pas défini, BizTalk Server tente d’utiliser des canaux bidirectionnels.|  
|False (initiée par l’adaptateur)|-Le développeur d’adaptateur doit implémenter la logique de transaction au sein de la carte.<br />-Adaptateur initiée par les transactions ne fonctionnent qu’avec un modèle (canal de réponse) de messagerie bidirectionnels.<br />-Une transaction peut s’étendre sur plusieurs messages, étant donné que les clones dépendants seront créés pour chaque message par le répartiteur.|  
  
### <a name="dispatcher-initiated-transactions"></a>Initiée par le répartiteur de Transactions  
 Lorsque SupportsTransactedInbound a la valeur **true**, le distributeur WCF crée alors automatiquement une transaction lorsque vous appelez le **TryReceive** méthode de l’adaptateur et valide la transaction une fois que le message est renvoyé à l’implémentation de service. Ceci ne nécessite pas de toute implémentation de code transactionnel spécifique au sein de l’adaptateur lui suffit d’affecter la `SupportsTransactedInbound` propriété **true**. Toutefois, cela dépend de l’adaptateur hébergé dans un hôte de service qui utilise le répartiteur WCF et se produira pas si vous utilisez la programmation au niveau du canal. Lorsque vous utilisez la programmation au niveau du canal, l’hôte doit respecter le `TransactedReceiveEnabled` propriété de la liaison WCF et assurez-vous que tous les appels à réception d’une transaction.  
  
 L’exemple suivant présente un client de création d’une transaction avant d’appeler l’adaptateur à l’aide de la programmation au niveau du canal.  
  
```csharp  
Message message;  
//Use a new TransactionScope  
using (System.Transactions.TransactionScope tx = new System.Transactions.TransactionScope())  
{  
    message = channel.Receive(TimeSpan.FromMinutes(2));  
    tx.Complete();  
}  
```  
  
### <a name="adapter-initiated-transactions"></a>Initiée par l’adaptateur de Transactions  
 Lorsque le `SupportsTransactedInbound` est définie sur **false**, prise en charge de la transaction doit être implémentée dans le code d’adaptateur en créant une nouvelle transaction. Avant de retourner un message à partir de **TryReceive**, la transaction doit être attachée au message en appelant le **définir** méthode de la **transactionmessageproperty en** classe. Cette implémentation nécessite la prise en charge de la transaction explicite dans le code d’adaptateur et offre un meilleur contrôle sur le comportement transactionnel de l’adaptateur.  
  
 L’exemple suivant présente la création d’une transaction dépendante et cela joindre au message avant d’être retournée au client.  
  
```csharp  
  
Transaction transaction = inboundConnection.CurrentTransaction; //Existing transaction  
DependentTransaction dt = transaction.DependentClone(DependentCloneOption.BlockCommitUntilComplete);  
TransactionMessageProperty.Set(dt, message);  
inboundReply.DependentTransaction = dt; //this will later be closed during Reply processing  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Activités de développement](../../esb-toolkit/development-activities.md)