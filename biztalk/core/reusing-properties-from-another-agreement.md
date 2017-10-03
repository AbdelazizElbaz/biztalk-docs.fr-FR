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
ms.openlocfilehash: 7e2a4e1efbfb7a86c18fb3643a789312a3707a72
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="reusing-properties-from-another-agreement"></a>Réutilisation des propriétés d'un autre accord
Vous pouvez réutiliser les propriétés entre les accords. Vous gagnez ainsi un temps précieux lorsque la plupart des propriétés d'un nouvel accord sont identiques à celles d'un accord existant. Dans [!INCLUDE[firstref_TPM](../includes/firstref-tpm-md.md)], l'interface utilisateur [!INCLUDE[prague](../includes/prague-md.md)] vous permet d'exporter un accord dans un fichier XML. Vous pouvez ensuite l'importer pour réutiliser les mêmes propriétés d'accord.  
  
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
  
-   [Exportation des propriétés de l’accord vers un fichier XML](../core/exporting-agreement-properties-to-an-xml-file.md)  
  
-   [L’importation des propriétés de l’accord d’un fichier XML](../core/importing-agreement-properties-from-an-xml-file.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Configuration des propriétés EDI](../core/configuring-edi-properties.md)