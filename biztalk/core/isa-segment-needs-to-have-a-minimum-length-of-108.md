---
title: Le segment ISA doit avoir une longueur minimale de 108 | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 57641445-cebb-4219-998d-54038d7ddf19
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 5ecd5c6761c6dbcc59ad6353efa2772b9eecf387
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="isa-segment-needs-to-have-a-minimum-length-of-108"></a>Le segment ISA doit avoir une longueur minimale de 108.
## <a name="details"></a>Détails  
  
|||  
|-|-|  
|Nom du produit|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|Version du produit|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|ID d'événement|-|  
|Source de l'événement|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] EDI|  
|Composant|Moteur EDI|  
|Nom symbolique|NseIsaSuffix1LFDescription|  
|Texte du message|Le segment ISA doit avoir une longueur minimale de 108, l'instance a {0}|  
  
## <a name="explanation"></a>Explication  
 Cet événement de type erreur/avertissement/information indique que le pipeline de réception n'a pas pu traiter l'échange entrant, car le segment ISA de celui-ci n'était pas conforme au nombre de chiffres établi par le schéma de service (X12ServiceSchema ou EdifactServiceSchema dans BaseArtifacts.dll).  
  
## <a name="user-action"></a>Action de l'utilisateur  
 Pour résoudre cette erreur, vérifiez que chacun des champs du segment ISA (de ISA01 à ISA16) comporte le nombre de chiffres minimum requis. Pour savoir quel est le nombre de chiffres minimum, ouvrez la console Administration de BizTalk Server, le nœud Groupe BizTalk, le nœud Applications, le nœud Application BizTalk EDI, puis le nœud de schéma. Ouvrez ensuite Microsoft.BizTalk.Edi.BaseArtifacts.X12ServiceSchema avec le nœud racine d'ISA, puis cliquez sur Affichage de schéma.