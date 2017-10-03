---
title: "Erreur d’obtention des extensions de liaison à partir de machine.config | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 65ab48cf-575b-4db6-984a-880f7e286959
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: b8dfdedb58e4372caed38c7c272cbaaf65fefbcb
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="error-getting-binding-extensions-from-machineconfig"></a><span data-ttu-id="67b5f-102">Erreur lors de l'obtention des extensions de liaison à partir de machine.config.</span><span class="sxs-lookup"><span data-stu-id="67b5f-102">Error getting binding extensions from machine.config</span></span>
## <a name="details"></a><span data-ttu-id="67b5f-103">Détails</span><span class="sxs-lookup"><span data-stu-id="67b5f-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="67b5f-104">Nom du produit</span><span class="sxs-lookup"><span data-stu-id="67b5f-104">Product Name</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|<span data-ttu-id="67b5f-105">Version du produit</span><span class="sxs-lookup"><span data-stu-id="67b5f-105">Product Version</span></span>|[!INCLUDE[btsWCFVersion](../includes/btswcfversion-md.md)]|  
|<span data-ttu-id="67b5f-106">ID d'événement</span><span class="sxs-lookup"><span data-stu-id="67b5f-106">Event ID</span></span>|<span data-ttu-id="67b5f-107">0</span><span class="sxs-lookup"><span data-stu-id="67b5f-107">0</span></span>|  
|<span data-ttu-id="67b5f-108">Source de l'événement</span><span class="sxs-lookup"><span data-stu-id="67b5f-108">Event Source</span></span>|<span data-ttu-id="67b5f-109">0</span><span class="sxs-lookup"><span data-stu-id="67b5f-109">0</span></span>|  
|<span data-ttu-id="67b5f-110">Composant</span><span class="sxs-lookup"><span data-stu-id="67b5f-110">Component</span></span>|<span data-ttu-id="67b5f-111">0</span><span class="sxs-lookup"><span data-stu-id="67b5f-111">0</span></span>|  
|<span data-ttu-id="67b5f-112">Nom symbolique</span><span class="sxs-lookup"><span data-stu-id="67b5f-112">Symbolic Name</span></span>|<span data-ttu-id="67b5f-113">0</span><span class="sxs-lookup"><span data-stu-id="67b5f-113">0</span></span>|  
|<span data-ttu-id="67b5f-114">Texte du message</span><span class="sxs-lookup"><span data-stu-id="67b5f-114">Message Text</span></span>|<span data-ttu-id="67b5f-115">Erreur lors de l'obtention des extensions de liaison à partir de machine.config.</span><span class="sxs-lookup"><span data-stu-id="67b5f-115">Error getting binding extensions from machine.config</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="67b5f-116">Explication</span><span class="sxs-lookup"><span data-stu-id="67b5f-116">Explanation</span></span>  
 <span data-ttu-id="67b5f-117">Cette erreur se produit lorsque la configuration de liaison d'un emplacement de réception ou d'un port d'envoi possède une extension de liaison mais que celle-ci n'est pas définie dans le fichier machine.config.</span><span class="sxs-lookup"><span data-stu-id="67b5f-117">This error occurs when a  receive location or send port binding configuration has a user defined binding extension, but it is not defined in machine.config file.</span></span> <span data-ttu-id="67b5f-118">Cette situation se produit essentiellement avec les adaptateurs WCF-Custom et WCF-CustomIsolated.</span><span class="sxs-lookup"><span data-stu-id="67b5f-118">This situation occurs primarily with the WCF-Custom and WCF-CustomIsolated adapters.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="67b5f-119">Action de l'utilisateur</span><span class="sxs-lookup"><span data-stu-id="67b5f-119">User Action</span></span>  
 <span data-ttu-id="67b5f-120">Définissez l'extension de liaison utilisée dans l'emplacement de réception ou le port d'envoi du fichier machine.config.</span><span class="sxs-lookup"><span data-stu-id="67b5f-120">Define the binding extension used in the receive location or send port in machine.config file.</span></span> <span data-ttu-id="67b5f-121">Par ailleurs, pour qu'un comportement personnalisé ou un élément de liaison fonctionne avec l'adaptateur WCF-Custom, procédez comme suit :</span><span class="sxs-lookup"><span data-stu-id="67b5f-121">Also, to get a custom behavior or binding element to work with WCF-Custom adapter, complete these steps:</span></span>  
  
1.  <span data-ttu-id="67b5f-122">Copiez l'assembly dans le GAC (Global Assembly Cache).</span><span class="sxs-lookup"><span data-stu-id="67b5f-122">GAC the assembly</span></span>  
  
2.  <span data-ttu-id="67b5f-123">Modifiez votre fichier machine.config (trouvé dans **%FrameworkDir%\v4.0.30319\CONFIG**).</span><span class="sxs-lookup"><span data-stu-id="67b5f-123">Modify your machine.config file (found in **%FrameworkDir%\v4.0.30319\CONFIG**).</span></span>  
  
    1.  <span data-ttu-id="67b5f-124">Charge le comportement de votre DLL à l’intérieur de l’éditeur de Configuration de Service (**svcConfigEditor.exe**).</span><span class="sxs-lookup"><span data-stu-id="67b5f-124">Load your behavior DLL inside the Service Configuration Editor (**svcConfigEditor.exe**).</span></span>  
  
    2.  <span data-ttu-id="67b5f-125">Enregistrer la configuration pour un **app.config** fichier</span><span class="sxs-lookup"><span data-stu-id="67b5f-125">Save the configuration to an **app.config** file</span></span>  
  
    3.  <span data-ttu-id="67b5f-126">Copiez et collez le **system.servicemodel** section des extensions dans une section similaire dans le fichier machine.config. Si **system.servicemodel** section n’est pas présente dans le fichier, vous devez en créer un.</span><span class="sxs-lookup"><span data-stu-id="67b5f-126">Copy and paste the **system.servicemodel** extensions section in a similar section in machine.config. If **system.servicemodel** section is not present in machine.config, your must create one.</span></span> <span data-ttu-id="67b5f-127">Vous trouverez ci-dessous un exemple de la section de configuration d'un fichier machine.config :</span><span class="sxs-lookup"><span data-stu-id="67b5f-127">The following is an example from the configuration section of a machine.config file:</span></span>  
  
        ```  
          <system.serviceModel>  
            <extensions>  
              <behaviorExtensions>  
                <add name="BizTalkWcfContractNamespaceTestServiceBehaviorExtension" type="ASB.BizTalk.Samples.BizTalkWcfContractNamespaceTestServiceBehaviorExtension, CustomBizTalkWcfBehaviors, Version=1.0.0.0, Culture=neutral, PublicKeyToken=7631521c07cf34b4" />  
              </behaviorExtensions>  
            </extensions>  
          </system.serviceModel>  
        ```  
  
> [!NOTE]
>  <span data-ttu-id="67b5f-128">Le code ci-dessus peut également être ajouté à l’onglet Extensions WCF. Si l’extension doit être du côté réception, consultez le  **\<nom d’hôte > boîte de dialogue Propriétés, les Extensions WCF** onglet (WCF-Custom ou Gestionnaire de réception de l’adaptateur WCF-CustomIsolated) [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)].</span><span class="sxs-lookup"><span data-stu-id="67b5f-128">The above code can also be added to the WCF Extensions tab. If the extension needs to be on the receive side, see the **\<Host Name> Properties Dialog Box, WCF Extensions** tab (WCF-Custom or WCF-CustomIsolated Adapter Receive Handler) [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)].</span></span> <span data-ttu-id="67b5f-129">Si l’extension doit se trouver du côté envoi, consultez  **\<nom d’hôte > boîte de dialogue Propriétés, les Extensions WCF** onglet (Gestionnaire d’envoi WCF-Custom adaptateur) [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)].</span><span class="sxs-lookup"><span data-stu-id="67b5f-129">If the extension needs to be on the send side, see **\<Host Name> Properties Dialog Box, WCF Extensions** tab (WCF-Custom Adapter Send Handler) [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)].</span></span>  
  
 3. <span data-ttu-id="67b5f-130">Fermez et rouvrez la console Administration.</span><span class="sxs-lookup"><span data-stu-id="67b5f-130">Close and reopen your admin console.</span></span> <span data-ttu-id="67b5f-131">L'adaptateur WCF-Custom doit désormais inclure le comportement personnalisé. Une fois activé, le port ne doit pas être désactivé.</span><span class="sxs-lookup"><span data-stu-id="67b5f-131">You should be able to see your custom behavior in the WCF-Custom adapter, and the port should stay enabled when you enable it.</span></span>