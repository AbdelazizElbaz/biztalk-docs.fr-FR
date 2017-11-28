---
title: Utilisation de Services Web | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- SOAP adapters, Web services
- orchestrations, Web services
- Web services, consuming
- Web services, orchestrations
ms.assetid: 803ba623-86e7-479a-a4b6-5b576fee8825
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 528f61910dfc5e2d24a40b0ed29a23fcf85a72bb
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="consuming-web-services"></a><span data-ttu-id="0c58d-102">Utilisation des services web</span><span class="sxs-lookup"><span data-stu-id="0c58d-102">Consuming Web Services</span></span>
<span data-ttu-id="0c58d-103">L'utilisation de services Web vous permet d'ajouter des services Web existants à vos processus d'entreprise.</span><span class="sxs-lookup"><span data-stu-id="0c58d-103">Consuming Web services enables you to add existing Web services to your business process.</span></span> <span data-ttu-id="0c58d-104">Vous pouvez agréger plusieurs services Web au sein d'une seule orchestration.</span><span class="sxs-lookup"><span data-stu-id="0c58d-104">You can aggregate several Web services into a single orchestration.</span></span>  
  
 <span data-ttu-id="0c58d-105">Vous pouvez utiliser (appeler) un service Web depuis une orchestration à l'aide de ports Web.</span><span class="sxs-lookup"><span data-stu-id="0c58d-105">You can consume (call) a Web service from your orchestration by using Web ports.</span></span> <span data-ttu-id="0c58d-106">Pour utiliser un service Web depuis une orchestration, vous devez au préalable créer un port Web puis construire des messages Web.</span><span class="sxs-lookup"><span data-stu-id="0c58d-106">To consume a Web service from an orchestration, you create a Web port and construct Web messages.</span></span>  
  
 <span data-ttu-id="0c58d-107">Vous pouvez utiliser des en-têtes SOAP avec le service Web utilisé, modifier l'URI de celui-ci et définir de manière dynamique l'URI d'un service Web utilisé.</span><span class="sxs-lookup"><span data-stu-id="0c58d-107">You can use SOAP headers with the consumed Web service, change the URI of a consumed Web service, and dynamically set the URI for a consumed Web service.</span></span>  
  
 <span data-ttu-id="0c58d-108">Pour plus d’informations sur la configuration d’un protocole SOAP Gestionnaire de réception, consultez [comment configurer un gestionnaire de réception SOAP](../core/how-to-configure-a-soap-receive-handler.md).</span><span class="sxs-lookup"><span data-stu-id="0c58d-108">For information about configuring a SOAP receive handler, see [How to Configure a SOAP Receive Handler](../core/how-to-configure-a-soap-receive-handler.md).</span></span> <span data-ttu-id="0c58d-109">Pour plus d’informations sur la configuration d’un protocole SOAP emplacement de réception, consultez [comment configurer un emplacement de réception SOAP](../core/how-to-configure-a-soap-receive-location.md).</span><span class="sxs-lookup"><span data-stu-id="0c58d-109">For information about configuring a SOAP receive location, see [How to Configure a SOAP Receive Location](../core/how-to-configure-a-soap-receive-location.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="0c58d-110">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="0c58d-110">In This Section</span></span>  
  
-   [<span data-ttu-id="0c58d-111">Ajout de références Web</span><span class="sxs-lookup"><span data-stu-id="0c58d-111">Adding Web References</span></span>](../core/adding-web-references.md)  
  
-   [<span data-ttu-id="0c58d-112">Construction de Messages Web</span><span class="sxs-lookup"><span data-stu-id="0c58d-112">Constructing Web Messages</span></span>](../core/constructing-web-messages.md)  
  
-   [<span data-ttu-id="0c58d-113">Création de Ports Web</span><span class="sxs-lookup"><span data-stu-id="0c58d-113">Creating Web Ports</span></span>](../core/creating-web-ports.md)  
  
-   [<span data-ttu-id="0c58d-114">Considérations relatives à la consommation de Services Web</span><span class="sxs-lookup"><span data-stu-id="0c58d-114">Considerations When Consuming Web Services</span></span>](../core/considerations-when-consuming-web-services.md)