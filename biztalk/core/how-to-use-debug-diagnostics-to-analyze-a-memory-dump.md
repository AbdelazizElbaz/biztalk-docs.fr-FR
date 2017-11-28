---
title: "L’utilisation de diagnostic de débogage pour analyser une image mémoire | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 986a91a7-feab-4014-bbd5-e8b966b8b841
caps.latest.revision: "5"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: ccc0faf72c9123ab7a501af8520f273e8c528b8d
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-use-debug-diagnostics-to-analyze-a-memory-dump"></a><span data-ttu-id="2bb60-102">Analyse d'une image mémoire à l'aide de l'outil de diagnostic de débogage</span><span class="sxs-lookup"><span data-stu-id="2bb60-102">How to Use Debug Diagnostics to Analyze a Memory Dump</span></span>
<span data-ttu-id="2bb60-103">Les tests de diagnostic IIS **outil** inclut une fonctionnalité qui peut fournir une analyse de base d’un fichier de vidage mémoire capturé.</span><span class="sxs-lookup"><span data-stu-id="2bb60-103">The IIS Diagnostics **Debug Diagnostics Tool** includes a feature that can provide a basic analysis of a captured memory dump file.</span></span> <span data-ttu-id="2bb60-104">Pour procéder à l'analyse d'un fichier d'image mémoire, procédez comme suit :</span><span class="sxs-lookup"><span data-stu-id="2bb60-104">To perform an analysis of a memory dump file follow these steps.</span></span>  
  
### <a name="to-analyze-the-dump-file"></a><span data-ttu-id="2bb60-105">Pour analyser un fichier d'image mémoire</span><span class="sxs-lookup"><span data-stu-id="2bb60-105">To analyze the dump file</span></span>  
  
1.  <span data-ttu-id="2bb60-106">Lancer l’outil de diagnostic de débogage à partir de **Démarrer**, **programmes**, **diagnostic IIS**, **outils de diagnostic de débogage**,  **L’outil Diagnostics 1.0 de débogage**.</span><span class="sxs-lookup"><span data-stu-id="2bb60-106">Launch the Debug Diagnostics tool from **Start**, **Programs**, **IIS Diagnostics**, **Debug Diagnostics Tools**, **Debug Diagnostics Tool 1.0**.</span></span>  
  
2.  <span data-ttu-id="2bb60-107">Cliquez sur le **analyse avancée** onglet.</span><span class="sxs-lookup"><span data-stu-id="2bb60-107">Click the **Advanced Analysis** tab.</span></span>  
  
3.  <span data-ttu-id="2bb60-108">Sous **Scripts d’analyse disponibles** sélectionnez **analyseurs d’incident/blocage** pour analyser un fichier de vidage sur incident/blocage ou sélectionnez **l’analyse de la sollicitation de la mémoire** pour analyser une mémoire image d’un processus suspecté de manquer de mémoire.</span><span class="sxs-lookup"><span data-stu-id="2bb60-108">Under **Available Analysis Scripts** click to select **Crash/Hang Analyzers** to analyze a crash/hang dump or click to select **Memory Pressure Analysis** to analyze a memory dump of a process suspected of leaking memory.</span></span>  
  
4.  <span data-ttu-id="2bb60-109">Cliquez sur le **ajouter des fichiers de données** bouton pour rechercher le fichier généré et cliquez sur le **ouvrir** pour ajouter le fichier de vidage à la liste des fichiers de données à analyser.</span><span class="sxs-lookup"><span data-stu-id="2bb60-109">Click the **Add Data Files** button to browse to the generated dump file and click the **Open** button to add the dump file to the possible list of data files to be analyzed.</span></span>  
  
5.  <span data-ttu-id="2bb60-110">Cliquez sur le fichier d'image mémoire que vous venez d'ajouter.</span><span class="sxs-lookup"><span data-stu-id="2bb60-110">Click to select the dump file that was added.</span></span>  
  
6.  <span data-ttu-id="2bb60-111">Cliquez sur le **démarrer l’analyse** bouton.</span><span class="sxs-lookup"><span data-stu-id="2bb60-111">Click the **Start Analysis** button.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="2bb60-112">L'analyseur tente de localiser et de télécharger les fichiers de symbole appropriés sur Internet s'ils ne sont pas installés sur l'ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="2bb60-112">The analyzer attempts to locate and download the appropriate symbol files from the internet if the symbol files are not installed on the local computer.</span></span> <span data-ttu-id="2bb60-113">Si le code personnalisé est en cours d’exécution dans le processus BTSNTSvc.exe, mettez à jour le **chemin d’accès de recherche de symbole de débogage** option disponible dans le **chemins de recherche et de dossier** onglet de la **Options & Paramètres** boîte de dialogue pour inclure les fichiers de symboles appropriés.</span><span class="sxs-lookup"><span data-stu-id="2bb60-113">If custom code is being executed in the BTSNTSvc.exe process, update the **Symbol Search Path For Debugging** option available in the **Folder And Search Paths** tab of the **Options & Settings** dialog to include the appropriate symbol files.</span></span> <span data-ttu-id="2bb60-114">Cliquez sur le **outils** menu et sélectionnez **les paramètres et Options** pour afficher les **Options et paramètres** boîte de dialogue.</span><span class="sxs-lookup"><span data-stu-id="2bb60-114">Click the **Tools** menu and select **Options And Settings** to display the **Options & Settings** dialog.</span></span>  
  
7.  <span data-ttu-id="2bb60-115">Une fois l'analyse terminée, un rapport est généré au format de fichier .mht et s'affiche dans Internet Explorer.</span><span class="sxs-lookup"><span data-stu-id="2bb60-115">Once the analysis is complete a report is generated in .mht file format and displayed in Internet Explorer.</span></span> <span data-ttu-id="2bb60-116">Par défaut, ce rapport est enregistré dans le répertoire \Program Files\IIS Resources\DebugDiag\Reports de l'ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="2bb60-116">By default this report is saved to the \Program Files\IIS Resources\DebugDiag\Reports directory of the local computer.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2bb60-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="2bb60-117">See Also</span></span>  
 [<span data-ttu-id="2bb60-118">Comment capturer une image mémoire d’un processus BizTalk</span><span class="sxs-lookup"><span data-stu-id="2bb60-118">How to Capture a Memory Dump of a BizTalk Process</span></span>](../core/how-to-capture-a-memory-dump-of-a-biztalk-process.md)