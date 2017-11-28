---
title: Commande ExportSettings | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: fa34dab1-c854-473e-a693-43ba45624e16
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: ab8c39ef6903affbd2a1446bbde18a56e1a7778c
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="exportsettings-command"></a><span data-ttu-id="5cb66-102">Commande ExportSettings</span><span class="sxs-lookup"><span data-stu-id="5cb66-102">ExportSettings Command</span></span>
<span data-ttu-id="5cb66-103">La commande ExportSettings permet d'exporter les paramètres de BizTalk Server d'une base de données de configuration BizTalk Server vers un fichier XML.</span><span class="sxs-lookup"><span data-stu-id="5cb66-103">The ExportSettings command nables you to export the BizTalk Server settings from a BizTalk Server configuration database to an XML file.</span></span> <span data-ttu-id="5cb66-104">Vous pouvez ensuite importer ces paramètres dans un autre environnement comme décrit dans [comment importer à l’aide de paramètres du Panneau de configuration BizTalk](../core/how-to-import-biztalk-settings-using-settings-dashboard.md) ou [comment importer des paramètres de BizTalk à l’aide de BTSTask](../core/how-to-import-biztalk-settings-using-btstask.md).</span><span class="sxs-lookup"><span data-stu-id="5cb66-104">You can then import these settings in another environment as described in [How to Import BizTalk Settings Using Settings Dashboard](../core/how-to-import-biztalk-settings-using-settings-dashboard.md) or [How to Import BizTalk Settings Using BTSTask](../core/how-to-import-biztalk-settings-using-btstask.md).</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="5cb66-105">Conditions préalables</span><span class="sxs-lookup"><span data-stu-id="5cb66-105">Prerequisites</span></span>  
 <span data-ttu-id="5cb66-106">Pour exécuter cette procédure, vous devez ouvrir une session en tant que membre du groupe Administrateurs BizTalk Server.</span><span class="sxs-lookup"><span data-stu-id="5cb66-106">To perform this operation, you must be logged on as a member of the BizTalk Server Administrators group.</span></span>  
  
## <a name="usage"></a><span data-ttu-id="5cb66-107">Utilisation</span><span class="sxs-lookup"><span data-stu-id="5cb66-107">Usage</span></span>  
 `ExportSettings –Destination:value[-Server:value] [-Database:value]`  
  
## <a name="parameters"></a><span data-ttu-id="5cb66-108">Paramètres</span><span class="sxs-lookup"><span data-stu-id="5cb66-108">Parameters</span></span>  
  
|<span data-ttu-id="5cb66-109">**Paramètre**</span><span class="sxs-lookup"><span data-stu-id="5cb66-109">**Parameter**</span></span>|<span data-ttu-id="5cb66-110">Requis</span><span class="sxs-lookup"><span data-stu-id="5cb66-110">Required</span></span>|<span data-ttu-id="5cb66-111">Valeur</span><span class="sxs-lookup"><span data-stu-id="5cb66-111">Value</span></span>|  
|-------------------|--------------|-----------|  
|<span data-ttu-id="5cb66-112">**-Destination**</span><span class="sxs-lookup"><span data-stu-id="5cb66-112">**-Destination**</span></span>|<span data-ttu-id="5cb66-113">Oui</span><span class="sxs-lookup"><span data-stu-id="5cb66-113">Yes</span></span>|<span data-ttu-id="5cb66-114">Nom et chemin d'accès au fichier XML à écrire.</span><span class="sxs-lookup"><span data-stu-id="5cb66-114">Path and file name of the XML file to write.</span></span>|  
|<span data-ttu-id="5cb66-115">**-Serveur**</span><span class="sxs-lookup"><span data-stu-id="5cb66-115">**-Server**</span></span>|<span data-ttu-id="5cb66-116">Ce paramètre est facultatif</span><span class="sxs-lookup"><span data-stu-id="5cb66-116">Optional</span></span>|<span data-ttu-id="5cb66-117">Nom du serveur SQL Server hébergeant la base de données de configuration BizTalk.</span><span class="sxs-lookup"><span data-stu-id="5cb66-117">The name of SQL Server hosting the BizTalk configuration database.</span></span>|  
|<span data-ttu-id="5cb66-118">**-Base de données**</span><span class="sxs-lookup"><span data-stu-id="5cb66-118">**-Database**</span></span>|<span data-ttu-id="5cb66-119">Ce paramètre est facultatif</span><span class="sxs-lookup"><span data-stu-id="5cb66-119">Optional</span></span>|<span data-ttu-id="5cb66-120">Nom de la base de données de configuration BizTalk.</span><span class="sxs-lookup"><span data-stu-id="5cb66-120">The name of the BizTalk configuration database.</span></span>|  
  
## <a name="sample"></a><span data-ttu-id="5cb66-121">Exemple</span><span class="sxs-lookup"><span data-stu-id="5cb66-121">Sample</span></span>  
 `BTSTask ExportSettings /Destination:MyFile.xml /Server:MyServer /Database:MyMgmtDb`  
  
## <a name="remarks"></a><span data-ttu-id="5cb66-122">Notes</span><span class="sxs-lookup"><span data-stu-id="5cb66-122">Remarks</span></span>  
 <span data-ttu-id="5cb66-123">Les paramètres ne respectent pas la casse.</span><span class="sxs-lookup"><span data-stu-id="5cb66-123">Parameters are not case-sensitive.</span></span> <span data-ttu-id="5cb66-124">Il n'est pas nécessaire de taper le nom complet du paramètre pour l'indiquer. Vous pouvez vous contenter de taper les premières lettres du nom à condition qu'elles suffisent à identifier le paramètre sans ambiguïté.</span><span class="sxs-lookup"><span data-stu-id="5cb66-124">You do not need to type the entire parameter name to specify it; you can type the first few letters of the parameter name that identify it unambiguously.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5cb66-125">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="5cb66-125">See Also</span></span>  
 [<span data-ttu-id="5cb66-126">Référence de ligne de commande BTSTask</span><span class="sxs-lookup"><span data-stu-id="5cb66-126">BTSTask Command-Line Reference</span></span>](../core/btstask-command-line-reference.md)