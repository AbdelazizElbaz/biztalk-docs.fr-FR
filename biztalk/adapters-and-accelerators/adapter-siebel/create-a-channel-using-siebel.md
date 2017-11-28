---
title: "Créer un canal à l’aide de Siebel | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- channel programming, creating a channel
- how to, create a channel
- creating a channel
ms.assetid: 5587cf51-7101-4035-b958-3fe070ba6252
caps.latest.revision: "4"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 87524160550cfe84c5e7e94efba1e44bff20c6ca
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="create-a-channel-using-siebel"></a><span data-ttu-id="2165f-102">Créer un canal à l’aide de Siebel</span><span class="sxs-lookup"><span data-stu-id="2165f-102">Create a channel using Siebel</span></span>
<span data-ttu-id="2165f-103">Cette section montre comment créer un canal pour la messagerie directe avec Siebel à fournir et de consommer des messages XML.</span><span class="sxs-lookup"><span data-stu-id="2165f-103">This section demonstrates how to create a channel for direct messaging with Siebel by providing and consuming XML messages.</span></span>  
  
```  
//create a channel factory, capable of sending a request to Siebel and receiving a reply (IRequestChannel)  
IChannelFactory<IRequestChannel> factory = binding.BuildChannelFactory<IRequestChannel>(new BindingParameterCollection());  
  
//open factory  
factory.Open();  
  
//obtain a channel from the factory by specifying the address you want to connect to  
IRequestChannel irc = factory.CreateChannel(address);  
  
//open the channel  
irc.Open();  
  
//perform operations  
…………  
…………  
…………  
  
//close the channel  
irc.Close();  
  
//close the factory  
factory.Close();  
```  
  
 <span data-ttu-id="2165f-104">Une fois que vous avez créé le canal, vous pouvez utiliser ce canal pour effectuer des opérations sur Siebel.</span><span class="sxs-lookup"><span data-stu-id="2165f-104">Once you have created the channel, you can use that channel to perform operations on Siebel.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2165f-105">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="2165f-105">See Also</span></span>  
 <span data-ttu-id="2165f-106">[Développer des Applications Siebel à l’aide du modèle de canal WCF](../../adapters-and-accelerators/adapter-siebel/develop-siebel-applications-using-the-wcf-channel-model3.md) </span><span class="sxs-lookup"><span data-stu-id="2165f-106">[Develop Siebel Applications Using the WCF Channel Model](../../adapters-and-accelerators/adapter-siebel/develop-siebel-applications-using-the-wcf-channel-model3.md) </span></span>  
 [<span data-ttu-id="2165f-107">Exécuter des opérations sur les composants d’entreprise avec l’adaptateur Siebel à l’aide du modèle de canal WCF</span><span class="sxs-lookup"><span data-stu-id="2165f-107">Run Operations on Business Components with the Siebel adapter using the WCF Channel Model</span></span>](../../adapters-and-accelerators/adapter-siebel/run-tasks-on-business-components-with-the-siebel-adapter-using-a-wcf-channel.md)