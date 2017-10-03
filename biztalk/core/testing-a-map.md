---
title: "Test d’un mappage | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 265afd62-3c1d-4b9a-9f51-176b9b079241
caps.latest.revision: "13"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: aee4c59783dd72e94ee222c0ee165c7c8f90a32f
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="testing-a-map"></a><span data-ttu-id="f8bb0-102">Test d’un mappage</span><span class="sxs-lookup"><span data-stu-id="f8bb0-102">Testing a Map</span></span>
<span data-ttu-id="f8bb0-103">Vous pouvez tester un mappage dans un projet au moment de la conception.</span><span class="sxs-lookup"><span data-stu-id="f8bb0-103">You can test a map in an EDI project at design time.</span></span> <span data-ttu-id="f8bb0-104">Pour ce faire, utilisez les extensions de l'outil XML à [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] dans l'environnement [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="f8bb0-104">To do so, you use the XML Tool extensions to [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] in the [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] environment.</span></span> <span data-ttu-id="f8bb0-105">Cette rubrique explique comment configurer et utiliser le **Test Map** fonctionnalité de l’extension de l’outil XML.</span><span class="sxs-lookup"><span data-stu-id="f8bb0-105">This topic describes how to set up and use the **Test Map** feature of the XML Tool extension.</span></span>  
  
 <span data-ttu-id="f8bb0-106">Pour tester un mappage, spécifiez un document source et le dossier dans lequel [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] enregistrera une instance générée (avec des données fictives).</span><span class="sxs-lookup"><span data-stu-id="f8bb0-106">You test a map by specifying a source document and specifying a folder where [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] will save a generated instance (with fictitious data).</span></span> <span data-ttu-id="f8bb0-107">Vous devez définir les délimiteurs que [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] utilisera pour traiter le document source et générer le document de destination en fonction des schémas EDI.</span><span class="sxs-lookup"><span data-stu-id="f8bb0-107">You need to set the delimiters that [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] will use to process the source document and generate the destination document according to EDI schemas.</span></span> <span data-ttu-id="f8bb0-108">Cela est vrai pour toutes les valeurs de la **TestMap** d’entrée de propriété dans les pages de propriétés de la carte : **générer l’Instance**, **XML**, ou **natif**.</span><span class="sxs-lookup"><span data-stu-id="f8bb0-108">This is true for all values of the **TestMap** input property in the map's property pages: **Generate Instance**, **XML**, or **Native**.</span></span> <span data-ttu-id="f8bb0-109">Ceci est vrai pour **générer l’Instance** car [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] a besoin de connaître les délimiteurs à utiliser pour générer l’instance.</span><span class="sxs-lookup"><span data-stu-id="f8bb0-109">It is true for **Generate Instance** because [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] needs to know what delimiters to use to generate the instance.</span></span> <span data-ttu-id="f8bb0-110">Ceci est vrai pour **XML** ou **natif** car [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] a besoin de savoir comment interpréter le fichier plat natif ou le fichier XML.</span><span class="sxs-lookup"><span data-stu-id="f8bb0-110">It is true for **XML** or **Native** because [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] needs to know how to interpret the native flat file or the XML file.</span></span> <span data-ttu-id="f8bb0-111">Vous devez également définir les délimiteurs que [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] utilisera lors de la génération du fichier de sortie.</span><span class="sxs-lookup"><span data-stu-id="f8bb0-111">You also need to set the delimiters that [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] will use when generating the output file.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="f8bb0-112">Conditions préalables</span><span class="sxs-lookup"><span data-stu-id="f8bb0-112">Prerequisites</span></span>  
 <span data-ttu-id="f8bb0-113">Vous devez ouvrir une session en tant que membre du groupe Administrateurs [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="f8bb0-113">You must be logged on as a member of the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administrators group.</span></span>  
  
### <a name="to-test-a-map"></a><span data-ttu-id="f8bb0-114">Pour tester un mappage</span><span class="sxs-lookup"><span data-stu-id="f8bb0-114">To test a map</span></span>  
  
1.  <span data-ttu-id="f8bb0-115">Dans [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)], ajoutez le mappage que vous souhaitez tester à un projet, puis ajoutez les schémas source et de destination de ce mappage au projet.</span><span class="sxs-lookup"><span data-stu-id="f8bb0-115">In [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)], add the map that you want to test to a project, and add the source and destination schemas for that map to the project.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="f8bb0-116">Il n'est pas nécessaire de créer le projet pour tester le mappage.</span><span class="sxs-lookup"><span data-stu-id="f8bb0-116">You do not have to build the project to test the map.</span></span>  
  
2.  <span data-ttu-id="f8bb0-117">Avec le bouton droit de la carte, puis cliquez sur **propriétés**.</span><span class="sxs-lookup"><span data-stu-id="f8bb0-117">Right-click the map and click **Properties**.</span></span>  
  
3.  <span data-ttu-id="f8bb0-118">Dans le **propriétés** , configurez **valider l’entrée TestMap** à **True** si vous souhaitez valider le fichier d’entrée par rapport au schéma source.</span><span class="sxs-lookup"><span data-stu-id="f8bb0-118">In the **Properties** window, set **Validate TestMap Input** to **True** if you want to validate the input file against the source schema.</span></span> <span data-ttu-id="f8bb0-119">Définissez **valider la sortie TestMap** à **True** si vous souhaitez valider le fichier de sortie par rapport au schéma de destination.</span><span class="sxs-lookup"><span data-stu-id="f8bb0-119">Set **Validate TestMap Output** to **True** if you want to validate the output file against the destination schema.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="f8bb0-120">Si vous testez un mappage avec le **entrée TestMap** propriété la valeur **natif** et **valider l’entrée TestMap** et **valider la sortie TestMap** les propriétés définies sur **False**, la validation est toujours effectuée.</span><span class="sxs-lookup"><span data-stu-id="f8bb0-120">If you test a map with the **TestMap Input** property set to **Native** and the **Validate TestMap Input** and **Validate TestMap Output** properties set to **False**, validation will still be performed.</span></span> <span data-ttu-id="f8bb0-121">Cela est dû au fait que le fichier d'entrée natif est converti au format XML et que [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] valide le code XML par rapport au schéma.</span><span class="sxs-lookup"><span data-stu-id="f8bb0-121">This occurs because the native-formatted input file will be converted into XML format, and [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] will validate the XML against the schema.</span></span> <span data-ttu-id="f8bb0-122">S’il existe des problèmes de validation dans l’instance d’entrée, le mécanisme de validation génère des erreurs, même si le **valider l’entrée TestMap** et **valider la sortie TestMap** propriétés sont définies sur **False**.</span><span class="sxs-lookup"><span data-stu-id="f8bb0-122">If there are validation issues in the input instance, the validation mechanism will post errors, even though the **Validate TestMap Input** and **Validate TestMap Output** properties are set to **False**.</span></span>  
  
4.  <span data-ttu-id="f8bb0-123">Définissez **entrée TestMap** à **natif** pour un fichier d’entrée qui a une extension EDI ou.</span><span class="sxs-lookup"><span data-stu-id="f8bb0-123">Set **TestMap Input** to **Native** for an input file that has an .edi extension.</span></span> <span data-ttu-id="f8bb0-124">Affectez-lui la valeur **XML** s’il a une extension .xml.</span><span class="sxs-lookup"><span data-stu-id="f8bb0-124">Set it to **XML** if it has an .xml extension.</span></span> <span data-ttu-id="f8bb0-125">Définissez **entrée TestMap** à **générer l’Instance** avoir [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] générer une instance d’entrée, au lieu de désigner une instance d’entrée manuellement.</span><span class="sxs-lookup"><span data-stu-id="f8bb0-125">Set **TestMap Input** to **Generate Instance** to have [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] generate an input instance, rather than you designating an input instance manually.</span></span>  
  
5.  <span data-ttu-id="f8bb0-126">Définissez **sortie TestMap** à **natif** pour un fichier de sortie qui a une extension EDI ou.</span><span class="sxs-lookup"><span data-stu-id="f8bb0-126">Set **TestMap Output** to **Native** for an output file that has an .edi extension.</span></span> <span data-ttu-id="f8bb0-127">Affectez-lui la valeur **XML** s’il a une extension .xml.</span><span class="sxs-lookup"><span data-stu-id="f8bb0-127">Set it to **XML** if it has an .xml extension.</span></span>  
  
6.  <span data-ttu-id="f8bb0-128">Pour **Instance d’entrée TestMap**, accédez à l’instance d’entrée que vous souhaitez utiliser pour tester le mappage, sélectionnez-le, puis **ouvrir**.</span><span class="sxs-lookup"><span data-stu-id="f8bb0-128">For **TestMap Input Instance**, browse to the input instance that you want to be used to test the map, select it, and then **Open**.</span></span> <span data-ttu-id="f8bb0-129">Si vous souhaitez laisser cette propriété vide, la valeur **entrée TestMap** à **générer l’Instance**.</span><span class="sxs-lookup"><span data-stu-id="f8bb0-129">If you want to leave this property blank, set **TestMap Input** to **Generate Instance**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="f8bb0-130">Vous devez soit désigner une instance d’entrée pour **Instance d’entrée TestMap** ou **entrée TestMap** à **générer l’Instance**.</span><span class="sxs-lookup"><span data-stu-id="f8bb0-130">You have to either designate an input instance for **TestMap Input Instance** or set **TestMap Input** to **Generate Instance**.</span></span> <span data-ttu-id="f8bb0-131">Dans le cas contraire, [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] génère une erreur.</span><span class="sxs-lookup"><span data-stu-id="f8bb0-131">If not, [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] will generate an error.</span></span>  
  
7.  <span data-ttu-id="f8bb0-132">Pour **Instance de sortie TestMap**, accédez à l’emplacement que vous souhaitez enregistrer l’instance de sortie, entrez un nom pour l’instance de sortie, puis cliquez sur **enregistrer**.</span><span class="sxs-lookup"><span data-stu-id="f8bb0-132">For **TestMap Output Instance**, browse to the location you want to save the output instance at, enter a name for the output instance, and then click **Save**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="f8bb0-133">Si vous ne désignez aucune instance de sortie, [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] crée un fichier de sortie, le place dans un dossier, puis indique les noms du fichier et du chemin d'accès.</span><span class="sxs-lookup"><span data-stu-id="f8bb0-133">If you do not designate an output instance, [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] will create an output file, place the output file into a folder, and indicate the file name and path.</span></span>  
  
8.  <span data-ttu-id="f8bb0-134">Avec le bouton droit de la carte que vous testez, puis cliquez sur **Test Map**.</span><span class="sxs-lookup"><span data-stu-id="f8bb0-134">Right-click the map you are testing, and then click **Test Map**.</span></span>  
  
9. <span data-ttu-id="f8bb0-135">Dans le X12 **propriétés de l’Instance EDI** boîte de dialogue, vérifiez que toutes les propriétés sont cohérentes avec les paramètres pour les instances d’entrée et de sortie.</span><span class="sxs-lookup"><span data-stu-id="f8bb0-135">In the X12 **EDI Instance Properties** dialog box, make sure that all properties are consistent with the settings for the input and output instances.</span></span>  
  
    > [!NOTE]
    >  [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="f8bb0-136">Affiche la **propriétés de l’Instance EDI** boîte de dialogue à deux reprises au cours du processus TestMap : une fois pour l’interprétation de l’instance de message d’entrée et une fois pour la génération de l’instance de message de sortie.</span><span class="sxs-lookup"><span data-stu-id="f8bb0-136"> will display the **EDI Instance Properties** dialog box twice during the TestMap process: once for interpreting the input message instance and once for generating the output message instance.</span></span> <span data-ttu-id="f8bb0-137">Toutefois, [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] peut afficher la boîte de dialogue plus de deux fois, ainsi qu'afficher celle-ci pour les schémas non-EDI.</span><span class="sxs-lookup"><span data-stu-id="f8bb0-137">However, [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] may display the dialog box more than just twice and may display the dialog box for non-EDI schema.</span></span> <span data-ttu-id="f8bb0-138">Dans ce cas, cliquez sur **OK** pour fermer la boîte de dialogue.</span><span class="sxs-lookup"><span data-stu-id="f8bb0-138">If so, click **OK** to close the dialog box.</span></span>  
  
10. <span data-ttu-id="f8bb0-139">Cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="f8bb0-139">Click **OK**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f8bb0-140">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f8bb0-140">See Also</span></span>  
 [<span data-ttu-id="f8bb0-141">À l’aide d’outils au moment du Design XML</span><span class="sxs-lookup"><span data-stu-id="f8bb0-141">Using Design-Time XML Tools</span></span>](../core/using-design-time-xml-tools.md)