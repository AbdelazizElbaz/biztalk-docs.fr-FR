---
title: "Validation d’une Instance de Message en utilisant le schéma XSD | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- schema XSD
- validating, messages
- messages, validating
- schemas, XSDs
ms.assetid: c4cbf6b4-130d-4e0f-840b-c8008fafac0b
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 50a4e0b08e3bbe9e29b3417fd6e53475fd98483c
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="validating-a-message-instance-using-the-schema-xsd"></a><span data-ttu-id="47fa5-102">Validation d’une Instance de Message en utilisant le schéma XSD</span><span class="sxs-lookup"><span data-stu-id="47fa5-102">Validating a Message Instance Using the Schema XSD</span></span>
<span data-ttu-id="47fa5-103">Cette rubrique décrit comment valider une instance de message à l’aide d’un des fichiers XSD de schéma que Microsoft® [!INCLUDE[BTARN_CurrentVersion_FirstRef](../../includes/btarn-currentversion-firstref-md.md)] a intégré dans le fichier d’assembly RNPIPs.</span><span class="sxs-lookup"><span data-stu-id="47fa5-103">This topic describes how to validate a message instance using one of the schema XSD files that Microsoft® [!INCLUDE[BTARN_CurrentVersion_FirstRef](../../includes/btarn-currentversion-firstref-md.md)] has built into the RNPIPs assembly file.</span></span>  
  
### <a name="to-validate-a-message-instance-using-the-schema-xsd"></a><span data-ttu-id="47fa5-104">Pour valider une instance de message en utilisant le schéma XSD</span><span class="sxs-lookup"><span data-stu-id="47fa5-104">To validate a message instance using the schema XSD</span></span>  
  
1.  <span data-ttu-id="47fa5-105">Démarrez **Microsoft Visual Studio 2012**.</span><span class="sxs-lookup"><span data-stu-id="47fa5-105">Start **Microsoft Visual Studio 2012**.</span></span>  
  
2.  <span data-ttu-id="47fa5-106">Sur le **fichier**, pointez sur **ouvrir**, puis cliquez sur **projet**.</span><span class="sxs-lookup"><span data-stu-id="47fa5-106">On the **File**, point to **Open**, and then click **Project**.</span></span>  
  
3.  <span data-ttu-id="47fa5-107">Recherchez  *\<lecteur >*\Program Files\Microsoft BizTalk \<version > Accelerator for RosettaNet\SDK\Schemas, cliquez sur **RNPIPs.btproj**, puis cliquez sur **Ouvrir**.</span><span class="sxs-lookup"><span data-stu-id="47fa5-107">Locate *\<drive>*\Program Files\Microsoft BizTalk \<version> Accelerator for RosettaNet\SDK\Schemas, click **RNPIPs.btproj**, and then click **Open**.</span></span>  
  
4.  <span data-ttu-id="47fa5-108">Dans l’Explorateur de solutions, développez **RNPIPs**, cliquez sur le schéma XSD que vous souhaitez utiliser pour valider une instance de message, puis cliquez sur **propriétés**.</span><span class="sxs-lookup"><span data-stu-id="47fa5-108">In Solution Explorer, expand **RNPIPs**, right-click the schema XSD that you want to use to validate a message instance, and then click **Properties**.</span></span>  
  
5.  <span data-ttu-id="47fa5-109">Dans la boîte de dialogue Pages de propriétés, cliquez sur **nom d’Instance d’entrée**, recherchez le dossier qui contient le fichier, sélectionnez le fichier d’instance de message XML, puis cliquez sur **ouvrir**.</span><span class="sxs-lookup"><span data-stu-id="47fa5-109">In the Property Pages dialog box, click **Input Instance Filename**, locate the folder that contains the file, select the message instance XML file, and then click **Open**.</span></span>  
  
6.  <span data-ttu-id="47fa5-110">Cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="47fa5-110">Click **OK**.</span></span>  
  
7.  <span data-ttu-id="47fa5-111">Dans l’Explorateur de solutions, cliquez sur le schéma XSD que vous souhaitez utiliser pour valider une instance de message, puis cliquez sur **valider l’Instance**.</span><span class="sxs-lookup"><span data-stu-id="47fa5-111">In Solution Explorer, right-click the schema XSD that you want to use to validate a message instance, and then click **Validate Instance**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="47fa5-112">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="47fa5-112">See Also</span></span>  
 <span data-ttu-id="47fa5-113">[Modification d’un PIP existant dans RNPIPs](../../adapters-and-accelerators/accelerator-rosettanet/modifying-an-existing-pip-in-rnpips.md) </span><span class="sxs-lookup"><span data-stu-id="47fa5-113">[Modifying an Existing PIP in RNPIPs](../../adapters-and-accelerators/accelerator-rosettanet/modifying-an-existing-pip-in-rnpips.md) </span></span>  
 [<span data-ttu-id="47fa5-114">Utilisation des adresses PIP</span><span class="sxs-lookup"><span data-stu-id="47fa5-114">Working with PIPs</span></span>](../../adapters-and-accelerators/accelerator-rosettanet/working-with-pips.md)