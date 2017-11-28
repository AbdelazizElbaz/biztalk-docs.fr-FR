---
title: "Comment faire pour diagnostiquer des problèmes avec l’adaptateur SMTP | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: eaf39fd8-b662-4b0c-b5e8-1af02cb4f79b
caps.latest.revision: "12"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 1a41a347534c07b522de5fc073933758870bf8a8
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-diagnose-problems-with-the-smtp-adapter"></a><span data-ttu-id="5900d-102">Diagnostic des problèmes relatifs à l'adaptateur SMTP</span><span class="sxs-lookup"><span data-stu-id="5900d-102">How to Diagnose Problems with the SMTP Adapter</span></span>
<span data-ttu-id="5900d-103">Cette rubrique présente la procédure de diagnostic des problèmes relatifs à l'adaptateur SMTP.</span><span class="sxs-lookup"><span data-stu-id="5900d-103">This section contains steps that can be followed to help diagnose problems with the SMTP adapter.</span></span>  
  
### <a name="check-the-smtp-log-files-of-the-smtp-server-for-errors"></a><span data-ttu-id="5900d-104">Recherche des erreurs dans les fichiers journaux SMTP du serveur SMTP</span><span class="sxs-lookup"><span data-stu-id="5900d-104">Check the SMTP log files of the SMTP Server for errors</span></span>  
  
-   <span data-ttu-id="5900d-105">Les fichiers journaux du serveur SMTP cible contiennent des informations qui peuvent s'avérer utiles pour résoudre les problèmes relatifs à l'adaptateur SMTP.</span><span class="sxs-lookup"><span data-stu-id="5900d-105">The target SMTP server log files can contain information that is helpful for troubleshooting problems with the SMTP adapter.</span></span> <span data-ttu-id="5900d-106">Les fichiers journaux SMTP sur [!INCLUDE[btsWinSvrNoVersion](../includes/btswinsvrnoversion-md.md)] se trouvent par défaut dans le répertoire suivant :</span><span class="sxs-lookup"><span data-stu-id="5900d-106">By default the SMTP log files on [!INCLUDE[btsWinSvrNoVersion](../includes/btswinsvrnoversion-md.md)] are located in the following directory:</span></span>  
  
     <span data-ttu-id="5900d-107">*%Windir%\\*system32\LogFiles\SMTPSVC1\\</span><span class="sxs-lookup"><span data-stu-id="5900d-107">*%WinDir%\\*system32\LogFiles\SMTPSVC1\\</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="5900d-108">*%Windir%* est un espace réservé pour l’emplacement du répertoire Windows sur le serveur SMTP.</span><span class="sxs-lookup"><span data-stu-id="5900d-108">*%WinDir%* is a placeholder for the location of the Windows directory on the SMTP server.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="5900d-109">La journalisation SMTP est désactivée par défaut sur [!INCLUDE[btsWinSvr2k8](../includes/btswinsvr2k8-md.md)].</span><span class="sxs-lookup"><span data-stu-id="5900d-109">SMTP logging is disabled by default on [!INCLUDE[btsWinSvr2k8](../includes/btswinsvr2k8-md.md)].</span></span> <span data-ttu-id="5900d-110">Pour plus d'informations sur l'activation de la journalisation pour SMTP, consultez la documentation Windows Server.</span><span class="sxs-lookup"><span data-stu-id="5900d-110">For information about enabling logging for SMTP, see the Windows Server documentation.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5900d-111">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="5900d-111">See Also</span></span>  
 <span data-ttu-id="5900d-112">[Outils et utilitaires à utiliser pour la résolution des problèmes](../core/tools-and-utilities-to-use-for-troubleshooting.md) </span><span class="sxs-lookup"><span data-stu-id="5900d-112">[Tools and Utilities to Use for Troubleshooting](../core/tools-and-utilities-to-use-for-troubleshooting.md) </span></span>  
 [<span data-ttu-id="5900d-113">Dépannage de l’adaptateur SMTP</span><span class="sxs-lookup"><span data-stu-id="5900d-113">Troubleshooting the SMTP Adapter</span></span>](../core/troubleshooting-the-smtp-adapter.md)