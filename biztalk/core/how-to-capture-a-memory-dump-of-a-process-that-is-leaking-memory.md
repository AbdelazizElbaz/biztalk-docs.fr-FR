---
title: "Comment capturer une image mémoire d’un processus qui est une fuite de mémoire | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 67404919-33a6-40ac-b1c4-09841db12fcf
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 5e1e57a3c4d3c035069c550cdc540de1c88e8880
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="how-to-capture-a-memory-dump-of-a-process-that-is-leaking-memory"></a><span data-ttu-id="13865-102">Capture de l'image mémoire d'un processus subissant des fuites de mémoire</span><span class="sxs-lookup"><span data-stu-id="13865-102">How to Capture a Memory Dump of a Process that is Leaking Memory</span></span>
<span data-ttu-id="13865-103">On considère que le processus BizTalk BTSNTSvc.exe subit une fuite de mémoire lorsqu'il ne parvient pas à libérer la mémoire dont il n'a plus besoin, ce qui entraîne avec le temps une réduction de la quantité de mémoire disponible.</span><span class="sxs-lookup"><span data-stu-id="13865-103">The BizTalk process BTSNTSvc.exe is defined as having a memory leak when it fails to release memory that it no longer needs, thereby reducing the amount of available memory over time.</span></span> <span data-ttu-id="13865-104">L’utilisation de la mémoire du processus peut être déterminée en consultant la valeur sous la **util** colonne de la **processus** onglet disponible dans **le Gestionnaire des tâches**.</span><span class="sxs-lookup"><span data-stu-id="13865-104">The memory usage of the process can be determined by viewing the value under the **Mem Usage** column of the **Processes** tab available in **Task Manager**.</span></span> <span data-ttu-id="13865-105">Si le processus continue à consommer de la mémoire dans le temps sans la libérer, les performances globales du système en seront affectées.</span><span class="sxs-lookup"><span data-stu-id="13865-105">If the process continues to consume memory over time without releasing memory then overall system performance will be adversely impacted.</span></span>  
  
 <span data-ttu-id="13865-106">Cette rubrique contient les instructions permettant de capturer l'image mémoire d'un processus BizTalk suspecté de subir des fuites de mémoire, à l'aide d'une règle ou par une capture manuelle de l'image mémoire.</span><span class="sxs-lookup"><span data-stu-id="13865-106">This topic contains instructions for capturing a memory dump of a BizTalk process that is suspected of leaking memory by using a Rule or by manually capturing the memory dump.</span></span> <span data-ttu-id="13865-107">Utilisez la méthode de capture manuelle de l'image mémoire si l'occurrence de la fuite de mémoire n'est pas prévisible.</span><span class="sxs-lookup"><span data-stu-id="13865-107">Use the manual method of capturing a memory dump if the occurrence of the memory leak is not predictable.</span></span>  
  
### <a name="to-capture-a-memory-dump-of-a-process-that-is-leaking-memory-by-using-a-rule"></a><span data-ttu-id="13865-108">Pour capturer l'image mémoire d'un processus subissant des fuites de mémoire à l'aide d'une règle</span><span class="sxs-lookup"><span data-stu-id="13865-108">To capture a memory dump of a process that is leaking memory by using a rule</span></span>  
  
1.  <span data-ttu-id="13865-109">Lancer l’outil de diagnostic de débogage à partir de **Démarrer**, **tous les programmes**, **diagnostic IIS**, **outils de diagnostic de débogage**, **Déboguer l’outil Diagnostics 1.0**.</span><span class="sxs-lookup"><span data-stu-id="13865-109">Launch the Debug Diagnostics tool from **Start**, **All Programs**, **IIS Diagnostics**, **Debug Diagnostics Tools**, **Debug Diagnostics Tool 1.0**.</span></span>  
  
2.  <span data-ttu-id="13865-110">Si le **sélectionner le Type de règle** boîte de dialogue de l’Assistant Ajout de règle n’est pas affichée, cliquez sur le **outils** menu, sélectionnez **les Actions de règle**, puis cliquez sur **ajouter une règle**pour afficher l’Assistant Ajout de règle.</span><span class="sxs-lookup"><span data-stu-id="13865-110">If the **Select Rule Type** dialog of the Add Rule Wizard is not displayed, click the **Tools** menu, select **Rule Actions**, and click **Add Rule** to display the Add Rule Wizard.</span></span>  
  
3.  <span data-ttu-id="13865-111">Sélectionnez le **fuite de mémoire et de mémoire** option dans le **sélectionner le Type de règle** boîte de dialogue et cliquez sur **suivant**.</span><span class="sxs-lookup"><span data-stu-id="13865-111">Select the **Memory and Handle Leak** option in the **Select Rule Type** dialog and click **Next**.</span></span>  
  
4.  <span data-ttu-id="13865-112">Sélectionnez le processus BTSNTSvc.exe suspecté de subir des fuites de mémoire et cliquez sur **suivant**.</span><span class="sxs-lookup"><span data-stu-id="13865-112">Select the BTSNTSvc.exe process that is suspected of leaking memory and click **Next**.</span></span>  
  
5.  <span data-ttu-id="13865-113">Dans le **configurer la durée du suivi** boîte de dialogue comme suit :</span><span class="sxs-lookup"><span data-stu-id="13865-113">In the **Configure Tracking Duration** dialog follow these steps:</span></span>  
  
    1.  <span data-ttu-id="13865-114">Si la croissance de mémoire se produit immédiatement, cochez l’option **démarrer le suivi immédiatement lorsque la règle est activée**.</span><span class="sxs-lookup"><span data-stu-id="13865-114">If the observed process memory growth occurs immediately, check the option to **Start memory tracking immediately when rule is activated**.</span></span> <span data-ttu-id="13865-115">Si la croissance de mémoire ne se produit pas immédiatement, spécifiez un nombre approprié de minutes dans le **mise en route** démarre après laquelle le suivi de zone de texte.</span><span class="sxs-lookup"><span data-stu-id="13865-115">If the observed process memory growth doesn't occur immediately, specify an appropriate number of minutes in the **Warm-up time** text box after which memory tracking will start.</span></span>  
  
        > [!NOTE]
        >  <span data-ttu-id="13865-116">Le croissance de la mémoire pour le processus peut ne pas être immédiatement observable si la fuite de mémoire n'intervient qu'avec le chargement d'un composant particulier dans la mémoire, par exemple si une orchestration BizTalk fait référence à un composant externe.</span><span class="sxs-lookup"><span data-stu-id="13865-116">The observed process memory growth may not occur immediately if the memory leak is caused when loading a particular component into memory, for example when a BizTalk orchestration references an external component.</span></span>  
  
    2.  <span data-ttu-id="13865-117">Spécifiez un nombre approprié de minutes dans le **le suivi des** zone de texte après laquelle le suivi sera arrêté.</span><span class="sxs-lookup"><span data-stu-id="13865-117">Specify an appropriate number of minutes in the **Tracking time** text box after which memory tracking will stop.</span></span> <span data-ttu-id="13865-118">Ce nombre de minutes doit être suffisamment élevé pour permettre la reproduction de la fuite de mémoire.</span><span class="sxs-lookup"><span data-stu-id="13865-118">This should be a number of minutes long enough to reproduce the memory leak.</span></span> <span data-ttu-id="13865-119">Une image mémoire du processus sera capturée à l'issue de ce délai.</span><span class="sxs-lookup"><span data-stu-id="13865-119">A memory dump of the process will be captured after this time period has elapsed.</span></span>  
  
    3.  <span data-ttu-id="13865-120">Cochez l’option **créer automatiquement un incident de règle pour obtenir une image utilisateur sur la sortie inattendue du processus**.</span><span class="sxs-lookup"><span data-stu-id="13865-120">Check the option to **Auto-create a crash rule to get userdump on unexpected process exit**.</span></span>  
  
    4.  <span data-ttu-id="13865-121">Cliquez sur **Suivant**.</span><span class="sxs-lookup"><span data-stu-id="13865-121">Click **Next**.</span></span>  
  
6.  <span data-ttu-id="13865-122">Dans le **sélectionnez Vider emplacement et nom de la règle** boîte de dialogue cliquez **suivant** pour accepter les valeurs par défaut.</span><span class="sxs-lookup"><span data-stu-id="13865-122">In the **Select Dump Location And Rule Name** dialog click **Next** to accept the default values.</span></span>  
  
7.  <span data-ttu-id="13865-123">Dans le **règle terminée** boîte de dialogue cliquez **Terminer** pour accepter la valeur par défaut de **activer la règle maintenant**.</span><span class="sxs-lookup"><span data-stu-id="13865-123">In the **Rule Completed** dialog click **Finish** to accept the default value of **Activate the rule now**.</span></span>  
  
8.  <span data-ttu-id="13865-124">Par défaut, une image mémoire du processus sera enregistrée à la Files\IIS Resources\DebugDiag\Logs\\<*nom de la règle d’arrêt* \> répertoire de l’ordinateur local après les intervalles de temps spécifié dans le **configurer la durée du suivi** boîte de dialogue s’est écoulé.</span><span class="sxs-lookup"><span data-stu-id="13865-124">By default, a memory dump of the process will be saved to the \Program Files\IIS Resources\DebugDiag\Logs\\<*name of crash rule*\> directory of the local computer after the time intervals specified in the **Configure Tracking Duration** dialog has elapsed.</span></span>  
  
### <a name="to-manually-capture-a-memory-dump-of-a-process-that-is-leaking-memory"></a><span data-ttu-id="13865-125">Pour capturer manuellement l'image mémoire d'un processus subissant des fuites de mémoire</span><span class="sxs-lookup"><span data-stu-id="13865-125">To manually capture a memory dump of a process that is leaking memory</span></span>  
  
1.  <span data-ttu-id="13865-126">Lancer l’outil de diagnostic de débogage à partir de **Démarrer**, **tous les programmes**, **diagnostic IIS**, **outils de diagnostic de débogage**, **Déboguer l’outil Diagnostics 1.0**.</span><span class="sxs-lookup"><span data-stu-id="13865-126">Launch the Debug Diagnostics tool from **Start**, **All Programs**, **IIS Diagnostics**, **Debug Diagnostics Tools**, **Debug Diagnostics Tool 1.0**.</span></span>  
  
2.  <span data-ttu-id="13865-127">Si le **sélectionner le Type de règle** boîte de dialogue de l’Assistant Ajout de règle s’affiche, cliquez sur **Annuler**.</span><span class="sxs-lookup"><span data-stu-id="13865-127">If the **Select Rule Type** dialog of the Add Rule Wizard is displayed, click **Cancel**.</span></span>  
  
3.  <span data-ttu-id="13865-128">Cliquez pour sélectionner le **processus** onglet de l’outil de Diagnostic de débogage.</span><span class="sxs-lookup"><span data-stu-id="13865-128">Click to select the **Processes** tab of the Debug Diagnostic Tool.</span></span>  
  
4.  <span data-ttu-id="13865-129">Cliquez sur le processus BTSNTSvc.exe suspecté de subir des fuites de mémoire et cliquez sur **surveiller les fuites**.</span><span class="sxs-lookup"><span data-stu-id="13865-129">Right-click the BTSNTSvc.exe process that is suspected of leaking memory and click **Monitor For Leaks**.</span></span>  
  
5.  <span data-ttu-id="13865-130">Surveiller l’utilisation de la mémoire du processus dans **le Gestionnaire des tâches** et lors de l’utilisation de la mémoire du processus est proche de 60-80 % de la mémoire disponible sur l’ordinateur BizTalk ; capturer manuellement une image mémoire du processus en cliquant sur le processus et en sélectionnant l’option à **créer une image utilisateur complète**.</span><span class="sxs-lookup"><span data-stu-id="13865-130">Monitor the memory usage of the process in **Task Manager** and when the memory usage of the process approaches 60-80% of the memory available on the BizTalk computer; manually capture a memory dump of the process by right-clicking the process and selecting the option to **Create Full Userdump**.</span></span>  
  
6.  <span data-ttu-id="13865-131">Par défaut, une image mémoire du processus sera enregistré dans le répertoire \Program Files\IIS Resources\DebugDiag\Logs\Misc\ de l'ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="13865-131">By default, a memory dump of the process will be saved to the \Program Files\IIS Resources\DebugDiag\Logs\Misc\ directory of the local computer.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="13865-132">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="13865-132">See Also</span></span>  
 [<span data-ttu-id="13865-133">L’utilisation de diagnostic de débogage pour analyser un vidage de mémoire</span><span class="sxs-lookup"><span data-stu-id="13865-133">How to Use Debug Diagnostics to Analyze a Memory Dump</span></span>](../core/how-to-use-debug-diagnostics-to-analyze-a-memory-dump.md)