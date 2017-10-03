---
title: "Développement personnalisé référencé fonctoid | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1e26d726-240c-4dfc-baa2-77451b8dc6c5
caps.latest.revision: "13"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: c70f9cfcfaf50d92758f808346380b0a351a2f45
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="developing-a-custom-referenced-functoid"></a><span data-ttu-id="f84f3-102">Développement d'un fonctoid référencé personnalisé</span><span class="sxs-lookup"><span data-stu-id="f84f3-102">Developing a Custom Referenced Functoid</span></span>
<span data-ttu-id="f84f3-103">Les fonctoids référencés personnalisés ne copient pas le code inline d'implémentation dans le mappage.</span><span class="sxs-lookup"><span data-stu-id="f84f3-103">Custom referenced functoids do not copy implementation code inline into the map.</span></span> <span data-ttu-id="f84f3-104">À la place, une référence à l’assembly, à la classe et à la méthode est placée dans le fichier de l'objet d'extension associé à la feuille de style générée et appelé au moment de l’exécution.</span><span class="sxs-lookup"><span data-stu-id="f84f3-104">Instead, a reference to the assembly, class, and method is placed in the extension object file associated with the generated style sheet and called at run time.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f84f3-105">Exemple</span><span class="sxs-lookup"><span data-stu-id="f84f3-105">Example</span></span>  
 <span data-ttu-id="f84f3-106">L'exemple suivant montre comment créer un fonctoid référencé personnalisé pour concaténer deux chaînes.</span><span class="sxs-lookup"><span data-stu-id="f84f3-106">The following example illustrates how to create a custom referenced functoid for concatenating two strings.</span></span> <span data-ttu-id="f84f3-107">Il repose sur un fichier de ressources contenant trois ressources de chaîne et une ressource bitmap 16 x 16 pixels.</span><span class="sxs-lookup"><span data-stu-id="f84f3-107">It relies on a resource file containing three string resources and a 16x16-pixel bitmap resource.</span></span>  
  
```  
using System;  
using Microsoft.BizTalk.BaseFunctoids;  
using System.Reflection;  
  
namespace Microsoft.Samples.BizTalk.CustomFunctoid  
{  
    /// <summary>  
    /// Performs a string concatenation through assembly referenced function. Assembly must be deployed with the BizTalk solution.  
    /// </summary>  
    public class CustomStringConcatFunctoid : BaseFunctoid  
    {  
        public CustomStringConcatFunctoid()  
            : base()  
        {  
            //ID for this functoid  
            this.ID = 6001;  
  
            // Resource assembly must be ProjectName.ResourceName if building with VS.Net  
            SetupResourceAssembly("Microsoft.Samples.BizTalk.CustomFunctoid.CustomFunctoidResources", Assembly.GetExecutingAssembly());  
  
            // Pass the resource ID names for functoid name, tooltip  
            // description and the 16x16 bitmap for the Map palette  
            SetName("IDS_CUSTOMSTRINGCONCATFUNCTOID_NAME");  
            SetTooltip("IDS_CUSTOMSTRINGCONCATFUNCTOID_TOOLTIP");  
            SetDescription("IDS_CUSTOMSTRINGCONCATFUNCTOID_DESCRIPTION");  
            SetBitmap("IDB_CUSTOMSTRINGCONCATFUNCTOID_BITMAP");  
  
            // Put this string handling function under the String   
            // Functoid tab in the Visual Studio toolbox for functoids  
            this.Category = FunctoidCategory.String;  
  
            // 2 required parameters, no optional parameters  
            this.SetMinParams(2);  
            this.SetMaxParams(2);  
  
            // Functoid accepts two inputs  
            AddInputConnectionType(ConnectionType.AllExceptRecord);  
            AddInputConnectionType(ConnectionType.AllExceptRecord);  
  
            // Set the output connection type  
            this.OutputConnectionType = ConnectionType.AllExceptRecord;  
  
            // Set the function name that needs to be called  
            // when this functoid is invoked.  The resulting assembly  
            // must be present in the Global Assembly Cache  
            // to ensure its availability.  
            SetExternalFunctionName(GetType().Assembly.FullName, "Microsoft.Samples.BizTalk.CustomFunctoid.CustomStringConcatFunctoid", "ConCatStrings");  
        }  
  
        // This function is executed by BizTalk to do the concatenation  
        public string ConCatStrings(string val1, string val2)  
        {  
            return val2 + val1;  
        }  
    }  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="f84f3-108">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f84f3-108">See Also</span></span>  
 <span data-ttu-id="f84f3-109">[Utilisation de BaseFunctoid](../core/using-basefunctoid.md) </span><span class="sxs-lookup"><span data-stu-id="f84f3-109">[Using BaseFunctoid](../core/using-basefunctoid.md) </span></span>  
 <span data-ttu-id="f84f3-110">[Développement d’un fonctoid Inline personnalisé](../core/developing-a-custom-inline-functoid.md) </span><span class="sxs-lookup"><span data-stu-id="f84f3-110">[Developing a Custom Inline Functoid](../core/developing-a-custom-inline-functoid.md) </span></span>  
 <span data-ttu-id="f84f3-111">[Développement d’un fonctoid cumulé personnalisé](../core/developing-a-custom-cumulative-functoid.md) </span><span class="sxs-lookup"><span data-stu-id="f84f3-111">[Developing a Custom Cumulative Functoid](../core/developing-a-custom-cumulative-functoid.md) </span></span>  
 [<span data-ttu-id="f84f3-112">Fonctoid personnalisé (exemple BizTalk Server)</span><span class="sxs-lookup"><span data-stu-id="f84f3-112">Custom Functoid (BizTalk Server Sample)</span></span>](../core/custom-functoid-biztalk-server-sample.md)