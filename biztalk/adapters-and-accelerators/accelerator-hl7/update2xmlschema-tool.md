---
title: Outil de Update2XMLSchema | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- 2.XML schemas, Update2XMLSchema tool
- schemas, Update2XMLSchema tool
- Update2XMLSchema tool
- Update2XMLSchema tool, syntax
ms.assetid: fd861e2f-ebda-427f-bd52-a2f05b7e22da
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: e673e55557af87e5f28005a50c2a01aedf09d2c9
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="update2xmlschema-tool"></a><span data-ttu-id="106f8-102">Outil de Update2XMLSchema</span><span class="sxs-lookup"><span data-stu-id="106f8-102">Update2XMLSchema Tool</span></span>
<span data-ttu-id="106f8-103">L’outil Update2XMLSchema vous permet de modifier les schémas HL7 2. pour fonctionner avec l’Éditeur BizTalk.</span><span class="sxs-lookup"><span data-stu-id="106f8-103">The Update2XMLSchema tool enables you to modify HL7 2.XML schemas to work with BizTalk Editor.</span></span> <span data-ttu-id="106f8-104">Cela est nécessaire car certains schémas XML de 2 HL7 ne fonctionnent pas correctement dans [!INCLUDE[btsCoName](../../includes/btsconame-md.md)] [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] sans modification.</span><span class="sxs-lookup"><span data-stu-id="106f8-104">This is necessary because certain HL7 2.XML schemas do not work correctly within [!INCLUDE[btsCoName](../../includes/btsconame-md.md)][!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] without modification.</span></span> <span data-ttu-id="106f8-105">Après avoir modifié les schémas, l’outil les place dans le dossier schémas où [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] est installé, par exemple,  *\<lecteur >*: \Program Files\Microsoft BizTalk \<version > Accelerator for HL7\Templates\Schemas.</span><span class="sxs-lookup"><span data-stu-id="106f8-105">After modifying the schemas, the tool places them in the Schemas folder where [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] is installed, for instance, *\<drive>*:\Program Files\Microsoft BizTalk \<version> Accelerator for HL7\Templates\Schemas.</span></span>  
  
 <span data-ttu-id="106f8-106">Vous devez mettre à jour manuellement certains champs des schémas qui résultent de l’exécution de l’outil Update2XMLSchema.</span><span class="sxs-lookup"><span data-stu-id="106f8-106">You need to update manually some fields of the schemas that result from running the Update2XMLSchema tool.</span></span> <span data-ttu-id="106f8-107">Consultez [mises à jour manuelles nécessaires](../../adapters-and-accelerators/accelerator-hl7/required-manual-updates.md) pour obtenir la liste de ces schémas.</span><span class="sxs-lookup"><span data-stu-id="106f8-107">See [Required Manual Updates](../../adapters-and-accelerators/accelerator-hl7/required-manual-updates.md) for a list of those schemas.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="106f8-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="106f8-108">Syntax</span></span>  
 <span data-ttu-id="106f8-109">Cet outil se trouve dans  *\<lecteur >*: \Program Files\Microsoft BizTalk \<version > Accelerator for HL7\SDK\2XML utilitaires.</span><span class="sxs-lookup"><span data-stu-id="106f8-109">This tool is located in *\<drive>*:\Program Files\Microsoft BizTalk \<version> Accelerator for HL7\SDK\2XML Utilities.</span></span> <span data-ttu-id="106f8-110">Vous exécutez cet outil à l’invite de commandes avec la commande suivante :</span><span class="sxs-lookup"><span data-stu-id="106f8-110">You run this tool at the command prompt with the following command:</span></span>  
  
```  
Update2XMLSchema /s /v  
```  
  
 <span data-ttu-id="106f8-111">Le tableau suivant répertorie les paramètres à utiliser avec cette commande.</span><span class="sxs-lookup"><span data-stu-id="106f8-111">The following table lists the parameters to use with this command.</span></span>  
  
|<span data-ttu-id="106f8-112">Paramètre</span><span class="sxs-lookup"><span data-stu-id="106f8-112">Parameter</span></span>|<span data-ttu-id="106f8-113">Nom</span><span class="sxs-lookup"><span data-stu-id="106f8-113">Name</span></span>|<span data-ttu-id="106f8-114">Valeur</span><span class="sxs-lookup"><span data-stu-id="106f8-114">Value</span></span>|  
|---------------|----------|-----------|  
|<span data-ttu-id="106f8-115">*S*</span><span class="sxs-lookup"><span data-stu-id="106f8-115">*S*</span></span>|<span data-ttu-id="106f8-116">Source</span><span class="sxs-lookup"><span data-stu-id="106f8-116">Source</span></span>|<span data-ttu-id="106f8-117">Chemin d’accès complet des schémas HL7 d’origine</span><span class="sxs-lookup"><span data-stu-id="106f8-117">Full path of the original HL7 schemas</span></span>|  
|<span data-ttu-id="106f8-118">*V*</span><span class="sxs-lookup"><span data-stu-id="106f8-118">*V*</span></span>|<span data-ttu-id="106f8-119">Version</span><span class="sxs-lookup"><span data-stu-id="106f8-119">Version</span></span>|<span data-ttu-id="106f8-120">La version des schémas XML 2 : 2.3.1, 2.4 ou 2.5</span><span class="sxs-lookup"><span data-stu-id="106f8-120">The version of the 2.XML schemas:  either 2.3.1, 2.4, or 2.5</span></span>|  
  
## <a name="example"></a><span data-ttu-id="106f8-121">Exemple</span><span class="sxs-lookup"><span data-stu-id="106f8-121">Example</span></span>  
  
-   <span data-ttu-id="106f8-122">Si vous souhaitez modifier des schémas XML de la version 2.3.1 2 situés dans le répertoire c:\231XML\v231\xsd, vous indiquez la commande suivante à l’invite de commandes :</span><span class="sxs-lookup"><span data-stu-id="106f8-122">If you want to modify version 2.3.1 2.XML schemas located in the c:\231XML\v231\xsd directory, you would type the following command at the command prompt:</span></span>  
  
```  
Update2XMLSchema /s c:\231XML\v231\xsd /v 2.3.1  
```  
  
## <a name="in-this-section"></a><span data-ttu-id="106f8-123">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="106f8-123">In This Section</span></span>  
  
-   [<span data-ttu-id="106f8-124">Mises à jour manuelles requises</span><span class="sxs-lookup"><span data-stu-id="106f8-124">Required Manual Updates</span></span>](../../adapters-and-accelerators/accelerator-hl7/required-manual-updates.md)