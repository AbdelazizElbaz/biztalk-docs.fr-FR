---
title: Avant d’installer le Service de la Solution orientée services | Documents Microsoft
ms.custom: ''
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- service solution tutorial, deployment prerequisites
ms.assetid: 865bd21c-e49a-4647-af91-fefee07ee806
caps.latest.revision: 36
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 23f326a6fe028c5b7ea5edf60216c1933eccbdb6
ms.sourcegitcommit: 3fc338e52d5dbca2c3ea1685a2faafc7582fe23a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/01/2017
---
# <a name="before-installing-the-service-oriented-solution"></a><span data-ttu-id="aeecc-102">Avant l'installation de la solution orientée services</span><span class="sxs-lookup"><span data-stu-id="aeecc-102">Before Installing the Service Oriented Solution</span></span>
<span data-ttu-id="aeecc-103">Les composants suivants doivent être disponibles pour installer la version stub de la solution orientée services sur un seul ordinateur :</span><span class="sxs-lookup"><span data-stu-id="aeecc-103">The following prerequisites must be available to install the stub version of the service-oriented solution on a single computer:</span></span>  
  
-   [!INCLUDE[bts2010R2](../includes/bts2010r2-md.md)]<span data-ttu-id="aeecc-104">.</span><span class="sxs-lookup"><span data-stu-id="aeecc-104">.</span></span>  
  
-   <span data-ttu-id="aeecc-105">Logiciels pris en charge pour [!INCLUDE[bts2010R2](../includes/bts2010r2-md.md)].</span><span class="sxs-lookup"><span data-stu-id="aeecc-105">Supported software for [!INCLUDE[bts2010R2](../includes/bts2010r2-md.md)].</span></span>  
  
-   <span data-ttu-id="aeecc-106">Dernière version du client IBM WebSphere MQ pour Windows</span><span class="sxs-lookup"><span data-stu-id="aeecc-106">The latest version of IBM WebSphere MQ Client for Windows</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="aeecc-107">MQSeries Server n'est pas requis pour la version stub de la solution.</span><span class="sxs-lookup"><span data-stu-id="aeecc-107">MQSeries Server is not required for the stub version of the solution.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="aeecc-108">Vous pouvez télécharger le client IBM WebSphere MQ pour Windows depuis le site Web d'IBM.</span><span class="sxs-lookup"><span data-stu-id="aeecc-108">You can download IBM WebSphere MQ Client for Windows from the IBM Web site.</span></span>  
  
 <span data-ttu-id="aeecc-109">Pour installer la version Inline et la version d'adaptateur de la solution orientée services sur un seul ordinateur :</span><span class="sxs-lookup"><span data-stu-id="aeecc-109">For installing the inline and adapter version of the service oriented solution on a single computer:</span></span>  
  
-   [!INCLUDE[bts2010R2](../includes/bts2010r2-md.md)]<span data-ttu-id="aeecc-110">.</span><span class="sxs-lookup"><span data-stu-id="aeecc-110">.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="aeecc-111">Un compte de domaine est requis pour mapper les informations d'identification pour l'authentification unique de l'entreprise.</span><span class="sxs-lookup"><span data-stu-id="aeecc-111">A domain account is required to map credentials for Enterprise Single Sign-On (SSO).</span></span> <span data-ttu-id="aeecc-112">Il est recommandé d'utiliser des comptes de domaine pour le service BizTalk et les comptes du service d'authentification unique de l'entreprise.</span><span class="sxs-lookup"><span data-stu-id="aeecc-112">We recommend using domain accounts for the BizTalk service and for the ENTSSO service accounts.</span></span>  
  
-   <span data-ttu-id="aeecc-113">Logiciels pris en charge pour [!INCLUDE[bts2010R2](../includes/bts2010r2-md.md)].</span><span class="sxs-lookup"><span data-stu-id="aeecc-113">Supported software for [!INCLUDE[bts2010R2](../includes/bts2010r2-md.md)].</span></span>  
  
-   <span data-ttu-id="aeecc-114">MQSeries Server sur l'ordinateur local ou l'accès à l'ordinateur exécutant MQSeries Server.</span><span class="sxs-lookup"><span data-stu-id="aeecc-114">MQSeries Server on the local computer or access to the computer running the MQSeries Server.</span></span> <span data-ttu-id="aeecc-115">Pour la version Inline, les API du client MQSeries doivent être accessibles sur le serveur BizTalk Server exécutant les orchestrations de la solution.</span><span class="sxs-lookup"><span data-stu-id="aeecc-115">For the inline version, MQSeries client APIs must be available on the BizTalk server running the solution’s orchestrations.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="aeecc-116">La version de MQSeries Server doit correspondre à la version requise par l’adaptateur MQSeries de BizTalk Server.</span><span class="sxs-lookup"><span data-stu-id="aeecc-116">The version of MQSeries Server must match the version required by the BizTalk Server MQSeries Adapter.</span></span> <span data-ttu-id="aeecc-117">Ceci peut inclure IBM WebSphere MQ pour Windows Version 5.3 with Fix Pack 10 (CSD10) ou une version ultérieure.</span><span class="sxs-lookup"><span data-stu-id="aeecc-117">This can include IBM WebSphere MQ for Windows Version 5.3 with Fix Pack 10 (CSD10) or later.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="aeecc-118">Lors de l'utilisation de fonctionnalités telles que MQSeries qui effectuent des appels DCOM (Distributed Component Object Model) au serveur, vérifiez que vous n'avez pas de pare-feu de traduction d'adresses réseau (NAT, Network Address Translation) activé.</span><span class="sxs-lookup"><span data-stu-id="aeecc-118">When using features such as MQSeries which make Distributed Component Object Model (DCOM) calls to the server, make sure you do not have a Network Address Translation (NAT)-based firewall enabled.</span></span> <span data-ttu-id="aeecc-119">Le client doit pouvoir accéder au serveur par son adresse IP réelle, or les pare-feu NAT convertissent cette adresse en un élément non reconnu par le client.</span><span class="sxs-lookup"><span data-stu-id="aeecc-119">The client must be able to access the server by its actual IP address, and NAT-based firewalls translate this address to something the client will not recognize.</span></span>  
  
-   <span data-ttu-id="aeecc-120">IBM Mainframe with CICS et Transaction X si vous utilisez une variation de la solution nécessitant un macroordinateur.</span><span class="sxs-lookup"><span data-stu-id="aeecc-120">IBM Mainframe with CICS and Transaction X if you are using a variation of the solution that requires a mainframe.</span></span> <span data-ttu-id="aeecc-121">Dans ce cas, l'application CICS (code COBOL) doit être installée sur le macroordinateur et Microsoft Host Integration Server (HIS) est requis pour accéder au macroordinateur.</span><span class="sxs-lookup"><span data-stu-id="aeecc-121">In this case, the CICS application (COBOL code) must be installed on the mainframe and Microsoft Host Integration Server (HIS) is required to access the mainframe.</span></span>  
  
     <span data-ttu-id="aeecc-122">Si vous ne disposez pas d'un macroordinateur pour la solution, vous pouvez modifier la liaison du port de manière à utiliser le service Web Pending Transactions stub.</span><span class="sxs-lookup"><span data-stu-id="aeecc-122">If you don’t have a mainframe for the solution, you can modify the port binding to use the stub Web service for Pending Transactions.</span></span> <span data-ttu-id="aeecc-123">Le service Web génère des transactions localement pour émuler celles du macroordinateur.</span><span class="sxs-lookup"><span data-stu-id="aeecc-123">The Web service generates transactions locally to emulate the mainframe transactions.</span></span> <span data-ttu-id="aeecc-124">Pour plus d’informations sur la façon de modifier la liaison de port pour le service Web Pending Transactions stub, consultez [comment installer les Versions d’adaptateur de la Solution orientée services Inline](../core/how-to-install-the-inline-and-adapter-versions-of-the-service-oriented-solution.md).</span><span class="sxs-lookup"><span data-stu-id="aeecc-124">For more information about how to modify the port binding for the stub Pending Transactions Web service, see [How to Install the Inline and Adapter Versions of the Service Oriented Solution](../core/how-to-install-the-inline-and-adapter-versions-of-the-service-oriented-solution.md).</span></span>  
  
-   <span data-ttu-id="aeecc-125">Host Integration Server est requis pour se connecter au macroordinateur.</span><span class="sxs-lookup"><span data-stu-id="aeecc-125">Host Integration Server is required to connect to the mainframe.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="aeecc-126">Host Integration Server est inclus dans BizTalk Server.</span><span class="sxs-lookup"><span data-stu-id="aeecc-126">Host Integration Server is included as part of BizTalk Server.</span></span>  
  
-   <span data-ttu-id="aeecc-127">Serveur Web configuré avec un certificat pour les connexions HTTPS.</span><span class="sxs-lookup"><span data-stu-id="aeecc-127">Web server configured with a certificate for HTTPS connections.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="aeecc-128">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="aeecc-128">See Also</span></span>  
 <span data-ttu-id="aeecc-129">[Pour installer la Version Stub de Service de la Solution orientée services](../core/how-to-install-the-stub-version-of-the-service-oriented-solution.md) </span><span class="sxs-lookup"><span data-stu-id="aeecc-129">[How to Install the Stub Version of the Service Oriented Solution](../core/how-to-install-the-stub-version-of-the-service-oriented-solution.md) </span></span>  
 <span data-ttu-id="aeecc-130">[Pour installer le Inline et les Versions du Service d’adaptateur Solution orientée services](../core/how-to-install-the-inline-and-adapter-versions-of-the-service-oriented-solution.md) </span><span class="sxs-lookup"><span data-stu-id="aeecc-130">[How to Install the Inline and Adapter Versions of the Service Oriented Solution](../core/how-to-install-the-inline-and-adapter-versions-of-the-service-oriented-solution.md) </span></span>  
 <span data-ttu-id="aeecc-131">[Pour exécuter le Service Solution orientée services](../core/how-to-run-the-service-oriented-solution.md) </span><span class="sxs-lookup"><span data-stu-id="aeecc-131">[How to Run the Service Oriented Solution](../core/how-to-run-the-service-oriented-solution.md) </span></span>  
 [<span data-ttu-id="aeecc-132">Configuration de l’ordinateur de développement pour la solution orientée services</span><span class="sxs-lookup"><span data-stu-id="aeecc-132">Developer Machine Setup for the Service Oriented Solution</span></span>](../core/developer-machine-setup-for-the-service-oriented-solution.md)