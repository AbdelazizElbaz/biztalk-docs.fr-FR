---
title: "Comment ajouter le comportement de l’intercepteur BAM au fichier Machine.config | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 2ea09925-264f-4976-8e34-f63bad70f886
caps.latest.revision: "15"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: abc8845333389c95ea52d440437935d4c4867dc1
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-add-the-bam-interceptor-behavior-to-the-machineconfig-file"></a><span data-ttu-id="b6d37-102">Ajout du comportement de l'intercepteur BAM au fichier Machine.config</span><span class="sxs-lookup"><span data-stu-id="b6d37-102">How to Add the BAM Interceptor Behavior to the Machine.config File</span></span>
<span data-ttu-id="b6d37-103">Pour intercepter des données dans l'analyse BAM, vous devez ajouter le comportement d'intercepteur BAM au fichier machine.config Microsoft .NET.</span><span class="sxs-lookup"><span data-stu-id="b6d37-103">To intercept data in BAM, you must add the BAM interceptor behavior to the Microsoft .NET machine.config file.</span></span> <span data-ttu-id="b6d37-104">Pour ce faire, deux possibilités :</span><span class="sxs-lookup"><span data-stu-id="b6d37-104">You can do this in two ways:</span></span>  
  
-   <span data-ttu-id="b6d37-105">modifier manuellement le fichier machine.config pour inclure le comportement ;</span><span class="sxs-lookup"><span data-stu-id="b6d37-105">Manually edit the machine.config file to include the behavior.</span></span>  
  
-   <span data-ttu-id="b6d37-106">utiliser l'éditeur de configuration de service pour inclure le comportement.</span><span class="sxs-lookup"><span data-stu-id="b6d37-106">Use the Service Configuration Editor to include the behavior.</span></span>  
  
### <a name="to-manually-edit-the-machineconfig-file"></a><span data-ttu-id="b6d37-107">Pour modifier manuellement le fichier machine.config</span><span class="sxs-lookup"><span data-stu-id="b6d37-107">To manually edit the machine.config file</span></span>  
  
1.  <span data-ttu-id="b6d37-108">Modifiez le fichier machine.config situé dans le dossier de configuration Microsoft .NET.</span><span class="sxs-lookup"><span data-stu-id="b6d37-108">Edit the machine.config file located in the Microsoft .NET configuration folder.</span></span> <span data-ttu-id="b6d37-109">Pour ce faire, cliquez sur **Démarrer**, cliquez sur **exécuter**, tapez notepad c:\WINDOWS\Microsoft.NET\Framework\v4.0.30319\Config\machine.config, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="b6d37-109">To do this, click **Start**, click **Run**, type notepad c:\WINDOWS\Microsoft.NET\Framework\v4.0.30319\Config\machine.config, and then click **OK**.</span></span>  
  
2.  <span data-ttu-id="b6d37-110">Mettez à jour le fichier machine.config avec les extensions de comportement suivantes.</span><span class="sxs-lookup"><span data-stu-id="b6d37-110">Update the machine.config file with the following behavior extensions.</span></span>  
  
    ```  
    <system.serviceModel>  
      <extensions>  
        <behaviorExtensions>  
          <add name="BAMEndPointBehaviorExtension" type="Microsoft.BizTalk.Bam.Interceptors.Wcf.BamEndpointBehavior, Microsoft.BizTalk.Bam.Interceptors, Version=3.0.1.0, Culture=neutral, PublicKeyToken=31bf3856ad364e35" />  
        </behaviorExtensions>  
      </extensions>  
    </system.serviceModel>  
    ```  
  
3.  <span data-ttu-id="b6d37-111">Fermez et enregistrez le fichier machine.config.</span><span class="sxs-lookup"><span data-stu-id="b6d37-111">Close and save the machine.config file.</span></span>  
  
#### <a name="to-edit-the-machineconfig-file-using-the-service-configuration-editor"></a><span data-ttu-id="b6d37-112">Pour modifier le fichier machine.config à l'aide de l'éditeur de configuration de service</span><span class="sxs-lookup"><span data-stu-id="b6d37-112">To edit the machine.config file using the Service Configuration Editor</span></span>  
  
1.  <span data-ttu-id="b6d37-113">Ouvrez l'éditeur de configuration de service.</span><span class="sxs-lookup"><span data-stu-id="b6d37-113">Open the Service Configuration Editor.</span></span> <span data-ttu-id="b6d37-114">Pour plus d’informations sur l’utilisation de l’éditeur de Configuration de Service, consultez [http://go.microsoft.com/fwlink/?LinkId=83557](http://go.microsoft.com/fwlink/?LinkId=83557).</span><span class="sxs-lookup"><span data-stu-id="b6d37-114">For information about using the Service Configuration Editor, see [http://go.microsoft.com/fwlink/?LinkId=83557](http://go.microsoft.com/fwlink/?LinkId=83557).</span></span>  
  
2.  <span data-ttu-id="b6d37-115">Dans le volet d’arborescence (étiqueté **Configuration**), développez l’arborescence de nœuds.</span><span class="sxs-lookup"><span data-stu-id="b6d37-115">In the tree view pane (labeled **Configuration**), expand the node tree.</span></span> <span data-ttu-id="b6d37-116">Cliquez sur le **avancé** dossier, cliquez sur le **Extensions** dossier, puis sélectionnez le **extensions d’élément de comportement** élément.</span><span class="sxs-lookup"><span data-stu-id="b6d37-116">Click the **Advanced** folder, click the **Extensions** folder, and then select the **behavior element extensions** element.</span></span>  
  
3.  <span data-ttu-id="b6d37-117">Créez une extension d'élément de comportement.</span><span class="sxs-lookup"><span data-stu-id="b6d37-117">Create a new behavior element extension.</span></span> <span data-ttu-id="b6d37-118">Cliquez sur le **nouveau** bouton pour ouvrir la boîte de dialogue Éditeur de Configuration d’élément d’Extension.</span><span class="sxs-lookup"><span data-stu-id="b6d37-118">Click the **New** button to open the Extension Configuration Element Editor dialog box.</span></span> <span data-ttu-id="b6d37-119">Dans **nom de la Configuration** Entrez un nom unique pour le comportement, par exemple BAMEndPointBehaviorExtension.</span><span class="sxs-lookup"><span data-stu-id="b6d37-119">In **Configuration Name** enter a unique name for the behavior, for example BAMEndPointBehaviorExtension.</span></span>  
  
     <span data-ttu-id="b6d37-120">![Éditeur de Configuration d’élément d’extension](../core/media/00a053ba-1993-4e52-a336-e452cc60691c.gif "00a053ba-1993-4e52-a336-e452cc60691c")</span><span class="sxs-lookup"><span data-stu-id="b6d37-120">![Extension Configuration Element Editor](../core/media/00a053ba-1993-4e52-a336-e452cc60691c.gif "00a053ba-1993-4e52-a336-e452cc60691c")</span></span>  
  
4.  <span data-ttu-id="b6d37-121">Cliquez sur le **Type** champ, puis cliquez sur le bouton de sélection (**...** ) pour ouvrir la boîte de dialogue Explorateur de Type Extension de comportement.</span><span class="sxs-lookup"><span data-stu-id="b6d37-121">Click the **Type** field, and then click the ellipsis button (**...**) button to open the Behavior Extension Type Browser dialog box.</span></span>  
  
5.  <span data-ttu-id="b6d37-122">Cliquez sur l'icône Global Assembly Cache (GAC) pour répertorier les DLL dans le GAC.</span><span class="sxs-lookup"><span data-stu-id="b6d37-122">Click the global assembly cache (GAC) icon to list the DLLs in GAC.</span></span>  
  
6.  <span data-ttu-id="b6d37-123">Sélectionnez l'assembly Microsoft.BizTalk.Bam.Interceptors.</span><span class="sxs-lookup"><span data-stu-id="b6d37-123">Select the Microsoft.BizTalk.Bam.Interceptors assembly.</span></span>  
  
7.  <span data-ttu-id="b6d37-124">Cliquez sur le **ouvrir** bouton pour sélectionner l’assembly, puis fermez la boîte de dialogue.</span><span class="sxs-lookup"><span data-stu-id="b6d37-124">Click the **Open** button to select the assembly, and then close the dialog box.</span></span>  
  
     <span data-ttu-id="b6d37-125">![Extensions Bejavopr](../core/media/0d525d4c-927c-42d6-96b7-0ebaf2691c6c.gif "0d525d4c-927c-42d6-96b7-0ebaf2691c6c")</span><span class="sxs-lookup"><span data-stu-id="b6d37-125">![Bejavopr Extension Type Browser](../core/media/0d525d4c-927c-42d6-96b7-0ebaf2691c6c.gif "0d525d4c-927c-42d6-96b7-0ebaf2691c6c")</span></span>  
  
8.  <span data-ttu-id="b6d37-126">Dans le volet Nom du type de la boîte de dialogue Explorateur de types d'extension de comportement, double-cliquez sur le type Microsoft.BizTalk.Bam.Interceptors.Wcf.BamEndpointBehavior (mis en surbrillance dans l'écran suivant).</span><span class="sxs-lookup"><span data-stu-id="b6d37-126">In the Type Name pane of the Behavior Extension Type Browser dialog box, double-click the Microsoft.BizTalk.Bam.Interceptors.Wcf.BamEndpointBehavior type (as highlighted in the following screen).</span></span>  
  
     <span data-ttu-id="b6d37-127">![Extensions Bejavopr](../core/media/67186ad6-8802-4214-be46-11e50e4ff15d.gif "67186ad6-8802-4214-be46-11e50e4ff15d")</span><span class="sxs-lookup"><span data-stu-id="b6d37-127">![Bejavopr Extension Type Browser](../core/media/67186ad6-8802-4214-be46-11e50e4ff15d.gif "67186ad6-8802-4214-be46-11e50e4ff15d")</span></span>  
  
     <span data-ttu-id="b6d37-128">Ceci permet d'ouvrir l'éditeur des éléments de configuration d'extension.</span><span class="sxs-lookup"><span data-stu-id="b6d37-128">This opens the Extension Configuration Element Editor.</span></span>  
  
9. <span data-ttu-id="b6d37-129">Cliquez sur **OK** pour fermer la boîte de dialogue Éditeur de Configuration d’élément d’Extension.</span><span class="sxs-lookup"><span data-stu-id="b6d37-129">Click **OK** to close the Extension Configuration Element Editor dialog box.</span></span>  
  
10. <span data-ttu-id="b6d37-130">Dans le volet Détails de l'éditeur de configuration de service, vérifiez que BAMEndPointBehaviorExtension apparaît.</span><span class="sxs-lookup"><span data-stu-id="b6d37-130">In the details pane of the Service Configuration Editor, verify that the BAMEndPointBehaviorExtension appears.</span></span>  
  
11. <span data-ttu-id="b6d37-131">Fermez l'éditeur de configuration de service.</span><span class="sxs-lookup"><span data-stu-id="b6d37-131">Close the Service Configuration Editor.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="b6d37-132">Étapes suivantes</span><span class="sxs-lookup"><span data-stu-id="b6d37-132">Next Steps</span></span>  
 [<span data-ttu-id="b6d37-133">Comment configurer l’Interception WCF BAM</span><span class="sxs-lookup"><span data-stu-id="b6d37-133">How to Configure the BAM WCF Interception</span></span>](../core/how-to-configure-the-bam-wcf-interception.md)  
  
## <a name="see-also"></a><span data-ttu-id="b6d37-134">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b6d37-134">See Also</span></span>  
 [<span data-ttu-id="b6d37-135">Configuration de l’adaptateur WCF pour intercepter les données BAM</span><span class="sxs-lookup"><span data-stu-id="b6d37-135">Configuring the WCF Adapter to Intercept BAM Data</span></span>](../core/configuring-the-wcf-adapter-to-intercept-bam-data.md)