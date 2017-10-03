---
title: "À l’aide de l’outil Microsoft BizTalk LoadGen 2007 | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- LoadGen tool, how to
- LoadGen tool, test environments
ms.assetid: d1973a26-1c98-4261-bd9a-6357cdb19ccf
caps.latest.revision: "5"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: b93018f093bbdffed64c44060f445a30d37344c7
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="using-the-microsoft-biztalk-loadgen-2007-tool"></a><span data-ttu-id="5082a-102">Utilisation de l'outil Microsoft BizTalk LoadGen 2007</span><span class="sxs-lookup"><span data-stu-id="5082a-102">Using the Microsoft BizTalk LoadGen 2007 Tool</span></span>
<span data-ttu-id="5082a-103">L'outil Microsoft BizTalk LoadGen 2007 permet aux développeurs et professionnels de l'informatique de simuler la présence d'une charge sur un serveur BizTalk Server.</span><span class="sxs-lookup"><span data-stu-id="5082a-103">The Microsoft BizTalk LoadGen 2007 Tool is intended for developers and IT professionals to simulate load on a BizTalk Server.</span></span> <span data-ttu-id="5082a-104">Avec cet outil, vous pouvez simuler une charge pour instrumenter les performances et le stress par rapport à un déploiement BizTalk.</span><span class="sxs-lookup"><span data-stu-id="5082a-104">Using this tool, you can simulate load to instrument performance and stress against a BizTalk deployment.</span></span> <span data-ttu-id="5082a-105">Cet outil peut en outre être étendu par les développeurs pour simuler une charge pour les transports personnalisés.</span><span class="sxs-lookup"><span data-stu-id="5082a-105">In addition, this tool may also be extended by developers to simulate load for custom transports.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="5082a-106">L’outil LoadGen 2007 est disponible pour téléchargement à l’adresse [http://go.microsoft.com/fwlink/?LinkId=59841](http://go.microsoft.com/fwlink/?LinkId=59841).</span><span class="sxs-lookup"><span data-stu-id="5082a-106">The LoadGen 2007 tool is available for download at [http://go.microsoft.com/fwlink/?LinkId=59841](http://go.microsoft.com/fwlink/?LinkId=59841).</span></span> <span data-ttu-id="5082a-107">La version précédente de cet outil, l’outil de génération de charge de BizTalk Server 2004 est disponible pour téléchargement à l’adresse [http://go.microsoft.com/fwlink/?LinkId=108999](http://go.microsoft.com/fwlink/?LinkId=108999).</span><span class="sxs-lookup"><span data-stu-id="5082a-107">The previous version of this tool, the BizTalk Server 2004 Load Generation Tool is available for download at [http://go.microsoft.com/fwlink/?LinkId=108999](http://go.microsoft.com/fwlink/?LinkId=108999).</span></span>  
  
 <span data-ttu-id="5082a-108">Cet outil doit être utilisé exclusivement dans un environnement de test et non de production.</span><span class="sxs-lookup"><span data-stu-id="5082a-108">This tool should be used in a test environment only, and should not be used in a production environment.</span></span> <span data-ttu-id="5082a-109">L'outil est fourni « en l'état » et n'est pas pris en charge.</span><span class="sxs-lookup"><span data-stu-id="5082a-109">This tool is provided "as-is" and is not supported.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="5082a-110">Vous pouvez associer l'outil BizTalk Server 2004 Load Generation Tool à l'adaptateur MSMQ, mais pour cela, quelques étapes supplémentaires sont nécessaires.</span><span class="sxs-lookup"><span data-stu-id="5082a-110">You can use BizTalk Server 2004 Load Generation Tool with the MSMQ adapter, but you must do some additional steps.</span></span> <span data-ttu-id="5082a-111">Pour obtenir des instructions, consultez [à l’aide de LoadGen 2007 avec MSMQ](../core/using-loadgen-2007-with-msmq.md).</span><span class="sxs-lookup"><span data-stu-id="5082a-111">For instructions, see [Using LoadGen 2007 with MSMQ](../core/using-loadgen-2007-with-msmq.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="5082a-112">L'outil LoadGen n'est pas pris en charge par les ordinateurs 64 bits.</span><span class="sxs-lookup"><span data-stu-id="5082a-112">LoadGen is not supported on 64-bit computers.</span></span> <span data-ttu-id="5082a-113">Vous pouvez l'utiliser à distance sur un ordinateur 32 bits de façon à générer une charge sur un serveur 64 bits.</span><span class="sxs-lookup"><span data-stu-id="5082a-113">You can use LoadGen remotely running on a 32-bit computer to generate load against a 64-bit server.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5082a-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="5082a-114">See Also</span></span>  
 [<span data-ttu-id="5082a-115">Test de surcharge</span><span class="sxs-lookup"><span data-stu-id="5082a-115">Overdrive Load Test</span></span>](../core/overdrive-load-test.md)