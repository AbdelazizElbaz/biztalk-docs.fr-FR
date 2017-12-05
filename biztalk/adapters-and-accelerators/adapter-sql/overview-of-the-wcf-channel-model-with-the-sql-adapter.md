---
title: "Vue d’ensemble du modèle de canal WCF avec l’adaptateur SQL | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a5e5f77c-c922-4039-92c7-38d2b7638459
caps.latest.revision: "11"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: ad124e7ce9fdf8c3dac6a1ac0ffda122127becb9
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="overview-of-the-wcf-channel-model-with-the-sql-adapter"></a>Vue d’ensemble du modèle de canal WCF avec l’adaptateur SQL
Pour appeler des opérations sur le [!INCLUDE[adaptersql](../../includes/adaptersql-md.md)], votre code se comporte comme un client WCF et envoie les opérations sortantes à l’adaptateur. Dans le modèle de canal WCF, votre code appelle les opérations sur la carte en envoyant un message de demande sur un canal.  
  
 Pour recevoir des messages modification de données reposant sur l’interrogation à l’aide de l’adaptateur, votre code se comporte comme un service WCF et reçoit le trafic entrant **d’interrogation**, **TypedPolling**, ou **Notification**opération à partir de l’adaptateur. En d’autres termes, votre code reçoit un message de demande pour les opérations de l’adaptateur sur un canal.  
  
 Les rubriques de cette section fournissent une vue d’ensemble de l’utilisation de la [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] avec le modèle de canal WCF.  
  
## <a name="wcf-channel-model-overview"></a>Vue d’ensemble du modèle de canal WCF  
 Les services et les clients communiquent en échangeant des messages SOAP. Le modèle de canal WCF est une abstraction de bas niveau de l’échange de messages. Il fournit des interfaces et des types qui vous permettent d’envoyer et recevoir des messages à l’aide d’une pile de protocole en couche appelée une pile de canaux. Chaque couche de la pile est composé d’un canal, et chaque canal est créé à partir d’une liaison WCF. Au niveau de la couche la plus basse est le canal de transport. Le canal de transport implémente le mécanisme de transport sous-jacent entre un service et un client et présente chaque message vers les couches supérieures (et, finalement, l’application consommatrice) comme un **System.ServiceModel.Message**. WCF **Message** classe est une abstraction d’un message SOAP. WCF fournit plusieurs interfaces de canal, appelés formes de canal, qui modèlent les SOAP message exchange modèles de base, telles que demande-réponse ou unidirectionnel. Un transport WCF liaison fournit une implémentation d’un ou plusieurs formes de canal supérieur couches peuvent utiliser pour envoyer et recevoir des messages. Pour plus d’informations sur le modèle de canal WCF, consultez [vue d’ensemble du modèle de canal](https://msdn.microsoft.com/library/ms729840.aspx).
  
 Le [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] est une liaison de transport personnalisé WCF qui expose une base de données SQL Server comme un service WCF.  
  
## <a name="supported-channel-shapes-for-the-sql-server-adapter"></a>Prise en charge des formes de canal pour l’adaptateur SQL Server  
 L’adaptateur implémente les formes de canal WCF suivantes :  
  
-   **IRequestChannel** (**System.ServiceModel.Channels.IRequestChannel**). Le **IRequestChannel** interface implémente le côté client d’un échange de messages de demande-réponse. Vous pouvez utiliser un **IRequestChannel** pour effectuer des opérations pour lesquelles vous souhaitez utiliser une réponse, par exemple, pour effectuer une sélection de requête sur une table.  
  
-   **IOutputChannel** (**System.ServiceModel.Channels.IOutputChannel**). Cette forme implémente le côté client d’un échange de messages unidirectionnels. Vous pouvez utiliser un **IOutputChannel** pour appeler une opération pour laquelle vous n’avez pas besoin de consommer une réponse, par exemple, pour appeler une procédure qui n’a aucun paramètre de retour.  
  
    > [!IMPORTANT]
    >  Tous les appels sous-jacente par l’adaptateur au client SQL Server sont synchrones. Cela inclut les appels au client SQL Server qui sont le résultat des opérations appelé sur un **IOutputChannel**. Lorsque vous utilisez un **IOutputChannel**, l’adaptateur rejette la réponse reçue à partir du client de SQL Server.  
  
-   **IInputChannel** (**System.ServiceModel.Channels.IInputChannel**). Cette forme implémente le côté service, d’un échange de messages unidirectionnels. Vous utilisez un **IInputChannel** pour recevoir des messages pour les opérations entrantes, telles que **d’interrogation** ou **Notification**, à partir de l’adaptateur.  
  
 Comme toute liaison WCF, le [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] utilise un modèle de fabrique pour fournir des canaux pour le code d’application. Vous utilisez un **Microsoft.Adapters.SQLBinding** pour créer des instances d’objet :  
  
-   **System.ServiceModel.ChannelFactory\<IRequestChannel\>**  pour fournir **IRequestChannel** canaux, vous pouvez utiliser pour appeler des opérations de requête-réponse sur la carte.  
  
-   **System.ServiceModel.ChannelFactory\<IOutputChannel\>**  pour fournir **IOutputChannel** canaux, vous pouvez utiliser pour appeler des opérations unidirectionnelles sur la carte.  
  
-   **System.ServiceModel.IChannelListener\<IInputChannel\>**  pour fournir **IInputChannel** vous pouvez utiliser pour recevoir des messages pour les opérations entrantes, telles que les canaux  **L’interrogation** ou **Notification**, à partir de l’adaptateur.  
  
### <a name="creating-messages-for-the-sql-server-database-adapter-in-the-wcf-channel-model"></a>Création de Messages pour l’adaptateur de base de données SQL Server dans le modèle de canal WCF  
 Dans WCF le **System.ServiceModel.Channels.Message** classe fournit une mémoire en représentation sous forme d’un message SOAP. Vous créez un **Message** instance en appelant la méthode statique **Message.Create** (méthode).  
  
 Deux parties importantes du message SOAP que vous devez spécifier lorsque vous créez un **Message** instance à envoyer à la [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)].  
  
-   L’action du message est une chaîne qui fait partie de l’en-tête du message SOAP. L’action du message identifie l’opération qui doit être appelée sur la base de données. L’exemple suivant montre l’action du message spécifiée pour appeler l’opération Select sur la table Employee : `TableOp/Select/dbo/Employee`.  
  
-   Le corps du message contient les données de paramètre pour l’opération. Le corps du message est composé de code XML bien formé qui correspond au schéma de message attendu par le [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] pour l’opération demandée. Le corps du message suivant spécifie une opération Select sur la table Employee (sélectionnez * à partir de l’employé où Employee_ID = 10001).  
  
    ```  
    <Select xmlns="http://schemas.microsoft.com/Sql/2008/05/TableOp/dbo/Employee">  
      <Columns>*</Columns>  
      <Query>where Employee_ID=10001</Query>  
    </Select>  
  
    ```  
  
 Pour plus d’informations sur la [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] schémas de message et les actions pour les opérations de message, consultez [Messages et des schémas de Message pour l’adaptateur BizTalk pour SQL Server](../../adapters-and-accelerators/adapter-sql/messages-and-message-schemas-for-biztalk-adapter-for-sql-server.md).  
  
 Cela **créer** méthode est surchargée et offre de nombreuses options pour fournir le corps du message. Le code suivant montre comment créer un **Message** instance en utilisant un **XmlReader** pour fournir le corps du message. Dans ce code, le corps du message est lu à partir d’un fichier.  
  
```  
XmlReader readerIn = XmlReader.Create("SelectInput.xml");  
Message messageIn = Message.CreateMessage(MessageVersion.Default,  
    "TableOp/Select/dbo/Employee",  
    readerIn);  
```  
  
> [!IMPORTANT]
>  Vous devez fournir une action de message dans votre **Message** instance. Cela est généralement le cas lorsque le **Message** instance est créée.  
  
## <a name="see-also"></a>Voir aussi  
[Développer des applications en utilisant le modèle de canal WCF](../../adapters-and-accelerators/adapter-sql/develop-sql-applications-using-the-wcf-channel-model.md)