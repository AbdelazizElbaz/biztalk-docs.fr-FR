---
title: Commande ListApps | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 7a5eb0af-e153-4639-a6c0-56c951827c7c
caps.latest.revision: "18"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 785d98655cbe1ef32c00120dc1e54227717ebcae
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="listapps-command"></a><span data-ttu-id="167bb-102">Commande ListApps</span><span class="sxs-lookup"><span data-stu-id="167bb-102">ListApps Command</span></span>
<span data-ttu-id="167bb-103">Cette commande permet d'imprimer sur la console une liste des noms et des descriptions de toutes les applications BizTalk dans la base de données de gestion BizTalk spécifiée.</span><span class="sxs-lookup"><span data-stu-id="167bb-103">Prints to the console the name and description of all of the BizTalk applications in the specified BizTalk Management database.</span></span>  
  
## <a name="usage"></a><span data-ttu-id="167bb-104">Utilisation</span><span class="sxs-lookup"><span data-stu-id="167bb-104">Usage</span></span>  
 <span data-ttu-id="167bb-105">**BTSTask ListApps** [**/Server :***valeur*] [**/Database :***valeur*]</span><span class="sxs-lookup"><span data-stu-id="167bb-105">**BTSTask ListApps** [**/Server:***value*] [**/Database:***value*]</span></span>  
  
## <a name="parameters"></a><span data-ttu-id="167bb-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="167bb-106">Parameters</span></span>  
  
|<span data-ttu-id="167bb-107">Paramètre</span><span class="sxs-lookup"><span data-stu-id="167bb-107">Parameter</span></span>|<span data-ttu-id="167bb-108">Requis</span><span class="sxs-lookup"><span data-stu-id="167bb-108">Required</span></span>|<span data-ttu-id="167bb-109"> Description</span><span class="sxs-lookup"><span data-stu-id="167bb-109">Description</span></span>|  
|---------------|--------------|-----------------|  
|<span data-ttu-id="167bb-110">**/ Serveur** (ou **/S**, consultez la section Notes)</span><span class="sxs-lookup"><span data-stu-id="167bb-110">**/Server** (or **/S**, see Remarks)</span></span>|<span data-ttu-id="167bb-111">Non</span><span class="sxs-lookup"><span data-stu-id="167bb-111">No</span></span>|<span data-ttu-id="167bb-112">Nom de l'instance SQL Server hébergeant la base de données de gestion BizTalk et indiqué sous la forme NomServeur\NomInstance,Port.</span><span class="sxs-lookup"><span data-stu-id="167bb-112">Name of the SQL Server instance hosting the BizTalk Management database, in the form ServerName\InstanceName,Port.</span></span><br /><br /> <span data-ttu-id="167bb-113">Le nom de l'instance est uniquement requis lorsqu'il est différent du nom du serveur.</span><span class="sxs-lookup"><span data-stu-id="167bb-113">Instance name is only required when the instance name is different than the server name.</span></span> <span data-ttu-id="167bb-114">Le port est uniquement requis lorsque le serveur SQL Server utilise un numéro de port autre que celui par défaut (1433).</span><span class="sxs-lookup"><span data-stu-id="167bb-114">Port is only required when SQL Server uses a port number other than the default (1433).</span></span><br /><br /> <span data-ttu-id="167bb-115">Exemples :</span><span class="sxs-lookup"><span data-stu-id="167bb-115">Examples:</span></span><br /><br /> <span data-ttu-id="167bb-116">Server=MyServer</span><span class="sxs-lookup"><span data-stu-id="167bb-116">Server=MyServer</span></span><br /><br /> <span data-ttu-id="167bb-117">Server=MyServer\MySQLServer,1533</span><span class="sxs-lookup"><span data-stu-id="167bb-117">Server=MyServer\MySQLServer,1533</span></span><br /><br /> <span data-ttu-id="167bb-118">Si vous n'indiquez pas de nom pour l'instance SQL Server, le nom d'instance utilisé est celui de l'instance SQL Server exécutée sur l'ordinateur local.</span><span class="sxs-lookup"><span data-stu-id="167bb-118">If not provided, the name of the SQL Server instance running on the local computer is used.</span></span>|  
|<span data-ttu-id="167bb-119">**/ Base de données** (ou **/D**, consultez la section Notes)</span><span class="sxs-lookup"><span data-stu-id="167bb-119">**/Database** (or **/D**, see Remarks)</span></span>|<span data-ttu-id="167bb-120">Non</span><span class="sxs-lookup"><span data-stu-id="167bb-120">No</span></span>|<span data-ttu-id="167bb-121">Nom de la base de données de gestion BizTalk.</span><span class="sxs-lookup"><span data-stu-id="167bb-121">Name of the BizTalk Management database.</span></span> <span data-ttu-id="167bb-122">Si vous ne l'indiquez pas, la base de données utilisée est la base de données de gestion BizTalk s'exécutant au sein de l'instance locale de SQL Server.</span><span class="sxs-lookup"><span data-stu-id="167bb-122">If not specified, the BizTalk Management database running in the local instance of SQL Server is used.</span></span>|  
  
## <a name="sample"></a><span data-ttu-id="167bb-123">Exemple</span><span class="sxs-lookup"><span data-stu-id="167bb-123">Sample</span></span>  
 <span data-ttu-id="167bb-124">**BTSTask ListApps**</span><span class="sxs-lookup"><span data-stu-id="167bb-124">**BTSTask ListApps**</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="167bb-125">Notes</span><span class="sxs-lookup"><span data-stu-id="167bb-125">Remarks</span></span>  
 <span data-ttu-id="167bb-126">Les paramètres ne respectent pas la casse.</span><span class="sxs-lookup"><span data-stu-id="167bb-126">Parameters are not case-sensitive.</span></span> <span data-ttu-id="167bb-127">Il n'est pas nécessaire de taper le nom complet du paramètre pour l'indiquer. Vous pouvez vous contenter de taper les premières lettres du nom à condition qu'elles suffisent à identifier le paramètre sans ambiguïté.</span><span class="sxs-lookup"><span data-stu-id="167bb-127">You do not need to type the entire parameter name to specify it; you can type the first few letters of the parameter name that identify it unambiguously.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="167bb-128">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="167bb-128">See Also</span></span>  
 [<span data-ttu-id="167bb-129">Référence de ligne de commande BTSTask</span><span class="sxs-lookup"><span data-stu-id="167bb-129">BTSTask Command-Line Reference</span></span>](../core/btstask-command-line-reference.md)