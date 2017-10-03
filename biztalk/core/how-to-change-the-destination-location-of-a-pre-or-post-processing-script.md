---
title: "Comment modifier l’emplacement de Destination d’un Script de pré-traitement ou post-traitement | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- scripts, file locations
- scripts, modifying
- managing [scripts], modifying
- managing [scripts], file locations
ms.assetid: 4a4fdaef-099f-4c29-9815-12404c7a2212
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 7eb4ba338790e301e54a9bf262a49808a0a55315
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-change-the-destination-location-of-a-pre--or-post-processing-script"></a><span data-ttu-id="9706f-102">Modification de l'emplacement de destination d'un script de pré-traitement ou de post-traitement</span><span class="sxs-lookup"><span data-stu-id="9706f-102">How to Change the Destination Location of a Pre- or Post-processing Script</span></span>
<span data-ttu-id="9706f-103">Cette rubrique décrit comment changer l'emplacement de destination d'un script de pré-traitement ou post-traitement à l'aide de la console Administration de BizTalk Server.</span><span class="sxs-lookup"><span data-stu-id="9706f-103">This topic describes how to use the BizTalk Server Administration console to change the destination location of a pre- or post-processing script.</span></span> <span data-ttu-id="9706f-104">Il s'agit de l'emplacement de copie du script lors de l'installation de l'application.</span><span class="sxs-lookup"><span data-stu-id="9706f-104">This is the location to which the script is copied when the application is installed.</span></span> <span data-ttu-id="9706f-105">Vous pouvez être amené à le changer lors du déploiement d'une application dans un autre environnement.</span><span class="sxs-lookup"><span data-stu-id="9706f-105">You might want to change the destination location when deploying an application into a different environment.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="9706f-106">Veillez à attribuer un emplacement de destination à un script devant s'exécuter lors de la désinstallation de l'application.</span><span class="sxs-lookup"><span data-stu-id="9706f-106">Be sure to provide a destination location for a script that will run when the application is uninstalled.</span></span> <span data-ttu-id="9706f-107">Dans le cas contraire, le script ne sera pas copié dans le système de fichiers local et ne pourra pas s'exécuter lors de la désinstallation.</span><span class="sxs-lookup"><span data-stu-id="9706f-107">If you do not, the script will not be copied to the local file system, and therefore will not run during uninstallation.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="9706f-108">Conditions préalables</span><span class="sxs-lookup"><span data-stu-id="9706f-108">Prerequisites</span></span>  
 <span data-ttu-id="9706f-109">Pour exécuter la procédure décrite dans cette rubrique, vous devez être connecté avec un compte membre du groupe d'administrateurs BizTalk Server.</span><span class="sxs-lookup"><span data-stu-id="9706f-109">To perform the procedure in this topic, you must be logged on with an account that is a member of the BizTalk Server Administrators group.</span></span> <span data-ttu-id="9706f-110">Pour plus d’informations sur les autorisations, consultez [autorisations requises pour déployer et gérer une Application BizTalk](../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md).</span><span class="sxs-lookup"><span data-stu-id="9706f-110">For more detailed information on permissions, see [Permissions Required for Deploying and Managing a BizTalk Application](../core/permissions-required-for-deploying-and-managing-a-biztalk-application.md).</span></span>  
  
### <a name="to-modify-the-deployment-properties-of-a-pre--or-post-processing-script"></a><span data-ttu-id="9706f-111">Pour modifier les propriétés de déploiement d'un script de pré-traitement ou post-traitement</span><span class="sxs-lookup"><span data-stu-id="9706f-111">To modify the deployment properties of a pre- or post-processing script</span></span>  
  
1.  <span data-ttu-id="9706f-112">Cliquez sur **Démarrer**, cliquez sur **tous les programmes**, cliquez sur [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], puis cliquez sur **Administration de BizTalk Server**.</span><span class="sxs-lookup"><span data-stu-id="9706f-112">Click **Start**, click **All Programs**, click [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], and then click **BizTalk Server Administration**.</span></span>  
  
2.  <span data-ttu-id="9706f-113">Dans l'arborescence de la console, développez successivement [!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)], le groupe BizTalk contenant le script à modifier, puis l'application contenant le script.</span><span class="sxs-lookup"><span data-stu-id="9706f-113">In the console tree, expand [!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)], expand the BizTalk group containing the script to modify, and then expand the application containing the script.</span></span>  
  
3.  <span data-ttu-id="9706f-114">Cliquez sur le **ressources** dossier, cliquez sur le script, puis cliquez sur **modifier**.</span><span class="sxs-lookup"><span data-stu-id="9706f-114">Click the **Resources** folder, right-click the script, and then click **Modify**.</span></span>  
  
4.  <span data-ttu-id="9706f-115">Dans **l’emplacement de Destination**, le chemin d’accès complet de l’emplacement de destination, y compris le nom de fichier, puis tapez **OK**.</span><span class="sxs-lookup"><span data-stu-id="9706f-115">In **Destination location**, type the full path of the destination location, including the file name, and then click **OK**.</span></span> <span data-ttu-id="9706f-116">Vous pouvez utiliser la variable d'environnement %BTAD_InstallDir% dans le chemin d'accès pour spécifier le dossier d'installation de l'application.</span><span class="sxs-lookup"><span data-stu-id="9706f-116">(You can use the environment variable %BTAD_InstallDir% in the path to specify the application installation folder.)</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9706f-117">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="9706f-117">See Also</span></span>  
 [<span data-ttu-id="9706f-118">Gestion des Scripts de pré-traitement et post-traitement</span><span class="sxs-lookup"><span data-stu-id="9706f-118">Managing Pre- and Post-processing Scripts</span></span>](../core/managing-pre-and-post-processing-scripts.md)