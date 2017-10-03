---
title: "Comment configurer les Types de corrélations | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- deleting, correlation types
- correlation types, configuring
- correlation types, deleting
- configuring, correlation types
ms.assetid: cfae4d2e-ec79-45c8-93b3-799dc5e0576e
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 646ac7dafd5207a2558e45252077efe2d9616a70
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-configure-correlation-types"></a><span data-ttu-id="ded7e-102">Configuration de types de corrélations</span><span class="sxs-lookup"><span data-stu-id="ded7e-102">How to Configure Correlation Types</span></span>
<span data-ttu-id="ded7e-103">Vous utilisez la **propriétés de corrélation** boîte de dialogue pour ajouter ou supprimer des propriétés d’un type de corrélation.</span><span class="sxs-lookup"><span data-stu-id="ded7e-103">You use the **Correlation Properties** dialog box to add or remove properties from a correlation type.</span></span> <span data-ttu-id="ded7e-104">Le type de corrélation répertorie dans un ensemble de corrélations les propriétés utilisées par les activités d'envoi et de réception pour garantir que les messages entrants sont correctement corrélés avec les bonnes instances d'une orchestration lors de l'exécution.</span><span class="sxs-lookup"><span data-stu-id="ded7e-104">The correlation type lists the properties in a correlation set which are used by Send and Receive activities to make sure that incoming messages are properly correlated with the right instances of an orchestration at run time.</span></span>  
  
 <span data-ttu-id="ded7e-105">La boîte de dialogue contient deux volets comportant chacun une liste de propriétés.</span><span class="sxs-lookup"><span data-stu-id="ded7e-105">There are two panes in the dialog box, each containing a list of properties.</span></span> <span data-ttu-id="ded7e-106">Le volet gauche, « Propriétés disponibles », contient une arborescence de toutes les propriétés définies dans votre projet ou référencées par lui.</span><span class="sxs-lookup"><span data-stu-id="ded7e-106">The left pane, "Available Properties", contains a tree view of all of the properties that are defined in your project or referenced by it.</span></span> <span data-ttu-id="ded7e-107">Les propriétés qui apparaissent par défaut sont des propriétés système définies par BizTalk Server, mais vous pouvez également définir vos propres propriétés dans un schéma de propriété.</span><span class="sxs-lookup"><span data-stu-id="ded7e-107">The properties that appear by default are system properties, defined by BizTalk Server, but you can also define your own properties in a property schema.</span></span> <span data-ttu-id="ded7e-108">Pour plus d’informations sur la création de schémas de propriété, consultez [les schémas de propriété](../core/property-schemas.md).</span><span class="sxs-lookup"><span data-stu-id="ded7e-108">For more information about creating property schemas, see [Property Schemas](../core/property-schemas.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="ded7e-109">Avant de pouvoir être utilisés dans un type de corrélation, les schémas de propriété doivent être promus.</span><span class="sxs-lookup"><span data-stu-id="ded7e-109">Schema properties must be promoted before they can be used in a correlation type.</span></span> <span data-ttu-id="ded7e-110">Pour plus d’informations, consultez [promotion des propriétés](../core/promoting-properties.md).</span><span class="sxs-lookup"><span data-stu-id="ded7e-110">For more information, see [Promoting Properties](../core/promoting-properties.md).</span></span>  
  
### <a name="to-add-and-configure-a-correlation-type"></a><span data-ttu-id="ded7e-111">Ajout et configuration d'un type de corrélation</span><span class="sxs-lookup"><span data-stu-id="ded7e-111">To add and configure a correlation type</span></span>  
  
-   <span data-ttu-id="ded7e-112">Dans la fenêtre Vue Orchestration, cliquez sur **Types de corrélations** puis cliquez sur **nouveau Type de corrélation**.</span><span class="sxs-lookup"><span data-stu-id="ded7e-112">In the Orchestration View window, right-click **Correlation Types** and then click **New Correlation Type**.</span></span>  
  
     <span data-ttu-id="ded7e-113">Le **propriétés de corrélation** boîte de dialogue s’affiche.</span><span class="sxs-lookup"><span data-stu-id="ded7e-113">The **Correlation Properties** dialog box comes up.</span></span> <span data-ttu-id="ded7e-114">Ajoutez les propriétés à inclure dans votre type de corrélation.</span><span class="sxs-lookup"><span data-stu-id="ded7e-114">Add properties that you want to include in your correlation type.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="ded7e-115">Si vous accédez à la **propriétés de corrélation** boîte de dialogue directement à partir d’une corrélation défini, un type de corrélation pour l’ensemble de corrélations est créé s’il n’existe pas déjà.</span><span class="sxs-lookup"><span data-stu-id="ded7e-115">If you access the **Correlation Properties** dialog box directly from a correlation set, a correlation type for the correlation set is created if one does not already exist.</span></span> <span data-ttu-id="ded7e-116">Vos modifications seront sauvegardées sous le nouveau type de corrélation et l'ensemble de corrélations sera configuré de manière à l'utiliser.</span><span class="sxs-lookup"><span data-stu-id="ded7e-116">Your changes will be saved to the new correlation type, and the correlation set will be configured to use the new correlation type.</span></span> <span data-ttu-id="ded7e-117">Si un type de corrélation existe déjà pour l'ensemble de corrélations et que vous apportez des modifications, ce type sera modifié.</span><span class="sxs-lookup"><span data-stu-id="ded7e-117">If a correlation type already existed for the correlation set and you make changes, the correlation type will be modified.</span></span>  
  
### <a name="to-remove-a-correlation-type"></a><span data-ttu-id="ded7e-118">Suppression d'un type de corrélation</span><span class="sxs-lookup"><span data-stu-id="ded7e-118">To remove a correlation type</span></span>  
  
-   <span data-ttu-id="ded7e-119">Dans la fenêtre Vue Orchestration, cliquez sur le type de corrélation que vous souhaitez supprimer, puis cliquez sur **supprimer**.</span><span class="sxs-lookup"><span data-stu-id="ded7e-119">In the Orchestration View window, right-click the correlation type you want to remove and then click **Delete**.</span></span>