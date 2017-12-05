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
ms.openlocfilehash: d5bb458af94d61ceb89a725f80606d8dda2af579
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="run-a-sqlexecute-operation-in-oracle-database-using-the-wcf-channel-model"></a>Exécuter une opération SQLEXECUTE dans la base de données Oracle à l’aide du modèle de canal WCF
Cette section montre comment effectuer une opération SQLEXECUTE sur une base de données Oracle sur un canal. Vous devez spécifier un message et une action de message sur le message SOAP. Pour plus d’informations sur l’opération SQLEXECUTE, consultez [opération SQLEXECUTE de s’exécuter dans la base de données Oracle à l’aide du modèle de Service WCF](../../adapters-and-accelerators/adapter-oracle-database/run-sqlexecute-operation-in-oracle-database-using-the-wcf-service-model.md).  
  
## <a name="the-sqlexecute-message"></a>Le Message SQLEXECUTE  
 Le code XML suivant affiche un message SQLEXECUTE qui retourne la valeur suivante d’une séquence Oracle.  
  
```  
<?xml version="1.0" encoding="utf-8" ?>  
<!-- New Action: http://Microsoft.LobServices.OracleDB/2007/03/SQLEXECUTE -->  
<SQLEXECUTE xmlns="http://Microsoft.LobServices.OracleDB/2007/03/SQLEXECUTE">  
    <SQLSTATEMENT>SELECT tid_seq.nextval id FROM dual</SQLSTATEMENT>  
</SQLEXECUTE>  
```  
  
 Le SQLEXECUTE peut spécifier un élément de schéma du paramètre et un bloc de paramètres qui contient plusieurs jeux de données du paramètre. Le message indiqué est pour un appel unique de l’instruction SQL spécifiée pour les éléments qui spécifient le bloc de paramètres et le schéma des paramètres sont omis dans le corps du message. Pour plus d’informations sur le schéma de message pour l’opération SQLEXECUTE, consultez [des schémas de Message pour l’opération SQLEXECUTE](../../adapters-and-accelerators/adapter-oracle-database/message-schemas-for-the-sqlexecute-operation.md).  
  
## <a name="specifying-the-sqlexecute-action"></a>Spécification de l’Action SQLEXECUTE  
 Vous devez spécifier une action pour le message. L’extrait de code suivant montre comment spécifier l’action du message SQLEXECUTE.  
  
```  
Message messageIn = Message.CreateMessage(MessageVersion.Default, "http://Microsoft.LobServices.OracleDB/2007/03/SQLEXECUTE", readerIn);  
```  
  
## <a name="sending-the-sqlexecute-message"></a>Envoi du Message SQLEXECUTE  
 L’extrait de code suivant montre comment appeler une opération SQLEXECUTE sur une base de données Oracle sur un canal.  
  
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
>  L’opération SQLEXECUTE toujours retourne un jeu de résultats de faiblement typée.  
  
## <a name="see-also"></a>Voir aussi  
 [Développer des applications de base de données Oracle à l’aide du modèle de canal WCF](../../adapters-and-accelerators/adapter-oracle-database/develop-oracle-database-applications-using-the-wcf-channel-model.md)  
 [Créer un canal à l’aide de la base de données Oracle](../../adapters-and-accelerators/adapter-oracle-database/create-a-channel-using-oracle-database.md)