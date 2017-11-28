---
title: Vous incorporez un nouveau Partner Interface Process | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- deploying, PIP schemas
- PIP schemas
- PIP schemas, deploying
- PIP schemas, downloading
- creating, PIP schemas
- PIP schemas, creating
ms.assetid: 6a5fcbcb-c6aa-40c0-bcca-dd0c391e7f42
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 4874c623c80a008a4f2c1aa5382c49e37616b6af
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="incorporating-a-new-partner-interface-process"></a><span data-ttu-id="32f55-102">Vous incorporez un nouveau Partner Interface Process</span><span class="sxs-lookup"><span data-stu-id="32f55-102">Incorporating a New Partner Interface Process</span></span>
<span data-ttu-id="32f55-103">Vous pouvez incorporer un nouveau schéma de RosettaNet processus PIP (Partner Interface) dans [!INCLUDE[btsCoName](../../includes/btsconame-md.md)]® [!INCLUDE[BTARN_CurrentVersion_FirstRef](../../includes/btarn-currentversion-firstref-md.md)] assemblys.</span><span class="sxs-lookup"><span data-stu-id="32f55-103">You can incorporate a new RosettaNet Partner Interface Process (PIP) schema in [!INCLUDE[btsCoName](../../includes/btsconame-md.md)]® [!INCLUDE[BTARN_CurrentVersion_FirstRef](../../includes/btarn-currentversion-firstref-md.md)] assemblies.</span></span> <span data-ttu-id="32f55-104">Pour faire en :</span><span class="sxs-lookup"><span data-stu-id="32f55-104">You do so by:</span></span>  
  
-   <span data-ttu-id="32f55-105">Télécharger le schéma PIP sur le site Web de RosettaNet à [http://go.microsoft.com/fwlink/?linkid=33859](http://go.microsoft.com/fwlink/?linkid=33859).</span><span class="sxs-lookup"><span data-stu-id="32f55-105">Downloading the PIP schema from the RosettaNet Web site at [http://go.microsoft.com/fwlink/?linkid=33859](http://go.microsoft.com/fwlink/?linkid=33859).</span></span>  
  
-   <span data-ttu-id="32f55-106">Déploiement du schéma à [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] dans le cadre de la [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] assembly RNPIPs ou dans le cadre d’une séparée [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] assembly.</span><span class="sxs-lookup"><span data-stu-id="32f55-106">Deploying the schema to [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] as part of the [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] RNPIPs assembly or as part of a separate [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] assembly.</span></span> <span data-ttu-id="32f55-107">Pour plus d’informations, consultez [extension de BTARN avec un nouveau PIP](../../adapters-and-accelerators/accelerator-rosettanet/extending-btarn-with-a-new-pip.md).</span><span class="sxs-lookup"><span data-stu-id="32f55-107">For more information, see [Extending BTARN with a New PIP](../../adapters-and-accelerators/accelerator-rosettanet/extending-btarn-with-a-new-pip.md).</span></span>  
  
-   <span data-ttu-id="32f55-108">Création d’un nouveau paramètre de Configuration de processus dans le [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] Console de gestion.</span><span class="sxs-lookup"><span data-stu-id="32f55-108">Creating a new Process Configuration Setting in the [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] Management Console.</span></span> <span data-ttu-id="32f55-109">Pour plus d’informations, consultez [comment créer ou modifier une Configuration de processus](../../adapters-and-accelerators/accelerator-rosettanet/how-to-create-or-edit-a-process-configuration.md).</span><span class="sxs-lookup"><span data-stu-id="32f55-109">For more information, see [How to Create or Edit a Process Configuration](../../adapters-and-accelerators/accelerator-rosettanet/how-to-create-or-edit-a-process-configuration.md).</span></span>  
  
 <span data-ttu-id="32f55-110">Le schéma téléchargé est généralement au format .dtd, avec une spécification PIP d’accompagnement de l’organisation RosettaNet sous forme de fichier .doc.</span><span class="sxs-lookup"><span data-stu-id="32f55-110">The downloaded schema is generally in .dtd format, with an accompanying PIP specification from the RosettaNet organization as a .doc file.</span></span> <span data-ttu-id="32f55-111">Le processus d’étendre le pipeline pour utiliser le nouveau schéma inclut la conversion du fichier .dtd PIP dans un fichier .xsd.</span><span class="sxs-lookup"><span data-stu-id="32f55-111">The process of extending the pipeline to use the new schema includes converting the PIP .dtd file into an .xsd file.</span></span>  
  
 <span data-ttu-id="32f55-112">Lorsque vous installez [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)], le [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] SDK inclut un nombre de schémas XSD.</span><span class="sxs-lookup"><span data-stu-id="32f55-112">When you install [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)], the [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] SDK includes a number of XSD schemas.</span></span> <span data-ttu-id="32f55-113">Vous pouvez trouver ces schémas dans le \< *lecteur*> : \Program Files\Microsoft BizTalk \<version > Accelerator for RosettaNet\SDK\Schemas dossier.</span><span class="sxs-lookup"><span data-stu-id="32f55-113">You can find those schemas in the \<*drive*>:\Program Files\Microsoft BizTalk \<version> Accelerator for RosettaNet\SDK\Schemas folder.</span></span> <span data-ttu-id="32f55-114">BTARN génère ces schémas dans un fichier RNPIPs.dll.</span><span class="sxs-lookup"><span data-stu-id="32f55-114">BTARN builds these schemas into an RNPIPs.dll file.</span></span> <span data-ttu-id="32f55-115">Si vous devez modifier l’un de ces schémas, vous devez ouvrir le projet RNPIPs dans le même dossier, modifier le schéma dans l’Éditeur BizTalk, puis recompiler et redéployer l’assembly.</span><span class="sxs-lookup"><span data-stu-id="32f55-115">If you have to change one of these schemas, you must open the RNPIPs project in the same folder, change the schema in BizTalk Editor, and then recompile and redeploy the assembly.</span></span> <span data-ttu-id="32f55-116">Une fois que vous redéployez le fichier RNPIPs.dll, vous devez redéployer le pipeline qui utilise le schéma.</span><span class="sxs-lookup"><span data-stu-id="32f55-116">After you redeploy the RNPIPs.dll file, you must redeploy the pipeline that uses the schema.</span></span> <span data-ttu-id="32f55-117">Ce processus vous permet d’incorporer un nouveau schéma dans BTARN, mais il est plus facile d’étendre le pipeline pour inclure le nouveau schéma.</span><span class="sxs-lookup"><span data-stu-id="32f55-117">You could use this process to incorporate a new schema in BTARN, but it is easier to extend the pipeline to include the new schema.</span></span>  
  
### <a name="to-obtain-the-pip-schema"></a><span data-ttu-id="32f55-118">Pour obtenir le schéma PIP</span><span class="sxs-lookup"><span data-stu-id="32f55-118">To obtain the PIP schema</span></span>  
  
-   <span data-ttu-id="32f55-119">Dans Internet Explorer, accédez au site Web de RosettaNet à [http://go.microsoft.com/fwlink/?linkid=33859](http://go.microsoft.com/fwlink/?linkid=33859).</span><span class="sxs-lookup"><span data-stu-id="32f55-119">In Internet Explorer, go to the RosettaNet Web site at [http://go.microsoft.com/fwlink/?linkid=33859](http://go.microsoft.com/fwlink/?linkid=33859).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="32f55-120">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="32f55-120">See Also</span></span>  
 [<span data-ttu-id="32f55-121">Extension de BTARN avec un nouveau PIP</span><span class="sxs-lookup"><span data-stu-id="32f55-121">Extending BTARN with a New PIP</span></span>](../../adapters-and-accelerators/accelerator-rosettanet/extending-btarn-with-a-new-pip.md)