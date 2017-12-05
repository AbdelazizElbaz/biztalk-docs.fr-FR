---
title: "À l’aide de l’outil XML Extensions | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 5613bf15-6c0a-4a82-b200-24d0801d7ece
caps.latest.revision: "11"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 976082fc14eb37d550956ec447eb63938706daa3
ms.sourcegitcommit: 3fc338e52d5dbca2c3ea1685a2faafc7582fe23a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/01/2017
---
# <a name="using-the-xml-tool-extensions"></a>Utilisation des extensions de l'outil XML
Les extensions de l'outil XML pour [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] permettent de réaliser des tâches sur les schémas, les mappages et les instances de message. Vous utilisez ces extensions au moment de la conception dans l'environnement [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]. Less tâches que vous pouvez réaliser sont les suivantes :  
  
-   **Validation d’un schéma**. Cette opération valide un schéma EDI selon des règles EDI. Pour plus d’informations, consultez [valider un schéma (EDI)](../core/validating-a-schema-edi.md).  
  
-   **Validation d’une instance de message**. Cette opération valide un document informatisé unique (sans en-tête d'échange et de groupe) ou un échange traité par lot complet comprenant plusieurs documents informatisés (avec en-têtes d'échange et de groupe). Pour valider un échange non regroupé, vous devez supprimer les en-têtes d'échange et de groupe de l'instance. Pour plus d’informations, consultez [valider une Instance (EDI)](../core/validating-an-instance-edi.md).  
  
-   **Génération d’une instance de message**. Cette opération génère soit un échange par lot complet, soit un document informatisé sans en-têtes d'échange et de groupe. Vous devez spécifier les séparateurs, les identificateurs et toute mise en forme utilisée pour générer l'instance. Pour plus d’informations, consultez [génération d’une Instance (EDI)](../core/generating-an-instance-edi.md).  
  
-   **Test d’un mappage**. Cette opération génère un document de sortie (avec des données fictives) basé sur un document source et un mappage. Pour plus d’informations, consultez [test d’un mappage](../core/testing-a-map.md).  
  
-   **Validation d’un mappage**. Cette opération a pour effet de générer un fichier contenant le XSLT sous-jacent du mappage ainsi qu'un autre fichier contenant les objets d'extension. Pour plus d’informations, consultez [valider un mappage (EDI)](../core/validating-a-map-edi.md).  
  
 Dans BizTalk Server, ces extensions fonctionnent sur les schémas EDI, les mappages et les instances de message. Elles vous permettent de travailler plus efficacement avec les schémas, mappages et échanges EDI complexes.  
  
 Les extensions de l'outil XML sont activées par défaut par le programme d'installation de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]. Si vous double-cliquez sur un schéma dans l’Explorateur de solutions de Visual Studio, le **Extensions de l’éditeur de schéma** du schéma est définie sur **Extension de l’éditeur de schéma EDI**. Cette configuration est nécessaire au bon fonctionnement des extensions de l'outil XML. Vous pouvez sélectionner une autre extension d'éditeur de schéma en conservant la sélection des extensions EDI.  
  
## <a name="see-also"></a>Voir aussi  
 [Génération d’une Instance (EDI)](../core/generating-an-instance-edi.md)   
 [Validation d’une Instance (EDI)](../core/validating-an-instance-edi.md)   
 [Validation d’un schéma (EDI)](../core/validating-a-schema-edi.md)   
 [Test d’un mappage](../core/testing-a-map.md)   
 [Validation d’un mappage (EDI)](../core/validating-a-map-edi.md)