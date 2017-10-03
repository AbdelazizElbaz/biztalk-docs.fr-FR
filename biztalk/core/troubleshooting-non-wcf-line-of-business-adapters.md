---
title: "Résolution des problèmes de non - WCF ligne des adaptateurs pour les entreprises | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 4d5f7877-656f-406e-9edb-d6b9a0705b02
caps.latest.revision: "2"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 9ba36ed8a8efb62e2eb8e885791c3c28012dcc49
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="troubleshooting-non-wcf-line-of-business-adapters"></a><span data-ttu-id="b2af4-102">Dépannage des adaptateurs LOB (Line of Business) non-WCF</span><span class="sxs-lookup"><span data-stu-id="b2af4-102">Troubleshooting non-WCF Line of Business Adapters</span></span>
## <a name="failed-to-retrieve-error"></a><span data-ttu-id="b2af4-103">Erreur « Échec d’extraction »</span><span class="sxs-lookup"><span data-stu-id="b2af4-103">“Failed to retrieve” error</span></span>  
 <span data-ttu-id="b2af4-104">Lors de l’utilisation d’un adaptateur LOB (Line of Business) non-WCF, les erreurs suivantes peuvent se produire :</span><span class="sxs-lookup"><span data-stu-id="b2af4-104">When using a non-WCF Line of Business (LOB) adapter, the following errors may occur:</span></span>  
  
-   <span data-ttu-id="b2af4-105">Échec d’extraction du système</span><span class="sxs-lookup"><span data-stu-id="b2af4-105">Failed to retrieve system</span></span>  
  
-   <span data-ttu-id="b2af4-106">L’agent de navigation : erreur interceptée dans le constructeur.</span><span class="sxs-lookup"><span data-stu-id="b2af4-106">Browsing agent: Error trapped in constructor.</span></span> <span data-ttu-id="b2af4-107">L’ordinateur cible a expressément refusé la connexion.</span><span class="sxs-lookup"><span data-stu-id="b2af4-107">Target machine Actively refused connection.</span></span>  
  
-   <span data-ttu-id="b2af4-108">Agent d’exécution : erreur interceptée dans le constructeur.</span><span class="sxs-lookup"><span data-stu-id="b2af4-108">Runtime agent: Error trapped in constructor.</span></span> <span data-ttu-id="b2af4-109">L’ordinateur cible a expressément refusé la connexion.</span><span class="sxs-lookup"><span data-stu-id="b2af4-109">Target machine Actively refused connection.</span></span>  
  
### <a name="cause"></a><span data-ttu-id="b2af4-110">Cause</span><span class="sxs-lookup"><span data-stu-id="b2af4-110">Cause</span></span>  
 <span data-ttu-id="b2af4-111">Les adaptateurs LOB utilisent l’accès à distance .NET.</span><span class="sxs-lookup"><span data-stu-id="b2af4-111">The LOB adapters use .Net Remoting.</span></span> <span data-ttu-id="b2af4-112">Si l’activation de l’accès à distance .NET prend plus de temps que prévu, l’adaptateur risque de renvoyer ces erreurs.</span><span class="sxs-lookup"><span data-stu-id="b2af4-112">If the .Net Remoting activation takes longer than expected, the adapter may return these errors.</span></span>  
  
### <a name="resolution"></a><span data-ttu-id="b2af4-113">Résolution</span><span class="sxs-lookup"><span data-stu-id="b2af4-113">Resolution</span></span>  
 <span data-ttu-id="b2af4-114">Créer le **StartAgentSleep** clé de Registre et augmentez la valeur de délai d’attente :</span><span class="sxs-lookup"><span data-stu-id="b2af4-114">Create the **StartAgentSleep** registry key and increase the timeout value:</span></span>  
  
1.  <span data-ttu-id="b2af4-115">Ouvrez le Registre et accédez à *HKEY_LOCAL_MACHINE\software\Microsoft\BizTalkAdapters*.</span><span class="sxs-lookup"><span data-stu-id="b2af4-115">Open the registry and go to *HKEY_LOCAL_MACHINE\software\Microsoft\BizTalkAdapters*.</span></span>  
  
2.  <span data-ttu-id="b2af4-116">Créez une valeur DWORD avec les propriétés suivantes :</span><span class="sxs-lookup"><span data-stu-id="b2af4-116">Create a new DWORD value with the following properties:</span></span>  
  
     <span data-ttu-id="b2af4-117">Nom : StartAgentSleep</span><span class="sxs-lookup"><span data-stu-id="b2af4-117">Name: StartAgentSleep</span></span>  
  
     <span data-ttu-id="b2af4-118">Base : décimal</span><span class="sxs-lookup"><span data-stu-id="b2af4-118">Base: Decimal</span></span>  
  
     <span data-ttu-id="b2af4-119">Données de la valeur : 1000</span><span class="sxs-lookup"><span data-stu-id="b2af4-119">Value data: 1000</span></span>  
  
 <span data-ttu-id="b2af4-120">Les données de la valeur sont mesurées en millisecondes (ms).</span><span class="sxs-lookup"><span data-stu-id="b2af4-120">Value data is measured in milliseconds (ms).</span></span> <span data-ttu-id="b2af4-121">1 000 ms équivalent à 1 seconde.</span><span class="sxs-lookup"><span data-stu-id="b2af4-121">1000ms equals 1 second.</span></span>  
  
 <span data-ttu-id="b2af4-122">Dans certains systèmes, une seconde n’est pas une valeur suffisante.</span><span class="sxs-lookup"><span data-stu-id="b2af4-122">In some systems, one second may not be enough.</span></span> <span data-ttu-id="b2af4-123">Augmentez la valeur et testez le résultat pour déterminer le délai d’attente approprié nécessaire.</span><span class="sxs-lookup"><span data-stu-id="b2af4-123">Increase the value and test to help determine the appropriate timeout needed.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="b2af4-124">Ajout de la **StartAgentSleep** impacts de clé de Registre **tous les** les adaptateurs WCF LOB.</span><span class="sxs-lookup"><span data-stu-id="b2af4-124">Adding the **StartAgentSleep** registry key impacts **all** the non-WCF LOB adapters.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b2af4-125">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b2af4-125">See Also</span></span>  
 [<span data-ttu-id="b2af4-126">Dépannage des adaptateurs BizTalk Server</span><span class="sxs-lookup"><span data-stu-id="b2af4-126">Troubleshooting BizTalk Server Adapters</span></span>](../core/troubleshooting-biztalk-server-adapters.md)