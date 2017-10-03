---
title: "TransportType (nœud SecondaryTransport) | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: TransportType node [binding file]
ms.assetid: ed66c7ef-32b6-4110-b932-f96a45a29618
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 7bb0b9460e6c4689dab169a37a9d6b6c51753598
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="transporttype-secondarytransport-node"></a>TransportType (nœud SecondaryTransport)
Le nœud TransportType du nœud SecondaryTransport d'un fichier de liaison contient des informations sur l'adaptateur associé à un transport exporté avec le fichier de liaison.  
  
## <a name="nodes-in-the-transporttype-node"></a>Nœuds du nœud TransportType  
 Le tableau suivant répertorie les propriétés que vous pouvez définir pour ce nœud d'un fichier de liaison :  
  
|**Nom**|**Type de nœud**|**Type de données**|**Description**|**Restrictions**|**Commentaires**|  
|--------------|-------------------|-------------------|---------------------|----------------------|------------------|  
|Nom|Attribut|xs:string|Spécifie le nom de l'adaptateur associé au transport.|Facultatif|Valeur par défaut : vide|  
|Fonctions|Attribut|xs:int|Spécifie les fonctions de l'adaptateur associé au transport.|Requis|Valeur par défaut : Aucun<br /><br /> Les valeurs possibles sont celles qui sont disponibles dans l'énumération [Microsoft.BizTalk.ExplorerOM.Capabilities](http://msdn.microsoft.com/library/microsoft.biztalk.explorerom.capabilities.aspx) .|  
|ConfigurationClsid|Attribut|xs:string|Spécifie le GUID de configuration de l'adaptateur associé au transport.|Facultatif|Valeur par défaut : vide|