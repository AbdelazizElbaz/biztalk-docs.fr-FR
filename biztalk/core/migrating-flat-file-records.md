---
title: Migration des enregistrements de fichier plat | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 75cd5fbc-66c1-4c8b-b81a-1d028e9647b4
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 28daa8426dff3d9cbe9330430e4ba3de64410e5b
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="migrating-flat-file-records"></a>Migration des enregistrements de fichier plat
Au cours de l'analyse et de la sérialisation, Microsoft [!INCLUDE[btsBizTalkServer2000](../includes/btsbiztalkserver2000-md.md)] et Microsoft [!INCLUDE[btsBizTalkServer2002](../includes/btsbiztalkserver2002-md.md)] ne prennent en charge que les délimiteurs à caractère unique dans les enregistrements de fichier plat. Cette restriction est compensée par une plus grande souplesse dans la gestion des délimiteurs. [!INCLUDE[btsBizTalkServer2000](../includes/btsbiztalkserver2000-md.md)]et [!INCLUDE[btsBizTalkServer2002](../includes/btsbiztalkserver2002-md.md)] prennent également en charge la définition de délimiteurs différents sur les enregistrements, les champs et sous-champs. Microsoft [!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)] prend par contre en charge les délimiteurs multicaractères, quoique d'un seul type appelé délimiteur enfant. Les améliorations relatives à la gestion des délimiteurs risquent d'avoir une incidence sur la manière dont les enregistrements de fichier plat [!INCLUDE[btsBizTalkServer2000](../includes/btsbiztalkserver2000-md.md)] et [!INCLUDE[btsBizTalkServer2002](../includes/btsbiztalkserver2002-md.md)] sont gérés dans [!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)].  
  
 Trois annotations de schéma contrôlent délimiteur de traitement dans [!INCLUDE[btsBizTalkServer2000](../includes/btsbiztalkserver2000-md.md)] et [!INCLUDE[btsBizTalkServer2002](../includes/btsbiztalkserver2002-md.md)], deux pour l’analyse (**skip_CR**, **skip_LF**) et une pour la sérialisation (**append_newline** ). [!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)]interprète ces annotations comme suit lors de la migration enregistrements :  
  
-   Si le **skip_CR** annotation a la valeur **true** et le délimiteur actuel n’est pas retour chariot (0x0D), [!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)] ajoute un retour chariot au délimiteur actuel. Par exemple, si le délimiteur actuel était la barre verticale (0x7C), le délimiteur résultant serait une barre verticale suivie d'un retour chariot (0x7C 0x0D). Si le délimiteur actuel est un retour chariot, il reste comme seul retour, quelle que soit la valeur de **skip_CR**.  
  
-   Si le **skip_LF** annotation a la valeur **true**, [!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)] ajoute un saut de ligne de caractères (0x0A) au délimiteur actuel. Notez que dans le cas précédent, où le délimiteur actuel est la barre verticale (0x7C), un délimiteur à trois caractères résulte (0x7C 0x0D 0x0A) si les deux **skip_CR** et **skip_LF** sont **lavaleurtrue**.  
  
-   [!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)]ignore le paramètre de la **append_newline** annotation.  
  
 Ces interprétations des annotations garantissent une migration sans difficulté la plupart du temps. Par exemple, si **skip_CR** et **skip_LF** sont tous deux **true** et le délimiteur actuel est le symbole de barre verticale (0x7C), [!INCLUDE[btsBizTalkServer2000](../includes/btsbiztalkserver2000-md.md)] et [!INCLUDE[btsBizTalkServer2002](../includes/btsbiztalkserver2002-md.md)] accepte tous les suivant en tant que délimiteurs valides dans un seul jeu d’enregistrements : 0x7C 0x0D 0x0A, 0x7C 0x0D, 0x7C 0x0A et 0x7C. Les enregistrements utilisant de tels ensembles de délimiteurs ne peuvent être migrés et requièrent un code d'analyseur personnalisé dans [!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)].  
  
 Bien que [!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)] n'ait qu'un seul type de délimiteur, il interprète les anciennes annotations de manière à ce que les enregistrements migrent facilement. Si un [!INCLUDE[btsBizTalkServer2000](../includes/btsbiztalkserver2000-md.md)] ou [!INCLUDE[btsBizTalkServer2002](../includes/btsbiztalkserver2002-md.md)] schéma comporte des valeurs pour **def_record_delimdef_field_delim**, **def_subfield_delim**, et ils sont référencés dans **delimiter_type** en tant que **inherit_record**, et ainsi de suite, [!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)] extrait la valeur correspondante et la stocke localement.  
  
 De plus, [!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)] ajoute des champs aux enregistrements positionnels marqués sans enfants.  
  
## <a name="see-also"></a>Voir aussi  
 [Problèmes connus avec la Validation et génération de schéma](../core/known-issues-with-schema-generation-and-validation.md)