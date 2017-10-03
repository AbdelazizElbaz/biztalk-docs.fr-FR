---
title: "Comment configurer la Validation de la carte et les paramètres de Test | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1768918c-e94f-476f-b288-9e030c691177
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: f691a58ece178ee00ce983e400e5420ef54fafdf
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-configure-map-validation-and-test-parameters"></a><span data-ttu-id="7f50d-102">Comment configurer la Validation de la carte et les paramètres de Test</span><span class="sxs-lookup"><span data-stu-id="7f50d-102">How to Configure Map Validation and Test Parameters</span></span>
<span data-ttu-id="7f50d-103">Avant de valider et tester un mappage, vous devez définir les paramètres de validation et de test le **propriétés** fenêtre de la carte.</span><span class="sxs-lookup"><span data-stu-id="7f50d-103">Before validating and testing a map, you need to set the map validation and test parameters in the **Properties** window of the map.</span></span>  
  
## <a name="configure-the-map-validation-and-test-parameters"></a><span data-ttu-id="7f50d-104">Configurer les paramètres de validation et de test du mappage</span><span class="sxs-lookup"><span data-stu-id="7f50d-104">Configure the map validation and test parameters</span></span>  
  
1.  <span data-ttu-id="7f50d-105">Dans l’Explorateur de solutions, cliquez sur la carte dont vous souhaitez configurer, puis cliquez sur les pages de propriété **propriétés**.</span><span class="sxs-lookup"><span data-stu-id="7f50d-105">In Solution Explorer, right-click the map whose property pages you want to configure, and then click **Properties**.</span></span>  
  
2.  <span data-ttu-id="7f50d-106">Dans la fenêtre Propriétés, procédez comme suit.</span><span class="sxs-lookup"><span data-stu-id="7f50d-106">In the Properties window, do the following.</span></span>  
  
    |<span data-ttu-id="7f50d-107">Utiliser</span><span class="sxs-lookup"><span data-stu-id="7f50d-107">Use this</span></span>|<span data-ttu-id="7f50d-108">Pour effectuer cette opération</span><span class="sxs-lookup"><span data-stu-id="7f50d-108">To do this</span></span>|  
    |--------------|----------------|  
    |<span data-ttu-id="7f50d-109">**Valider l’entrée TestMap**</span><span class="sxs-lookup"><span data-stu-id="7f50d-109">**Validate TestMap Input**</span></span>|<span data-ttu-id="7f50d-110">Déterminer s'il faut valider le message d’instance par rapport au schéma source avant de tester le mappage.</span><span class="sxs-lookup"><span data-stu-id="7f50d-110">Configure whether you want to have the instance message validated against the source schema before you test the map.</span></span>|  
    |<span data-ttu-id="7f50d-111">**Valider la sortie TestMap**</span><span class="sxs-lookup"><span data-stu-id="7f50d-111">**Validate TestMap Output**</span></span>|<span data-ttu-id="7f50d-112">Déterminer s'il faut valider le message d’instance par rapport au schéma de destination après le test du mappage.</span><span class="sxs-lookup"><span data-stu-id="7f50d-112">Configure whether you want to have the instance message validated against the destination schema after you test the map.</span></span>|  
    |<span data-ttu-id="7f50d-113">**Instance d’entrée TestMap**</span><span class="sxs-lookup"><span data-stu-id="7f50d-113">**TestMap Input Instance**</span></span>|<span data-ttu-id="7f50d-114">Configurer l'emplacement des données du message d'instance à utiliser lors du test du mappage.</span><span class="sxs-lookup"><span data-stu-id="7f50d-114">Configure the location of the instance message data to use when you test the map.</span></span><br /><br /> <span data-ttu-id="7f50d-115">Si vous configurez cette propriété, vous devez également configurer le **entrée TestMap** propriété.</span><span class="sxs-lookup"><span data-stu-id="7f50d-115">If you configure this property, you must also configure the **TestMap Input** property.</span></span>|  
    |<span data-ttu-id="7f50d-116">**Instance de sortie TestMap**</span><span class="sxs-lookup"><span data-stu-id="7f50d-116">**TestMap Output Instance**</span></span>|<span data-ttu-id="7f50d-117">Configurez l'emplacement du fichier où vous souhaitez enregistrer le résultat de l'opération Test Map.</span><span class="sxs-lookup"><span data-stu-id="7f50d-117">Configure the location of the file where you want the output of the test map operation to be stored.</span></span><br /><br /> <span data-ttu-id="7f50d-118">Si vous configurez cette propriété, vous devez également configurer le **sortie TestMap** propriété.</span><span class="sxs-lookup"><span data-stu-id="7f50d-118">If you configure this property, you must also configure the **TestMap Output** property.</span></span>|  
    |<span data-ttu-id="7f50d-119">**Entrée TestMap**</span><span class="sxs-lookup"><span data-stu-id="7f50d-119">**TestMap Input**</span></span>|<span data-ttu-id="7f50d-120">Configurer le format de données de l'instance d'entrée.</span><span class="sxs-lookup"><span data-stu-id="7f50d-120">Configure the input instance data format.</span></span>|  
    |<span data-ttu-id="7f50d-121">**Sortie TestMap**</span><span class="sxs-lookup"><span data-stu-id="7f50d-121">**TestMap Output**</span></span>|<span data-ttu-id="7f50d-122">Configurer le type de données de sortie à utiliser lors du test du mappage.</span><span class="sxs-lookup"><span data-stu-id="7f50d-122">Configure the output data type to use when you test the map.</span></span>|  
  
    > [!IMPORTANT]
    >  <span data-ttu-id="7f50d-123">Pour tester votre mappage, vous devez d'abord configurer les pages de propriétés du mappage.</span><span class="sxs-lookup"><span data-stu-id="7f50d-123">If you want to test your map, you must configure the map properties first.</span></span>  

<span data-ttu-id="7f50d-124">L'une des étapes qui suit le développement d'un mappage est celle de la validation.</span><span class="sxs-lookup"><span data-stu-id="7f50d-124">After you have developed your map, one of the next steps is to validate it.</span></span> <span data-ttu-id="7f50d-125">Cette rubrique contient des instructions détaillées concernant la validation des mappages.</span><span class="sxs-lookup"><span data-stu-id="7f50d-125">This topic provides step-by-step instructions for validating maps.</span></span>  
  
## <a name="validate-a-biztalk-map"></a><span data-ttu-id="7f50d-126">Valider un mappage BizTalk</span><span class="sxs-lookup"><span data-stu-id="7f50d-126">Validate a BizTalk map</span></span>  
  
1.  <span data-ttu-id="7f50d-127">Dans l'Explorateur de solutions, ouvrez le mappage que vous souhaitez valider.</span><span class="sxs-lookup"><span data-stu-id="7f50d-127">In Solution Explorer, open the map that you want to validate.</span></span>  
  
2.  <span data-ttu-id="7f50d-128">Dans l’Explorateur de solutions, cliquez sur la carte, puis **valider le mappage**.</span><span class="sxs-lookup"><span data-stu-id="7f50d-128">In Solution Explorer, right-click the map, and then select **Validate Map**.</span></span>  
  
3.  <span data-ttu-id="7f50d-129">Dans le **sortie** fenêtre, vérifier les résultats.</span><span class="sxs-lookup"><span data-stu-id="7f50d-129">In the **Output** window, verify the results.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="7f50d-130">Si vous utilisez des données personnalisées ou des constantes dans votre sortie, vous devez vérifier que les types de vos données de test sources et les valeurs des constantes cibles sont valides.</span><span class="sxs-lookup"><span data-stu-id="7f50d-130">If you use custom data or constants in your output, you must verify that the data types of your source test data and target constant values are valid.</span></span> <span data-ttu-id="7f50d-131">Lorsque vous validez un mappage, le Mappeur BizTalk ne vérifie pas si les données d'instance violent des types de données définis dans les schémas.</span><span class="sxs-lookup"><span data-stu-id="7f50d-131">When you validate a map, BizTalk Mapper does not check if the instance data violates any data types defined in the schemas.</span></span> <span data-ttu-id="7f50d-132">Cela lorsque vous testez le mappage ou validez les données d’instance avec l’Éditeur BizTalk.</span><span class="sxs-lookup"><span data-stu-id="7f50d-132">This is done when you test the map or validate the instance data with BizTalk Editor.</span></span> 

## <a name="test-a-biztalk-map"></a><span data-ttu-id="7f50d-133">Tester un mappage BizTalk</span><span class="sxs-lookup"><span data-stu-id="7f50d-133">Test a BizTalk map</span></span>

<span data-ttu-id="7f50d-134">L'étape qui suit le développement d'un mappage est celle du test.</span><span class="sxs-lookup"><span data-stu-id="7f50d-134">After you have developed your map, one of the next steps is to test it.</span></span> <span data-ttu-id="7f50d-135">Cette rubrique contient des instructions détaillées relatives au test des mappages, notamment la procédure à effectuer pour afficher le fichier XSLT généré par le compilateur de mappage.</span><span class="sxs-lookup"><span data-stu-id="7f50d-135">This topic provides step-by-step instructions for testing maps including steps to view the XSLT generated by the map compiler.</span></span>  
  
1.  <span data-ttu-id="7f50d-136">Dans l’Explorateur de solutions, cliquez sur la carte que vous souhaitez tester, puis sélectionnez **tester le mappage**.</span><span class="sxs-lookup"><span data-stu-id="7f50d-136">In Solution Explorer, right-click the map you want to test, and then select **Test Map**.</span></span>  
  
2.  <span data-ttu-id="7f50d-137">Vérifier les résultats dans le **sortie** fenêtre.</span><span class="sxs-lookup"><span data-stu-id="7f50d-137">Verify the results in the **Output** window.</span></span>  
  
    > [!IMPORTANT]
    >  <span data-ttu-id="7f50d-138">Avant de tester un mappage, il est recommandé de configurer les propriétés d'instance d'entrée et de sortie dans la fenêtre Propriétés.</span><span class="sxs-lookup"><span data-stu-id="7f50d-138">It is recommended that you configure the input and output instance properties in the Properties window before you test a map.</span></span>  
  
## <a name="review-the-xslt"></a><span data-ttu-id="7f50d-139">Passez en revue le fichier XSLT</span><span class="sxs-lookup"><span data-stu-id="7f50d-139">Review the XSLT</span></span>  
 <span data-ttu-id="7f50d-140">Il est souvent utile de contrôler le fichier XSLT généré par le compilateur de mappage.</span><span class="sxs-lookup"><span data-stu-id="7f50d-140">It is often useful to inspect the XSLT generated by the map compiler.</span></span> <span data-ttu-id="7f50d-141">L'inspection du fichier XSLT présente notamment les avantages suivants :</span><span class="sxs-lookup"><span data-stu-id="7f50d-141">Some of the benefits of inspecting XSLT include:</span></span>  
  
-   <span data-ttu-id="7f50d-142">Si vous utilisez le bouclage ou des fonctoids personnalisés, vous comprendrez mieux la manière dont le bouclage est exécuté ou dont le fonctoid personnalisé est appelé.</span><span class="sxs-lookup"><span data-stu-id="7f50d-142">If you are using looping or custom functoids, you will better understand how the looping is performed and how the custom functoid is invoked.</span></span>  
  
-   <span data-ttu-id="7f50d-143">Si vous avez un mappage complexe, examen du fichier XSLT vous permettra de voir comment le mappage est traduit en une transformation et peut-être vous donner une comment mieux structurer, remplacer ou rationaliser une ou plusieurs parties.</span><span class="sxs-lookup"><span data-stu-id="7f50d-143">If you have a complicated map, reviewing the XSLT will enable you to see how the map is translated into a transform, and may give you insight on how to better structure, replace, or streamline one or more parts.</span></span>  
  
-   <span data-ttu-id="7f50d-144">Si vous utilisez des scripts personnalisés ou tout autre artefact, l'examen du fichier XSLT vous permettra de mieux comprendre l'interaction entre les scripts, les artefacts et les autres parties du mappage.</span><span class="sxs-lookup"><span data-stu-id="7f50d-144">If you are using custom scripts or other artifacts, reviewing the XSLT will enable you to see how the scripts, artifacts, and other parts of the map interact.</span></span>  
  
 <span data-ttu-id="7f50d-145">En d'autres termes, l'examen du fichier XSLT constitue un moyen remarquable pour déboguer un mappage.</span><span class="sxs-lookup"><span data-stu-id="7f50d-145">In other words, reviewing the XSLT is a great way to debug a map.</span></span>  
  
#### <a name="view-the-xslt-generated-by-the-map-compiler"></a><span data-ttu-id="7f50d-146">Afficher le XSLT généré par le compilateur de mappage</span><span class="sxs-lookup"><span data-stu-id="7f50d-146">View the XSLT generated by the map compiler</span></span>  
  
1.  <span data-ttu-id="7f50d-147">À partir d’un projet BizTalk Visual Studio, sélectionnez le **l’Explorateur de solutions** onglet, cliquez sur une carte, puis sélectionnez **valider le mappage**.</span><span class="sxs-lookup"><span data-stu-id="7f50d-147">From a Visual Studio BizTalk project, select the **Solution Explorer** tab, right-click a map, and then select **Validate Map**.</span></span>  
  
2.  <span data-ttu-id="7f50d-148">Faites défiler la fenêtre Sortie pour rechercher l'URL du fichier XSL.</span><span class="sxs-lookup"><span data-stu-id="7f50d-148">Scroll the Output window to find the URL for the XSL file.</span></span> <span data-ttu-id="7f50d-149">Appuyez sur **CTRL**, puis sélectionnez l’URL pour afficher le fichier.</span><span class="sxs-lookup"><span data-stu-id="7f50d-149">Press **CTRL**, and select the URL to view the file.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="7f50d-150">Les modifications apportées au fichier XSL ne sont pas répercutées dans le mappage et sont écrasées lors de la génération suivante.</span><span class="sxs-lookup"><span data-stu-id="7f50d-150">Changes made to the XSL file are not reflected in the map and are overwritten on the next build.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7f50d-151">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="7f50d-151">See also</span></span>  

[<span data-ttu-id="7f50d-152">Comment déboguer des mappages</span><span class="sxs-lookup"><span data-stu-id="7f50d-152">How to Debug Maps</span></span>](../core/how-to-debug-maps.md)  
[<span data-ttu-id="7f50d-153">Résolution des problèmes de mappages</span><span class="sxs-lookup"><span data-stu-id="7f50d-153">Troubleshooting Maps</span></span>](../core/troubleshooting-maps.md)  