---
title: Commande UninstallApp | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f45c9530-8138-40f1-b279-1428c5a7fbbc
caps.latest.revision: "15"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: ea94335882ffbcf01b69c450ef4a5eb80ef4fa3d
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="uninstallapp-command"></a><span data-ttu-id="3aaaa-102">Commande UninstallApp</span><span class="sxs-lookup"><span data-stu-id="3aaaa-102">UninstallApp Command</span></span>
<span data-ttu-id="3aaaa-103">Cette commande permet de désinstaller une application BizTalk de l'ordinateur local et de la supprimer de la liste des programmes dans la fenêtre Ajout/Suppression de programmes du Panneau de configuration.</span><span class="sxs-lookup"><span data-stu-id="3aaaa-103">Uninstalls a BizTalk application from the local computer and also removes the application from the list of programs in Add or Remove Programs in Control Panel.</span></span> <span data-ttu-id="3aaaa-104">Son action est identique à l'utilisation de l'option Ajout/Suppression de programmes.</span><span class="sxs-lookup"><span data-stu-id="3aaaa-104">This command has the same effect as removing an application by using Add or Remove Programs.</span></span> <span data-ttu-id="3aaaa-105">Si plusieurs fichiers .msi ont été installés pour cette application, tous les éléments installés par ces fichiers .msi sont désinstallés.</span><span class="sxs-lookup"><span data-stu-id="3aaaa-105">If multiple .msi files have been installed for this application, all of the items installed by all of the .msi files are uninstalled.</span></span>  
  
 <span data-ttu-id="3aaaa-106">Le nom de l'application que vous spécifiez pour cette commande doit correspondre au nom de l'application tel qu'il est affiché dans la fenêtre Ajout/Suppression de programmes.</span><span class="sxs-lookup"><span data-stu-id="3aaaa-106">The application name that you specify for this command must match the name of the application as displayed in Add or Remove Programs.</span></span> <span data-ttu-id="3aaaa-107">Si vous ne connaissez pas le nom de l’application, vous pouvez utiliser la **ListPackage** commande pour l’obtenir, comme décrit dans [commande ListPackage](../core/listpackage-command.md).</span><span class="sxs-lookup"><span data-stu-id="3aaaa-107">If you are unsure of the application name, you can use the **ListPackage** command to obtain it, as described in [ListPackage Command](../core/listpackage-command.md).</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="3aaaa-108">Bien qu'il soit possible de désinstaller une application en double-cliquant sur le fichier .msi, cette opération n'est pas prise en charge.</span><span class="sxs-lookup"><span data-stu-id="3aaaa-108">Although it is possible to uninstall an application by double-clicking the .msi file, doing this is not supported.</span></span> <span data-ttu-id="3aaaa-109">En effet, plusieurs fichiers .msi pouvant être installés pour une même application, cette méthode ne permet pas de désinstaller tous les éléments associés à l'application.</span><span class="sxs-lookup"><span data-stu-id="3aaaa-109">This is because multiple .msi files can be installed for the same application, and using this method will not uninstall all of the items associated with the application.</span></span>  
  
## <a name="usage"></a><span data-ttu-id="3aaaa-110">Utilisation</span><span class="sxs-lookup"><span data-stu-id="3aaaa-110">Usage</span></span>  
 <span data-ttu-id="3aaaa-111">**« ApplicationName » BTSTask UninstallApp :** *valeur*</span><span class="sxs-lookup"><span data-stu-id="3aaaa-111">**BTSTask UninstallApp /ApplicationName:** *value*</span></span>  
  
## <a name="parameters"></a><span data-ttu-id="3aaaa-112">Paramètres</span><span class="sxs-lookup"><span data-stu-id="3aaaa-112">Parameters</span></span>  
  
|<span data-ttu-id="3aaaa-113">Paramètre</span><span class="sxs-lookup"><span data-stu-id="3aaaa-113">Parameter</span></span>|<span data-ttu-id="3aaaa-114">Requis</span><span class="sxs-lookup"><span data-stu-id="3aaaa-114">Required</span></span>|<span data-ttu-id="3aaaa-115"> Description</span><span class="sxs-lookup"><span data-stu-id="3aaaa-115">Description</span></span>|  
|---------------|--------------|-----------------|  
|<span data-ttu-id="3aaaa-116">**/ ApplicationName** (ou **/A**, consultez la section Notes)</span><span class="sxs-lookup"><span data-stu-id="3aaaa-116">**/ApplicationName** (or **/A**, see Remarks)</span></span>|<span data-ttu-id="3aaaa-117">Oui</span><span class="sxs-lookup"><span data-stu-id="3aaaa-117">Yes</span></span>|<span data-ttu-id="3aaaa-118">Nom de l'application BizTalk à désinstaller.</span><span class="sxs-lookup"><span data-stu-id="3aaaa-118">Name of the BizTalk application to uninstall.</span></span> <span data-ttu-id="3aaaa-119">Si le nom comprend des espaces, vous devez le placer entre guillemets doubles («).</span><span class="sxs-lookup"><span data-stu-id="3aaaa-119">If the name includes spaces, you must enclose it in double quotation marks (").</span></span>|  
  
## <a name="sample"></a><span data-ttu-id="3aaaa-120">Exemple</span><span class="sxs-lookup"><span data-stu-id="3aaaa-120">Sample</span></span>  
 <span data-ttu-id="3aaaa-121">**BTSTask UninstallApp /ApplicationName:MyApplication**</span><span class="sxs-lookup"><span data-stu-id="3aaaa-121">**BTSTask UninstallApp /ApplicationName:MyApplication**</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3aaaa-122">Notes</span><span class="sxs-lookup"><span data-stu-id="3aaaa-122">Remarks</span></span>  
 <span data-ttu-id="3aaaa-123">Les paramètres ne respectent pas la casse.</span><span class="sxs-lookup"><span data-stu-id="3aaaa-123">Parameters are not case-sensitive.</span></span> <span data-ttu-id="3aaaa-124">Il n'est pas nécessaire de taper le nom complet du paramètre pour l'indiquer. Vous pouvez vous contenter de taper les premières lettres du nom à condition qu'elles suffisent à identifier le paramètre sans ambiguïté.</span><span class="sxs-lookup"><span data-stu-id="3aaaa-124">You do not need to type the entire parameter name to specify it; you can type the first few letters of the parameter name that identify it unambiguously.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3aaaa-125">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="3aaaa-125">See Also</span></span>  
 <span data-ttu-id="3aaaa-126">[Référence de ligne de commande BTSTask](../core/btstask-command-line-reference.md) </span><span class="sxs-lookup"><span data-stu-id="3aaaa-126">[BTSTask Command-Line Reference](../core/btstask-command-line-reference.md) </span></span>  
 [<span data-ttu-id="3aaaa-127">Comment désinstaller une Application BizTalk</span><span class="sxs-lookup"><span data-stu-id="3aaaa-127">How to Uninstall a BizTalk Application</span></span>](../core/how-to-uninstall-a-biztalk-application.md)