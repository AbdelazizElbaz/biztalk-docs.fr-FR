---
title: "Configuration de la Validation de champ croisé | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 8f0c6ae8-0b8a-4826-9dfb-bf27e5ff7fa6
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 4bde88ac82d69cdaa0dec7513e294953b7164b56
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="configuring-cross-field-validation"></a><span data-ttu-id="83c41-102">Configuration de la validation de champ croisé</span><span class="sxs-lookup"><span data-stu-id="83c41-102">Configuring Cross-Field Validation</span></span>
<span data-ttu-id="83c41-103">Cette rubrique décrit l'activation de la validation de champ croisé/segment sur les éléments de données de document informatisé dans les messages EDI.</span><span class="sxs-lookup"><span data-stu-id="83c41-103">This topic describes how to enable cross field/segment validation on transaction-set data elements in EDI-encoded messages.</span></span> <span data-ttu-id="83c41-104">Pour ce faire, vous devez définir deux paramètres :</span><span class="sxs-lookup"><span data-stu-id="83c41-104">To do so, you need to make two settings:</span></span>  
  
-   <span data-ttu-id="83c41-105">Définissez l'indicateur de validation de champ croisé dans une annotation du schéma EDI.</span><span class="sxs-lookup"><span data-stu-id="83c41-105">Set the cross-field validation flag in an annotation of the EDI schema.</span></span> <span data-ttu-id="83c41-106">Pour X12 ou les schémas HIPAA, il s’agit du **X12ConditionDesignator_Check** indicateur.</span><span class="sxs-lookup"><span data-stu-id="83c41-106">For X12 or HIPAA schemas, this is the **X12ConditionDesignator_Check** flag.</span></span> <span data-ttu-id="83c41-107">Pour les schémas EDIFACT, il s’agit du **EdifactDependencyRule_Check** indicateur.</span><span class="sxs-lookup"><span data-stu-id="83c41-107">For EDIFACT schemas, this is the **EdifactDependencyRule_Check** flag.</span></span>  
  
-   <span data-ttu-id="83c41-108">Activez la validation de type EDI dans les propriétés de l'accord.</span><span class="sxs-lookup"><span data-stu-id="83c41-108">Enable EDI-type validation in the agreement properties.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="83c41-109">Conditions préalables</span><span class="sxs-lookup"><span data-stu-id="83c41-109">Prerequisites</span></span>  
 <span data-ttu-id="83c41-110">Vous devez ouvrir une session en tant que membre du groupe Administrateurs [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="83c41-110">You must be logged on as a member of the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administrators group.</span></span>  
  
### <a name="configuring-cross-field-validation"></a><span data-ttu-id="83c41-111">Configuration de la validation de champ croisé</span><span class="sxs-lookup"><span data-stu-id="83c41-111">Configuring Cross-Field Validation</span></span>  
  
1.  <span data-ttu-id="83c41-112">Ouvrez votre schéma dans l'Éditeur BizTalk.</span><span class="sxs-lookup"><span data-stu-id="83c41-112">Open your schema in BizTalk Editor.</span></span>  
  
2.  <span data-ttu-id="83c41-113">Pour un X12 ou schéma HIPAA, recherchez le **X12ConditionDesignator_Check** indicateur dans une annotation de la section appinfo du schéma.</span><span class="sxs-lookup"><span data-stu-id="83c41-113">For an X12 or HIPAA schema, find the **X12ConditionDesignator_Check** flag in an annotation in the appinfo section of the schema.</span></span> <span data-ttu-id="83c41-114">Affectez-lui la valeur **Oui**.</span><span class="sxs-lookup"><span data-stu-id="83c41-114">Set it to **Yes**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="83c41-115">Définition de l’indicateur X12ConditionDesignator_Check à **Oui** ne peut pas être effectuée à partir de l’éditeur de schéma BizTalk.</span><span class="sxs-lookup"><span data-stu-id="83c41-115">Setting the flag X12ConditionDesignator_Check to **Yes** cannot be performed from BizTalk Schema Editor.</span></span> <span data-ttu-id="83c41-116">Pour définir cet indicateur; vous devez l’ouvrir dans le Bloc-notes ou un éditeur de texte similaire, le modifier, puis enregistrer le fichier de schéma (.xsd).</span><span class="sxs-lookup"><span data-stu-id="83c41-116">For setting the flag, you will have to open it in a notepad or similar text editor, edit, and then save the schema file (.xsd).</span></span>  
  
3.  <span data-ttu-id="83c41-117">Pour un schéma EDIFACT, recherchez le **EdifactDependencyRule_Check** indicateur dans l’annotation dans la section appinfo du schéma.</span><span class="sxs-lookup"><span data-stu-id="83c41-117">For an EDIFACT schema, find the **EdifactDependencyRule_Check** flag in the annotation in the appinfo section of the schema.</span></span> <span data-ttu-id="83c41-118">Affectez-lui la valeur **Oui**.</span><span class="sxs-lookup"><span data-stu-id="83c41-118">Set it to **Yes**.</span></span>  
  
4.  <span data-ttu-id="83c41-119">Pour les segments applicables du schéma, spécifiez les conditions relationnelles (X12 et HIPAA) ou les règles de dépendance (EDIFACT) applicables.</span><span class="sxs-lookup"><span data-stu-id="83c41-119">For the applicable segments of the schema, specify the relational conditions (X12 and HIPAA) or dependency rules (EDIFACT) that apply.</span></span> <span data-ttu-id="83c41-120">Pour plus d’informations, consultez [Validation croisée du Segment de champ](../core/cross-field-segment-validation.md).</span><span class="sxs-lookup"><span data-stu-id="83c41-120">For more information, see [Cross Field-Segment Validation](../core/cross-field-segment-validation.md).</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="83c41-121">Une condition ou une règle de validation de champ croisé est entrée pour un segment dans un schéma EDI.</span><span class="sxs-lookup"><span data-stu-id="83c41-121">A cross-field validation condition or rule is entered for a segment in an EDI schema.</span></span> <span data-ttu-id="83c41-122">Si vous entrez une règle de validation de champ croisé pour un élément de données au lieu d'un segment, [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] génère un avertissement lors de la validation du schéma.</span><span class="sxs-lookup"><span data-stu-id="83c41-122">If you enter a cross-field validation rule for a data element, rather than a segment, [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] will generate a warning when schema validation is performed.</span></span>  
  
5.  <span data-ttu-id="83c41-123">Dans le **Validation** page (sous la **paramètres des documents informatisés** section) de l’onglet d’accord unidirectionnel de la **propriétés de l’accord** boîte de dialogue pour l’accord approprié, Assurez-vous que le **Validation de type EDI** propriété est sélectionnée.</span><span class="sxs-lookup"><span data-stu-id="83c41-123">In the **Validation** page (under the **Transaction Set Settings** section) of the one-way agreement tab of the **Agreement Properties** dialog box for relevant agreement, make sure that the **EDI type Validation** property is selected.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="83c41-124">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="83c41-124">See Also</span></span>  
 [<span data-ttu-id="83c41-125">Développement des schémas EDI</span><span class="sxs-lookup"><span data-stu-id="83c41-125">Developing EDI Schemas</span></span>](../core/developing-edi-schemas.md)