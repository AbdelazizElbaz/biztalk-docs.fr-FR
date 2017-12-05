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
ms.openlocfilehash: a55491f0a44bec6a5cd5eaf4fe120f693b3996c5
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="table-values-common-schemas"></a><span data-ttu-id="151dd-102">Table les valeurs des schémas courants</span><span class="sxs-lookup"><span data-stu-id="151dd-102">Table Values Common Schemas</span></span>
[!INCLUDE[btsCoName](../../includes/btsconame-md.md)]<span data-ttu-id="151dd-103">BizTalk Accelerator pour HL7 ([!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]) génère le  **tablevalues_*\<version\>*.xsd ** de fichier pour chaque version HL7 et recherche le fichier à la racine de la Dossier spécifique à la version de HL7.</span><span class="sxs-lookup"><span data-stu-id="151dd-103"> BizTalk Accelerator for HL7 ([!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)]) generates the **tablevalues_*\<version\>*.xsd** file for each HL7 version, and locates the file at the root of the HL7 version-specific folder.</span></span> <span data-ttu-id="151dd-104">Le fichier de schéma commune du type de données référence le fichier de schéma table les valeurs courantes.</span><span class="sxs-lookup"><span data-stu-id="151dd-104">The data type common schema file references the table values common schema file.</span></span>  
  
 <span data-ttu-id="151dd-105">Les valeurs dans ces tables sont sous la forme d’énumérations.</span><span class="sxs-lookup"><span data-stu-id="151dd-105">Values in these tables are in the form of enumerations.</span></span> <span data-ttu-id="151dd-106">Chaque énumération définit les valeurs qui sont acceptables dans un ou plusieurs champs des schémas de message.</span><span class="sxs-lookup"><span data-stu-id="151dd-106">Each enumeration defines the values that are acceptable within one or more fields of the message schemas.</span></span> <span data-ttu-id="151dd-107">Vous pouvez voir la table qui s’applique à un nœud d’un schéma de message en ouvrant le schéma dans l’Éditeur BizTalk, en cliquant sur un nœud et en examinant le **Base Data Type** propriété dans le volet Propriétés.</span><span class="sxs-lookup"><span data-stu-id="151dd-107">You can see which table applies to a node of a message schema by opening the schema in BizTalk Editor, clicking a node, and looking at the **Base Data Type** property in the Properties pane.</span></span>  
  
 <span data-ttu-id="151dd-108">Vous ne serez pas en mesure de voir quels sont les valeurs acceptables pour ce nœud, toutefois, en affichant l’énumération dans le volet Propriétés pour le nœud de schéma de message.</span><span class="sxs-lookup"><span data-stu-id="151dd-108">You will not be able to see what the acceptable values for this node are, however, by viewing the enumeration in the Properties pane for the message-schema node.</span></span> <span data-ttu-id="151dd-109">Il s’agit, car le fichier de schéma commune table valeurs définit l’énumération.</span><span class="sxs-lookup"><span data-stu-id="151dd-109">This is because the table values common schema file defines the enumeration.</span></span> <span data-ttu-id="151dd-110">Pour afficher les énumérations, cliquez sur  **tablevalues_*\<version\>*.xsd ** dans le schéma de l’arborescence dans l’Éditeur BizTalk, puis cliquez sur le bouton de sélection (**...** ) bouton sur la ligne de l’énumération dans le volet Propriétés.</span><span class="sxs-lookup"><span data-stu-id="151dd-110">To view the enumerations, click **tablevalues_*\<version\>*.xsd** in the Schema tree in BizTalk Editor, and then click the ellipsis (**...**) button on the Enumeration row in the Properties pane.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="151dd-111">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="151dd-111">See Also</span></span>  
 <span data-ttu-id="151dd-112">[Fichiers de schéma HL7 2.X communs](../../adapters-and-accelerators/accelerator-hl7/hl7-2-x-common-schema-files.md) </span><span class="sxs-lookup"><span data-stu-id="151dd-112">[HL7 2.X Common Schema Files](../../adapters-and-accelerators/accelerator-hl7/hl7-2-x-common-schema-files.md) </span></span>  
 <span data-ttu-id="151dd-113">[Types de données des schémas courants](../../adapters-and-accelerators/accelerator-hl7/data-types-common-schemas.md) </span><span class="sxs-lookup"><span data-stu-id="151dd-113">[Data Types Common Schemas](../../adapters-and-accelerators/accelerator-hl7/data-types-common-schemas.md) </span></span>  
 [<span data-ttu-id="151dd-114">Schémas communs de segments</span><span class="sxs-lookup"><span data-stu-id="151dd-114">Segments Common Schemas</span></span>](../../adapters-and-accelerators/accelerator-hl7/segments-common-schemas.md)