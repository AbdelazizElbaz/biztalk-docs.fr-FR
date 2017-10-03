---
title: "Configuration d’un Port d’envoi dynamique pour envoyer des échanges EDI et les accusés de réception | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a124059c-c29c-4a7f-a8a3-13dffc09ae5c
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 9a793fc22394c2b4d294bcd48fae1f9403ae9278
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="configuring-a-dynamic-send-port-to-send-edi-interchanges-and-acknowledgments"></a>Configuration d'un port d'envoi dynamique pour l'envoi d'échanges et d'accusés de réception EDI
Pour envoyer un accusé de réception ou un échange EDI, vous pouvez utiliser un port d'envoi statique ou dynamique. Un port d'envoi dynamique permet d'envoyer un échange à n'importe quelle destination d'entre plusieurs parce qu'il résout l'accord et détermine la destination sur la base de la valeur de la propriété de contexte DestinationPartyName.  
  
> [!NOTE]
>  Si vous envoyez un échange EDI basé sur un message XML reçu et que vous utilisiez un pipeline de réception PassThrough pour recevoir cette application, vous devez promouvoir la propriété de contexte DestinationPartyName. Pour plus d’informations, consultez [résolution de l’accord et détermination du schéma pour les Messages EDI sortants](../core/agreement-resolution-and-schema-determination-for-outgoing-edi-messages.md).  
  
> [!NOTE]
>  Si le port d'envoi dynamique doit envoyer un accusé de réception, la propriété de contexte DestinationPartyName est déjà promue parce que le Désassembleur EDI dans le port ayant reçu l'échange renseigne la propriété DestinationPartyName sur l'accusé de réception.  
  
 Pour créer un port d'envoi unidirectionnel dynamique, utilisez la configuration suivante :  
  
|Emplacement|Propriété|Paramètre|  
|--------------|--------------|-------------|  
|**Propriétés du Port d’envoi : général**|Type de port|Unidirectionnel dynamique|  
|**Propriétés du Port d’envoi : général**|Gestionnaire d'envoi|BizTalkServerApplication|  
|**Propriétés du Port d’envoi : général**|Pipeline d’envoi|EdiSend|  
|**Propriétés du Transport FILE : authentification**|Utiliser ces informations d'identification lorsque l'hôte n'a pas accès au partage réseau (avec un nom d'utilisateur et un mot de passe)|Définir si l'authentification est requise.|  
|**Propriétés du Port d’envoi : filtres**|Propriété|BTS.MessageType|  
|**Propriétés du Port d’envoi : filtres**|Opérateur|==|  
|**Propriétés du Port d’envoi : filtres**|Valeur|**Pour les échanges**:<br /><br /> - `http://schemas.microsoft.com/Edi/X12/2006#<schema name>`, ou<br /><br /> -                   `http://schemas.microsoft.com/Edi/Edifact/2006#<schema name>`, ou<br /><br /> **Pour les accusés de réception**:<br /><br /> -                   `http://schemas.microsoft.com/Edi/X12#X12_997_Root`, ou<br /><br /> -                   `http://schemas.microsoft.com/Edi/X12#X12_TA1_Root`, ou<br /><br /> -                   `http://schemas.microsoft.com/Edi/Edifact#Efact_Contrl_Root`|  
  
## <a name="setting-agreement-properties"></a>Définition des propriétés de l'accord  
 Après avoir créé le port d'envoi, vous devez définir les propriétés de l'accord requises pour que le pipeline d'envoi fonctionne. Ces propriétés sont définies dans les différentes pages de le **propriétés de l’accord** boîte de dialogue.  
  
## <a name="see-also"></a>Voir aussi  
 [Configuration des Ports pour une Solution EDI](../core/configuring-ports-for-an-edi-solution.md)