---
title: "Comment faire pour diagnostiquer des problèmes avec l’adaptateur HTTP | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 91f818dd-11fa-4ea4-b904-e8e00b3e49b4
caps.latest.revision: "13"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 545e095624c30b4611c74dcfbdead13d685164ab
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-diagnose-problems-with-the-http-adapter"></a><span data-ttu-id="3e388-102">Diagnostic des problèmes relatifs à l'adaptateur HTTP</span><span class="sxs-lookup"><span data-stu-id="3e388-102">How to Diagnose Problems with the HTTP Adapter</span></span>
<span data-ttu-id="3e388-103">Cette rubrique présente la procédure de diagnostic des problèmes relatifs à l'adaptateur HTTP.</span><span class="sxs-lookup"><span data-stu-id="3e388-103">This section contains steps that can be followed to help diagnose problems with the HTTP adapter.</span></span>  
  
### <a name="check-the-iis-and-httperr-log-files-of-the-iis-server-for-errors"></a><span data-ttu-id="3e388-104">Recherche des erreurs dans les fichiers journaux IIS et HTTPERR du serveur IIS</span><span class="sxs-lookup"><span data-stu-id="3e388-104">Check the IIS and HTTPERR log files of the IIS Server for errors</span></span>  
  
-   <span data-ttu-id="3e388-105">Les fichiers journaux du serveur IIS source ou cible contiennent des informations qui peuvent s'avérer utiles pour la résolution de problèmes relatifs à l'adaptateur HTTP.</span><span class="sxs-lookup"><span data-stu-id="3e388-105">The source or target IIS server log files can contain information that is helpful for troubleshooting problems with the HTTP adapter.</span></span> <span data-ttu-id="3e388-106">Ces fichiers journaux se trouvent par défaut dans le répertoire suivant (Windows Server) :</span><span class="sxs-lookup"><span data-stu-id="3e388-106">By default the IIS log files on a Windows Server are located in the following directory:</span></span>  
  
     <span data-ttu-id="3e388-107">*%Windir%\\*system32\LogFiles\W3SVC1\\</span><span class="sxs-lookup"><span data-stu-id="3e388-107">*%WinDir%\\*system32\LogFiles\W3SVC1\\</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="3e388-108">*%Windir%* est un espace réservé pour l’emplacement du répertoire Windows sur le serveur IIS.</span><span class="sxs-lookup"><span data-stu-id="3e388-108">*%WinDir%* is a placeholder for the location of the Windows directory on the IIS server.</span></span>  
  
     <span data-ttu-id="3e388-109">Les fichiers journaux HTTPERR d'un ordinateur [!INCLUDE[btsWinSvrNoVersion](../includes/btswinsvrnoversion-md.md)] se trouvent par défaut dans le répertoire suivant :</span><span class="sxs-lookup"><span data-stu-id="3e388-109">By default the HTTPERR log files on a [!INCLUDE[btsWinSvrNoVersion](../includes/btswinsvrnoversion-md.md)] based computer are located in the following directory:</span></span>  
  
     <span data-ttu-id="3e388-110">*%Windir%\\*system32\LogFiles\HTTPERR\\</span><span class="sxs-lookup"><span data-stu-id="3e388-110">*%WinDir%\\*system32\LogFiles\HTTPERR\\</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="3e388-111">Le fichier journal HTTPERR est uniquement disponible sur [!INCLUDE[btsWinSvr2k8](../includes/btswinsvr2k8-md.md)] ordinateurs.</span><span class="sxs-lookup"><span data-stu-id="3e388-111">The HTTPERR log file is available only on [!INCLUDE[btsWinSvr2k8](../includes/btswinsvr2k8-md.md)] computers.</span></span>  
  
### <a name="isolate-problems-with-the-http-send-adapter-by-posting-to-the-destination-url-with-a-client-that-uses-the-systemnethttpwebrequest-class"></a><span data-ttu-id="3e388-112">Isolez le problème relatif à l'adaptateur d'envoi HTTP en le publiant sur l'URL de destination à l'aide d'un client qui utilise la classe System.Net.HttpWebRequest.</span><span class="sxs-lookup"><span data-stu-id="3e388-112">Isolate problems with the HTTP send adapter by posting to the destination URL with a client that uses the System.Net.HttpWebRequest class</span></span>  
  
1.  <span data-ttu-id="3e388-113">Si l'adaptateur d'envoi HTTP génère des erreurs lors de la publication sur l'URL de destination, créez un client qui utilise les classes System.Net.HttpWebRequest et HttpWebResponse pour effectuer la publication sur l'URL de destination.</span><span class="sxs-lookup"><span data-stu-id="3e388-113">If the HTTP send adapter is generating errors when posting to the destination URL, create a client that uses the System.Net.HttpWebRequest and HttpWebResponse classes to post to the destination URL.</span></span> <span data-ttu-id="3e388-114">Cette méthode permet de déterminer si le problème est spécifique à l'adaptateur d'envoi HTTP ou s'il concerne la publication sur l'URL de destination en général.</span><span class="sxs-lookup"><span data-stu-id="3e388-114">This approach will help determine if the problem is specific to the HTTP send adapter or if there is a problem posting to the destination URL in general.</span></span>  
  
2.  <span data-ttu-id="3e388-115">Pour plus d’informations sur la création d’un client qui utilise les classes System.Net.HttpWebRequest et HttpWebResponse, consultez [comment utiliser les classes System.Net nouvelles pour créer un client HTTP](http://go.microsoft.com/fwlink/?LinkId=66987).</span><span class="sxs-lookup"><span data-stu-id="3e388-115">For more information about creating a client that uses the System.Net.HttpWebRequest and HttpWebResponse classes see [How to use the new System.Net classes to create an HTTP client](http://go.microsoft.com/fwlink/?LinkId=66987).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3e388-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="3e388-116">See Also</span></span>  
 <span data-ttu-id="3e388-117">[Outils et utilitaires à utiliser pour la résolution des problèmes](../core/tools-and-utilities-to-use-for-troubleshooting.md) </span><span class="sxs-lookup"><span data-stu-id="3e388-117">[Tools and Utilities to Use for Troubleshooting](../core/tools-and-utilities-to-use-for-troubleshooting.md) </span></span>  
 [<span data-ttu-id="3e388-118">Dépannage de l’adaptateur HTTP</span><span class="sxs-lookup"><span data-stu-id="3e388-118">Troubleshooting the HTTP Adapter</span></span>](../core/troubleshooting-the-http-adapter.md)