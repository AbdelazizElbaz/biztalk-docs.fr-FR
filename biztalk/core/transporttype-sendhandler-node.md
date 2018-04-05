---
title: TransportType (nœud SendHandler) | Documents Microsoft
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- TransportType node [binding file]
ms.assetid: ee87a409-33dd-4111-ba6a-ead3bacc80aa
caps.latest.revision: 7
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: c3525b78fa9812c1e4fa8690a622f9b8cccce8d7
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="transporttype-sendhandler-node"></a>TransportType (nœud SendHandler)
Le nœud TransportType du nœud SendHandler d'un fichier de liaison contient des informations sur l'adaptateur associé à un gestionnaire d'envoi exporté avec le fichier de liaison.  
  
## <a name="nodes-in-the-transporttype-node"></a>Nœuds du nœud TransportType  
 Le tableau suivant répertorie les propriétés que vous pouvez définir pour ce nœud d'un fichier de liaison :  
  
|**Nom**|**Type de nœud**|**Type de données**|**Description**|**Restrictions**|**Commentaires**|  
|--------------|-------------------|-------------------|---------------------|----------------------|------------------|  
|Nom|Attribut|xs:string|Spécifie le nom de l'adaptateur associé au gestionnaire d'envoi.|Facultatif|Valeur par défaut : vide|  
|Fonctions|Attribut|xs:int|Spécifie les fonctions de l'adaptateur associé au gestionnaire d'envoi.|Requis|Valeur par défaut : Aucun<br /><br /> Les valeurs possibles sont celles qui sont disponibles dans l'énumération [Microsoft.BizTalk.ExplorerOM.Capabilities](http://msdn.microsoft.com/library/microsoft.biztalk.explorerom.capabilities.aspx) .|  
|ConfigurationClsid|Attribut|xs:string|Spécifie le GUID de configuration de l'adaptateur associé au gestionnaire d'envoi.|Facultatif|Valeur par défaut : vide|