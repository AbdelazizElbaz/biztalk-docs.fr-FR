---
title: "Exécuter des opérations sur les composants d’entreprise avec l’adaptateur Siebel à l’aide du modèle de canal WCF | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- how to, perform operations using the channel
- performing operations, using the channel
ms.assetid: bae74013-38fa-413c-ba91-4e4ba096339e
caps.latest.revision: "5"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: bf0aa0287eb13f522324080ce97fe357540947cd
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="run-operations-on-business-components-with-the-siebel-adapter-using-the-wcf-channel-model"></a><span data-ttu-id="0ccfd-102">Exécuter des opérations sur les composants d’entreprise avec l’adaptateur Siebel à l’aide du modèle de canal WCF</span><span class="sxs-lookup"><span data-stu-id="0ccfd-102">Run Operations on Business Components with the Siebel adapter using the WCF Channel Model</span></span>
<span data-ttu-id="0ccfd-103">Cette section montre comment effectuer des opérations sur Siebel en utilisant le canal créé dans [créer un canal à l’aide de Siebel](../../adapters-and-accelerators/adapter-siebel/create-a-channel-using-siebel.md).</span><span class="sxs-lookup"><span data-stu-id="0ccfd-103">This section demonstrates how to perform operations on Siebel using the channel created in [Create a Channel using Siebel](../../adapters-and-accelerators/adapter-siebel/create-a-channel-using-siebel.md).</span></span>  
  
```  
// create binding  
SiebelBinding binding = new SiebelBinding();  
  
//set up an endpoint address  
EndpointAddress address = new EndpointAddress("siebel://Username=myuser;Password=mypass@mysiebelserver:1234?SiebelObjectManager=SSEObjMgr&SiebelEnterpriseServer=ent771&Language=enu");  
  
//create request channel factory  
IChannelFactory<IRequestChannel> factory = binding.BuildChannelFactory<IRequestChannel>(new BindingParameterCollection());  
  
//open factory  
factory.Open();  
  
//create request channel using endpoint  
IRequestChannel channel = factory.CreateChannel(address);  
  
//open the channel  
channel.Open();  
  
// send request message and receive reply  
System.Xml.XmlReader readerIn = System.Xml.XmlReader.Create(inputXml);  
System.ServiceModel.Channels.Message messageIn = System.ServiceModel.Channels.Message.CreateMessage(MessageVersion.Default,action,readerIn);  
System.ServiceModel.Channels.Message messageOut = channel.Request(messageIn);  
  
// get response XML from SOAP message  
System.Xml.XmlReader readerOut = messageOut.GetReaderAtBodyContents();  
  
// save output file  
XmlDocument doc = new XmlDocument();  
doc.Load(readerOut);  
doc.Save(outputXml);  
Console.WriteLine("XML written out to {0}", outputXml);  
  
// close the channel and the factory  
channel.Close();  
factory.Close();  
```  
  
## <a name="see-also"></a><span data-ttu-id="0ccfd-104">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="0ccfd-104">See Also</span></span>  
 <span data-ttu-id="0ccfd-105">[Développer des Applications Siebel à l’aide du modèle de canal WCF](../../adapters-and-accelerators/adapter-siebel/develop-siebel-applications-using-the-wcf-channel-model3.md) </span><span class="sxs-lookup"><span data-stu-id="0ccfd-105">[Develop Siebel Applications Using the WCF Channel Model](../../adapters-and-accelerators/adapter-siebel/develop-siebel-applications-using-the-wcf-channel-model3.md) </span></span>  
 [<span data-ttu-id="0ccfd-106">Exécuter des opérations sur les composants d’entreprise avec l’adaptateur Siebel à l’aide du modèle de Service WCF</span><span class="sxs-lookup"><span data-stu-id="0ccfd-106">Run Operations on Business Components with the Siebel adapter Using the WCF Service Model</span></span>](../../adapters-and-accelerators/adapter-siebel/run-operations-on-business-components-with-the-siebel-adapter-using-wcf-service.md)