---
title: "Valider les données d’Instance | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 19c3ca83-0abf-42ba-8e29-653ff12d5e20
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 86cde9d6133959e34ec09880be8a6beca5c37191
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="validate-instance-data"></a><span data-ttu-id="a7874-102">Valider les données d’Instance</span><span class="sxs-lookup"><span data-stu-id="a7874-102">Validate Instance Data</span></span>

## <a name="overview"></a><span data-ttu-id="a7874-103">Vue d'ensemble</span><span class="sxs-lookup"><span data-stu-id="a7874-103">Overview</span></span>
<span data-ttu-id="a7874-104">Au cours du processus de test d'un mappage, vous souhaiterez peut-être valider les données de l'instance par rapport aux schémas source et de destination afin de vérifier que les données de l'instance sont conformes à la structure des schémas.</span><span class="sxs-lookup"><span data-stu-id="a7874-104">During the process of testing a map, you may want to validate instance data against the source and destination schemas to verify that the instance data adheres to the schema structure.</span></span> <span data-ttu-id="a7874-105">Pour valider un message d’instance par rapport au schéma source ou de destination, cliquez sur le schéma dans l’Explorateur de solutions, puis cliquez sur **valider l’Instance**.</span><span class="sxs-lookup"><span data-stu-id="a7874-105">To validate an instance message against the source or destination schema, right-click the schema in the Solution Explorer, and then click **Validate Instance**.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="a7874-106">Si vous utilisez des données personnalisées ou des constantes dans votre sortie, vous devez vérifier que les types de vos données de test sources et les valeurs des constantes cibles sont valides.</span><span class="sxs-lookup"><span data-stu-id="a7874-106">If you use custom data or constants in your output, you must verify that the data types of your source test data and target constant values are valid.</span></span> <span data-ttu-id="a7874-107">Quand vous validez un mappage, le Mappeur BizTalk ne vérifie pas si les données d'instance violent des types de données définis dans les schémas.</span><span class="sxs-lookup"><span data-stu-id="a7874-107">When you validate a map, BizTalk Mapper does not check whether or not the instance data violates any data types defined by the schemas.</span></span> <span data-ttu-id="a7874-108">Cette vérification a lieu lorsque vous testez le mappage ou que vous validez les données d'instance.</span><span class="sxs-lookup"><span data-stu-id="a7874-108">This is done when you test the map or validate the instance data.</span></span>  
  
 <span data-ttu-id="a7874-109">Pour plus d’informations sur comment générer et valider les données d’instance à l’aide de l’Éditeur BizTalk, consultez [génération d’un Message d’Instance et la Validation](../core/instance-message-generation-and-validation.md) et [Validation de l’Instance](../core/instance-validation.md).</span><span class="sxs-lookup"><span data-stu-id="a7874-109">For more information about how to generate and validate instance data by using BizTalk Editor, see [Instance Message Generation and Validation](../core/instance-message-generation-and-validation.md) and [Instance Validation](../core/instance-validation.md).</span></span> <span data-ttu-id="a7874-110">.</span><span class="sxs-lookup"><span data-stu-id="a7874-110">.</span></span> <span data-ttu-id="a7874-111">Le **valeur** propriété du nœud d’un schéma affecte également la façon dont BizTalk génère des données d’instance.</span><span class="sxs-lookup"><span data-stu-id="a7874-111">The **Value** property of the node of a schema also affects how BizTalk generates instance data.</span></span> <span data-ttu-id="a7874-112">Pour plus d’informations, consultez la **propriétés de nœud de schéma** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)].</span><span class="sxs-lookup"><span data-stu-id="a7874-112">For more information, see the **Schema Node Properties** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)].</span></span>
  
## <a name="see-also"></a><span data-ttu-id="a7874-113">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a7874-113">See Also</span></span>  
-  [<span data-ttu-id="a7874-114">Validation et génération de Message d’instance</span><span class="sxs-lookup"><span data-stu-id="a7874-114">Instance Message Generation and Validation</span></span>](../core/instance-message-generation-and-validation.md)   
-  [<span data-ttu-id="a7874-115">Comment valider des schémas dans Visual Studio</span><span class="sxs-lookup"><span data-stu-id="a7874-115">How to Validate Schemas in Visual Studio</span></span>](../core/how-to-validate-schemas-in-visual-studio.md)   
-  <span data-ttu-id="a7874-116">**Référence de la propriété de mappage**[!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]</span><span class="sxs-lookup"><span data-stu-id="a7874-116">**Map Property Reference** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)]</span></span>  
-  [<span data-ttu-id="a7874-117">Test de mappages</span><span class="sxs-lookup"><span data-stu-id="a7874-117">Testing Maps</span></span>](../core/testing-maps.md)