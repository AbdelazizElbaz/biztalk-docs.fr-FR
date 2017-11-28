---
title: "Procédure d’ouverture, enregistrement, fermeture et renommage des mappages | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 9aa88ca7-a731-4295-8692-6dd36fdf0872
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 2bad04c72e4c3f0caf1af8e223d3f17e4687b736
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-open-save-close-and-rename-maps"></a><span data-ttu-id="4a399-102">Ouverture, enregistrement, fermeture et renommage des mappages</span><span class="sxs-lookup"><span data-stu-id="4a399-102">How to Open, Save, Close, and Rename Maps</span></span>
<span data-ttu-id="4a399-103">Dans Microsoft [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], les mappages sont des fichiers du système de fichiers dotés de l'extension .btm.</span><span class="sxs-lookup"><span data-stu-id="4a399-103">In Microsoft [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], maps exist as files in the file system with .btm extensions.</span></span> <span data-ttu-id="4a399-104">Toutefois, il est beaucoup plus courant de travailler avec les mappages en tant qu'éléments d'un projet BizTalk à partir desquels vous effectuez des opérations comme ouvrir, enregistrer et fermer des mappages.</span><span class="sxs-lookup"><span data-stu-id="4a399-104">Nevertheless, it is much more common to work with maps as items in a BizTalk project, from which you perform operations such as opening, saving, and closing maps.</span></span>  
  
### <a name="to-open-a-map"></a><span data-ttu-id="4a399-105">Pour ouvrir un mappage</span><span class="sxs-lookup"><span data-stu-id="4a399-105">To open a map</span></span>  
  
1.  <span data-ttu-id="4a399-106">Dans l'Explorateur de solutions, sélectionnez le mappage que vous souhaitez ouvrir.</span><span class="sxs-lookup"><span data-stu-id="4a399-106">In Solution Explorer, select the map you want to open.</span></span>  
  
2.  <span data-ttu-id="4a399-107">Sur le **vue** menu, cliquez sur **ouvrir**.</span><span class="sxs-lookup"><span data-stu-id="4a399-107">On the **View** menu, click **Open**.</span></span>  
  
     <span data-ttu-id="4a399-108">Le mappage s'ouvre dans le Mappeur BizTalk.</span><span class="sxs-lookup"><span data-stu-id="4a399-108">The map opens in BizTalk Mapper.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="4a399-109">Vous pouvez également avec le bouton droit de la carte dans l’Explorateur de solutions, puis cliquez sur **ouvrir**, ou double-cliquez simplement sur la carte dans l’Explorateur de solutions.</span><span class="sxs-lookup"><span data-stu-id="4a399-109">You can also right-click the map in Solution Explorer, and then click **Open**, or simply double-click the map in Solution Explorer.</span></span>  
  
### <a name="to-save-a-map"></a><span data-ttu-id="4a399-110">Pour enregistrer un mappage</span><span class="sxs-lookup"><span data-stu-id="4a399-110">To save a map</span></span>  
  
1.  <span data-ttu-id="4a399-111">Dans l'Explorateur de solutions, sélectionnez le mappage que vous souhaitez enregistrer.</span><span class="sxs-lookup"><span data-stu-id="4a399-111">In Solution Explorer, select the map you want to save.</span></span>  
  
2.  <span data-ttu-id="4a399-112">Sur le **fichier** menu, cliquez sur **enregistrer  *\<nom de la carte >***.</span><span class="sxs-lookup"><span data-stu-id="4a399-112">On the **File** menu, click **Save *\<Name of Map>***.</span></span>  
  
### <a name="to-save-a-map-to-a-new-location"></a><span data-ttu-id="4a399-113">Pour enregistrer un mappage à un nouvel emplacement</span><span class="sxs-lookup"><span data-stu-id="4a399-113">To save a map to a new location</span></span>  
  
1.  <span data-ttu-id="4a399-114">Dans l'Explorateur de solutions, sélectionnez le mappage que vous souhaitez enregistrer à un nouvel emplacement.</span><span class="sxs-lookup"><span data-stu-id="4a399-114">In Solution Explorer, select the map you want to save to a new location.</span></span>  
  
2.  <span data-ttu-id="4a399-115">Sur le **fichier** menu, cliquez sur **enregistrer  *\<nom de la carte >* comme**.</span><span class="sxs-lookup"><span data-stu-id="4a399-115">On the **File** menu, click **Save *\<Name of Map>* As**.</span></span>  
  
3.  <span data-ttu-id="4a399-116">Dans le **enregistrer le fichier sous** boîte de dialogue, accédez à l’emplacement du dossier où vous souhaitez enregistrer la carte.</span><span class="sxs-lookup"><span data-stu-id="4a399-116">In the **Save File As** dialog box, browse to the folder location where you want to save the map.</span></span>  
  
4.  <span data-ttu-id="4a399-117">Dans le **nom de fichier** zone, tapez un nom pour le fichier, puis cliquez sur **enregistrer**.</span><span class="sxs-lookup"><span data-stu-id="4a399-117">In the **File name** box, type a name for the file, and then click **Save**.</span></span>  
  
    > [!IMPORTANT]
    >  <span data-ttu-id="4a399-118">N’utilisez pas les noms suivants pour les mappages : « XmlContent », « SourceSchemas », « TargetSchemas » ou « Et » ; Cela entraîne des problèmes de compilation dans le code c# généré dans l’assembly .NET correspondant.</span><span class="sxs-lookup"><span data-stu-id="4a399-118">Do not use the following names for maps: "XmlContent", "SourceSchemas", "TargetSchemas", or "XsltArgumentListContent"; doing so will cause compilation problems in the generated C# code in the corresponding .NET assembly.</span></span> <span data-ttu-id="4a399-119">Pour plus d’informations sur les problèmes et leur résolution, consultez [résolution des problèmes de cartes](../core/troubleshooting-maps.md).</span><span class="sxs-lookup"><span data-stu-id="4a399-119">For information about issues and their resolution, see [Troubleshooting Maps](../core/troubleshooting-maps.md).</span></span>  
  
### <a name="to-rename-a-map"></a><span data-ttu-id="4a399-120">Pour renommer un mappage</span><span class="sxs-lookup"><span data-stu-id="4a399-120">To rename a map</span></span>  
  
1.  <span data-ttu-id="4a399-121">Dans l’Explorateur de solutions, cliquez sur la carte que vous souhaitez renommer, puis cliquez sur **renommer**.</span><span class="sxs-lookup"><span data-stu-id="4a399-121">In Solution Explorer, right-click the map that you want to rename, and then click **Rename**.</span></span>  
  
2.  <span data-ttu-id="4a399-122">Dans la zone d'édition qui apparaît à l'emplacement du mappage dans l'Explorateur de solutions, tapez le nouveau nom du mappage ou modifiez son nom actuel, puis appuyez sur ENTRÉE.</span><span class="sxs-lookup"><span data-stu-id="4a399-122">In the editing box that appears in the location of the map in Solution Explorer, type the new name for the map, or alter its existing name, and then press ENTER.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="4a399-123">Vous pouvez également modifier le **nom de Type** de la carte lorsque vous le renommez.</span><span class="sxs-lookup"><span data-stu-id="4a399-123">You may also want to change the **Type Name** of the map when you rename it.</span></span> <span data-ttu-id="4a399-124">Vous modifiez le **nom de Type** en sélectionnant le **carte** dans l’Explorateur de solutions et entrer le nouveau nom dans la **nom de Type** dans la fenêtre Propriétés.</span><span class="sxs-lookup"><span data-stu-id="4a399-124">You change the **Type Name** by selecting the **map** in the solution explorer and entering the new name in the **Type Name** in the Properties window.</span></span>  
  
#### <a name="to-close-a-map"></a><span data-ttu-id="4a399-125">Pour fermer un mappage</span><span class="sxs-lookup"><span data-stu-id="4a399-125">To close a map</span></span>  
  
1.  <span data-ttu-id="4a399-126">Dans l'Explorateur de solutions, sélectionnez le mappage que vous souhaitez fermer.</span><span class="sxs-lookup"><span data-stu-id="4a399-126">In Solution Explorer, select the map you want to close.</span></span>  
  
2.  <span data-ttu-id="4a399-127">Dans le menu **Fichier** , cliquez sur **Fermer**.</span><span class="sxs-lookup"><span data-stu-id="4a399-127">On the **File** menu, click **Close**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="4a399-128">Vous pouvez également cliquer sur l’icône de fermeture ([**x**]) dans le coin supérieur droit de Microsoft [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] fenêtre d’édition.</span><span class="sxs-lookup"><span data-stu-id="4a399-128">You can also click the close icon ([**x**]) in the upper-right corner of the Microsoft [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] editing window.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4a399-129">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="4a399-129">See Also</span></span>  
 [<span data-ttu-id="4a399-130">La gestion des mappages dans des projets</span><span class="sxs-lookup"><span data-stu-id="4a399-130">Managing Maps Within Projects</span></span>](../core/managing-maps-within-projects.md)