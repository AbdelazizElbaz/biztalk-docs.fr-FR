---
title: "Message d’erreur installation | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- installation, error message
- error messages, installation
ms.assetid: 593b033f-03da-43ae-a948-f87aa5e4bccd
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 5ec99a2e9f20b09c4daddad0336037c7f539782a
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="installation-error-message"></a><span data-ttu-id="611e9-102">Message d'erreur relatif à l'installation</span><span class="sxs-lookup"><span data-stu-id="611e9-102">Installation Error Message</span></span>
<span data-ttu-id="611e9-103">Après avoir installé l'adaptateur Microsoft BizTalk pour TIBCO Enterprise Message Service, la définition d'un emplacement d'envoi et de réception qui lui sont associés risque d'entraîner l'erreur suivante :</span><span class="sxs-lookup"><span data-stu-id="611e9-103">After you install Microsoft BizTalk Adapter for TIBCO Enterprise Message Service, defining a send or receive location for it might result in the following error:</span></span>  
  
 <span data-ttu-id="611e9-104">Le moteur de messagerie Impossible d’ajouter une URL de réception «\< envoi/réception\>» à l’adaptateur « TIBCO EMS ».</span><span class="sxs-lookup"><span data-stu-id="611e9-104">The Messaging Engine failed to add a receive URL "\< send/receive location URL\>" to the adapter "TIBCO EMS".</span></span> <span data-ttu-id="611e9-105">Raison : « assembly nom de fichier ou TIBCO. EMS, ou une de ses dépendances, est introuvable. »</span><span class="sxs-lookup"><span data-stu-id="611e9-105">Reason: "File or assembly name TIBCO.EMS, or one of its dependencies, was not found."</span></span>  
  
## <a name="possible-causes"></a><span data-ttu-id="611e9-106">Causes possibles</span><span class="sxs-lookup"><span data-stu-id="611e9-106">Possible Causes</span></span>  
 <span data-ttu-id="611e9-107">Cette erreur provient généralement d'une des causes suivantes.</span><span class="sxs-lookup"><span data-stu-id="611e9-107">This error usually has one of the following causes.</span></span>  
  
### <a name="assembly-not-in-gac"></a><span data-ttu-id="611e9-108">L'assembly ne se trouve pas dans le GAC</span><span class="sxs-lookup"><span data-stu-id="611e9-108">Assembly Not in GAC</span></span>  
 <span data-ttu-id="611e9-109">L’adaptateur BizTalk pour TIBCO EMS est une application .NET Framework et utilise l’assembly .NET Framework, TIBCO. EMS.</span><span class="sxs-lookup"><span data-stu-id="611e9-109">BizTalk Adapter for TIBCO EMS is a .NET Framework application, and uses the .NET Framework assembly, TIBCO.EMS.</span></span> <span data-ttu-id="611e9-110">Cet assembly doit être présent dans le .NET Framework global assembly cache (GAC) pour le .NET Framework se trouve en cours d’exécution.</span><span class="sxs-lookup"><span data-stu-id="611e9-110">This assembly must be present in the .NET Framework global assembly cache (GAC) for the .NET Framework to find it at run time.</span></span>  
  
#### <a name="solution"></a><span data-ttu-id="611e9-111">Solution</span><span class="sxs-lookup"><span data-stu-id="611e9-111">Solution</span></span>  
 <span data-ttu-id="611e9-112">Pour déterminer si l'assembly est présent dans le GAC ou non, ouvrez une invite de commandes, puis tapez la commande suivante :</span><span class="sxs-lookup"><span data-stu-id="611e9-112">To determine if the assembly is present in the GAC, open a command prompt and type the following command:</span></span>  
  
 `GACUTIL /L TIBCO.EMS`  
  
 <span data-ttu-id="611e9-113">Si le résultat n'affiche aucun élément, vous devez ajouter l'assembly au GAC.</span><span class="sxs-lookup"><span data-stu-id="611e9-113">If the result shows zero items, you must add the assembly to the GAC.</span></span> <span data-ttu-id="611e9-114">Pour ce faire, ouvrez une invite de commandes, accédez au répertoire client/cs de l'installation de TIBCO EMS (l'emplacement d'installation par défaut est C:\TIBCO\EMS\Clients\CS), puis exécutez la commande suivante :</span><span class="sxs-lookup"><span data-stu-id="611e9-114">To do this, open a command prompt, change directories to your TIBCO EMS installation clients\cs directory (the default installation location is C:\TIBCO\EMS\Clients\CS), and run the following command:</span></span>  
  
 `GACUTIL /i TIBCO.EMS.DLL`  
  
### <a name="different-version-of-assembly-in-gac"></a><span data-ttu-id="611e9-115">Version de l'assembly différente dans le GAC</span><span class="sxs-lookup"><span data-stu-id="611e9-115">Different Version of Assembly in GAC</span></span>  
 <span data-ttu-id="611e9-116">L'assembly TIBCO.EMS.dll est présent dans le GAC, mais il s'agit d'une version différente de celle utilisée pour créer l'adaptateur BizTalk pour TIBCO EMS.</span><span class="sxs-lookup"><span data-stu-id="611e9-116">The TIBCO.EMS.dll assembly is in the GAC, but it is a different version from the one used to build BizTalk Adapter for TIBCO EMS.</span></span> <span data-ttu-id="611e9-117">Si l'assembly TIBCO.EMS installé sur l'ordinateur provient d'une version 4.2 ou supérieure, il doit être compatible avec la version utilisée pour créer l'adaptateur (vous pouvez vérifiez cette information avec TIBCO).</span><span class="sxs-lookup"><span data-stu-id="611e9-117">If the TIBCO.EMS.dll that is installed on the computer is from a product version 4.2 or above, it should be compatible with the version used to build the adapter (you can verify that information with TIBCO).</span></span>  
  
#### <a name="solution"></a><span data-ttu-id="611e9-118">Solution</span><span class="sxs-lookup"><span data-stu-id="611e9-118">Solution</span></span>  
 <span data-ttu-id="611e9-119">Le .NET Framework fournit une méthode permettant de contourner ce problème.</span><span class="sxs-lookup"><span data-stu-id="611e9-119">The .NET Framework provides a way to work around this problem.</span></span> <span data-ttu-id="611e9-120">Il est appelé *la redirection de liaison*, qui utilise un fichier de configuration.</span><span class="sxs-lookup"><span data-stu-id="611e9-120">It is called *binding redirection*, which uses a configuration file.</span></span>  
  
 <span data-ttu-id="611e9-121">Suivez la procédure suivante pour éliminer le message d'erreur :</span><span class="sxs-lookup"><span data-stu-id="611e9-121">Follow these steps to eliminate the error message:</span></span>  
  
1.  <span data-ttu-id="611e9-122">À l'aide d'un éditeur de texte, ouvrez le fichier BTSNTSVC.exe.config.</span><span class="sxs-lookup"><span data-stu-id="611e9-122">With any text editor, open the file BTSNTSVC.exe.config.</span></span>  
  
     <span data-ttu-id="611e9-123">Ce fichier est situé dans le répertoire [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] (l'emplacement d'installation par défaut est [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]).</span><span class="sxs-lookup"><span data-stu-id="611e9-123">The file is located in the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] directory (the default installation location is: [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]).</span></span>  
  
2.  <span data-ttu-id="611e9-124">Ajoutez l’entrée suivante au fichier BTSNTSVC.exe.config, en tant qu’enfant de la \<assemblyBinding\> élément :</span><span class="sxs-lookup"><span data-stu-id="611e9-124">Add the following entry to the BTSNTSVC.exe.config file, as a child of the \<assemblyBinding\> element:</span></span>  
  
```  
<dependentAssembly>  
    <assemblyIdentity name='TIBCO.EMS'  
        publicKeyToken='5b83db8ff05c64ba ' culture='neutral' />  
    <bindingRedirect oldVersion='1.0.0.0-65535.65535.65535.65535'  
        newVersion='1.0.0.0' />  
</dependentAssembly>  
```  
  
 <span data-ttu-id="611e9-125">Si le fichier BTSNTSVC.exe.config n’a pas été préalablement modifié, le \<assemblyBinding\> élément ne peut pas ressembler à ceci :</span><span class="sxs-lookup"><span data-stu-id="611e9-125">If the BTSNTSVC.exe.config file has not been previously modified, the \<assemblyBinding\> element would not look like this:</span></span>  
  
```  
<assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1">  
    <probing privatePath="BizTalk Assemblies;Developer  
        Tools;Tracking;Tracking\interop" />  
    <dependentAssembly>  
        <assemblyIdentity name='TIBCO.EMS'  
            publicKeyToken='5b83db8ff05c64ba ' culture='neutral' />  
        <bindingRedirect oldVersion='1.0.0.0-65535.65535.65535.65535'  
            newVersion='1.0.0.0' />  
    </dependentAssembly>  
</assemblyBinding>  
```  
  
1.  <span data-ttu-id="611e9-126">Dans une invite de commandes, tapez la commande : `GACUTIL /L TIBCO.EMS`.</span><span class="sxs-lookup"><span data-stu-id="611e9-126">In a command prompt, type the command: `GACUTIL /L TIBCO.EMS`.</span></span>  
  
2.  <span data-ttu-id="611e9-127">Copiez le numéro de version de l'assembly TIBCO.EMS à partir de la sortie.</span><span class="sxs-lookup"><span data-stu-id="611e9-127">Copy the TIBCO.EMS assembly version number from the output.</span></span>  
  
    > [!CAUTION]
    >  <span data-ttu-id="611e9-128">Deux numéros de version s’affichent : un est le numéro de version de l’utilitaire gacutil.</span><span class="sxs-lookup"><span data-stu-id="611e9-128">Two version numbers appear: one is the version number of the gacutil utility.</span></span> <span data-ttu-id="611e9-129">Vous souhaitez que le deuxième numéro de version, il apparaît juste après **Version =**.</span><span class="sxs-lookup"><span data-stu-id="611e9-129">You want the second version number, which appears just after **Version=**.</span></span>  
  
3.  <span data-ttu-id="611e9-130">Collez le numéro de version dans le fichier BTSNTSVC.exe.config, entre guillemets, juste après **newVersion =** (gras les caractères dans l’exemple XML précédent).</span><span class="sxs-lookup"><span data-stu-id="611e9-130">Paste the version number in the BTSNTSVC.exe.config file, between the quotation marks, right after **newVersion=** (bold characters in the previous XML example).</span></span>  
  
4.  <span data-ttu-id="611e9-131">Enregistrez le fichier BTSNTSVC.exe.config modifié.</span><span class="sxs-lookup"><span data-stu-id="611e9-131">Save the modified BTSNTSVC.exe.config file.</span></span>  
  
5.  <span data-ttu-id="611e9-132">Redémarrez l'hôte [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="611e9-132">Restart the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] host.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="611e9-133">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="611e9-133">See Also</span></span>  
 [<span data-ttu-id="611e9-134">Dépannage de TIBCO Enterprise Message Service</span><span class="sxs-lookup"><span data-stu-id="611e9-134">Troubleshooting TIBCO Enterprise Message Service</span></span>](../core/troubleshooting-tibco-enterprise-message-service.md)