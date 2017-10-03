---
title: "Comment faire pour diagnostiquer des problèmes avec l’adaptateur SOAP | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 16c93333-cb32-49bc-a1c4-9d726ab41850
caps.latest.revision: "13"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: db1d495eb301f93100a6ac9a4e50c8f1c57e5f5a
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-diagnose-problems-with-the-soap-adapter"></a><span data-ttu-id="09b46-102">Diagnostic des problèmes relatifs à l'adaptateur SOAP</span><span class="sxs-lookup"><span data-stu-id="09b46-102">How to Diagnose Problems with the SOAP Adapter</span></span>
<span data-ttu-id="09b46-103">Cette rubrique présente la procédure de diagnostic des problèmes relatifs à l'adaptateur SOAP.</span><span class="sxs-lookup"><span data-stu-id="09b46-103">This section contains steps that can be followed to help diagnose problems with the SOAP adapter.</span></span>  
  
### <a name="check-the-iis-log-and-httperr-log-of-the-iis-server-for-errors"></a><span data-ttu-id="09b46-104">Vérifiez le journal d’IIS et HTTPERR du serveur IIS pour les erreurs</span><span class="sxs-lookup"><span data-stu-id="09b46-104">Check the IIS log and HTTPERR log of the IIS Server for errors</span></span>  
  
-   <span data-ttu-id="09b46-105">Les fichiers journaux du serveur IIS source ou cible contiennent des informations qui peuvent s'avérer utiles pour la résolution de problèmes relatifs à l'adaptateur SOAP.</span><span class="sxs-lookup"><span data-stu-id="09b46-105">The source or target IIS server log files can contain information that is helpful for troubleshooting problems with the SOAP adapter.</span></span> <span data-ttu-id="09b46-106">Les fichiers journaux IIS d'un ordinateur [!INCLUDE[btsWinSvrNoVersion](../includes/btswinsvrnoversion-md.md)] se trouvent par défaut dans le répertoire suivant :</span><span class="sxs-lookup"><span data-stu-id="09b46-106">By default the IIS log files on a [!INCLUDE[btsWinSvrNoVersion](../includes/btswinsvrnoversion-md.md)] computer are located in the following directory:</span></span>  
  
     <span data-ttu-id="09b46-107">*%Windir%\\*system32\LogFiles\W3SVC1\\</span><span class="sxs-lookup"><span data-stu-id="09b46-107">*%WinDir%\\*system32\LogFiles\W3SVC1\\</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="09b46-108">*%Windir%* est un espace réservé pour l’emplacement du répertoire Windows sur le serveur IIS.</span><span class="sxs-lookup"><span data-stu-id="09b46-108">*%WinDir%* is a placeholder for the location of the Windows directory on the IIS server.</span></span>  
  
     <span data-ttu-id="09b46-109">Les fichiers journaux HTTPERR d'un ordinateur [!INCLUDE[btsWinSvrNoVersion](../includes/btswinsvrnoversion-md.md)] se trouvent par défaut dans le répertoire suivant :</span><span class="sxs-lookup"><span data-stu-id="09b46-109">By default the HTTPERR log files on a [!INCLUDE[btsWinSvrNoVersion](../includes/btswinsvrnoversion-md.md)] based computer are located in the following directory:</span></span>  
  
     <span data-ttu-id="09b46-110">*%Windir%\\*system32\LogFiles\HTTPERR\\</span><span class="sxs-lookup"><span data-stu-id="09b46-110">*%WinDir%\\*system32\LogFiles\HTTPERR\\</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="09b46-111">Le fichier journal HTTPERR est uniquement disponible sur [!INCLUDE[btsWinSvr2k8](../includes/btswinsvr2k8-md.md)] ordinateurs.</span><span class="sxs-lookup"><span data-stu-id="09b46-111">The HTTPERR log file is available only on [!INCLUDE[btsWinSvr2k8](../includes/btswinsvr2k8-md.md)] computers.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="09b46-112">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="09b46-112">See Also</span></span>  
 <span data-ttu-id="09b46-113">[Outils et utilitaires à utiliser pour la résolution des problèmes](../core/tools-and-utilities-to-use-for-troubleshooting.md) </span><span class="sxs-lookup"><span data-stu-id="09b46-113">[Tools and Utilities to Use for Troubleshooting](../core/tools-and-utilities-to-use-for-troubleshooting.md) </span></span>  
 [<span data-ttu-id="09b46-114">Dépannage de l’adaptateur SOAP</span><span class="sxs-lookup"><span data-stu-id="09b46-114">Troubleshooting the SOAP Adapter</span></span>](../core/troubleshooting-the-soap-adapter.md)