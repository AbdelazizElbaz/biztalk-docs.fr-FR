---
title: "Publication à partir de la Console Administration de BizTalk Server | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b78b1981-b227-4cf5-9435-6fc57963552a
caps.latest.revision: "2"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 313bfb773a94914ed9bebd3930dfd0033ecf4ac3
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="publishing-from-the-biztalk-server-administration-console"></a>Publication à partir de la Console Administration de BizTalk Server
Si vous souhaitez gérer la publication de point de terminaison via la [!INCLUDE[prague](../includes/prague-md.md)] Console d’Administration au lieu du portail de gestion ESB, vous pouvez le faire en entrant un moniker Universal Description, Discovery and Integration (UDDI) dans le champ de description de la points de terminaison à la publication dans UDDI. Voici un moniker de l’exemple.  
  
```  
uddi://TransportType=other;Status=Published.  
```  
  
 Vous pouvez définir les propriétés suivantes de UDDI à l’aide de la **Description** champ dans le [!INCLUDE[prague](../includes/prague-md.md)] Console d’Administration :  
  
-   **ModifiedBy**. Cette propriété facultative comporte le nom du compte d’utilisateur qui a modifié le point de terminaison ; par exemple, MyDomainName\MyUserName.  
  
-   **UDDIContact**. Cette propriété facultative est le nom du contact de l’utilisateur défini pour le fournisseur d’entreprise UDDI.  
  
-   **UDDIUserType**. Cette propriété facultative est le type d’utilisateur de l’utilisateur défini pour le fournisseur d’entreprise UDDI.  
  
-   **UDDIEmail**. Cette propriété facultative est l’adresse de messagerie de l’utilisateur défini pour le fournisseur d’entreprise UDDI.  
  
-   **Type de transport**. Cette propriété facultative est le type de carte de point de terminaison, tel que **fichier MQS, WCF-WsHttp, SOAP, HTTP,** ou **FTP**.  
  
-   **État**. Cette propriété facultative est l’état du point de terminaison, tel que **publié** ou **en attente**. Le Service de publication UDDI utilise cet attribut pour détecter l’état du point de terminaison.  
  
-   **BindingType**. Cette propriété facultative est le protocole spécifique (Type d’URL) prenant en charge la liaison UDDI, tel que **mailto, http, https, ftp, fax, téléphone,** ou **autres**. Le Service de publication UDDI utilise cet attribut pour créer la liaison de point de terminaison.