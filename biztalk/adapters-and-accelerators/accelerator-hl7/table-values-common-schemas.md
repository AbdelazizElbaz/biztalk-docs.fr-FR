---
title: "Table les valeurs des schémas courants | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- 2.X schemas, common schemas
- 2.X schemas, table values
- common schemas
ms.assetid: 2421e150-1bae-43bd-aba3-6322c679b22b
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 8b93434c57988b8ef0cdb068ffb960e6fb342edc
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="table-values-common-schemas"></a>Table les valeurs des schémas courants
[!INCLUDE[btsCoName](../../includes/btsconame-md.md)]BizTalk Accelerator pour HL7 ([!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]) génère le  **tablevalues_*\<version >*.xsd ** de fichier pour chaque version HL7 et recherche le fichier à la racine de la HL7 dossier de version spécifique. Le fichier de schéma commune du type de données référence le fichier de schéma table les valeurs courantes.  
  
 Les valeurs dans ces tables sont sous la forme d’énumérations. Chaque énumération définit les valeurs qui sont acceptables dans un ou plusieurs champs des schémas de message. Vous pouvez voir la table qui s’applique à un nœud d’un schéma de message en ouvrant le schéma dans l’Éditeur BizTalk, en cliquant sur un nœud et en examinant le **Base Data Type** propriété dans le volet Propriétés.  
  
 Vous ne serez pas en mesure de voir quels sont les valeurs acceptables pour ce nœud, toutefois, en affichant l’énumération dans le volet Propriétés pour le nœud de schéma de message. Il s’agit, car le fichier de schéma commune table valeurs définit l’énumération. Pour afficher les énumérations, cliquez sur  **tablevalues_*\<version >*.xsd ** dans le schéma de l’arborescence dans l’Éditeur BizTalk, puis cliquez sur le bouton de sélection (**...** ) bouton sur la ligne de l’énumération dans le volet Propriétés.  
  
## <a name="see-also"></a>Voir aussi  
 [Fichiers de schéma HL7 2.X communs](../../adapters-and-accelerators/accelerator-hl7/hl7-2-x-common-schema-files.md)   
 [Types de données des schémas courants](../../adapters-and-accelerators/accelerator-hl7/data-types-common-schemas.md)   
 [Les segments de schémas courants](../../adapters-and-accelerators/accelerator-hl7/segments-common-schemas.md)