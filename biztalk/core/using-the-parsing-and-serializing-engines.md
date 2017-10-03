---
title: "À l’aide de l’analyse et la sérialisation des moteurs | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- parsing engine
- pipeline components [custom], engines
- serialization engine
- pipeline components [custom], assembling
- pipeline components [custom], parsing
ms.assetid: a9d19703-b074-402a-971a-b2a6cd5d0724
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 1e820b2dce1257ec948aa214c9fdf1d43a6a7152
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="using-the-parsing-and-serializing-engines"></a>À l’aide de moteurs d’analyse et de sérialisation
Microsoft [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] inclut un moteur d'analyse et de sérialisation permettant de simplifier le processus d'analyse et de sérialisation des documents de fichier plat.  
  
 Le moteur d'analyse est un cadre piloté par schéma qui peut analyser un grand nombre de formats de document différents dans XML. Par ailleurs, il dispose d'un modèle d'extensibilité bien défini permettant de simplifier encore plus facilement l'analyse des formats personnalisés.  
  
 Des désassembleurs sont utilisés pour les analyses complexes. Outre la conversion du format natif en XML, le désassembleur peut également séparer un document unique en plusieurs documents.  
  
 Le moteur de sérialisation fonctionne de la même manière, excepté qu'il effectue la procédure inverse. Alors que le moteur d'analyse convertit les formats natifs en XML, celui de sérialisation convertit les XML en formats natifs. Et tout comme le moteur d'analyse utilise des désassembleurs, celui de sérialisation utilise des assembleurs.  
  
 Cette section explique comment procéder au codage des caractères, à l'analyse et à la sérialisation basées sur les schémas XSD (XML Schema Definition language), ainsi qu'à d'autres tâches courantes à l'aide des API des moteurs d'analyse et de sérialisation.  
  
## <a name="in-this-section"></a>Dans cette section  
  
-   [Implémentation d’encodage de caractères dans un composant de Pipeline](../core/implementing-character-encoding-in-a-pipeline-component.md)  
  
-   [À l’aide de schémas](../core/using-schemas.md)  
  
-   [Utilisation du moteur d’analyse de fichier plat](../core/using-the-flat-file-parsing-engine.md)  
  
-   [Utilisation du moteur de sérialisation de fichier plat](../core/using-the-flat-file-serializing-engine.md)