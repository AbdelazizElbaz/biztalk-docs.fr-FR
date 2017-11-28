---
title: "Comment faire pour diagnostiquer des problèmes avec l’adaptateur FTP | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 499d23d3-b705-4527-9929-147be157e6b3
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 4e66be2e498449b1cdcc70e05c6195ccd8e4395d
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-diagnose-problems-with-the-ftp-adapter"></a><span data-ttu-id="e1083-102">Diagnostic des problèmes relatifs à l'adaptateur FTP</span><span class="sxs-lookup"><span data-stu-id="e1083-102">How to Diagnose Problems with the FTP Adapter</span></span>
<span data-ttu-id="e1083-103">Cette rubrique présente la procédure de diagnostic des problèmes relatifs à l'adaptateur FTP.</span><span class="sxs-lookup"><span data-stu-id="e1083-103">This section contains steps that can be followed to help diagnose problems with the FTP adapter.</span></span>  
  
### <a name="check-the-ftp-log-files-on-the-ftp-server-for-errors"></a><span data-ttu-id="e1083-104">Recherche des erreurs dans les fichiers journaux FTP du serveur FTP</span><span class="sxs-lookup"><span data-stu-id="e1083-104">Check the FTP log files on the FTP Server for errors</span></span>  
  
-   <span data-ttu-id="e1083-105">Les fichiers journaux du serveur FTP source ou cible contiennent des informations qui peuvent s'avérer utiles pour la résolution de problèmes relatifs à l'adaptateur FTP.</span><span class="sxs-lookup"><span data-stu-id="e1083-105">The source or target FTP server log files can contain information that is helpful for troubleshooting problems with the FTP adapter.</span></span> <span data-ttu-id="e1083-106">Les fichiers journaux FTP d'un ordinateur Windows Server ou Windows XP se trouvent par défaut dans le répertoire suivant :</span><span class="sxs-lookup"><span data-stu-id="e1083-106">By default the FTP log files on a Windows Server or Windows XP computer are located in the following directory:</span></span>  
  
     <span data-ttu-id="e1083-107">*%Windir%\\*system32\LogFiles\MSFTPSVC1\\</span><span class="sxs-lookup"><span data-stu-id="e1083-107">*%WinDir%\\*system32\LogFiles\MSFTPSVC1\\</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="e1083-108">*%Windir%* est un espace réservé pour l’emplacement du répertoire Windows sur le serveur FTP.</span><span class="sxs-lookup"><span data-stu-id="e1083-108">*%WinDir%* is a placeholder for the location of the Windows directory on the FTP server.</span></span>  
  
### <a name="enable-logging-for-the-ftp-receive-location-or-send-port"></a><span data-ttu-id="e1083-109">Activer l'enregistrement dans des fichiers journaux pour l'emplacement de réception ou le port d'envoi FTP</span><span class="sxs-lookup"><span data-stu-id="e1083-109">Enable logging for the FTP Receive location or Send Port</span></span>  
  
-   <span data-ttu-id="e1083-110">Configurer le FTP emplacement de réception ou port d’envoi avec un **journal** dossier.</span><span class="sxs-lookup"><span data-stu-id="e1083-110">Configure the FTP receive location or send port with a **Log** folder.</span></span> <span data-ttu-id="e1083-111">L'adaptateur FTP y consignera des informations de journalisation détaillées.</span><span class="sxs-lookup"><span data-stu-id="e1083-111">The FTP adapter will save detailed logging information to this folder.</span></span> <span data-ttu-id="e1083-112">Le **journal** dossier option est disponible sur le **propriétés du Transport FTP** boîte de dialogue lors de la configuration d’un port de réception emplacement ou d’envoi avec le type de transport FTP.</span><span class="sxs-lookup"><span data-stu-id="e1083-112">The **Log** folder option is available on the **FTP Transport Properties** dialog box when configuring a receive location or send port with the FTP transport type.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e1083-113">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="e1083-113">See Also</span></span>  
 [<span data-ttu-id="e1083-114">Outils et utilitaires à utiliser pour la résolution des problèmes</span><span class="sxs-lookup"><span data-stu-id="e1083-114">Tools and Utilities to Use for Troubleshooting</span></span>](../core/tools-and-utilities-to-use-for-troubleshooting.md)