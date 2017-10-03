---
title: "Rétrogradation de propriétés dans les composants de Pipeline assembleur | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- XML Assembler [pipeline component], properties
- pipeline components, properties
- BizTalk Framework Assembler [pipeline component], properties
- XML Assembler [pipeline component], about XML Assembler
- Flat File Assembler [pipeline component], properties
ms.assetid: c5275638-d594-4b0d-a818-b7a9460b41a6
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: af634d302f01b18c91ebdbb7533673e8b9c545c5
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="property-demotion-in-assembler-pipeline-components"></a>Rétrogradation de propriétés dans les composants de Pipeline assembleur
Vous pouvez utiliser la rétrogradation de propriétés pour copier la valeur d'une propriété du contexte du message dans le contenu du message, son en-tête ou son code de fin. Pour rétrograder des propriétés, vous utilisez une expression XPath spécifiée dans le document ou dans le schéma d'en-tête et de code de fin.  
  
 Lors de l'écriture des données de date et d'heure de la propriété de contexte dans le document résultant, BizTalk Server considère que toutes les données de date et d'heure sont au format UTC.  
  
 Le format utilisé pour écrire des propriétés dans les données est déterminé par le type de données XSD comme indiqué dans le tableau suivant.  
  
|Type de données|Format|  
|---------------|------------|  
|xs:datetime|jj-MM-aaaaTHH:mm:ss.fffffffZ|  
|xs:date|jj-MM-aaaaZ|  
|xs:gDay|---jjZ|  
|xs:gMonth|--MM—Z|  
|xs:gMonthDay|--jj-MMZ|  
|xs:gYear|aaaaZ|  
|xs:gYearMonth|MM-aaaaZ|  
|xs:time|HH:mm:ss.fffffffZ|  
  
## <a name="property-demotion-and-envelopes"></a>Promotion des propriétés et enveloppes  
 Il est souvent utile de rétrograder les valeurs provenant d'un ou de plusieurs espaces de noms système, ou de l'un de vos propres espaces de noms, lors de l'assemblage de fichiers à l'intérieur d'une enveloppe. Voici des exemples de scénarios courants :  
  
-   Vous souhaitez inclure le nom du fichier d'origine envoyé au système dans des messages sortants de sorte que les systèmes principaux puissent suivre l'origine des données.  
  
-   Vous souhaitez écrire des données provenant du corps du message dans l'en-tête. Par exemple, pour un bon de commande, il peut être utile d'écrire le nom de livraison dans l'enveloppe pour les systèmes en aval.  
  
-   Vous souhaitez combiner plusieurs champs différents dans l'en-tête sans écrire de code personnalisé. La rétrogradation de propriétés dans l'assembleur Xml ou l'assembleur de fichier plat peut suffire.  
  
 Il est important de se souvenir que les composants Assembleur XML et Assembleur de fichier plat vous permettent de spécifier le schéma à utiliser pour l'enveloppe et le corps du document. Vous pouvez choisir les mêmes schémas utilisés lors du désassemblage ou créer un schéma d'enveloppe avec des champs différents.  
  
 Pour obtenir un exemple de ces concepts, consultez [EnvelopeProcessing (exemple BizTalk Server)](../core/envelopeprocessing-biztalk-server-sample.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Composant de Pipeline assembleur de fichier plat](../core/flat-file-assembler-pipeline-component.md)   
 [Comment configurer le composant de Pipeline d’assembleur de fichier plat](../core/how-to-configure-the-flat-file-assembler-pipeline-component.md)