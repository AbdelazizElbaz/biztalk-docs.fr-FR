---
title: "L’échange contenait un ISA incorrect ou le schéma de Service n’était pas disponible | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 78d285f6-26fb-4a3b-a959-a17623321b20
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 84aec7600b71d48becfdeb30e34f837292c5ecfa
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="the-interchange-contained-a-malformed-isa-or-the-service-schema-was-not-available"></a>L'échange contenait un ISA incorrect ou le schéma Service n'était pas disponible
## <a name="details"></a>Détails  
  
|||  
|-|-|  
|Nom du produit|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|Version du produit|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|ID d'événement|-|  
|Source de l'événement|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] EDI|  
|Composant|Moteur EDI|  
|Nom symbolique|MalformedIsaError|  
|Texte du message|L'échange contenait un ISA incorrect ou le schéma Service n'était pas disponible, il est entièrement rejeté|  
  
## <a name="explanation"></a>Explication  
 Cet événement d'erreur/d'avertissement/d'informations indique que le pipeline de réception n'a pas pu traiter l'échange entrant, car le segment ISA ou IEA n'est pas conforme au X12ServiceSchema, ou X12ServiceSchema (dans BaseArtifacts.dll) n'est pas déployé.  
  
## <a name="user-action"></a>Action de l'utilisateur  
 Pour résoudre cette erreur, effectuez l’une des opérations suivantes :  
  
-   Demandez à l'expéditeur de l'échange de modifier les segments ISA et IEA de manière à ce qu'ils soient conformes au X12ServiceSchema.  
  
-   Assurez-vous que le fichier BaseArtifacts.dll inclut le X12ServiceSchema et que ce dernier est déployé. Pour ce faire, ouvrez la console Administration de BizTalk Server, développez successivement le nœud Application BizTalk EDI, le nœud Schémas, puis vérifiez que X12ServiceSchema est bien répertorié.