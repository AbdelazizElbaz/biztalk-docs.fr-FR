---
title: "Exécuter une opération SQLEXECUTE dans la base de données Oracle à l’aide du modèle de canal WCF | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- running a SQLEXECUTE statement, using a channel
- how to, run a SQLEXECUTE statement by using a channel
- WCF channel model, running a SQLEXECUTE statement
ms.assetid: e1af11ef-3f44-4726-99ca-d6961d79e651
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 4c7928affeafd40197401fa75d44658e0e975507
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="run-a-sqlexecute-operation-in-oracle-database-using-the-wcf-channel-model"></a><span data-ttu-id="338ca-102">Exécuter une opération SQLEXECUTE dans la base de données Oracle à l’aide du modèle de canal WCF</span><span class="sxs-lookup"><span data-stu-id="338ca-102">Run a SQLEXECUTE Operation in Oracle Database using the WCF Channel Model</span></span>
<span data-ttu-id="338ca-103">Cette section montre comment effectuer une opération SQLEXECUTE sur une base de données Oracle sur un canal.</span><span class="sxs-lookup"><span data-stu-id="338ca-103">This section shows how to perform a SQLEXECUTE operation on an Oracle database over a channel.</span></span> <span data-ttu-id="338ca-104">Vous devez spécifier un message et une action de message sur le message SOAP.</span><span class="sxs-lookup"><span data-stu-id="338ca-104">You must specify both a message and a message action on the SOAP message.</span></span> <span data-ttu-id="338ca-105">Pour plus d’informations sur l’opération SQLEXECUTE, consultez [opération SQLEXECUTE de s’exécuter dans la base de données Oracle à l’aide du modèle de Service WCF](../../adapters-and-accelerators/adapter-oracle-database/run-sqlexecute-operation-in-oracle-database-using-the-wcf-service-model.md).</span><span class="sxs-lookup"><span data-stu-id="338ca-105">For more information about the SQLEXECUTE operation, see [Run SQLEXECUTE operation in Oracle Database using the WCF Service Model](../../adapters-and-accelerators/adapter-oracle-database/run-sqlexecute-operation-in-oracle-database-using-the-wcf-service-model.md).</span></span>  
  
## <a name="the-sqlexecute-message"></a><span data-ttu-id="338ca-106">Le Message SQLEXECUTE</span><span class="sxs-lookup"><span data-stu-id="338ca-106">The SQLEXECUTE Message</span></span>  
 <span data-ttu-id="338ca-107">Le code XML suivant affiche un message SQLEXECUTE qui retourne la valeur suivante d’une séquence Oracle.</span><span class="sxs-lookup"><span data-stu-id="338ca-107">The following XML shows a SQLEXECUTE message that returns the next value of an Oracle SEQUENCE.</span></span>  
  
```  
\<?xml version="1.0" encoding="utf-8" ?>  
\<!-- New Action: http://Microsoft.LobServices.OracleDB/2007/03/SQLEXECUTE -->  
<SQLEXECUTE xmlns="http://Microsoft.LobServices.OracleDB/2007/03/SQLEXECUTE">  
    <SQLSTATEMENT>SELECT tid_seq.nextval id FROM dual</SQLSTATEMENT>  
</SQLEXECUTE>  
```  
  
 <span data-ttu-id="338ca-108">Le SQLEXECUTE peut spécifier un élément de schéma du paramètre et un bloc de paramètres qui contient plusieurs jeux de données du paramètre.</span><span class="sxs-lookup"><span data-stu-id="338ca-108">The SQLEXECUTE can specify a parameter schema element and a parameter block that contains multiple sets of parameter data.</span></span> <span data-ttu-id="338ca-109">Le message indiqué est pour un appel unique de l’instruction SQL spécifiée pour les éléments qui spécifient le bloc de paramètres et le schéma des paramètres sont omis dans le corps du message.</span><span class="sxs-lookup"><span data-stu-id="338ca-109">The message shown is for a single invocation of the specified SQL statement so the elements that specify the parameter schema and parameter block are omitted from the message body.</span></span> <span data-ttu-id="338ca-110">Pour plus d’informations sur le schéma de message pour l’opération SQLEXECUTE, consultez [des schémas de Message pour l’opération SQLEXECUTE](../../adapters-and-accelerators/adapter-oracle-database/message-schemas-for-the-sqlexecute-operation.md).</span><span class="sxs-lookup"><span data-stu-id="338ca-110">For information about the message schema for the SQLEXECUTE operation, see [Message Schemas for the SQLEXECUTE Operation](../../adapters-and-accelerators/adapter-oracle-database/message-schemas-for-the-sqlexecute-operation.md).</span></span>  
  
## <a name="specifying-the-sqlexecute-action"></a><span data-ttu-id="338ca-111">Spécification de l’Action SQLEXECUTE</span><span class="sxs-lookup"><span data-stu-id="338ca-111">Specifying the SQLEXECUTE Action</span></span>  
 <span data-ttu-id="338ca-112">Vous devez spécifier une action pour le message.</span><span class="sxs-lookup"><span data-stu-id="338ca-112">You must specify an action for the message.</span></span> <span data-ttu-id="338ca-113">L’extrait de code suivant montre comment spécifier l’action du message SQLEXECUTE.</span><span class="sxs-lookup"><span data-stu-id="338ca-113">The following code excerpt shows how to specify the action for the SQLEXECUTE message.</span></span>  
  
```  
Message messageIn = Message.CreateMessage(MessageVersion.Default, "http://Microsoft.LobServices.OracleDB/2007/03/SQLEXECUTE", readerIn);  
```  
  
## <a name="sending-the-sqlexecute-message"></a><span data-ttu-id="338ca-114">Envoi du Message SQLEXECUTE</span><span class="sxs-lookup"><span data-stu-id="338ca-114">Sending the SQLEXECUTE Message</span></span>  
 <span data-ttu-id="338ca-115">L’extrait de code suivant montre comment appeler une opération SQLEXECUTE sur une base de données Oracle sur un canal.</span><span class="sxs-lookup"><span data-stu-id="338ca-115">The following code excerpt demonstrates how to invoke a SQLEXECUTE operation on an Oracle database over a channel.</span></span>  
  
```  
// Create Endpoint  
EndpointAddress address = new EndpointAddress("oracledb://ADAPTER");  
  
// Create Binding  
OracleDBBinding binding = new OracleDBBinding();  
  
// Create Channel Factory  
ChannelFactory<IRequestChannel> factory = new ChannelFactory<IRequestChannel>(binding, address);  
factory.Credentials.UserName.UserName = "SCOTT";  
factory.Credentials.UserName.Password = "TIGER";  
factory.Open();  
  
// Create Request Channel  
IRequestChannel channel = factory.CreateChannel();  
channel.Open();  
  
// Send Request  
System.Xml.XmlReader readerIn = System.Xml.XmlReader.Create("SQLExecute.xml");  
  
Message messageIn = Message.CreateMessage(MessageVersion.Default, "http://Microsoft.LobServices.OracleDB/2007/03/SQLEXECUTE", readerIn);  
Message messageOut = channel.Request(messageIn);  
  
// Get Response XML  
XmlReader readerOut = messageOut.GetReaderAtBodyContents();  
  
// Get tid_seq SEQUENCE  
string id = null;  
XmlDocument doc = new XmlDocument();  
doc.Load(readerOut);  
XmlNodeList list = doc.GetElementsByTagName("ColumnValue");  
if (list.Count > 0) id = list[0].InnerXml;  
```  
  
> [!NOTE]
>  <span data-ttu-id="338ca-116">L’opération SQLEXECUTE toujours retourne un jeu de résultats de faiblement typée.</span><span class="sxs-lookup"><span data-stu-id="338ca-116">The SQLEXECUTE operation always returns a weakly-typed result set.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="338ca-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="338ca-117">See Also</span></span>  
 [<span data-ttu-id="338ca-118">Développer des applications de base de données Oracle à l’aide du modèle de canal WCF</span><span class="sxs-lookup"><span data-stu-id="338ca-118">Develop Oracle Database applications using the WCF Channel Model</span></span>](../../adapters-and-accelerators/adapter-oracle-database/develop-oracle-database-applications-using-the-wcf-channel-model.md)  
 [<span data-ttu-id="338ca-119">Créer un canal à l’aide de la base de données Oracle</span><span class="sxs-lookup"><span data-stu-id="338ca-119">Create a channel using Oracle Database</span></span>](../../adapters-and-accelerators/adapter-oracle-database/create-a-channel-using-oracle-database.md)