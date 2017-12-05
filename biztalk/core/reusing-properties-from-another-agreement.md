---
title: "Réutilisation des propriétés d’un autre accord | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d8e1cc60-d581-43ca-aa70-1e0d6238497a
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: d7db2118f372014a3e8f108c1ff2273bc5aad976
ms.sourcegitcommit: 3fc338e52d5dbca2c3ea1685a2faafc7582fe23a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/01/2017
---
# <a name="reusing-properties-from-another-agreement"></a>Réutilisation des propriétés d'un autre accord
Vous pouvez réutiliser les propriétés entre les accords. Vous gagnez ainsi un temps précieux lorsque la plupart des propriétés d'un nouvel accord sont identiques à celles d'un accord existant. Le [!INCLUDE[firstref_TPM](../includes/firstref-tpm-md.md)] interface utilisateur de BizTalk Server vous permet d’exporter un accord dans un fichier de modèle XML. Vous pouvez ensuite l'importer pour réutiliser les mêmes propriétés d'accord.  
  
 L'exportation de l'accord dans un modèle XML permet de capturer la majorité, et non pas la totalité, des propriétés d'un accord. Les propriétés suivantes seront *pas* être exportées vers le fichier XML :  
  
-   Toutes les propriétés de la **propriétés générales** page dans le **général** onglet.  
  
-   Toutes les propriétés de la **Contacts** page dans le **général** onglet.  
  
-   Toutes les propriétés de la **des propriétés supplémentaires** page dans le **général** onglet.  
  
-   Dépendant de l’identificateur de paramètres à partir de la **identificateurs** page sous l’onglet d’accord unidirectionnel. Il s'agit des paramètres suivants :  
  
    -   **Pour X12**: ISA5, ISA6, ISA7, ISA8 et les paramètres du résolveur d’accord supplémentaire  
  
    -   **Pour EDIFACT**: UNB 2.1, UNB 2.2, UNB 3.1, UNB 3.2 et paramètres du résolveur d’accord supplémentaire  
  
    -   **Pour AS2**: AS2-To, AS2-From et les paramètres du résolveur d’accord supplémentaire  
  
-   Envoyer l’association de ports à partir de la **Ports d’envoi** page sous l’onglet d’accord unidirectionnel pour X12, EDIFACT et AS2 de contrats.  
  
 À l'exception des propriétés mentionnées précédemment, les propriétés suivantes seront exportées dans le fichier XML :  
  
-   Tous les paramètres ayant trait au protocole de codage (X12, EDIFACT ou AS2).  
  
-   Tous les paramètres ayant trait aux lots (autres que l'ID de lot).  
  
> [!NOTE]
>  Toutes les propriétés applicables seront remplacées lors de la copie des propriétés dans l'accord de destination.  
  
## <a name="in-this-section"></a>Dans cette section  
  
-   [Exportation des propriétés d’un accord vers un fichier XML](../core/exporting-agreement-properties-to-an-xml-file.md)  
  
-   [Importation des propriétés d’un accord à partir d’un fichier XML](../core/importing-agreement-properties-from-an-xml-file.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Configuration des propriétés EDI](../core/configuring-edi-properties.md)