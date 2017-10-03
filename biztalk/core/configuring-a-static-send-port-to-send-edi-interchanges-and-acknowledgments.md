---
title: "Configuration d’un Port d’envoi statique pour envoyer des échanges EDI et les accusés de réception | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 5b432c5e-ea0c-4174-bb4a-958b061c1827
caps.latest.revision: "16"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: eb8645cd36447c814a5c43534e6c01de51e4be52
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="configuring-a-static-send-port-to-send-edi-interchanges-and-acknowledgments"></a>Configuration d'un port d'envoi statique pour l'envoi des échanges et accusés de réception EDI
Pour envoyer un accusé de réception ou un échange EDI, vous pouvez utiliser un port d'envoi unidirectionnel statique ou un port d'envoi de sollicitation-réponse statique (bidirectionnel).  
  
-   Créez un port d'envoi unidirectionnel si vous souhaitez également créer un port de réception unidirectionnel pour recevoir les accusés de réception EDI (si cette option est activée).  
  
-   Créez un port d'envoi de sollicitation-réponse pour envoyer les échanges EDI et recevoir les accusés de réception EDI (si cette option est activée) via le pipeline de réception associé.  
  
## <a name="configuring-a-static-one-way-send-port"></a>Configuration d'un port d'envoi unidirectionnel statique  
 Pour créer un port d'envoi unidirectionnel statique pour envoyer les échanges et accusés de réception EDI, utilisez la configuration suivante :  
  
|Emplacement|Propriété|Paramètre|  
|--------------|--------------|-------------|  
|**Propriétés du Port d’envoi : général**|Type de port|Unidirectionnel statique|  
|**Propriétés du Port d’envoi : général**|Type de transport|Plusieurs types possibles, notamment les types FILE, FTP, HTTP, MQSeries, MSMQ, SMTP, SOAP, SQL et WCF, ainsi que Windows SharePoint Services.|  
|**Propriétés du Port d’envoi : général**|Gestionnaire d'envoi|BizTalkServerApplication|  
|**Propriétés du Port d’envoi : général**|Pipeline d’envoi|EdiSend|  
|**Propriétés du transport : L’authentification (pour le type de transport de fichier)**|Utiliser ces informations d'identification lorsque l'hôte n'a pas accès au partage réseau (avec un nom d'utilisateur et un mot de passe)|Définir si l'authentification est requise.|  
|**Propriétés du Port d’envoi : filtres**|Propriété|BTS.MessageType<br /><br /> Remarque :<br /><br /> Vous pouvez également utiliser BTS.ReceivePortName ou d'autres propriétés promues.|  
|**Propriétés du Port d’envoi : filtres**|Opérateur|==|  
|**Propriétés du Port d’envoi : filtres**|Valeur|**À l’aide de BizTalk Server. MessageType pour les échanges :**<br /><br /> - **Pour X12**: `http://schemas.microsoft.com/Edi/X12/2006#<schema name>`, ou<br /><br /> - **Pour EDIFACT**:`http://schemas.microsoft.com/Edi/Edifact/2006#<schema name>`<br /><br /> **À l’aide de BizTalk Server. MessageType d’accusés de réception**:<br /><br /> -                     **Pour X12**: `http://schemas.microsoft.com/Edi/X12#X12_997_Root`, ou<br /><br /> -                     **Pour X12**: `http://schemas.microsoft.com/Edi/X12#X12_TA1_Root`, ou<br /><br /> -                     **Pour EDIFACT**:`http://schemas.microsoft.com/Edi/Edifact#Efact_Contrl_Root`|  
  
## <a name="configuring-a-static-solicit-response-send-port"></a>Configuration d'un port d'envoi de sollicitation-réponse statique  
 Pour créer un port d'envoi de sollicitation-réponse statique (bidirectionnel) pour envoyer les échanges et accusés de réception EDI, utilisez la configuration suivante :  
  
|Emplacement|Propriété|Paramètre|  
|--------------|--------------|-------------|  
|**Propriétés du Port d’envoi : général**|Type de port|Sollicitation-réponse statique|  
|**Propriétés du Port d’envoi : général**|Type de transport|Plusieurs types possibles, notamment les types HTTP, MQSeries, MSMQ, SOAP, SQL et WCF. Types FILE, FTP, SMTP et Windows SharePoint Services impossibles.|  
|**Propriétés du Port d’envoi : général**|Gestionnaire d'envoi|BizTalkServerApplication|  
|**Propriétés du Port d’envoi : général**|Pipeline d’envoi|EdiSend|  
|**Propriétés du Port d’envoi : général**|Pipeline de réception|EdiReceive|  
|**Propriétés du transport : L’authentification (pour le type de transport HTTP)**|Utiliser ces informations d'identification lorsque l'hôte n'a pas accès au partage réseau (avec un nom d'utilisateur et un mot de passe)|Définir si l'authentification est requise.|  
|**Propriétés du Port d’envoi : filtres**|Propriété|BTS.MessageType<br /><br /> Remarque :<br /><br /> Vous pouvez également utiliser BTS.ReceivePortName ou d'autres propriétés promues.|  
|**Propriétés du Port d’envoi : filtres**|Opérateur|==|  
|**Propriétés du Port d’envoi : filtres**|Valeur|**À l’aide de BizTalk Server. MessageType pour les échanges :**<br /><br /> -                     **Pour X12**: `http://schemas.microsoft.com/Edi/X12/2006#<schema name>`, ou<br /><br /> -                     **Pour EDIFACT**:`http://schemas.microsoft.com/Edi/Edifact/2006#<schema name>`<br /><br /> **À l’aide de BizTalk Server. MessageType d’accusés de réception**:<br /><br /> -                     **Pour X12**: `http://schemas.microsoft.com/Edi/X12#X12_997_Root`, ou<br /><br /> -                     **Pour X12**: `http://schemas.microsoft.com/Edi/X12#X12_TA1_Root`, ou<br /><br /> -                     **Pour EDIFACT**:`http://schemas.microsoft.com/Edi/Edifact#Efact_Contrl_Root`|  
  
## <a name="setting-agreement-properties"></a>Définition des propriétés de l'accord  
 Après avoir créé le port d'envoi, vous devez définir les propriétés de l'accord requises pour que le pipeline d'envoi fonctionne. Ces propriétés sont définies dans les différentes pages de le **propriétés de l’accord** boîte de dialogue.  
  
## <a name="see-also"></a>Voir aussi  
 [Configuration des Ports pour une Solution EDI](../core/configuring-ports-for-an-edi-solution.md)   
 [Comment créer un Port d’envoi](../core/how-to-create-a-send-port2.md)