---
title: 'Erreur : le fichier d’entrée n’existe pas | Documents Microsoft'
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- bts10.map.error.inputFileDoesNotExist
ms.assetid: 6cd2f076-6c3e-46e3-8be4-dad2d9b95d37
caps.latest.revision: 5
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 7a14221857ebb567020a52c2ff0939b506d28937
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="error---input-file-does-not-exist"></a><span data-ttu-id="522a0-102">Erreur : le fichier d’entrée n’existe pas</span><span class="sxs-lookup"><span data-stu-id="522a0-102">Error - Input File Does Not Exist</span></span>
<span data-ttu-id="522a0-103">**Code d’erreur**</span><span class="sxs-lookup"><span data-stu-id="522a0-103">**Error Code**</span></span>  
  
 <span data-ttu-id="522a0-104">btm1037</span><span class="sxs-lookup"><span data-stu-id="522a0-104">btm1037</span></span>  
  
 <span data-ttu-id="522a0-105">**Explication**</span><span class="sxs-lookup"><span data-stu-id="522a0-105">**Explanation**</span></span>  
  
 <span data-ttu-id="522a0-106">Le fichier de message d’instance d’entrée spécifié pour l’opération Test Map n’existe pas, et le type de Test Map d’entrée n’est pas défini **générer l’Instance**.</span><span class="sxs-lookup"><span data-stu-id="522a0-106">The input instance message file specified for the Test Map operation does not exist, and the type of the Test Map input is not set to **Generate Instance**.</span></span> <span data-ttu-id="522a0-107">Lorsque la valeur de la **entrée TestMap** mapper la propriété n’est pas définie sur **générer l’Instance**, vous devez spécifier un fichier de message d’instance existant pour le **Instance d’entrée TestMap** propriété de mappage.</span><span class="sxs-lookup"><span data-stu-id="522a0-107">When the value of the **TestMap Input** map property is not set to **Generate Instance**, you must specify an existing instance message file for the **TestMap Input Instance** map property.</span></span>  
  
 <span data-ttu-id="522a0-108">**Action de l’utilisateur**</span><span class="sxs-lookup"><span data-stu-id="522a0-108">**User Action**</span></span>  
  
 <span data-ttu-id="522a0-109">Si nécessaire, définissez l'une ou l'autre des propriétés de mappage suivantes :</span><span class="sxs-lookup"><span data-stu-id="522a0-109">As appropriate, set one or the other of the following map properties:</span></span>  
  
-   <span data-ttu-id="522a0-110">**Instance d’entrée TestMap.**</span><span class="sxs-lookup"><span data-stu-id="522a0-110">**TestMap Input Instance.**</span></span> <span data-ttu-id="522a0-111">Sur le mappage approprié dans l’Explorateur de solutions, cliquez **propriétés**, puis, dans le **Test Map** onglet dans le **Pages de propriétés** boîte de dialogue de la carte, cliquez sur le bouton de sélection ( **...** ) dans le champ de valeur de la **Instance d’entrée TestMap** propriété.</span><span class="sxs-lookup"><span data-stu-id="522a0-111">Right-click the relevant map in Solution Explorer, click **Properties**, and then on the **Test Map** tab in the **Property Pages** dialog box for the map, click the ellipsis (**...**) button in the value field of the **TestMap Input Instance** property.</span></span> <span data-ttu-id="522a0-112">À l’aide de la **sélectionner le fichier d’entrée** boîte de dialogue, sélectionnez une instance existante de message de fichier conforme au schéma source du mappage.</span><span class="sxs-lookup"><span data-stu-id="522a0-112">Using the **Select Input File** dialog box, select an existing instance message file that conforms to the source schema of the map.</span></span> <span data-ttu-id="522a0-113">Ou bien, vous pouvez taper le chemin d’accès de ce fichier directement dans le champ de valeur de la **Instance d’entrée TestMap** propriété.</span><span class="sxs-lookup"><span data-stu-id="522a0-113">Alternatively, you can type the path of this file directly into the value field of the **TestMap Input Instance** property.</span></span>  
  
-   <span data-ttu-id="522a0-114">**Entrée TestMap.**</span><span class="sxs-lookup"><span data-stu-id="522a0-114">**TestMap Input.**</span></span> <span data-ttu-id="522a0-115">Pour éviter de spécifier un fichier de message d’instance d’entrée, cliquez sur le mappage approprié dans l’Explorateur de solutions, cliquez sur **propriétés**, puis, dans le **Test Map** onglet du **Pages de propriétés**boîte de dialogue pour le mappage, utilisez la liste déroulante de liste dans le champ de valeur de la **entrée TestMap** propriété pour sélectionner **générer l’Instance**.</span><span class="sxs-lookup"><span data-stu-id="522a0-115">To avoid specifying an input instance message file, right-click the relevant map in Solution Explorer, click **Properties**, and then on the **Test Map** tab of the **Property Pages** dialog box for the map, use the drop-down list in the value field of the **TestMap Input** property to select **Generate Instance**.</span></span> <span data-ttu-id="522a0-116">Dans ce cas, vous ne devez pas spécifier un fichier pour le **Instance d’entrée TestMap** propriété.</span><span class="sxs-lookup"><span data-stu-id="522a0-116">In this case, you need not specify a file for the **TestMap Input Instance** property.</span></span>