---
title: "Spécification de Page pour les schémas de fichier plat de code | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 825e75f1-893c-4c61-b566-f893d732a907
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 64d5cfbc960346e702ed0d4a39ca74bbc4b3634c
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="code-page-specification-for-flat-file-schemas"></a>Spécification de Page de codes pour les schémas de fichier plat

## <a name="overview"></a>Vue d'ensemble
La valeur de la **Page de codes** propriété est utilisée pour créer un objet d’encodage qui est utilisé pendant le désassemblage et assemblage de documents de fichier plat. Cet objet de codage permet à l'analyseur de fichier plat de convertir le codage natif d'un document de fichier plat entrant en codage UTF-8 normalisé, utilisé de façon interne par Microsoft [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]. L'objet de codage permet également au sérialiseur de fichier plat de reconvertir le codage UTF-8 interne en codage natif du document de fichier plat.  
  
 Le paramètre de la **Page de codes** propriété joue un rôle d’important mais non exclusif pour déterminer le schéma de codage de caractères utilisé par vos documents commerciaux de fichier plat. Vous devez prendre en compte la manière dont les messages de fichier plat entrants sont interprétés par le désassembleur de fichier plat et dont l'assembleur de fichier plat codera les caractères tandis que les messages sortants seront convertis au format de fichier plat.  

## <a name="character-encoding"></a>Encodage de caractères  
 Plusieurs facteurs déterminent la manière dont le codage de caractères pour un message d'instance donné est géré :  
  
-   Lors du désassemblage d'un message d'instance de fichier plat, l'algorithme suivant est utilisé pour déterminer et conserver les informations de codage :  
  
    1.  Si le **Charset** dans le corps du Message n’est définie, sa valeur est utilisée.  
  
    2.  Sinon, si le schéma d’enveloppe (ou de document) spécifie une page de code à l’aide de la **Page de codes** propriété, sa valeur est utilisée.  
  
    3.  Sinon, si une marque d'ordre de tri est présente, sa valeur est utilisée.  
  
    4.  Sinon, on suppose UTF-8.  
  
-   Lors de l’assemblage d’un message d’instance de fichier plat, l’algorithme suivant est utilisé pour déterminer le jeu de caractères à utiliser pour le décodage :  
  
-   Si le **XMLNorm.TargetCharset** propriété de contexte de message est définie, sa valeur est utilisée.  
  
-   Sinon, si le **TargetCharset** assembleur (au moment du design) est définie, sa valeur est utilisée.  
  
-   Sinon, si le schéma d’enveloppe (ou de document) spécifie une page de code à l’aide de la **Page de codes** propriété, sa valeur est utilisée.  
  
    1.  Sinon, si le **SourceCharset** propriété de contexte de message est définie, sa valeur est utilisée.  
  
    2.  Sinon, utiliser UTF-8.  
  
## <a name="see-also"></a>Voir aussi  
 **Schémas de Message de fichier de considérations relatives à la création de plat** et **(propriété de nœud des schémas de fichier plat) de Page de codes**[!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]