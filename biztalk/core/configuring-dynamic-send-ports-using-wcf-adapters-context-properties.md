---
title: "Configuration des Ports d’envoi dynamiques à l’aide des propriétés de contexte des adaptateurs WCF | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- WCF services, send ports
- send ports, WCF services
- dynamic send ports, WCF services
- send ports, dynamic
ms.assetid: 2a7e2cd2-fa2d-45da-bb8e-eb8bab21bfa3
caps.latest.revision: "19"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 2bca34afa85c8764215f47d1272c115354889fa5
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="configuring-dynamic-send-ports-using-wcf-adapters-context-properties"></a>Configuration des ports d'envoi dynamiques à l'aide des propriétés de contexte des adaptateurs WCF
Vous pouvez configurer des ports d'envoi dynamiques pour les adaptateurs WCF. L’URI, une action et une liaison peuvent être déterminées à partir d’une propriété d’un message entrant et ensuite spécifiés dans le **Expression** mettre en forme, comme indiqué dans l’adaptateur WCF-NetTcp suivant :  
  
```  
MessageOut=MessageIn;  
MessageOut(WCF.Action)="http://tempuri.org/IReceiveMessage/ReceiveMessage";  
MessageOut(WCF.SecurityMode)="Transport";  
MessageOut(WCF.TransportClientCredentialType)="Windows";  
DynamicSendPort(Microsoft.XLANGs.BaseTypes.Address)="net.tcp://localhost:8001/netTcp";  
DynamicSendPort(Microsoft.XLANGs.BaseTypes.TransportType)="WCF-NetTcp";  
```  
  
 Le code suivant montre comment spécifier les propriétés de contexte WCF dans le **Expression** forme pour un adaptateur WCF-Custom :  
  
```  
MessageOut=MessageIn;  
MessageOut(WCF.BindingType)="customBinding";  
MessageOut(WCF.Action)="http://tempuri.org/IReceiveMessage/ReceiveMessage";  
MessageOut(WCF.BindingConfiguration)=@"<binding name=""customBinding""><binaryMessageEncoding /><tcpTransport /></binding>";  
DynamicSendPort(Microsoft.XLANGs.BaseTypes.Address)="net.tcp://localhost:8001/customNetTcp";  
DynamicSendPort(Microsoft.XLANGs.BaseTypes.TransportType)="WCF-Custom";  
```  
  
 Lors de la configuration des propriétés de contexte WCF, les éléments à prendre en compte sont les suivants :  
  
-   Certaines adresses peuvent être mappées vers plusieurs adaptateurs. Par exemple, une adresse commençant par http:// ou https:// peut être traitée par l'adaptateur HTTP comme par les adaptateurs WCF-BasicHttp, WCF-WsHttp ou WCF-Custom. Un autre exemple réside dans l'utilisation du début d'adresse net.tcp:// dans les deux exemples de code précédents ; toutefois, étant donné que le deuxième exemple de code fait appel à une liaison personnalisée, il est recommandé d'utiliser l'adaptateur WCF-Custom pour traiter cette adresse. Par conséquent, pour identifier l’adaptateur adéquat, vous devez configurer le paramètre facultatif **Microsoft.XLANGs.BaseTypes.TransportType** champ dans un **Expression** forme avec la carte que vous souhaitez utiliser.  
  
    > [!NOTE]
    >  Si l’adresse commence par http:// ou https:// et si vous ne spécifiez pas le **Microsoft.XLANGs.BaseTypes.TransportType** champ, par défaut, le moteur BizTalk utilise l’adaptateur HTTP.  
  
-   Le **WCF. BindingType** identifie la liaison par nom. Les valeurs possibles sont les suivantes :  
  
    -   basicHttpBinding  
  
    -   customBinding  
  
    -   netMsmqBinding  
  
    -   netNamedPipeBinding  
  
    -   netTcpBinding  
  
    -   wsFederationHttpBinding  
  
    -   wsHttpBinding  
  
     La liste ci-dessus peut être étendue. Vous pouvez y ajouter votre propre liaison, par exemple FtpBinding.  
  
-   Le **WCF. BindingConfiguration** spécifie la configuration de liaison pour le type de liaison. Elle récupère toute liaison inscrite dans le fichier de configuration de l'ordinateur. Elle récupère également la configuration XML dans un format identique à celui utilisé dans la configuration des liaisons du fichier de configuration WCF.  
  
-   Vous devrez peut-être spécifier des propriétés WCF supplémentaires. Vous pouvez taper **WCF** dans l’éditeur d’Expression et IntelliSense fonctionnalité doit répertorier toutes les propriétés de contexte disponibles. Pour plus d’informations sur les propriétés de contexte WCF, consultez [propriétés et schéma de propriété des adaptateurs WCF](../core/wcf-adapters-property-schema-and-properties.md).  
  
 Les exemples précédents montrent comment configurer **WCF. Action** en une seule action. Pour les scénarios de mappage à plusieurs actions, l'adaptateur WCF ne prend pas en charge l'utilisation du mappage à plusieurs actions avec les ports d'envoi dynamiques. Vous pouvez définir l’action réelle le **WCF. Action** propriété de contexte comme décrit ci-dessus.  
  
## <a name="see-also"></a>Voir aussi  
 [Spécification des Actions SOAP pour WCF des adaptateurs d’envoi](../core/specifying-soap-actions-for-wcf-send-adapters.md)   
 [Comment utiliser des Expressions pour affecter des valeurs à des Ports dynamiques](../core/how-to-use-expressions-to-assign-values-to-dynamic-ports.md)   
 [Liaisons de port](../core/port-bindings.md)