---
title: Commande de ExportParties | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b421c8ed-d505-48ba-9d1d-8519c9d51750
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 6ca525872ccc1cd941673189c4ac176fc4631f22
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="exportparties-command"></a><span data-ttu-id="ec5c3-102">Commande de ExportParties</span><span class="sxs-lookup"><span data-stu-id="ec5c3-102">ExportParties Command</span></span>
<span data-ttu-id="ec5c3-103">Exporte toutes les parties et les contrats à un fichier de liaison XML.</span><span class="sxs-lookup"><span data-stu-id="ec5c3-103">Exports all the parties and agreements to an XML bindings file.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="ec5c3-104">Cette commande est nouvelle, en commençant par  **[!INCLUDE[bts2016_md](../includes/bts2016-md.md)]** et les versions plus récentes.</span><span class="sxs-lookup"><span data-stu-id="ec5c3-104">This command is new starting with **[!INCLUDE[bts2016_md](../includes/bts2016-md.md)]**, and any newer versions.</span></span>

## <a name="usage"></a><span data-ttu-id="ec5c3-105">Utilisation</span><span class="sxs-lookup"><span data-stu-id="ec5c3-105">Usage</span></span>
  <span data-ttu-id="ec5c3-106">**BTSTask ExportParties-Destination**:*valeur* [**-Server**:*valeur*] [**-base de données**: *valeur*]</span><span class="sxs-lookup"><span data-stu-id="ec5c3-106">**BTSTask ExportParties -Destination**:*value* [**-Server**:*value*] [**-Database**:*value*]</span></span>
  
## <a name="parameters"></a><span data-ttu-id="ec5c3-107">Paramètres</span><span class="sxs-lookup"><span data-stu-id="ec5c3-107">Parameters</span></span>

|<span data-ttu-id="ec5c3-108">Paramètre</span><span class="sxs-lookup"><span data-stu-id="ec5c3-108">Parameter</span></span>|<span data-ttu-id="ec5c3-109">Requis</span><span class="sxs-lookup"><span data-stu-id="ec5c3-109">Required</span></span>|<span data-ttu-id="ec5c3-110">Valeur</span><span class="sxs-lookup"><span data-stu-id="ec5c3-110">Value</span></span>|  
|---|---|---|  
| <span data-ttu-id="ec5c3-111">**-Destination**</span><span class="sxs-lookup"><span data-stu-id="ec5c3-111">**-Destination**</span></span> | <span data-ttu-id="ec5c3-112">Requis</span><span class="sxs-lookup"><span data-stu-id="ec5c3-112">Required</span></span> | <span data-ttu-id="ec5c3-113">Chemin d’accès et le nom du fichier de liaison XML à écrire.</span><span class="sxs-lookup"><span data-stu-id="ec5c3-113">Path and file name of the XML binding file to write.</span></span> |
| <span data-ttu-id="ec5c3-114">**-Serveur**</span><span class="sxs-lookup"><span data-stu-id="ec5c3-114">**-Server**</span></span> | <span data-ttu-id="ec5c3-115">Ce paramètre est facultatif</span><span class="sxs-lookup"><span data-stu-id="ec5c3-115">Optional</span></span> | <span data-ttu-id="ec5c3-116">Le nom de serveur SQL server hébergeant la base de données de configuration BizTalk.</span><span class="sxs-lookup"><span data-stu-id="ec5c3-116">The name of SQL server hosting the BizTalk configuration database.</span></span> |
| <span data-ttu-id="ec5c3-117">**-Base de données**</span><span class="sxs-lookup"><span data-stu-id="ec5c3-117">**-Database**</span></span> | <span data-ttu-id="ec5c3-118">Ce paramètre est facultatif</span><span class="sxs-lookup"><span data-stu-id="ec5c3-118">Optional</span></span> | <span data-ttu-id="ec5c3-119">Nom de la base de données de configuration BizTalk.</span><span class="sxs-lookup"><span data-stu-id="ec5c3-119">The name of the BizTalk configuration database.</span></span>|

## <a name="sample"></a><span data-ttu-id="ec5c3-120">Exemple</span><span class="sxs-lookup"><span data-stu-id="ec5c3-120">Sample</span></span>
  `ExportParties  -Destination:"C:\Temp\MyParties.Xml"` 

## <a name="remarks"></a><span data-ttu-id="ec5c3-121">Notes</span><span class="sxs-lookup"><span data-stu-id="ec5c3-121">Remarks</span></span>
  <span data-ttu-id="ec5c3-122">Uniquement les parties, les contrats et les paramètres de secours EDI sont exportés.</span><span class="sxs-lookup"><span data-stu-id="ec5c3-122">Only parties, agreements, and EDI fallback settings are exported.</span></span> <span data-ttu-id="ec5c3-123">Aucun artefact d’application n’est exportés.</span><span class="sxs-lookup"><span data-stu-id="ec5c3-123">No application artifacts are exported.</span></span>
