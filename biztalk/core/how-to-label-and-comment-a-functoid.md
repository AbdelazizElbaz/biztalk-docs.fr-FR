---
title: "Étiquette et commentaires à un fonctoid | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: bts10.mapper.functiod.general
ms.assetid: 58ff3a07-cbb6-4817-b301-d2b434ed2ad9
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: fccdeefa35f9abb5a0c3158dba518d524811c611
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-label-and-comment-a-functoid"></a><span data-ttu-id="4b02e-102">Attribution d'une étiquette et ajout de commentaires à un fonctoid</span><span class="sxs-lookup"><span data-stu-id="4b02e-102">How to Label and Comment a Functoid</span></span>
<span data-ttu-id="4b02e-103">L'utilité des étiquettes et des commentaires est de renseigner sur la finalité d'un fonctoid ou d'un lien dans un mappage.</span><span class="sxs-lookup"><span data-stu-id="4b02e-103">Labels and comments are helpful to document the purpose of a functoid or a link in a map.</span></span> <span data-ttu-id="4b02e-104">Vous pouvez utiliser la **étiquette** propriété afin de fournir un nom d’un fonctoid.</span><span class="sxs-lookup"><span data-stu-id="4b02e-104">You can use the **Label** property to provide a name for a functoid.</span></span> <span data-ttu-id="4b02e-105">Le **commentaires** propriété vous permet de fournir plus d’informations sur le fonctoid, des informations pertinentes en général sur l’opération en cours par celui-ci.</span><span class="sxs-lookup"><span data-stu-id="4b02e-105">The **Comments** property enables you to provide additional information about the functoid, typically relevant information about the operation being performed by it.</span></span>  
  
 <span data-ttu-id="4b02e-106">La figure suivante illustre l'étiquette et les commentaires pour un fonctoid.</span><span class="sxs-lookup"><span data-stu-id="4b02e-106">The following figure shows the label and comments for a functoid.</span></span> <span data-ttu-id="4b02e-107">Le fonctoid ajoute deux entrées (Field1 et Field3) à partir du schéma source et affiche le résultat dans l'entrée Field4 du schéma cible.</span><span class="sxs-lookup"><span data-stu-id="4b02e-107">The functoid adds two inputs (Field1 and Field3) from the source schema and outputs the result to Field4 in the target schema.</span></span> <span data-ttu-id="4b02e-108">Dans cet exemple, l'étiquette du fonctoid est « Ajout de Field1 et Field3 » et le commentaire est « L'ajout correspond à une sortie dans Field4 ».</span><span class="sxs-lookup"><span data-stu-id="4b02e-108">In this example, the functoid label is “Add Field1 and Field3” and the comment is “The addition is an output to Field4”.</span></span>  
  
 <span data-ttu-id="4b02e-109">![Insertion d’étiquettes de fonctoid et des commentaires](../core/media/label.gif "Label_")</span><span class="sxs-lookup"><span data-stu-id="4b02e-109">![Inserting functoid labels and comments](../core/media/label.gif "Label_")</span></span>  
  
 <span data-ttu-id="4b02e-110">Étant donné qu'un fonctoid peut faire partie d'un mappage très complexe, il est important de lui attribuer une étiquette appropriée et d'ajouter des commentaires pertinents.</span><span class="sxs-lookup"><span data-stu-id="4b02e-110">Because a functoid can be a part of very complex mapping, it is important to label it properly and also to provide relevant comments.</span></span> <span data-ttu-id="4b02e-111">Vous pouvez attribuer une étiquette aux fonctoids et aux liens.</span><span class="sxs-lookup"><span data-stu-id="4b02e-111">You can label both functoids and links.</span></span> <span data-ttu-id="4b02e-112">Pour plus d’informations sur l’étiquette à un lien, consultez [étiquette un lien à](../core/how-to-label-a-link.md).</span><span class="sxs-lookup"><span data-stu-id="4b02e-112">For information on how to label a link, see [How to Label a Link](../core/how-to-label-a-link.md).</span></span>  
  
 <span data-ttu-id="4b02e-113">Vous pouvez attribuer une étiquette à un fonctoid et lui ajouter des commentaires de l'une des manières suivantes :</span><span class="sxs-lookup"><span data-stu-id="4b02e-113">You can label and comment a functoid in the following ways:</span></span>  
  
-   <span data-ttu-id="4b02e-114">À l’aide de la **configurer \<fonctoid > fonctoid** boîte de dialogue.</span><span class="sxs-lookup"><span data-stu-id="4b02e-114">By using the **Configure \<Functoid> Functoid** dialog box.</span></span>  
  
-   <span data-ttu-id="4b02e-115">À l’aide de la **propriétés** fenêtre.</span><span class="sxs-lookup"><span data-stu-id="4b02e-115">By using the **Properties** window.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="4b02e-116">Conditions préalables</span><span class="sxs-lookup"><span data-stu-id="4b02e-116">Prerequisites</span></span>  
 <span data-ttu-id="4b02e-117">Les instructions suivantes requièrent que le Mappeur BizTalk est en cours d’exécution.</span><span class="sxs-lookup"><span data-stu-id="4b02e-117">These instructions require that BizTalk Mapper is running.</span></span>  
  
### <a name="to-label-and-comment-a-functoid-from-configure-dialog-box"></a><span data-ttu-id="4b02e-118">Pour attribuer une étiquette et des commentaires à un fonctoid à l'aide de la boîte de dialogue Configurer</span><span class="sxs-lookup"><span data-stu-id="4b02e-118">To label and comment a functoid from Configure dialog box</span></span>  
  
1.  <span data-ttu-id="4b02e-119">Cliquez sur le fonctoid que vous souhaitez attribuer une étiquette et commentaire, puis cliquez sur **configurer les entrées de fonctoid**.</span><span class="sxs-lookup"><span data-stu-id="4b02e-119">Right-click the functoid you want to label and comment, and then click **Configure Functoid Inputs**.</span></span>  
  
2.  <span data-ttu-id="4b02e-120">Dans le **configurer \<fonctoid > fonctoid** boîte de dialogue, cliquez sur le **étiquette et commentaires** onglet.</span><span class="sxs-lookup"><span data-stu-id="4b02e-120">In the **Configure \<Functoid> Functoid** dialog box, click the **Label and Comments** tab.</span></span>  
  
3.  <span data-ttu-id="4b02e-121">Entrez les informations suivantes, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="4b02e-121">Enter the following information, and then click **OK**.</span></span>  
  
    -   <span data-ttu-id="4b02e-122">**Étiquette –** Entrez le nouveau nom.</span><span class="sxs-lookup"><span data-stu-id="4b02e-122">**Label –** Enter the new name.</span></span>  
  
        > [!IMPORTANT]
        >  <span data-ttu-id="4b02e-123">Le nombre maximal de caractères autorisé est de 256.</span><span class="sxs-lookup"><span data-stu-id="4b02e-123">The maximum number of characters allowed is 256.</span></span> <span data-ttu-id="4b02e-124">Si une chaîne comportant plus de 256 caractères est spécifiée, les 256 premiers caractères sont acceptés et le reste est ignoré.</span><span class="sxs-lookup"><span data-stu-id="4b02e-124">If a string with more than 256 characters is specified, the first 256 characters are accepted and the rest are discarded.</span></span>  
  
    -   <span data-ttu-id="4b02e-125">**Commentaires –** Entrez les commentaires pour le fonctoid.</span><span class="sxs-lookup"><span data-stu-id="4b02e-125">**Comments –** Enter the comments for the functoid.</span></span>  
  
        > [!IMPORTANT]
        >  <span data-ttu-id="4b02e-126">Le nombre maximal de caractères autorisé est 1024.</span><span class="sxs-lookup"><span data-stu-id="4b02e-126">The maximum number of characters allowed is 1024.</span></span> <span data-ttu-id="4b02e-127">Si une chaîne comportant plus de 1 024 caractères est spécifiée, les 1024 premiers caractères sont acceptés et le reste est ignoré.</span><span class="sxs-lookup"><span data-stu-id="4b02e-127">If a string with more than 1024 characters is specified, the first 1024 characters are accepted and the rest are discarded.</span></span>  
  
### <a name="to-label-and-comment-a-functoid-from-properties-window"></a><span data-ttu-id="4b02e-128">Pour attribuer une étiquette et des commentaires à un fonctoid à l'aide de la fenêtre Propriétés</span><span class="sxs-lookup"><span data-stu-id="4b02e-128">To label and comment a functoid from Properties window</span></span>  
  
1.  <span data-ttu-id="4b02e-129">Sélectionnez le fonctoid auquel attribuer une étiquette et des commentaires.</span><span class="sxs-lookup"><span data-stu-id="4b02e-129">Select the functoid you want to label and comment.</span></span>  
  
2.  <span data-ttu-id="4b02e-130">Dans le **propriétés** fenêtre, entrez les informations suivantes, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="4b02e-130">In the **Properties** window, enter the following information, and then click **OK**.</span></span>  
  
    -   <span data-ttu-id="4b02e-131">**Étiquette –** Entrez le nouveau nom.</span><span class="sxs-lookup"><span data-stu-id="4b02e-131">**Label –** Enter the new name.</span></span>  
  
        > [!IMPORTANT]
        >  <span data-ttu-id="4b02e-132">Le nombre maximal de caractères autorisé est de 256.</span><span class="sxs-lookup"><span data-stu-id="4b02e-132">The maximum number of characters allowed is 256.</span></span> <span data-ttu-id="4b02e-133">Si une chaîne comportant plus de 256 caractères est spécifiée, les 256 premiers caractères sont acceptés et le reste est ignoré.</span><span class="sxs-lookup"><span data-stu-id="4b02e-133">If a string with more than 256 characters is specified, the first 256 characters are accepted and the rest are discarded.</span></span>  
  
    -   <span data-ttu-id="4b02e-134">**Commentaires –** Entrez les commentaires pour le fonctoid.</span><span class="sxs-lookup"><span data-stu-id="4b02e-134">**Comments –** Enter the comments for the functoid.</span></span>  
  
        > [!IMPORTANT]
        >  <span data-ttu-id="4b02e-135">Le nombre maximal de caractères autorisé est 1024.</span><span class="sxs-lookup"><span data-stu-id="4b02e-135">The maximum number of characters allowed is 1024.</span></span> <span data-ttu-id="4b02e-136">Si une chaîne comportant plus de 1 024 caractères est spécifiée, les 1024 premiers caractères sont acceptés et le reste est ignoré.</span><span class="sxs-lookup"><span data-stu-id="4b02e-136">If a string with more than 1024 characters is specified, the first 1024 characters are accepted and the rest are discarded.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4b02e-137">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="4b02e-137">See Also</span></span>  
 [<span data-ttu-id="4b02e-138">Modification des propriétés des fonctoids et des paramètres d’entrée</span><span class="sxs-lookup"><span data-stu-id="4b02e-138">Editing Functoid Properties and Input Parameters</span></span>](../core/editing-functoid-properties-and-input-parameters.md)