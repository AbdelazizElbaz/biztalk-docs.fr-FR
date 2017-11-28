---
title: Commande de ImportParties | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 87d43e2c-401c-4450-ad9b-2528086b99e4
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 15edad97134d3dbccc6f4b1af9395cb0bc01febd
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="importparties-command"></a><span data-ttu-id="c837b-102">Commande de ImportParties</span><span class="sxs-lookup"><span data-stu-id="c837b-102">ImportParties Command</span></span>
<span data-ttu-id="c837b-103">Importe les contrats et les parties de l’entreprise-entreprise à partir d’un fichier de liaison XML source dans la base de données de configuration, sans importer les artefacts d’application.</span><span class="sxs-lookup"><span data-stu-id="c837b-103">Imports the business-to-business parties and agreements from a source XML binding file in the configuration database, without importing any of the application artifacts.</span></span> <span data-ttu-id="c837b-104">Pour plus d’informations, consultez **notes** dans cette rubrique.</span><span class="sxs-lookup"><span data-stu-id="c837b-104">For more information, see **Remarks** in this topic.</span></span>  

> [!IMPORTANT]
> <span data-ttu-id="c837b-105">Cette commande est nouvelle, en commençant par  **[!INCLUDE[bts2016_md](../includes/bts2016-md.md)]** et les versions plus récentes.</span><span class="sxs-lookup"><span data-stu-id="c837b-105">This command is new starting with **[!INCLUDE[bts2016_md](../includes/bts2016-md.md)]**, and any newer versions.</span></span>
  
> [!NOTE]
>  <span data-ttu-id="c837b-106">Aucune application n'est spécifiée pour les fichiers de liaison générés dans [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="c837b-106">Binding files generated in [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] do not have an application specified.</span></span> <span data-ttu-id="c837b-107">Ceux-ci sont donc importés dans l'application par défaut.</span><span class="sxs-lookup"><span data-stu-id="c837b-107">They are imported into the default application.</span></span>  
  
## <a name="usage"></a><span data-ttu-id="c837b-108">Utilisation</span><span class="sxs-lookup"><span data-stu-id="c837b-108">Usage</span></span>  
  <span data-ttu-id="c837b-109">**BTSTask ImportParties-Source**:*valeur* [**- ExcludeEdiFallbackSettings**] [**-Server**:*valeur*] [**-Base de données**:*valeur*]</span><span class="sxs-lookup"><span data-stu-id="c837b-109">**BTSTask ImportParties -Source**:*value* [**-ExcludeEdiFallbackSettings**] [**-Server**:*value*] [**-Database**:*value*]</span></span>
  
## <a name="parameters"></a><span data-ttu-id="c837b-110">Paramètres</span><span class="sxs-lookup"><span data-stu-id="c837b-110">Parameters</span></span>  
  
|<span data-ttu-id="c837b-111">Paramètre</span><span class="sxs-lookup"><span data-stu-id="c837b-111">Parameter</span></span>|<span data-ttu-id="c837b-112">Requis</span><span class="sxs-lookup"><span data-stu-id="c837b-112">Required</span></span>|<span data-ttu-id="c837b-113">Valeur</span><span class="sxs-lookup"><span data-stu-id="c837b-113">Value</span></span>|  
|---|---|---|  
|<span data-ttu-id="c837b-114">**-Source**</span><span class="sxs-lookup"><span data-stu-id="c837b-114">**-Source**</span></span> | <span data-ttu-id="c837b-115">Requis</span><span class="sxs-lookup"><span data-stu-id="c837b-115">Required</span></span> | <span data-ttu-id="c837b-116">Le chemin d’accès et le nom du fichier de liaison XML à lire.</span><span class="sxs-lookup"><span data-stu-id="c837b-116">The path and file name of the XML binding file to read.</span></span>|
|<span data-ttu-id="c837b-117">**-ExcludeEdiFallbackSettings**</span><span class="sxs-lookup"><span data-stu-id="c837b-117">**-ExcludeEdiFallbackSettings**</span></span> | <span data-ttu-id="c837b-118">Ce paramètre est facultatif</span><span class="sxs-lookup"><span data-stu-id="c837b-118">Optional</span></span> | <span data-ttu-id="c837b-119">Si spécifié, il exclut les paramètres de (x12 et edifact) de secours edi à partir du fichier de liaison.</span><span class="sxs-lookup"><span data-stu-id="c837b-119">If specified, it excludes edi fallback (x12 and edifact) settings from the binding file.</span></span>  |
| <span data-ttu-id="c837b-120">**-Serveur**</span><span class="sxs-lookup"><span data-stu-id="c837b-120">**-Server**</span></span> | <span data-ttu-id="c837b-121">Ce paramètre est facultatif</span><span class="sxs-lookup"><span data-stu-id="c837b-121">Optional</span></span> | <span data-ttu-id="c837b-122">Le nom de serveur SQL server hébergeant la base de données de configuration BizTalk.</span><span class="sxs-lookup"><span data-stu-id="c837b-122">The name of SQL server hosting the BizTalk configuration database.</span></span> |
| <span data-ttu-id="c837b-123">**-Base de données**</span><span class="sxs-lookup"><span data-stu-id="c837b-123">**-Database**</span></span> | <span data-ttu-id="c837b-124">Ce paramètre est facultatif</span><span class="sxs-lookup"><span data-stu-id="c837b-124">Optional</span></span> | <span data-ttu-id="c837b-125">Nom de la base de données de configuration BizTalk.</span><span class="sxs-lookup"><span data-stu-id="c837b-125">The name of the BizTalk configuration database.</span></span> |

## <a name="sample"></a><span data-ttu-id="c837b-126">Exemple</span><span class="sxs-lookup"><span data-stu-id="c837b-126">Sample</span></span>
  `BTSTask ImportParties  -Source:"C:\Temp\MyParties.Xml" -ExcludeEdiFallbackSettings`

## <a name="remarks"></a><span data-ttu-id="c837b-127">Notes</span><span class="sxs-lookup"><span data-stu-id="c837b-127">Remarks</span></span>
<span data-ttu-id="c837b-128">Si le fichier de liaison a également les artefacts de l’application, puis ils ne sont pas importés.</span><span class="sxs-lookup"><span data-stu-id="c837b-128">If the binding file also has application artifacts, then they are not imported.</span></span> <span data-ttu-id="c837b-129">Uniquement les parties et les accords sont importés.</span><span class="sxs-lookup"><span data-stu-id="c837b-129">Only parties and agreements are imported.</span></span>