---
title: "Vue d’ensemble du modèle de canal WCF avec l’adaptateur de base de données Oracle | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: WCF channel model, overview
ms.assetid: 4712ba62-8360-475c-b2e4-422e499eca21
caps.latest.revision: "5"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 94cb4b8cfdb0315b55aa88ddd385396ff967b8f6
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="overview-of-the-wcf-channel-model-with-the-oracle-database-adapter"></a>Vue d’ensemble du modèle de canal WCF avec l’adaptateur de base de données Oracle
Pour appeler des opérations sur le [!INCLUDE[adapteroracle](../../includes/adapteroracle-md.md)], votre code se comporte comme un client WCF et envoie les opérations sortantes à l’adaptateur. Dans le modèle de canal WCF, votre code appelle les opérations sur la carte en envoyant un message de demande sur un canal.  
  
 Pour appeler des opérations entrantes, telles qu’entrant d’interrogation de messages basés sur Modification de données à l’aide de l’opération de POLLINGSTMT fournie par l’adaptateur, votre code fonctionne comme un service WCF et reçoit l’opération entrante à partir de l’adaptateur. En d’autres termes, votre code reçoit un message de demande de l’adaptateur sur un canal.  
  
 Les rubriques de cette section fournissent une vue d’ensemble de l’utilisation de la [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] avec le modèle de canal WCF.  
  
## <a name="wcf-channel-model-overview"></a>Vue d’ensemble du modèle de canal WCF  
 Les services et les clients communiquent en échangeant des messages SOAP. Le modèle de canal WCF est une abstraction de bas niveau de l’échange de messages. Il fournit des interfaces et des types qui vous permettent d’envoyer et recevoir des messages à l’aide d’une pile de protocole en couche appelée une pile de canaux. Chaque couche de la pile est composé d’un canal, et chaque canal est créé à partir d’une liaison WCF. Au niveau de la couche la plus basse est le canal de transport. Le canal de transport implémente le mécanisme de transport sous-jacent entre un service et un client et présente chaque message vers les couches supérieures (et, finalement, l’application consommatrice) comme un **System.ServiceModel.Message**. WCF **Message** classe est une abstraction d’un message SOAP. WCF fournit plusieurs interfaces de canal, appelés formes de canal, qui modèlent les SOAP message exchange modèles de base, telles que demande-réponse ou unidirectionnel. Un transport WCF liaison fournit une implémentation d’un ou plusieurs formes de canal supérieur couches peuvent utiliser pour envoyer et recevoir des messages. Pour plus d’informations sur le modèle de canal WCF, consultez [vue d’ensemble du modèle de canal](https://msdn.microsoft.com/library/ms729840.aspx).   
  
 Le [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] est une liaison de transport personnalisé WCF qui expose une base de données Oracle en tant qu’un service WCF.  
  
## <a name="supported-channel-shapes-for-the-oracle-database-adapter"></a>Prise en charge des formes de canal pour l’adaptateur de base de données Oracle  
 L’adaptateur implémente les formes de canal WCF suivantes :  
  
-   **IRequestChannel** (**System.ServiceModel.Channels.IRequestChannel**). Le **IRequestChannel** interface implémente le côté client d’un échange de messages de demande-réponse. Vous pouvez utiliser un **IRequestChannel** pour effectuer des opérations pour lesquelles vous souhaitez utiliser une réponse, par exemple, pour effectuer une sélection de requête sur une table Oracle.  
  
-   **IOutputChannel** (**System.ServiceModel.Channels.IOutputChannel**). Cette forme implémente le côté client d’un échange de messages unidirectionnels. Vous pouvez utiliser un **IOutputChannel** pour appeler une opération pour laquelle vous n’avez pas besoin de consommer une réponse, par exemple, pour appeler une procédure d’Oracle qui n’a aucun paramètre de sortie.  
  
    > [!IMPORTANT]
    >  Tous les appels sous-jacente par l’adaptateur pour le client Oracle sont synchrones. Cela inclut les appels au client d’Oracle qui sont le résultat des opérations appelé sur un **IOutputChannel**. Lorsque vous utilisez un **IOutputChannel**, l’adaptateur rejette la réponse reçue à partir du client Oracle.  
  
-   **IInputChannel** (**System.ServiceModel.Channels.IInputChannel**). Cette forme implémente le côté service, d’un échange de messages unidirectionnels. Vous utilisez un **IInputChannel** pour recevoir des messages pour les opérations entrantes à partir de l’adaptateur.  
  
 Comme toute liaison WCF, le [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] utilise un modèle de fabrique pour fournir des canaux pour le code d’application. Vous utilisez un **Microsoft.Adapters.OracleDBBinding** pour créer des instances d’objet :  
  
-   **System.ServiceModel.ChannelFactory\<IRequestChannel\>**  pour fournir **IRequestChannel** canaux, vous pouvez utiliser pour appeler des opérations de requête-réponse sur la carte.  
  
-   **System.ServiceModel.ChannelFactory\<IOutputChannel\>**  pour fournir **IOutputChannel** canaux, vous pouvez utiliser pour appeler des opérations unidirectionnelles sur la carte.  
  
-   **System.ServiceModel.IChannelListener\<IInputChannel\>**  pour fournir **IInputChannel** canaux, vous pouvez utiliser pour recevoir des messages entrants (par exemple, une opération POLLINGSTMT) de l’adaptateur .  
  
### <a name="creating-messages-for-the-oracle-database-adapter-in-the-wcf-channel-model"></a>Création de Messages pour l’adaptateur de base de données Oracle dans le modèle de canal WCF  
 Dans WCF le **System.ServiceModel.Channels.Message** classe fournit une mémoire en représentation sous forme d’un message SOAP. Vous créez un **Message** instance en appelant la méthode statique **Message.Create** (méthode).  
  
 Deux parties importantes du message SOAP que vous devez spécifier lorsque vous créez un **Message** instance à envoyer à la [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)].  
  
-   L’action du message est une chaîne qui fait partie de l’en-tête du message SOAP. L’action du message identifie l’opération qui doit être appelée sur la base de données Oracle. L’exemple suivant montre l’action du message spécifiée pour appeler l’opération Select sur la table/SCOTT/EMP : `http://Microsoft.LobServices.OracleDB/2007/03/SCOTT/Table/EMP/Select`.  
  
-   Le corps du message contient les données de paramètre pour l’opération. Le corps du message est composé de code XML bien formé qui correspond au schéma de message attendu par le [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] pour l’opération demandée. Le corps du message suivant spécifie une opération Select sur SCOTT. Table EMP (sélectionnez * à partir de EMP).  
  
    ```  
    <?xml version="1.0" encoding="utf-8" ?>  
    <Select xmlns="http://Microsoft.LobServices.OracleDB/2007/03/SCOTT/Table/EMP">  
        <COLUMN_NAMES>*</COLUMN_NAMES>  
    </Select>  
    ```  
  
 Pour plus d’informations sur la [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] schémas de message et les actions pour les opérations de message, consultez [Messages et des schémas de Message pour l’adaptateur BizTalk pour base de données Oracle](../../adapters-and-accelerators/adapter-oracle-database/messages-and-message-schemas-for-biztalk-adapter-for-oracle-database.md).  
  
 Cela **créer** méthode est surchargée et offre de nombreuses options pour fournir le corps du message. Le code suivant montre comment créer un **Message** instance en utilisant un **XmlReader** pour fournir le corps du message. Dans ce code, le corps du message est lu à partir d’un fichier.  
  
```  
XmlReader readerIn = XmlReader.Create("SelectAllActivity.xml");  
Message messageIn = Message.CreateMessage(MessageVersion.Default,  
    "http://Microsoft.LobServices.OracleDB/2007/03/SCOTT/Table/EMP/Select",  
    readerIn);  
```  
  
> [!IMPORTANT]
>  Vous devez fournir une action de message dans votre **Message** instance. Cela est généralement le cas lorsque le **Message** instance est créée.  
  
## <a name="streaming-support-for-lob-data-types-in-the-wcf-channel-model"></a>Prise en charge de diffusion en continu pour les Types de données LOB dans le modèle de canal WCF  
 Diffusion en continu de bout en bout de types de données LOB est pris en charge pour certaines opérations exposées par l’adaptateur. Pour ces opérations, comment créer et consommer les messages que vous envoyez et recevez sur le canal détermine si le flux est pris en charge sur les données LOB.  
  
 Pour plus d’informations sur la façon dont [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] prend en charge la diffusion en continu des données LOB, consultez [diffusion en continu des types de données dans la carte de base de données Oracle](../../adapters-and-accelerators/adapter-oracle-database/streaming-large-object-data-types-in-oracle-database-adapter.md).  
  
 Pour plus d’informations sur l’implémentation de diffusion en continu dans votre code pour prendre en charge la diffusion en continu de bout en bout des données LOB de valeur de nœud, consultez [de diffusion en continu Oracle de base de données LOB données Types à l’aide du modèle de canal WCF](../../adapters-and-accelerators/adapter-oracle-database/streaming-oracle-database-lob-data-types-using-the-wcf-channel-model.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Développer des applications de base de données Oracle à l’aide du modèle de canal WCF](../../adapters-and-accelerators/adapter-oracle-database/develop-oracle-database-applications-using-the-wcf-channel-model.md)