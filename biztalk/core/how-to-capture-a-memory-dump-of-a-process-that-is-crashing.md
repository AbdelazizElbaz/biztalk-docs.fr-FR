---
title: "Comment capturer une image mémoire d’un processus bloqué | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 5f436b72-2b6a-4519-acc3-e7ba978651fe
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: fda8dd26908b241a9897bb4f1b2ba697b55f6532
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-capture-a-memory-dump-of-a-process-that-is-crashing"></a><span data-ttu-id="0d08e-102">Capture de l'image mémoire d'un processus bloqué</span><span class="sxs-lookup"><span data-stu-id="0d08e-102">How to Capture a Memory Dump of a Process that is Crashing</span></span>
<span data-ttu-id="0d08e-103">Le processus BizTalk BTSNTSvc.exe est défini en tant que **bloqué** lorsque le processus est arrêté inopinément par Windows.</span><span class="sxs-lookup"><span data-stu-id="0d08e-103">The BizTalk process BTSNTSvc.exe is defined as **crashing** when the process is unexpectedly terminated by Windows.</span></span> <span data-ttu-id="0d08e-104">Un blocage est généralement le résultat d'une exception non gérée dans le processus, comme une violation d'accès ou un dépassement de capacité de pile.</span><span class="sxs-lookup"><span data-stu-id="0d08e-104">A crash is typically caused by an unhandled exception in the process such as an access violation or a stack overflow.</span></span> <span data-ttu-id="0d08e-105">Dans ces situations, les fenêtres par défaut du débogueur, récupération d’urgence. Watson (drwtsn32.exe) intercepte l’exception et met fin au processus.</span><span class="sxs-lookup"><span data-stu-id="0d08e-105">In these situations, the Windows default debugger, Dr. Watson (drwtsn32.exe) catches the exception and terminates the process.</span></span>  
  
 <span data-ttu-id="0d08e-106">Pour capturer l'image mémoire d'un processus bloqué, configurez l'outil de diagnostic de débogage de sorte qu'il intercepte l'exception non gérée en procédant comme suit :</span><span class="sxs-lookup"><span data-stu-id="0d08e-106">To capture a memory dump of a process that is crashing, configure the Debug Diagnostics tool to catch the unhandled exception by following these steps:</span></span>  
  
### <a name="to-configure-the-debug-diagnostics-tool-to-capture-a-crash-dump"></a><span data-ttu-id="0d08e-107">Pour configurer l'outil de diagnostic de débogage afin de capturer l'image d'un processus bloqué</span><span class="sxs-lookup"><span data-stu-id="0d08e-107">To configure the Debug Diagnostics tool to capture a crash dump</span></span>  
  
1.  <span data-ttu-id="0d08e-108">Lancer l’outil de diagnostic de débogage à partir de **Démarrer**, **tous les programmes**, **diagnostic IIS**, **outils de diagnostic de débogage**, **Déboguer l’outil Diagnostics 1.0**.</span><span class="sxs-lookup"><span data-stu-id="0d08e-108">Launch the Debug Diagnostics tool from **Start**, **All Programs**, **IIS Diagnostics**, **Debug Diagnostics Tools**, **Debug Diagnostics Tool 1.0**.</span></span>  
  
2.  <span data-ttu-id="0d08e-109">Si le **sélectionner le Type de règle** boîte de dialogue de l’Assistant Ajout de règle n’est pas affichée, cliquez sur le **outils** menu, sélectionnez **les Actions de règle**, puis cliquez sur **ajouter une règle**pour afficher l’Assistant Ajout de règle.</span><span class="sxs-lookup"><span data-stu-id="0d08e-109">If the **Select Rule Type** dialog of the Add Rule Wizard is not displayed, click the **Tools** menu, select **Rule Actions**, and click **Add Rule** to display the Add Rule Wizard.</span></span>  
  
3.  <span data-ttu-id="0d08e-110">Sélectionnez le **Crash** option dans le **sélectionner le Type de règle** boîte de dialogue et cliquez sur **suivant**.</span><span class="sxs-lookup"><span data-stu-id="0d08e-110">Select the **Crash** option in the **Select Rule Type** dialog and click **Next**.</span></span>  
  
4.  <span data-ttu-id="0d08e-111">Sélectionnez **un processus spécifique** dans les **sélectionner le Type de cible** boîte de dialogue et cliquez sur **suivant**.</span><span class="sxs-lookup"><span data-stu-id="0d08e-111">Select **A specific process** in the **Select Target Type** dialog and click **Next**.</span></span>  
  
5.  <span data-ttu-id="0d08e-112">Sélectionnez le processus BTSNTSvc.exe bloqué et cliquez sur **suivant**.</span><span class="sxs-lookup"><span data-stu-id="0d08e-112">Select the BTSNTSvc.exe process that is crashing and click **Next**.</span></span>  
  
6.  <span data-ttu-id="0d08e-113">Dans le **Configuration avancée** boîte de dialogue cliquez **suivant** pour accepter les valeurs par défaut.</span><span class="sxs-lookup"><span data-stu-id="0d08e-113">In the **Advanced Configuration** dialog click **Next** to accept the default values.</span></span>  
  
7.  <span data-ttu-id="0d08e-114">Dans le **sélectionnez Vider emplacement et nom de la règle** boîte de dialogue cliquez **suivant** pour accepter les valeurs par défaut.</span><span class="sxs-lookup"><span data-stu-id="0d08e-114">In the **Select Dump Location And Rule Name** dialog click **Next** to accept the default values.</span></span>  
  
8.  <span data-ttu-id="0d08e-115">Dans le **règle terminée** boîte de dialogue cliquez **Terminer** pour accepter la valeur par défaut de **activer la règle maintenant**.</span><span class="sxs-lookup"><span data-stu-id="0d08e-115">In the **Rule Completed** dialog click **Finish** to accept the default value of **Activate the rule now**.</span></span>  
  
9. <span data-ttu-id="0d08e-116">Par défaut, une image mémoire du processus sera enregistrée à la Files\IIS Resources\DebugDiag\Logs\\<*nom de règle de blocage*> répertoire de l’ordinateur local la prochaine fois qu’une non prise en charge une exception se produit dans le processus.</span><span class="sxs-lookup"><span data-stu-id="0d08e-116">By default, a memory dump of the process will be saved to the \Program Files\IIS Resources\DebugDiag\Logs\\<*name of crash rule*> directory of the local computer the next time that an unhandled exception occurs in the process.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0d08e-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="0d08e-117">See Also</span></span>  
 [<span data-ttu-id="0d08e-118">L’utilisation de diagnostic de débogage pour analyser un vidage de mémoire</span><span class="sxs-lookup"><span data-stu-id="0d08e-118">How to Use Debug Diagnostics to Analyze a Memory Dump</span></span>](../core/how-to-use-debug-diagnostics-to-analyze-a-memory-dump.md)