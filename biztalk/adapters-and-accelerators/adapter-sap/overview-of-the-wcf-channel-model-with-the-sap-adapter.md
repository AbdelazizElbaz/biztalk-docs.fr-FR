---
title: "Vue d’ensemble du modèle de canal WCF avec l’adaptateur SAP | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- WCF channel model, overview
- WCF channel model, creating messages for the SAP adapter
ms.assetid: 6192d637-efac-4580-8880-b5bae9d16f31
caps.latest.revision: "5"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 8083f7dc691010f4128b3ddb99729b0b2b1ebd1f
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="overview-of-the-wcf-channel-model-with-the-sap-adapter"></a>Vue d’ensemble du modèle de canal WCF avec l’adaptateur SAP
Pour appeler les RFC ou BAPI tRFCs sur un système SAP, ou pour envoyer des IDOC à un système SAP, votre code agit comme un client WCF et envoie les opérations sortantes à l’adaptateur. Dans le modèle de canal WCF, votre code appelle les opérations sur la carte en envoyant un message de demande sur un canal.  
  
 Pour agir en tant que tRFC ou serveur RFC à un système SAP, votre code se comporte comme un service WCF. Autrement dit, l’adaptateur appelle une opération entrante sur votre code, par exemple, une demande de changement ou l’opération ReceiveIdoc (pour recevoir un IDOC sous forme de chaîne à partir d’un système SAP). Dans ce scénario, votre code reçoit un message de demande pour l’opération sur un canal à partir de l’adaptateur.  
  
 Les rubriques de cette section fournissent une vue d’ensemble de l’utilisation de la [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] avec le modèle de canal WCF.  
  
## <a name="wcf-channel-model-overview"></a>Vue d’ensemble du modèle de canal WCF  
 Les services et les clients communiquent en échangeant des messages SOAP. Le modèle de canal WCF est une abstraction de bas niveau de l’échange de messages. Il fournit des interfaces et des types qui vous permettent d’envoyer et recevoir des messages à l’aide d’une pile de protocole en couche appelée une pile de canaux. Chaque couche de la pile est composé d’un canal, et chaque canal est créé à partir d’une liaison WCF. Au niveau de la couche la plus basse est le canal de transport. Le canal de transport implémente le mécanisme de transport sous-jacent entre un service et un client et présente chaque message vers les couches supérieures (et, finalement, l’application consommatrice) comme un **System.ServiceModel.Message**. WCF **Message** classe est une abstraction d’un message SOAP. WCF fournit plusieurs interfaces de canal, appelés formes de canal, qui modèlent les SOAP message exchange modèles de base, telles que demande-réponse ou unidirectionnel. Un transport WCF liaison fournit une implémentation d’un ou plusieurs formes de canal supérieur couches peuvent utiliser pour envoyer et recevoir des messages. Pour plus d’informations sur le modèle de canal WCF, consultez [vue d’ensemble du modèle de canal](https://msdn.microsoft.com/library/ms729840.aspx).
  
 Le [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] est une liaison de transport personnalisé WCF qui expose un système SAP comme un service WCF.  
  
## <a name="supported-channel-shapes-for-the-sap-adapter"></a>Prise en charge des formes de canal pour l’adaptateur SAP  
 L’adaptateur implémente les formes de canal WCF suivantes :  
  
-   **IRequestChannel** (**System.ServiceModel.Channels.IRequestChannel**). Le **IRequestChannel** interface implémente le côté client d’un échange de messages de demande-réponse. Vous pouvez utiliser un **IRequestChannel** pour effectuer des opérations pour lesquelles vous souhaitez utiliser une réponse, par exemple, pour appeler une commande RFC sur le système SAP qui retourne des données.  
  
-   **IOutputChannel** (**System.ServiceModel.Channels.IOutputChannel**). Cette forme implémente le côté client d’un échange de messages unidirectionnels. Vous pouvez utiliser un **IOutputChannel** pour appeler une opération pour laquelle vous n’avez pas besoin de consommer une réponse, par exemple, pour appeler une commande RFC sur le système SAP qui ne retourne pas de données.  
  
-   **IReplyChannel** (**System.ServiceModel.Channels.IReplyChannel**). Cette forme implémente le côté service, d’un échange de messages de demande-réponse. Vous pouvez utiliser un **IReplyChannel** pour implémenter un serveur RFC ou tRFC ou de recevoir des IDOC à partir d’un système SAP.  
  
 Comme toute liaison WCF, le [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] utilise un modèle de fabrique pour fournir des canaux pour le code d’application. Vous utilisez un **Microsoft.Adapters.SAPBinding** pour créer des instances d’objet :  
  
-   **System.ServiceModel.ChannelFactory\<IRequestChannel >** pour fournir **IRequestChannel** canaux, vous pouvez utiliser pour appeler des opérations de requête-réponse sur la carte.  
  
-   **System.ServiceModel.ChannelFactory\<IOutputChannel >** pour fournir **IOutputChannel** canaux, vous pouvez utiliser pour appeler des opérations unidirectionnelles sur la carte.  
  
-   **System.ServiceModel.IChannelListener\<IReplyChannel >** pour fournir **IReplyChannel** canaux, vous pouvez utiliser pour recevoir des opérations de demande-réponse à partir de l’adaptateur.  
  
## <a name="creating-messages-for-the-sap-adapter-in-the-wcf-channel-model"></a>Création de Messages pour l’adaptateur SAP dans le modèle de canal WCF  
 Dans WCF le **System.ServiceModel.Channels.Message** classe fournit une mémoire en représentation sous forme d’un message SOAP. Vous créez un **Message** instance en appelant la méthode statique **Message.Create** (méthode).  
  
 Deux parties importantes du message SOAP que vous devez spécifier lorsque vous construisez un **Message** instance à envoyer à la [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)].  
  
-   L’action du message est une chaîne qui fait partie de l’en-tête du message SOAP. L’action du message identifie l’opération qui doit être appelée sur [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)]. L’exemple suivant montre l’action du message qui est spécifiée pour appeler le RFC SD_RFC_CUSTOMER_GET sur un système SAP : `http://Microsoft.LobServices.Sap/2007/03/Rfc/SD_RFC_CUSTOMER_GET`.  
  
-   Le corps du message contient les données de paramètre pour l’opération. Le corps du message est composé de code XML bien formé qui correspond au schéma de message attendu par le [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] pour l’opération demandée. Le corps du message suivant contient les paramètres de la RFC SD_RFC_CUSTOMER_GET sur un système SAP.  
  
    ```  
    <SD_RFC_CUSTOMER_GET xmlns=\"http://Microsoft.LobServices.Sap/2007/03/Rfc/\"> <KUNNR i:nil=\"true\" xmlns:i=\"http://www.w3.org/2001/XMLSchema-instance\"> </KUNNR> <NAME1>AB*</NAME1> <CUSTOMER_T> </CUSTOMER_T> </SD_RFC_CUSTOMER_GET>  
    ```  
  
 Pour plus d’informations sur la [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] schémas de message et les actions pour les opérations de message, consultez [Messages et des schémas de Message pour l’adaptateur BizTalk pour mySAP Business Suite](../../adapters-and-accelerators/adapter-sap/messages-and-message-schemas-for-biztalk-adapter-for-mysap-business-suite.md).  
  
 Le **Message.Create** méthode est surchargée et offre de nombreuses options pour fournir le corps du message. Le code suivant montre comment créer un **Message** instance en utilisant un **System.Xml.XmlReader** pour fournir le corps du message. Dans ce code, le corps du message est lu à partir d’une constante de chaîne.  
  
```  
//create an XML message to send to the SAP system  
//We are invoking the SD_RFC_CUSTOMER_GET RFC.  
//The XML below specifies that we want to search for customers with names starting with "AB"  
string inputXml = "\<SD_RFC_CUSTOMER_GET xmlns=\"http://Microsoft.LobServices.Sap/2007/03/Rfc/\"> \<KUNNR i:nil=\"true\" xmlns:i=\"http://www.w3.org/2001/XMLSchema-instance\"> </KUNNR> <NAME1>AB*</NAME1> <CUSTOMER_T> </CUSTOMER_T> </SD_RFC_CUSTOMER_GET>";  
  
//create an XML reader from the input XML  
XmlReader reader = XmlReader.Create(new MemoryStream(Encoding.Default.GetBytes(inputXml)));  
  
//create a WCF message from the XML reader  
Message inputMessge = Message.CreateMessage(MessageVersion.Soap11, "http://Microsoft.LobServices.Sap/2007/03/Rfc/SD_RFC_CUSTOMER_GET", reader);  
```  
  
> [!IMPORTANT]
>  Vous devez fournir une action de message dans votre **Message** instance. Cela est généralement le cas lorsque le **Message** instance est créée.  
  
## <a name="streaming-support-on-the-sap-adapter-in-the-wcf-channel-model"></a>Prise en charge de diffusion en continu sur l’adaptateur SAP dans le modèle de canal WCF  
 Comment créer et consommer les messages que vous échangez avec l’adaptateur SAP détermine la façon dont le message est transmis en continu entre votre code et de la carte.  
  
### <a name="node-streaming"></a>Nœud de diffusion en continu  
 Nœud de diffusion en continu est le seul niveau de prise en charge pour toutes les opérations à l’exception des opérations SendIdoc et ReceiveIdoc de diffusion en continu.  
  
 Pour effectuer le nœud de diffusion en continu pour un message, vous :  
  
-   Créer un message sortant à l’aide un **XmlReader** pour fournir le corps du message.  
  
-   Consommer un message entrant à l’aide un **XmlReader**. Vous obtenez le lecteur en appelant le **GetReaderAtBodyContents** méthode entrant **Message**.  
  
### <a name="node-value-streaming"></a>Valeur du nœud de diffusion en continu  
 Étant donné que les opérations SendIdoc et ReceiveIdoc contiennent des données IDOC d’une chaîne sous un nœud XML unique (\<idocData >), la carte prend en charge-valeur du nœud sur ces opérations de diffusion en continu.  
  
 Pour effectuer la valeur du nœud de diffusion en continu pour ces opérations, vous pouvez :  
  
-   Créer le SendIdoc demande message (sortant) en utilisant un **BodyWriter** qui implémente la valeur du nœud de diffusion en continu pour fournir le corps du message.  
  
-   Consommer le message de demande ReceiveIdoc (entrant) en appelant le **WriteBodyContents** méthode sur le message avec un **XmlDictionaryWriter** qui implémente la diffusion en continu de la valeur du nœud.  
  
 Pour plus d’informations sur la diffusion en continu des IDOC de fichier plat (chaîne) à l’aide du modèle de canal WCF, consultez [de diffusion en continu de fichier plat IDOC dans SAP à l’aide du modèle de canal WCF](../../adapters-and-accelerators/adapter-sap/stream-flat-file-idocs-in-sap-using-the-wcf-channel-model.md).  
  
## <a name="see-also"></a>Voir aussi  
[Développer des applications à l’aide du modèle de canal WCF](../../adapters-and-accelerators/adapter-sap/develop-sap-applications-using-the-wcf-channel-model.md)