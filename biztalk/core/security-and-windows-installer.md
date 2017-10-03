---
title: "Sécurité et le programme d’installation Windows | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- security, Windows installer
- Windows installer
ms.assetid: efa68c3e-2006-4665-bd41-07defaf4e2e2
caps.latest.revision: "12"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 4418994a4b5ff705d1faef751ac8c96ba86f9dc7
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="security-and-windows-installer"></a><span data-ttu-id="76dc9-102">Sécurité et Windows Installer</span><span class="sxs-lookup"><span data-stu-id="76dc9-102">Security and Windows Installer</span></span>
<span data-ttu-id="76dc9-103">Windows Installer est un outil puissant permettant d'installer et de mettre à jour des applications BizTalk.</span><span class="sxs-lookup"><span data-stu-id="76dc9-103">Windows Installer is a powerful tool for installing and updating BizTalk applications.</span></span> <span data-ttu-id="76dc9-104">Lorsque vous l'utilisez, vous devez connaître les problèmes de sécurité posés par certains créateurs de fichiers Windows Installer (.msi) malveillants afin de savoir les éviter.</span><span class="sxs-lookup"><span data-stu-id="76dc9-104">When using Windows Installer, you should be aware of the security issues that can be created by malicious Windows Installer (.msi) file creators and take steps to prevent them.</span></span>  
  
 <span data-ttu-id="76dc9-105">Ce sont les administrateurs qui exécutent généralement les fichiers .msi. Par conséquent, les processus exécutés au cours de l'installation ou de la mise à jour d'une application sont associés à des privilèges très élevés.</span><span class="sxs-lookup"><span data-stu-id="76dc9-105">Administrators typically run .msi files, and therefore the processes that run during application installation or update have very high privileges.</span></span> <span data-ttu-id="76dc9-106">Un créateur de fichiers .msi malveillant peut donc exploiter ce fait de plusieurs façons et notamment :</span><span class="sxs-lookup"><span data-stu-id="76dc9-106">A malicious .msi file creator could exploit this fact in a number of ways, including the following:</span></span>  
  
-   <span data-ttu-id="76dc9-107">Exécuter des fichiers de script apportant des changements non souhaités à votre système ou vos fichiers.</span><span class="sxs-lookup"><span data-stu-id="76dc9-107">Running script files that make undesirable changes to your system or files.</span></span>  
  
-   <span data-ttu-id="76dc9-108">Écraser le catalogue COM.</span><span class="sxs-lookup"><span data-stu-id="76dc9-108">Overwriting the COM catalog.</span></span>  
  
-   <span data-ttu-id="76dc9-109">Écraser les valeurs du registre.</span><span class="sxs-lookup"><span data-stu-id="76dc9-109">Overwriting registry values.</span></span> <span data-ttu-id="76dc9-110">Ces modifications ne peuvent pas être restaurées.</span><span class="sxs-lookup"><span data-stu-id="76dc9-110">These changes cannot be rolled back.</span></span>  
  
-   <span data-ttu-id="76dc9-111">Inonder le système de fichiers.</span><span class="sxs-lookup"><span data-stu-id="76dc9-111">Flooding the file system.</span></span>  
  
 <span data-ttu-id="76dc9-112">Lorsque vous manipulez des fichiers .msi, vous devez, au minimum, prendre les précautions suivantes :</span><span class="sxs-lookup"><span data-stu-id="76dc9-112">When dealing with .msi files, you should take the following precautions at a minimum:</span></span>  
  
-   <span data-ttu-id="76dc9-113">Installer uniquement des fichiers .msi approuvés.</span><span class="sxs-lookup"><span data-stu-id="76dc9-113">Install only .msi files that you completely trust.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="76dc9-114">Il est conseillé aux personnes chargées de générer des fichiers .msi de prendre des mesures supplémentaires pour signer les fichiers .msi afin que les utilisateurs puissent vérifier que leur source est approuvée.</span><span class="sxs-lookup"><span data-stu-id="76dc9-114">As a best practice, individuals who are responsible for generating .msi files should take additional steps to sign the .msi files so that users can verify that the source of the file is trusted.</span></span>  
  
-   <span data-ttu-id="76dc9-115">Tester minutieusement les fichiers .msi avant de les utiliser dans un environnement de production.</span><span class="sxs-lookup"><span data-stu-id="76dc9-115">Thoroughly test your .msi files before using them in a production environment.</span></span>  
  
-   <span data-ttu-id="76dc9-116">Stocker les fichiers .msi dans des dossiers protégés, sécurisés par les listes de contrôle d'accès discrétionnaires (DACL) appropriées.</span><span class="sxs-lookup"><span data-stu-id="76dc9-116">Store the .msi files in protected folders that are secured with appropriate discretionary access control lists (DACLs).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="76dc9-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="76dc9-117">See Also</span></span>  
 [<span data-ttu-id="76dc9-118">Considérations de sécurité pour le déploiement d’Application</span><span class="sxs-lookup"><span data-stu-id="76dc9-118">Security Considerations for Application Deployment</span></span>](../core/security-considerations-for-application-deployment.md)