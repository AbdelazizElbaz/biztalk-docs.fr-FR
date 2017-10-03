---
title: "Diffusion en continu et l’adaptateur SAP | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- streaming, support in WCF service model
- streaming, node-value
- streaming, node
- streaming, support in BizTalk Server
- streaming, and the SAP adapter
- streaming, support in WCF channel model
ms.assetid: 9fa1788b-f21b-4dec-be14-27dd8080a9d4
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 48b97b0349822dcca1ae6486e4a0b515778b4d4d
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="streaming-and-the-sap-adapter"></a>Diffusion en continu et l’adaptateur SAP
Le [!INCLUDE[adaptersap](../../includes/adaptersap-md.md)] prend en charge les messages de diffusion en continu entre lui-même et une application cliente. Avec la [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] opérations sont appelées et les réponses sont retournées en échangeant des messages SOAP. Un corps de message SOAP est composé de nœuds XML.  
  
 Il existe deux types de messages de diffusion en continu sont pris en charge par l’adaptateur :  
  
-   **Nœud de diffusion en continu**. Dans le nœud de diffusion en continu, un message peut être diffusé en continu un nœud à la fois entre le client et l’adaptateur. Cela signifie que, la valeur entière d’un nœud est lus dans une mémoire tampon et est ensuite envoyée au récepteur.  
  
-   **Diffusion en continu de la valeur du nœud**. Dans valeur de nœud de diffusion en continu de la valeur réelle du nœud peut être diffusée en segments entre le client et l’adaptateur. Valeur de nœud de diffusion en continu est utile pour envoyer ou recevoir des IDOC volumineux à l’aide de la SendIdoc ou les opérations de ReceiveIdoc. Il s’agit, car l’IDOC entière est contenue dans un seul nœud. (Par opposition à la fortement typé envoyer ou recevoir d’opération dans laquelle les données IDOC sont divisées en plusieurs nœuds).  
  
> [!IMPORTANT]
>  Valeur de nœud de diffusion en continu est uniquement prise en charge entre l’adaptateur et une application cliente. Le [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] ne prend pas en charge de bout en bout-valeur de nœud de diffusion en continu avec le système SAP. Il s’agit, car cette fonctionnalité n’est pas pris en charge par la bibliothèque cliente SAP.  
  
 Les deux de ces modes de diffusion en continu s’appuient sur la prise en charge pour le nœud de diffusion en continu et la valeur du nœud de diffusion en continu sur les messages dans WCF. Pour cette raison, diffusion en continu dépend étroitement comment les messages sont créés et consommées par l’adaptateur et par une application cliente. Une conséquence de cela est que la prise en charge pour les messages de diffusion en continu n’est pas le même sur tous les modèles de programmation.  
  
 Les sections de cette rubrique fournissent :  
  
-   Informations fondamentales sur la prise en charge des messages de diffusion en continu dans WCF et comment il est implémenté par l’adaptateur.  
  
-   Informations sur la diffusion en continu de message comment est pris en charge lorsque vous utilisez l’adaptateur dans chaque modèle de programmation.  
  
## <a name="streaming-fundamentals"></a>Notions de base de diffusion en continu  
 La prise en charge pour la diffusion implémentée par le [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] est une combinaison de :  
  
-   Prise en charge de la diffusion en continu message dans WCF.  
  
-   Prise en charge dans la bibliothèque cliente SAP de diffusion en continu.  
  
-   Les façon dont les messages sont créés et consommés en interne par l’adaptateur.  
  
### <a name="message-streaming-support-in-wcf"></a>Prise en charge des messages de diffusion en continu dans WCF  
 Comment WCF prend en charge la diffusion en continu sur un message dépend à la fois sur la façon dont le message est créé et comment le message est utilisé.  
  
-   Un message WCF est créé à l’aide de la méthode statique **créer** méthode **System.ServiceModel.Channels.Message**. Cette méthode a plusieurs surcharges qui prennent en charge de différentes façons de passer le corps du message. Un message WCF peut être créé en passant le corps de message à l’aide de :  
  
    -   A **System.Xml.XmlReader**, ou  
  
    -   A **System.ServiceModel.Channels.BodyWriter**.  
  
-   Un message WCF peut être consommé à l’aide de  
  
    -   Un **XmlReader** en appelant **Message.GetReaderAtBodyContents()**, ou  
  
    -   Un **XmlDictionaryWriter** en appelant **Message.WriteBodyContents(XmlDictionaryWriter)**.  
  
 Le tableau suivant montre comment se comporte de WCF pour différentes combinaisons de la création et la consommation des messages.  
  
|Message créé avec|Message consommée avec|Comportement WCF|  
|--------------------------|---------------------------|------------------|  
|**XmlBodyWriter**|**XmlDictionaryWriter**|**Valeur de nœud de diffusion en continu** est pris en charge. WCF dirige les deux enregistreurs pour activer la diffusion en continu. Les deux le **XmlBodyWriter** et **XmlDictionaryWriter** doit prendre en charge les valeur du nœud de diffusion en continu pour qu’il puisse se produire.|  
|**XmlBodyWriter**|**XmlReader**|**Nœud de diffusion en continu** est pris en charge. WCF met en mémoire tampon en interne le **XmlReader**.|  
|**XmlReader**|**XmlDictionaryWriter**|**Nœud de diffusion en continu** est pris en charge. WCF met en mémoire tampon en interne le **XmlReader** et rappelle le **XmlDictionaryWriter**.|  
|**XmlReader**|**XmlReader**|**Nœud de diffusion en continu** est pris en charge. WCF met en mémoire tampon en interne le **XmlReader**.|  
  
### <a name="streaming-support-in-the-sap-client-library"></a>Prise en charge de diffusion en continu dans la bibliothèque cliente SAP  
 La bibliothèque cliente SAP ne prend pas en charge la diffusion en continu. Par conséquent, la diffusion en continu de bout en bout-valeur de nœud n'est pas pris en charge par le [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)].  
  
### <a name="internal-message-handling-by-the-adapter"></a>Gestion des messages interne par l’adaptateur  
 L’adaptateur prend en charge la diffusion en continu de la manière suivante :  
  
-   L’adaptateur utilise le message de demande SendIdDoc a reçu du client à l’aide d’une implémentation personnalisée de **XmlDictionaryWriter**. Elle consomme tous les autres messages reçus à partir du client à l’aide un **XmlReader**.  
  
-   L’adaptateur crée le message de demande ReceiveIdoc qu’il envoie au client à l’aide d’une implémentation personnalisée de **XmlBodyWriter**. Il crée tous les autres messages qu’il envoie au client à l’aide un **XmlReader**.  
  
## <a name="streaming-support-in-the-wcf-channel-model"></a>Prise en charge de diffusion en continu dans le modèle de canal WCF  
 Le tableau suivant fournit des informations détaillées sur la diffusion en continu est prise en charge dans le modèle de canal WCF.  
  
|Opération|Nœud de diffusion en continu|Valeur du nœud de diffusion en continu| Description|  
|---------------|--------------------|---------------------------|-----------------|  
|Opérations RFC et BAPI sortantes (depuis le client à l’adaptateur)|Non pris en charge|Non pris en charge||  
|Opérations tRFC sortant (depuis le client à l’adaptateur)|Non pris en charge|Non pris en charge||  
|Opération d’envoi IDOC (fortement typée)|Non pris en charge|Non pris en charge||  
|Opération de réception IDOC (fortement typée)|Pris en charge|Non pris en charge||  
|Opération SendIdoc (string)|Pris en charge|Pris en charge|L’adaptateur utilise un **XmlDictionaryWriter** pour consommer le message de demande. Si le client crée le message avec un **BodyWriter**, valeur du nœud de diffusion en continu à partir du client à l’adaptateur se produit.|  
|Opération ReceiveIdoc (string)|Pris en charge|Pris en charge|L’adaptateur utilise un **BodyWriter** pour créer le message de demande. Si le client utilise le message en utilisant un **XmlDictionaryWriter**, valeur du nœud de diffusion en continu à partir de l’adaptateur pour le client se produit.|  
|RFC opérations entrantes|Non pris en charge|Non pris en charge||  
|Les opérations tRFC entrantes|Non pris en charge|Non pris en charge||  
  
 Pour plus d’informations sur l’implémentation de diffusion en continu dans votre code pour envoyer et recevoir des IDOC de fichier plat (chaîne) à l’aide d’opérations SendIdoc et ReceiveIdoc-valeur de nœud, consultez [IDOC de fichier plat de flux de données dans SAP à l’aide du modèle de canal WCF](../../adapters-and-accelerators/adapter-sap/stream-flat-file-idocs-in-sap-using-the-wcf-channel-model.md).  
  
## <a name="streaming-support-in-the-wcf-service-model"></a>Prise en charge de diffusion en continu dans le modèle de Service WCF  
 Sérialisation et la désérialisation entre la représentation XML d’un message et la représentation d’objet de code managé de ce message requièrent l’écriture et de la lecture de la totalité du message en mémoire. Pour cette raison, nœud de diffusion en continu, ni diffusion en continu de valeur de nœud est pris en charge à partir du modèle de service WCF.  
  
## <a name="streaming-support-in-biztalk-server"></a>Prise en charge de diffusion en continu dans BizTalk Server  
 Le tableau suivant fournit des informations détaillées sur la diffusion en continu est prise en charge dans BizTalk Server.  
  
|Opération|Nœud de diffusion en continu|Valeur du nœud de diffusion en continu| Description|  
|---------------|--------------------|---------------------------|-----------------|  
|Opérations RFC et BAPI (depuis le client à l’adaptateur)|Non pris en charge|Non pris en charge||  
|opérations tRFC (depuis le client à l’adaptateur)|Non pris en charge|Non pris en charge||  
|Opération d’envoi IDOC (fortement typée)|Non pris en charge|Non pris en charge||  
|Opération de réception IDOC (fortement typée)|Pris en charge|Non pris en charge||  
|Opération SendIdoc (string)|Pris en charge|Pris en charge|L’adaptateur WCF-Custom utilise un **BodyWriter** pour créer le message de demande, diffusion en continu de la valeur du nœud est prise en charge.|  
|Opération ReceiveIdoc (string)|Pris en charge|Pris en charge|L’adaptateur WCF-Custom utilise un **XmlDictionaryWriter** pour consommer le message de demande, diffusion en continu de la valeur du nœud est prise en charge.|  
|RFC opérations entrantes|Non pris en charge|Non pris en charge||  
|Les opérations tRFC entrantes|Non pris en charge|Non pris en charge||  
  
## <a name="see-also"></a>Voir aussi  
[Développer vos applications SAP](../../adapters-and-accelerators/adapter-sap/develop-your-sap-applications.md)