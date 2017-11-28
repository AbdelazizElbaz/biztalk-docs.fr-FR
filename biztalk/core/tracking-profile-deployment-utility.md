---
title: "Utilitaire de déploiement de profil de suivi | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1d631b7c-a40f-4cee-88a4-3d932ab7fde0
caps.latest.revision: "12"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 3c4d261069b83741413e255a3f8bacd6dd9260d2
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="tracking-profile-deployment-utility"></a><span data-ttu-id="a89f0-102">Utilitaire de déploiement de profil de suivi</span><span class="sxs-lookup"><span data-stu-id="a89f0-102">Tracking Profile Deployment Utility</span></span>
<span data-ttu-id="a89f0-103">Les développeurs utilisent l'utilitaire bttdeploy pour appliquer des modèles de suivi à l'infrastructure BAM et les supprimer.</span><span class="sxs-lookup"><span data-stu-id="a89f0-103">Developers use the bttdeploy utility to apply tracking profiles to and remove them from the BAM infrastructure.</span></span> <span data-ttu-id="a89f0-104">En pratique, l'utilisation de l'utilitaire bttdeploy revient à cliquer sur l'option de menu Appliquer le modèle de suivi de l'Éditeur de modèle de suivi (TPE).</span><span class="sxs-lookup"><span data-stu-id="a89f0-104">Using the bttdeploy utility is functionally equivalent to clicking the Apply Tracking Profile menu option in the Tracking Profile Editor (TPE).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="a89f0-105">Sur les systèmes qui prennent en charge le contrôle de compte d'utilisateur, vous devrez peut-être exécuter l'outil avec des privilèges d'administrateur.</span><span class="sxs-lookup"><span data-stu-id="a89f0-105">On a system that supports User Account Control (UAC), you may need to run the tool with Administrative privileges.</span></span>  
  
 <span data-ttu-id="a89f0-106">**Utilisation**</span><span class="sxs-lookup"><span data-stu-id="a89f0-106">**Usage**</span></span>  
  
 <span data-ttu-id="a89f0-107">**nom de fichier BttDeploy.exe [options]**</span><span class="sxs-lookup"><span data-stu-id="a89f0-107">**bttdeploy.exe [options] file name**</span></span>  
  
|<span data-ttu-id="a89f0-108">Option</span><span class="sxs-lookup"><span data-stu-id="a89f0-108">Option</span></span>|<span data-ttu-id="a89f0-109"> Description</span><span class="sxs-lookup"><span data-stu-id="a89f0-109">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="a89f0-110">/h ou /?</span><span class="sxs-lookup"><span data-stu-id="a89f0-110">/h or /?</span></span>|<span data-ttu-id="a89f0-111">Facultatif : Affiche la syntaxe pour bttdeploy.</span><span class="sxs-lookup"><span data-stu-id="a89f0-111">Optional: Displays the syntax summary for bttdeploy.</span></span>|  
|<span data-ttu-id="a89f0-112">/mgdb \<nom du serveur [, port] >\\< nom de la base de données\></span><span class="sxs-lookup"><span data-stu-id="a89f0-112">/mgdb \<server name[,port]>\\<database name\></span></span>|<span data-ttu-id="a89f0-113">Facultatif : Spécifie que le serveur d’administration, le port et le nom de la base de données à laquelle appliquer le profil.</span><span class="sxs-lookup"><span data-stu-id="a89f0-113">Optional: Specifies the management server, port, and database name to which to apply the profile.</span></span> <span data-ttu-id="a89f0-114">**Remarque :** lorsque vous utilisez ce paramètre, le port est facultatif.</span><span class="sxs-lookup"><span data-stu-id="a89f0-114">**Note:**  When using this parameter, the port is optional.</span></span>|  
|<span data-ttu-id="a89f0-115">/remove</span><span class="sxs-lookup"><span data-stu-id="a89f0-115">/remove</span></span>|<span data-ttu-id="a89f0-116">Facultatif : Spécifie que le modèle de suivi à supprimer de la base de données BAM.</span><span class="sxs-lookup"><span data-stu-id="a89f0-116">Optional: Specifies that the tracking profile is to be removed from the BAM database.</span></span>|  
|<span data-ttu-id="a89f0-117">filename</span><span class="sxs-lookup"><span data-stu-id="a89f0-117">filename</span></span>|<span data-ttu-id="a89f0-118">Nom du fichier de modèle de suivi à appliquer ou à supprimer.</span><span class="sxs-lookup"><span data-stu-id="a89f0-118">The name of the tracking profile file to apply or remove.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="a89f0-119">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a89f0-119">See Also</span></span>  
 <span data-ttu-id="a89f0-120">[Éditeur de modèle de suivi](../core/tracking-profile-editor.md) </span><span class="sxs-lookup"><span data-stu-id="a89f0-120">[Tracking Profile Editor](../core/tracking-profile-editor.md) </span></span>  
 [<span data-ttu-id="a89f0-121">Comment supprimer des profils de suivi orphelins</span><span class="sxs-lookup"><span data-stu-id="a89f0-121">How to Remove Orphaned Tracking Profiles</span></span>](../core/how-to-remove-orphaned-tracking-profiles.md)