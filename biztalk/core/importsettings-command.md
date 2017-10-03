---
title: Commande ImportSettings | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 587f7e1f-9cf7-4e7b-90cd-11a266f474dc
caps.latest.revision: "2"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 9c609634422f8c8b5f2c1a96691fe4eda708e5c9
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="importsettings-command"></a><span data-ttu-id="68c10-102">Commande ImportSettings</span><span class="sxs-lookup"><span data-stu-id="68c10-102">ImportSettings Command</span></span>
<span data-ttu-id="68c10-103">Importe les paramètres de groupe, de l'hôte ou de l'instance d'hôte BizTalk dans la base de données de configuration à partir d'un fichier XML source.</span><span class="sxs-lookup"><span data-stu-id="68c10-103">Imports the BizTalk group, host, or host instance settings from a source XML file to the configuration database.</span></span> <span data-ttu-id="68c10-104">Les paramètres sont mappés tels qu'ils le sont dans le fichier XML.</span><span class="sxs-lookup"><span data-stu-id="68c10-104">The settings are mapped as they are in the mapping XML file.</span></span> <span data-ttu-id="68c10-105">Ces paramètres ont été exportés comme décrit dans [importer ou exporter le panneau de configuration à l’aide de paramètres de BizTalk](how-to-import-biztalk-settings-using-settings-dashboard.md) ou [importation ou exportation BizTalk paramètres à l’aide de BTSTask](how-to-import-biztalk-settings-using-btstask.md).</span><span class="sxs-lookup"><span data-stu-id="68c10-105">These settings may have been exported as described in [Import or export BizTalk Settings Using Settings Dashboard](how-to-import-biztalk-settings-using-settings-dashboard.md) or [Import or export BizTalk Settings Using BTSTask](how-to-import-biztalk-settings-using-btstask.md).</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="68c10-106">Conditions préalables</span><span class="sxs-lookup"><span data-stu-id="68c10-106">Prerequisites</span></span>  
 <span data-ttu-id="68c10-107">Pour effectuer cette opération, vous devez être connecté en tant que membre du groupe Administrateurs de BizTalk Server.</span><span class="sxs-lookup"><span data-stu-id="68c10-107">To perform this operation, you must be signed in as a member of the BizTalk Server Administrators group.</span></span>  
  
## <a name="usage"></a><span data-ttu-id="68c10-108">Utilisation</span><span class="sxs-lookup"><span data-stu-id="68c10-108">Usage</span></span>  
 `ImportSettings –Source:value –Map: value [-Server:value] [-Database:value]`  
  
## <a name="parameters"></a><span data-ttu-id="68c10-109">Paramètres</span><span class="sxs-lookup"><span data-stu-id="68c10-109">Parameters</span></span>  
  
|<span data-ttu-id="68c10-110">**Paramètre**</span><span class="sxs-lookup"><span data-stu-id="68c10-110">**Parameter**</span></span>|<span data-ttu-id="68c10-111">Requis</span><span class="sxs-lookup"><span data-stu-id="68c10-111">Required</span></span>|<span data-ttu-id="68c10-112">Valeur</span><span class="sxs-lookup"><span data-stu-id="68c10-112">Value</span></span>|  
|-------------------|--------------|-----------|  
|<span data-ttu-id="68c10-113">**-Source**</span><span class="sxs-lookup"><span data-stu-id="68c10-113">**-Source**</span></span>|<span data-ttu-id="68c10-114">Oui</span><span class="sxs-lookup"><span data-stu-id="68c10-114">Yes</span></span>|<span data-ttu-id="68c10-115">Nom et chemin d'accès au fichier XML contenant les paramètres exportés.</span><span class="sxs-lookup"><span data-stu-id="68c10-115">Path and file name of the exported settings XML file.</span></span>|  
|<span data-ttu-id="68c10-116">**-Map**</span><span class="sxs-lookup"><span data-stu-id="68c10-116">**-Map**</span></span>|<span data-ttu-id="68c10-117">Oui</span><span class="sxs-lookup"><span data-stu-id="68c10-117">Yes</span></span>|<span data-ttu-id="68c10-118">Nom et chemin d'accès au fichier XML de mappage.</span><span class="sxs-lookup"><span data-stu-id="68c10-118">Path and file name of the mapping XML file.</span></span>|  
|<span data-ttu-id="68c10-119">**-Serveur**</span><span class="sxs-lookup"><span data-stu-id="68c10-119">**-Server**</span></span>|<span data-ttu-id="68c10-120">Ce paramètre est facultatif</span><span class="sxs-lookup"><span data-stu-id="68c10-120">Optional</span></span>|<span data-ttu-id="68c10-121">Nom de l'ordinateur SQL Server hébergeant la base de données de configuration BizTalk.</span><span class="sxs-lookup"><span data-stu-id="68c10-121">The name of SQL Server computer hosting the BizTalk configuration database.</span></span>|  
|<span data-ttu-id="68c10-122">**-Base de données**</span><span class="sxs-lookup"><span data-stu-id="68c10-122">**-Database**</span></span>|<span data-ttu-id="68c10-123">Ce paramètre est facultatif</span><span class="sxs-lookup"><span data-stu-id="68c10-123">Optional</span></span>|<span data-ttu-id="68c10-124">Nom de la base de données de configuration BizTalk.</span><span class="sxs-lookup"><span data-stu-id="68c10-124">The name of the BizTalk configuration database.</span></span>|  
  
## <a name="sample"></a><span data-ttu-id="68c10-125">Exemple</span><span class="sxs-lookup"><span data-stu-id="68c10-125">Sample</span></span>  
 `BTSTask ImportSettings /Source:”C:\My Folder>\ExportedSettings.xml” /Map:Mappings.xml /Server:MyServer /Database:MyMgmtDb`  
  
## <a name="remarks"></a><span data-ttu-id="68c10-126">Notes</span><span class="sxs-lookup"><span data-stu-id="68c10-126">Remarks</span></span>  
 <span data-ttu-id="68c10-127">Les paramètres ne respectent pas la casse.</span><span class="sxs-lookup"><span data-stu-id="68c10-127">Parameters are not case-sensitive.</span></span> <span data-ttu-id="68c10-128">Il n'est pas nécessaire de taper le nom complet du paramètre pour l'indiquer. Vous pouvez vous contenter de taper les premières lettres du nom à condition qu'elles suffisent à identifier le paramètre sans ambiguïté.</span><span class="sxs-lookup"><span data-stu-id="68c10-128">You do not need to type the entire parameter name to specify it; you can type the first few letters of the parameter name that identify it unambiguously.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="68c10-129">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="68c10-129">See Also</span></span>  
 [<span data-ttu-id="68c10-130">Référence de ligne de commande BTSTask</span><span class="sxs-lookup"><span data-stu-id="68c10-130">BTSTask Command-Line Reference</span></span>](../core/btstask-command-line-reference.md)