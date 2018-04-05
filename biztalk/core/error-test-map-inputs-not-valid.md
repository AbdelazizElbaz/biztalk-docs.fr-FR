---
title: 'Erreur : les entrées de mappage de Test non valide | Documents Microsoft'
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- bts10.map.error.testMapInputsNotValid
ms.assetid: d885d366-92a3-4d2a-8e2b-58e06960864f
caps.latest.revision: 5
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 912b70bcd74180a20d54da11dffdab79f54fc5b6
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="error---test-map-inputs-not-valid"></a><span data-ttu-id="d7cdd-102">Erreur : les entrées de mappage de Test non valide</span><span class="sxs-lookup"><span data-stu-id="d7cdd-102">Error - Test Map Inputs Not Valid</span></span>
<span data-ttu-id="d7cdd-103">**Code d’erreur**</span><span class="sxs-lookup"><span data-stu-id="d7cdd-103">**Error Code**</span></span>  
  
 <span data-ttu-id="d7cdd-104">btm1036</span><span class="sxs-lookup"><span data-stu-id="d7cdd-104">btm1036</span></span>  
  
 <span data-ttu-id="d7cdd-105">**Explication**</span><span class="sxs-lookup"><span data-stu-id="d7cdd-105">**Explanation**</span></span>  
  
 <span data-ttu-id="d7cdd-106">Aucun fichier de message d’instance d’entrée n’a été spécifié pour l’opération Test Map et le type de l’entrée TestMap n’est pas défini sur **générer l’Instance**.</span><span class="sxs-lookup"><span data-stu-id="d7cdd-106">No input instance message file has been specified for the Test Map operation, and the type of the TestMap input is not set to **Generate Instance**.</span></span> <span data-ttu-id="d7cdd-107">Lorsque la valeur de la **entrée TestMap** mapper la propriété n’est pas définie sur **générer l’Instance**, vous devez spécifier un fichier de message d’instance pour le **Instance d’entrée TestMap** carte propriété.</span><span class="sxs-lookup"><span data-stu-id="d7cdd-107">When the value of the **TestMap Input** map property is not set to **Generate Instance**, you must specify an instance message file for the **TestMap Input Instance** map property.</span></span>  
  
 <span data-ttu-id="d7cdd-108">**Action de l’utilisateur**</span><span class="sxs-lookup"><span data-stu-id="d7cdd-108">**User Action**</span></span>  
  
 <span data-ttu-id="d7cdd-109">Si nécessaire, définissez l'une ou l'autre des propriétés de mappage suivantes :</span><span class="sxs-lookup"><span data-stu-id="d7cdd-109">As appropriate, set one or the other of the following map properties:</span></span>  
  
-   <span data-ttu-id="d7cdd-110">**Instance d’entrée TestMap.**</span><span class="sxs-lookup"><span data-stu-id="d7cdd-110">**TestMap Input Instance.**</span></span> <span data-ttu-id="d7cdd-111">Sur le mappage approprié dans l’Explorateur de solutions, cliquez **propriétés**, puis, dans le **Test Map** onglet dans le **Pages de propriétés** boîte de dialogue de la carte, cliquez sur le bouton de sélection ( **...** ) dans le champ de valeur de la **Instance d’entrée TestMap** propriété.</span><span class="sxs-lookup"><span data-stu-id="d7cdd-111">Right-click the relevant map in Solution Explorer, click **Properties**, and then on the **Test Map** tab in the **Property Pages** dialog box for the map, click the ellipsis (**...**) button in the value field of the **TestMap Input Instance** property.</span></span> <span data-ttu-id="d7cdd-112">À l’aide de la **sélectionner le fichier d’entrée** boîte de dialogue, sélectionnez une instance de message de fichier conforme au schéma source du mappage.</span><span class="sxs-lookup"><span data-stu-id="d7cdd-112">Using the **Select Input File** dialog box, select an instance message file that conforms to the source schema of the map.</span></span> <span data-ttu-id="d7cdd-113">Ou bien, vous pouvez taper le chemin d’accès de ce fichier directement dans le champ de valeur de la **Instance d’entrée TestMap** propriété.</span><span class="sxs-lookup"><span data-stu-id="d7cdd-113">Alternatively, you can type the path of this file directly into the value field of the **TestMap Input Instance** property.</span></span>  
  
-   <span data-ttu-id="d7cdd-114">**Entrée TestMap.**</span><span class="sxs-lookup"><span data-stu-id="d7cdd-114">**TestMap Input.**</span></span> <span data-ttu-id="d7cdd-115">Pour éviter de spécifier un fichier de message d’instance d’entrée, cliquez sur le mappage approprié dans l’Explorateur de solutions, cliquez sur **propriétés**, puis, dans le **Test Map** onglet dans le **Pages de propriétés**boîte de dialogue pour le mappage, utilisez la liste déroulante de liste dans le champ de valeur de la **entrée TestMap** propriété pour sélectionner **générer l’Instance**.</span><span class="sxs-lookup"><span data-stu-id="d7cdd-115">To avoid specifying an input instance message file, right-click the relevant map in Solution Explorer, click **Properties**, and then on the **Test Map** tab in the **Property Pages** dialog box for the map, use the drop-down list in the value field of the **TestMap Input** property to select **Generate Instance**.</span></span> <span data-ttu-id="d7cdd-116">Dans ce cas, vous ne devez pas spécifier un fichier pour le **Instance d’entrée TestMap** propriété.</span><span class="sxs-lookup"><span data-stu-id="d7cdd-116">In this case, you need not specify a file for the **TestMap Input Instance** property.</span></span>