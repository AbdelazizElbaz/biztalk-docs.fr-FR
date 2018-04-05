---
title: EncryptionCert (nœud ReceiveLocation) | Documents Microsoft
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- EncryptionCert node [binding file]
ms.assetid: 04dc4021-8cd9-45e7-8339-8f22e29f4be6
caps.latest.revision: 7
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: ec4d0ff769c7a8ca297800f427c4ebbae48a8640
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="encryptioncert-receivelocation-node"></a>EncryptionCert (nœud ReceiveLocation)
Le nœud EncryptionCert du nœud ReceiveLocation d'un fichier de liaison contient des informations sur le certificat de chiffrement utilisé avec un port de réception exporté avec le fichier de liaison.  
  
## <a name="nodes-in-the-encryptioncert-node"></a>Nœuds du nœud EncryptionCert  
 Le tableau suivant répertorie les propriétés que vous pouvez définir pour ce nœud d'un fichier de liaison :  
  
|**Nom**|**Type de nœud**|**Type de données**|**Description**|**Restrictions**|**Commentaires**|  
|--------------|-------------------|-------------------|---------------------|----------------------|------------------|  
|LongName|Attribut|xs:string|Spécifie le nom long du certificat.|Facultatif|Valeur par défaut : vide|  
|NomCourt|Attribut|xs:string|Spécifie le nom court du certificat.|Facultatif|Valeur par défaut : vide|  
|UsageType|Attribut|CertUsageType (SimpleType)|Indique l'utilisation prévue du certificat.|Requis|Valeur par défaut : Aucun<br /><br /> Les valeurs possibles sont celles qui sont disponibles dans le [Microsoft.BizTalk.ExplorerOM.CertUsageType](http://msdn.microsoft.com/library/microsoft.biztalk.explorerom.certusagetype.aspx) énumération.|  
|ThumbPrint|Attribut|xs:string|Indique l'empreinte, ou l'ID unique, du certificat.|Facultatif|Valeur par défaut : vide|