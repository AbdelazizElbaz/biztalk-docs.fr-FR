---
title: "Déploiement et démarrage d’une nouvelle Version d’une Orchestration par programme | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f90025ec-3641-49ef-8918-88238d6ad420
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 26887b70a09d4a7af8d41a4385dffda20e964690
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="deploying-and-starting-a-new-version-of-an-orchestration-programmatically"></a><span data-ttu-id="92cc4-102">Déploiement et démarrage d'une nouvelle version d'une orchestration par programme</span><span class="sxs-lookup"><span data-stu-id="92cc4-102">Deploying and Starting a New Version of an Orchestration Programmatically</span></span>
<span data-ttu-id="92cc4-103">Le code de cette rubrique illustre comment déployer et démarrer rapidement une nouvelle version de l’orchestration.</span><span class="sxs-lookup"><span data-stu-id="92cc4-103">The code in this topic illustrates how to quickly deploy and start a new version of the orchestration.</span></span> <span data-ttu-id="92cc4-104">Les opérations manuelles pouvant durer quelques secondes, désinscrire une orchestration puis en démarrer une nouvelle version peut provoquer la suspension ou la duplication des messages.</span><span class="sxs-lookup"><span data-stu-id="92cc4-104">Because manual operations can take a few seconds to perform, manually unenlisting an orchestration and then starting a new version of it can result in suspended or duplicate messages.</span></span> <span data-ttu-id="92cc4-105">La méthode par programme illustrée dans cette rubrique vous permet d’effectuer ces opérations beaucoup plus rapidement –  ce qui réduit les risques de suspension et de duplication de messages - et en une seule transaction, de sorte que si une opération échoue, toutes les orchestrations restent dans le même état qu'au démarrage.</span><span class="sxs-lookup"><span data-stu-id="92cc4-105">The programmatic method illustrated in this topic allows you to perform these operations much more quickly – reducing the likelihood of suspended and duplicate messages – and as a single transaction, so that if one operation fails, both orchestrations are left in the same state as they were at the beginning.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="92cc4-106">Dans de rares cas, lorsque l’orchestration que vous mettez à jour avec une nouvelle version fonctionne sous une charge élevée, certains messages peuvent être suspendus même lorsque vous désinscrivez et inscrivez les orchestrations par programme.</span><span class="sxs-lookup"><span data-stu-id="92cc4-106">In rare cases, when the orchestration you are updating with a new version is operating under high load, some messages can become suspended even when you unenlist and enlist the orchestrations programmatically.</span></span>  <span data-ttu-id="92cc4-107">Nous recommandons qu’après avoir effectué ces opérations, vous vérifiez votre file d’attente de messages suspendus et reprenez tous les messages suspendus.</span><span class="sxs-lookup"><span data-stu-id="92cc4-107">We recommend that after performing these operations, you check your suspended message queue and resume any suspended messages.</span></span>  
  
 <span data-ttu-id="92cc4-108">L’exemple de code suivant illustre comment utiliser les API de modèles objet de l'explorateur pour désinscrire une orchestration existante et démarrer la nouvelle version de l'orchestration.</span><span class="sxs-lookup"><span data-stu-id="92cc4-108">The following code sample illustrates how to use the Explorer OM API to unenlist an existing orchestration and start the new version of the orchestration.</span></span>  
  
```  
using System;  
using Microsoft.BizTalk.ExplorerOM;  
#endregion  
namespace OrchestrationBinding  
{  
class OrchestrationBinding  
{  
static void Main(string[] args)  
{  
            UpdateOrchestration();  
}  
        static public void UpdateOrchestration()  
        {  
            // Create the root object and set the connection string  
            BtsCatalogExplorer catalog = new BtsCatalogExplorer();  
            catalog.ConnectionString = "SERVER=.;DATABASE=BizTalkMgmtDb;Integrated Security=SSPI";  
            string orchestrationAssemblyV1 = "HelloWorld, Version=1.0.0.0, Culture=neutral, PublicKeyToken=99561c477e487f14";  
            string orchestrationAssemblyV2 = "HelloWorld, Version=2.0.0.0, Culture=neutral, PublicKeyToken=99561c477e487f14";  
            string orchestrationName = "Microsoft.Samples.BizTalk.HelloWorld.HelloSchedule";  
            try  
            {  
                BtsAssembly assemblyV1 = FindAssemblyByFullName(catalog.Assemblies, orchestrationAssemblyV1);  
                BtsAssembly assemblyV2 = FindAssemblyByFullName(catalog.Assemblies, orchestrationAssemblyV2);  
                BtsOrchestration orchestrationV1 = assemblyV1.Orchestrations[orchestrationName];  
                BtsOrchestration orchestrationV2 = assemblyV2.Orchestrations[orchestrationName];  
                orchestrationV1.Status = OrchestrationStatus.Unenlisted;  
                orchestrationV2.Status = OrchestrationStatus.Started;  
                // Commit the accumulated changes transactionally  
                catalog.SaveChanges();  
            }  
            catch (Exception e)  
            {  
                catalog.DiscardChanges();  
                throw;  
            }  
        }  
        static BtsAssembly FindAssemblyByFullName(BtsAssemblyCollection assemblies, string fullName)  
        {  
            foreach (BtsAssembly assembly in assemblies)  
            {  
                if (assembly.DisplayName == fullName)  
                    return assembly;  
            }  
            return null;  
        }  
}  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="92cc4-109">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="92cc4-109">See Also</span></span>  
 <span data-ttu-id="92cc4-110">[Mise à jour des Applications BizTalk](../core/updating-biztalk-applications.md) </span><span class="sxs-lookup"><span data-stu-id="92cc4-110">[Updating BizTalk Applications](../core/updating-biztalk-applications.md) </span></span>  
 <span data-ttu-id="92cc4-111">[Comment inscrire une Orchestration](../core/how-to-enlist-an-orchestration.md) </span><span class="sxs-lookup"><span data-stu-id="92cc4-111">[How to Enlist an Orchestration](../core/how-to-enlist-an-orchestration.md) </span></span>  
 [<span data-ttu-id="92cc4-112">Comment désinscrire une Orchestration</span><span class="sxs-lookup"><span data-stu-id="92cc4-112">How to Unenlist an Orchestration</span></span>](../core/how-to-unenlist-an-orchestration.md)