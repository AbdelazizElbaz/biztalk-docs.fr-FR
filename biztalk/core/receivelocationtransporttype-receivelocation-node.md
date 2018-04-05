---
title: ReceiveLocationTransportType (nœud ReceiveLocation) | Documents Microsoft
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- ReceiveLocationTransportType node [binding file]
ms.assetid: 375076c3-d5e6-4c25-b054-b452e29717e0
caps.latest.revision: 6
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: d0eae3e2c4fd9f5f668cb12ffd630640b1b63c74
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="receivelocationtransporttype-receivelocation-node"></a>ReceiveLocationTransportType (nœud ReceiveLocation)
Le nœud ReceiveLocationTransportType du nœud ReceiveLocation d'un fichier de liaison contient des informations sur l'adaptateur associé à un transport exporté avec le fichier de liaison.  
  
## <a name="nodes-in-the-receivelocationtransporttype-node"></a>Nœuds du nœud ReceiveLocationTransportType  
 Le tableau suivant répertorie les propriétés que vous pouvez définir pour ce nœud d'un fichier de liaison :  
  
|**Nom**|**Type de nœud**|**Type de données**|**Description**|**Restrictions**|**Commentaires**|  
|--------------|-------------------|-------------------|---------------------|----------------------|------------------|  
|Nom|Attribut|xs:string|Spécifie le nom de l'adaptateur associé au transport.|Facultatif|Valeur par défaut : vide|  
|Fonctions|Attribut|xs:int|Spécifie les fonctions de l'adaptateur associé au transport.|Requis|Valeur par défaut : Aucun<br /><br /> Les valeurs possibles sont celles qui sont disponibles dans l'énumération [Microsoft.BizTalk.ExplorerOM.Capabilities](http://msdn.microsoft.com/library/microsoft.biztalk.explorerom.capabilities.aspx) .|  
|ConfigurationClsid|Attribut|xs:string|Spécifie le GUID de configuration de l'adaptateur associé au transport.|Facultatif|Valeur par défaut : vide|