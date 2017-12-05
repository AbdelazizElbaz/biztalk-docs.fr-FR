---
title: "Vue d’ensemble du modèle de canal WCF avec l’adaptateur Oracle E-Business Suite | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3afd2a97-5734-4c25-87a3-702d8461898b
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: f5317099b1a576c9dd4e0b13593c16f4ef3a6831
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="overview-of-the-wcf-channel-model-with-the-oracle-e-business-suite-adapter"></a>Vue d’ensemble du modèle de canal WCF avec l’adaptateur Oracle E-Business Suite
Pour appeler des opérations sur le [!INCLUDE[adapteroracleebusinesslong](../../includes/adapteroracleebusinesslong-md.md)], votre code se comporte comme un client WCF et envoie les opérations sortantes à l’adaptateur. Dans le modèle de canal WCF, votre code appelle les opérations sur la carte en envoyant un message de demande sur un canal.  
  
 Pour appeler des opérations entrantes, notamment la réception d’interrogation de données modifiées les messages à l’aide de la **interrogation** opération fournie par l’adaptateur, votre code se comporte comme un service WCF et reçoit l’opération entrante à partir de l’adaptateur. En d’autres termes, votre code reçoit un message de demande de l’adaptateur sur un canal.  
  
 Les rubriques de cette section fournissent une vue d’ensemble de l’utilisation de la [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] avec le modèle de canal WCF.  
  
## <a name="wcf-channel-model-overview"></a>Vue d’ensemble du modèle de canal WCF  
 Les services et les clients communiquent en échangeant des messages SOAP. Le modèle de canal WCF est une abstraction de bas niveau de l’échange de messages. Il fournit des interfaces et des types qui vous permettent d’envoyer et recevoir des messages à l’aide d’une pile de protocole en couche appelée une pile de canaux. Chaque couche de la pile est composé d’un canal, et chaque canal est créé à partir d’une liaison WCF. Au niveau de la couche la plus basse est le canal de transport. Le canal de transport implémente le mécanisme de transport sous-jacent entre un service et un client et présente chaque message vers les couches supérieures (et, finalement, l’application consommatrice) comme un **System.ServiceModel.Message**. WCF **Message** classe est une abstraction d’un message SOAP. WCF fournit plusieurs interfaces de canal, appelés formes de canal, qui modèlent les SOAP message exchange modèles de base, telles que demande-réponse ou unidirectionnel. Un transport WCF liaison fournit une implémentation d’un ou plusieurs formes de canal supérieur couches peuvent utiliser pour envoyer et recevoir des messages. Pour plus d’informations sur le modèle de canal WCF, consultez « Présentation du modèle de canal » à [http://go.microsoft.com/fwlink/?LinkId=82614](http://go.microsoft.com/fwlink/?LinkId=82614).  
  
 Le [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] est une liaison de transport personnalisé WCF qui expose un artefact d’Oracle E-Business Suite comme service WCF.  
  
## <a name="supported-channel-shapes-for-the-oracle-e-business-suite-adapter"></a>Prise en charge des formes de canal pour l’adaptateur Oracle E-Business Suite  
 L’adaptateur implémente les formes de canal WCF suivantes :  
  
-   **IRequestChannel** (**System.ServiceModel.Channels.IRequestChannel**). Le **IRequestChannel** interface implémente le côté client d’un échange de messages de demande-réponse. Vous pouvez utiliser un **IRequestChannel** pour effectuer des opérations pour lesquelles vous souhaitez utiliser une réponse, par exemple, pour effectuer une sélection de requête sur une table d’interface.  
  
-   **IOutputChannel** (**System.ServiceModel.Channels.IOutputChannel**). Cette forme implémente le côté client d’un échange de messages unidirectionnels. Vous pouvez utiliser un **IOutputChannel** pour appeler une opération pour laquelle vous n’avez pas besoin de consommer une réponse, par exemple, pour appeler une procédure qui n’a aucun paramètre de sortie.  
  
    > [!IMPORTANT]
    >  Tous les appels sous-jacente par l’adaptateur pour le client Oracle sont synchrones. Cela inclut les appels au client d’Oracle qui sont le résultat des opérations appelé sur un **IOutputChannel**. Lorsque vous utilisez un **IOutputChannel**, l’adaptateur rejette la réponse reçue à partir du client Oracle.  
  
-   **IInputChannel** (**System.ServiceModel.Channels.IInputChannel**). Cette forme implémente le côté service, d’un échange de messages unidirectionnels. Vous utilisez un **IInputChannel** pour recevoir les messages entrants à partir de l’adaptateur.  
  
 Comme toute liaison WCF, le [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] utilise un modèle de fabrique pour fournir des canaux pour le code d’application. Vous utilisez un **Microsoft.Adapters.OracleEBSBinding** pour créer des instances d’objet :  
  
-   **System.ServiceModel.ChannelFactory\<IRequestChannel\>**  pour fournir **IRequestChannel** canaux, vous pouvez utiliser pour appeler des opérations de requête-réponse sur la carte.  
  
-   **System.ServiceModel.ChannelFactory\<IOutputChannel\>**  pour fournir **IOutputChannel** canaux, vous pouvez utiliser pour appeler des opérations unidirectionnelles sur la carte.  
  
-   **System.ServiceModel.IChannelListener\<IInputChannel\>**  pour fournir **IInputChannel** canaux, vous pouvez utiliser pour recevoir les messages entrants à partir de l’adaptateur.  
  
### <a name="creating-messages-for-the-oracle-enterprise-business-solution-in-the-wcf-channel-model"></a>Création de Messages pour la Solution d’entreprise Oracle Enterprise dans le modèle de canal WCF  
 Dans WCF le **System.ServiceModel.Channels.Message** classe fournit une mémoire en représentation sous forme d’un message SOAP. Vous créez un **Message** instance en appelant la méthode statique **Message.Create** (méthode).  
  
 Deux parties importantes du message SOAP que vous devez spécifier lorsque vous créez un **Message** instance à envoyer à la [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)].  
  
-   L’action du message est une chaîne qui fait partie de l’en-tête du message SOAP. L’action du message identifie l’opération qui doit être appelée sur Oracle E-Business Suite. L’exemple suivant montre l’action du message spécifiée pour appeler le **Interface client** simultanées du programme sous la **des comptes clients** application dans Oracle E-Business Suite : `ConcurrentPrograms/AR/RACUST`.  
  
-   Le corps du message contient les données de paramètre pour l’opération. Le corps du message est composé de code XML bien formé qui correspond au schéma de message attendu par le [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] pour l’opération demandée. Le corps du message suivant spécifie un message de demande pour appeler le **Interface client** simultanées du programme.  
  
    ```  
    <RACUST xmlns="http://schemas.microsoft.com/OracleEBS/2008/05/ConcurrentPrograms/AR">  
      <Description>Customer Interface Program</Description>  
      <StartTime></StartTime>  
      <CREATE_RECIPROCAL_CUSTOMER>Yes</CREATE_RECIPROCAL_CUSTOMER>  
      <ORG_ID>203</ORG_ID>  
    </RACUST>  
  
    ```  
  
 Pour plus d’informations sur la [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] schémas de message et les actions pour les opérations de message, consultez [Messages et des schémas de Message pour l’adaptateur BizTalk pour Oracle E-Business Suite](../../adapters-and-accelerators/adapter-oracle-ebs/messages-and-message-schemas-for-biztalk-adapter-for-oracle-e-business-suite.md).  
  
 Le **créer** méthode est surchargée et offre de nombreuses options pour fournir le corps du message. Le code suivant montre comment créer un **Message** instance en utilisant un **XmlReader** pour fournir le corps du message. Dans ce code, le corps du message est lu à partir d’un fichier.  
  
```  
XmlReader readerIn = XmlReader.Create("ConcProgRequest.xml");  
Message messageIn = Message.CreateMessage(MessageVersion.Default,  
    "ConcurrentPrograms/AR/RACUST",  
    readerIn);  
```  
  
 WHERE, ConProgRequest.xml contient le message de demande.  
  
> [!IMPORTANT]
>  Vous devez fournir une action de message dans votre **Message** instance. Cela est généralement le cas lorsque le **Message** instance est créée.  
  
## <a name="see-also"></a>Voir aussi  
 [Développer des applications d’Oracle E-Business Suite à l’aide du modèle de canal WCF](../../adapters-and-accelerators/adapter-oracle-ebs/develop-oracle-e-business-suite-applications-using-the-wcf-channel-model.md)