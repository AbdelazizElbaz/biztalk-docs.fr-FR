---
title: "Comment faire pour diagnostiquer des problèmes avec l’adaptateur File | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f06089a5-4747-4879-a796-157088868dba
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: f0481a3abdf497c093a87d7d74ea0356c7cad0d0
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-diagnose-problems-with-the-file-adapter"></a><span data-ttu-id="33179-102">Diagnostic des problèmes relatifs à l'adaptateur FILE</span><span class="sxs-lookup"><span data-stu-id="33179-102">How to Diagnose Problems with the File Adapter</span></span>
<span data-ttu-id="33179-103">Cette rubrique présente la procédure de diagnostic des problèmes relatifs à l'adaptateur FILE.</span><span class="sxs-lookup"><span data-stu-id="33179-103">This section contains steps that can be followed to help diagnose problems with the File adapter.</span></span>  
  
### <a name="run-the-filemon-utility-to-diagnose-errors-that-occur-using-the-file-receive-or-file-send-adapter"></a><span data-ttu-id="33179-104">Exécutez l'utilitaire FileMon pour diagnostiquer les erreurs qui se produisent lors de l'utilisation des adaptateurs de réception et d'envoi FILE.</span><span class="sxs-lookup"><span data-stu-id="33179-104">Run the FileMon Utility to diagnose errors that occur using the File Receive or File Send Adapter</span></span>  
  
1.  <span data-ttu-id="33179-105">Téléchargez l’utilitaire FileMon à partir de [www.sysinternals.com](http://go.microsoft.com/fwlink/?LinkId=66235).</span><span class="sxs-lookup"><span data-stu-id="33179-105">Download the FileMon utility from [www.sysinternals.com](http://go.microsoft.com/fwlink/?LinkId=66235).</span></span>  
  
2.  <span data-ttu-id="33179-106">Installez l'utilitaire Filemon sur le serveur qui héberge le dossier ou le partage en cours de lecture ou d'écriture par l'adaptateur FILE.</span><span class="sxs-lookup"><span data-stu-id="33179-106">Install the Filemon utility on the server that hosts the folder or share that is being read from or written to by the File Adapter.</span></span>  
  
3.  <span data-ttu-id="33179-107">Lancez l'utilitaire Filemon et appliquez un filtre pour surveiller uniquement les accès fichier effectués par l'instance BizTalk Host exécutant les gestionnaires d'adaptateur FILE (par exemple, BTSNTSvc.exe).</span><span class="sxs-lookup"><span data-stu-id="33179-107">Launch the Filemon utility and apply a filter to monitor only file accesses that are being made by the BizTalk Host instance that the file adapter handlers are running in (for example BTSNTSvc.exe).</span></span>  
  
4.  <span data-ttu-id="33179-108">Reproduisez le scénario à l'origine du problème.</span><span class="sxs-lookup"><span data-stu-id="33179-108">Run the scenario that caused the problem.</span></span>  
  
5.  <span data-ttu-id="33179-109">Désactivez la fonctionnalité de contrôle des fichiers de l'utilitaire Filemon, puis enregistrez le fichier journal généré sur le disque.</span><span class="sxs-lookup"><span data-stu-id="33179-109">Disable file monitoring in the Filemon utility, then save the generated log file to disk.</span></span>  
  
6.  <span data-ttu-id="33179-110">Vérifiez que le fichier journal généré ne contient pas d'erreurs.</span><span class="sxs-lookup"><span data-stu-id="33179-110">Review the generated log file for any errors.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="33179-111">Microsoft n'apporte aucune assistance relative à FileMon et ne garantit pas la pertinence de ce programme.</span><span class="sxs-lookup"><span data-stu-id="33179-111">FileMon is not supported by Microsoft, and Microsoft makes no guarantees about the suitability of this program.</span></span> <span data-ttu-id="33179-112">L'utilisation de ce programme relève de votre seule responsabilité.</span><span class="sxs-lookup"><span data-stu-id="33179-112">Use of this program is entirely at your own risk.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="33179-113">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="33179-113">See Also</span></span>  
 <span data-ttu-id="33179-114">[Outils et utilitaires à utiliser pour la résolution des problèmes](../core/tools-and-utilities-to-use-for-troubleshooting.md) </span><span class="sxs-lookup"><span data-stu-id="33179-114">[Tools and Utilities to Use for Troubleshooting](../core/tools-and-utilities-to-use-for-troubleshooting.md) </span></span>  
 [<span data-ttu-id="33179-115">Dépannage de l’adaptateur de fichier</span><span class="sxs-lookup"><span data-stu-id="33179-115">Troubleshooting the File Adapter</span></span>](../core/troubleshooting-the-file-adapter.md)