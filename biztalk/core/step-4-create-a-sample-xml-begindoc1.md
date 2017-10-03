---
title: "Étape 4 : Créer un BeginDoc1 XML d’exemple | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e494b4b2-4c83-4293-8ae8-acae29018e7f
caps.latest.revision: "4"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 9a48a4ee378560ad2d0360445e3fb732bb46e79f
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="step-4-create-a-sample-xml-begindoc"></a><span data-ttu-id="7423e-102">Étape 4 : Créer un exemple XML BeginDoc</span><span class="sxs-lookup"><span data-stu-id="7423e-102">Step 4: Create a Sample XML BeginDoc</span></span>
<span data-ttu-id="7423e-103">Enregistrez ce qui suit dans un fichier XML.</span><span class="sxs-lookup"><span data-stu-id="7423e-103">Save the following into an XML file.</span></span> <span data-ttu-id="7423e-104">Si votre test utilise les étapes dans cet exemple et J.D. de l’exemple</span><span class="sxs-lookup"><span data-stu-id="7423e-104">If your test uses the steps in this example, and uses the example's J.D.</span></span> <span data-ttu-id="7423e-105">Sélection d’un objet Edwards OneWorld, ([JDE://CSALES/B4200310]), vous pouvez le supprimer dans le dossier d’entrée et qu’elle provient du dossier de sortie désigné (dossier lié au port EndDocOut).</span><span class="sxs-lookup"><span data-stu-id="7423e-105">Edwards OneWorld object selection, [JDE://CSALES/B4200310], you can drop this into the Input folder and what it come out the designated Out folder (the folder bound to the EndDocOut port).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="7423e-106">Vous devez modifier certaines valeurs pour pointer vers votre J.D.</span><span class="sxs-lookup"><span data-stu-id="7423e-106">You will have to modify some of the values to point to your J.D.</span></span> <span data-ttu-id="7423e-107">Serveur Edwards OneWorld, par exemple, la valeur définie dans szCMComputerID.</span><span class="sxs-lookup"><span data-stu-id="7423e-107">Edwards OneWorld server, for example, the value set in szCMComputerID.</span></span>  
  
```  
<ns0:F4211FSBeginDoc xmlns:ns0="http://schemas.microsoft.com/  
   [JDE://CSALES/B4200310]">  
   <ns0:mnCMJobNumber></ns0:mnCMJobNumber>  
   <ns0:cCMDocAction>A</ns0:cCMDocAction>  
   <ns0:cCMProcessEdits>1</ns0:cCMProcessEdits>  
   <ns0:szCMComputerID>BVISION01</ns0:szCMComputerID>  
   <ns0:cCMUpdateWriteToWF>2</ns0:cCMUpdateWriteToWF>  
   <ns0:szCMProgramID>XMLInterop</ns0:szCMProgramID>  
   <ns0:szCMVersion>ZJDE0001</ns0:szCMVersion>  
   <ns0:szOrderType>SO</ns0:szOrderType>  
   <ns0:szBusinessUnit>M30</ns0:szBusinessUnit>  
   <ns0:szOriginalOrderCo></ns0:szOriginalOrderCo>  
   <ns0:szOriginalOrderNo></ns0:szOriginalOrderNo>  
   <ns0:szOriginalOrderType></ns0:szOriginalOrderType>  
   <ns0:mnAddressNumber>1001</ns0:mnAddressNumber>  
   <ns0:jdOrderDate></ns0:jdOrderDate>  
   <ns0:szReference></ns0:szReference>  
   <ns0:cApplyFreightYN>Y</ns0:cApplyFreightYN>  
   <ns0:szCurrencyCode></ns0:szCurrencyCode>  
   <ns0:cWKSourceOfData></ns0:cWKSourceOfData>  
   <ns0:cWKProcMode></ns0:cWKProcMode>  
   <ns0:mnWKSuppressProcess>0</ns0:mnWKSuppressProcess>  
   <ns0:cRetrieveOrderNo>1</ns0:cRetrieveOrderNo>  
   <ns0:nSourceOfOrder>0</ns0:nSourceOfOrder>  
</ns0:F4211FSBeginDoc>  
```  
  
## <a name="see-also"></a><span data-ttu-id="7423e-108">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="7423e-108">See Also</span></span>  
 <span data-ttu-id="7423e-109">[Étape 1 : Faire référence à la DLL du schéma](../core/step-1-reference-the-schema-dll2.md) </span><span class="sxs-lookup"><span data-stu-id="7423e-109">[Step 1: Reference the Schema DLL](../core/step-1-reference-the-schema-dll2.md) </span></span>  
 <span data-ttu-id="7423e-110">[Étape 2 : Créer l’Orchestration](../core/step-2-create-the-orchestration1.md) </span><span class="sxs-lookup"><span data-stu-id="7423e-110">[Step 2: Create the Orchestration](../core/step-2-create-the-orchestration1.md) </span></span>  
 [<span data-ttu-id="7423e-111">Étape 3 : Créer et exécuter le projet</span><span class="sxs-lookup"><span data-stu-id="7423e-111">Step 3: Complete and Run the Project</span></span>](../core/step-3-complete-and-run-the-project2.md)