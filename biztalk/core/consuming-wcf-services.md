---
title: Utilisation des Services WCF | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- consuming, WCF services
- WCF services, consuming
ms.assetid: ca6c0514-c1df-43ad-8f02-df117271b0b5
caps.latest.revision: "11"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: c3fc0764295cbbc793b07757691e1f0c730a4049
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="consuming-wcf-services"></a><span data-ttu-id="11273-102">Utilisation des services WCF</span><span class="sxs-lookup"><span data-stu-id="11273-102">Consuming WCF Services</span></span>
<span data-ttu-id="11273-103">L'utilisation de services WCF vous permet d'ajouter des services WCF existants à vos processus d'entreprise.</span><span class="sxs-lookup"><span data-stu-id="11273-103">Consuming WCF services enables you to add existing WCF services to your business process.</span></span> <span data-ttu-id="11273-104">Vous pouvez agréger plusieurs services WCF au sein d'une seule orchestration.</span><span class="sxs-lookup"><span data-stu-id="11273-104">You can aggregate several WCF services into a single orchestration.</span></span>  
  
 <span data-ttu-id="11273-105">Vous pouvez utiliser (appeler) un service WCF depuis votre orchestration à l'aide de l'Assistant Consommation de service WCF BizTalk.</span><span class="sxs-lookup"><span data-stu-id="11273-105">You can consume (call) a WCF service from your orchestration by using the BizTalk WCF Service Consuming Wizard.</span></span> <span data-ttu-id="11273-106">Celui-ci crée les types de ports et de messages nécessaires à l'utilisation des services WCF.</span><span class="sxs-lookup"><span data-stu-id="11273-106">The BizTalk WCF Service Consuming Wizard creates port types and message types necessary for consuming WCF services.</span></span> <span data-ttu-id="11273-107">L'Assistant Consommation de service WCF BizTalk crée deux fichiers de liaison qui peuvent être importés à l'aide de l'outil de ligne de commande de développement ou de l'Assistant pour configurer les ports d'envoi avec les adaptateurs WCF de la liaison fournie par le système et l'adaptateur WCF-Custom.</span><span class="sxs-lookup"><span data-stu-id="11273-107">The BizTalk WCF Service Consuming Wizard also creates two binding files that can be imported by the development command-line tool or wizard to configure the send ports with the system-provided binding WCF adapters and the WCF-Custom adapter.</span></span> <span data-ttu-id="11273-108">Il vous permet d'utiliser les en-têtes SOAP avec un service WCF consommé, de modifier l'URI d'un service WCF consommé et de définir de manière dynamique le service WCF pour un service Web consommé.</span><span class="sxs-lookup"><span data-stu-id="11273-108">The wizard allows you to use SOAP headers with a consumed WCF service, change the URI of a consumed WCF service, and dynamically set the WCF for a consumed Web service.</span></span> <span data-ttu-id="11273-109">Les adaptateurs d'envoi WCF utilisent les services WCF et les emplacements de réception WCF publient les services WCF.</span><span class="sxs-lookup"><span data-stu-id="11273-109">WCF send adapters consume WCF services and WCF receive locations publish WCF services.</span></span>  
  
 <span data-ttu-id="11273-110">Les adaptateurs d’envoi WCF BizTalk incluent cinq adaptateurs d’envoi physiques qui représentent les liaisons prédéfinies WCF **BasicHttpBinding**, **WsHttpBinding**, **NetTcpBinding**, **NetNamedPipeBinding**, et **NetMsmqBinding**.</span><span class="sxs-lookup"><span data-stu-id="11273-110">The BizTalk WCF send adapters include five physical send adapters that represent the WCF predefined bindings **BasicHttpBinding**, **WsHttpBinding**, **NetTcpBinding**, **NetNamedPipeBinding**, and **NetMsmqBinding**.</span></span> <span data-ttu-id="11273-111">Les adaptateurs WCF BizTalk incluent également les adaptateurs personnalisés qui vous permettent de configurer librement les informations de liaison et de comportement WCF d'un port d'envoi.</span><span class="sxs-lookup"><span data-stu-id="11273-111">The BizTalk WCF adapters also include the custom adapters that enable you to freely configure WCF binding and behavior information for a send port.</span></span> <span data-ttu-id="11273-112">Pour plus d’informations sur la façon de configurer un gestionnaire d’envoi WCF et le port d’envoi, consultez les rubriques de procédures pour chaque adaptateur WCF dans [adaptateurs WCF](../core/wcf-adapters.md).</span><span class="sxs-lookup"><span data-stu-id="11273-112">For more information about how to configure a WCF send handler and send port, see how-to topics for each WCF adapter in [WCF Adapters](../core/wcf-adapters.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="11273-113">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="11273-113">In This Section</span></span>  
  
-   [<span data-ttu-id="11273-114">Considérations relatives à l’utilisation des Services WCF avec WCF des adaptateurs d’envoi</span><span class="sxs-lookup"><span data-stu-id="11273-114">Considerations When Consuming WCF Services with the WCF Send Adapters</span></span>](../core/considerations-when-consuming-wcf-services-with-the-wcf-send-adapters.md)  
  
-   [<span data-ttu-id="11273-115">En-têtes SOAP avec les Services WCF utilisés</span><span class="sxs-lookup"><span data-stu-id="11273-115">SOAP Headers with Consumed WCF Services</span></span>](../core/soap-headers-with-consumed-wcf-services.md)  
  
-   [<span data-ttu-id="11273-116">Configuration des Ports d’envoi dynamiques à l’aide des propriétés de contexte des adaptateurs WCF</span><span class="sxs-lookup"><span data-stu-id="11273-116">Configuring Dynamic Send Ports Using WCF Adapters Context Properties</span></span>](../core/configuring-dynamic-send-ports-using-wcf-adapters-context-properties.md)  
  
-   [<span data-ttu-id="11273-117">Comment utiliser l’Assistant consommation de Service WCF BizTalk pour utiliser un Service WCF</span><span class="sxs-lookup"><span data-stu-id="11273-117">How to Use the BizTalk WCF Service Consuming Wizard to Consume a WCF Service</span></span>](../core/how-to-use-the-biztalk-wcf-service-consuming-wizard-to-consume-a-wcf-service.md)  
  
-   [<span data-ttu-id="11273-118">Comment gérer les contrats d’erreurs typées dans les Orchestrations</span><span class="sxs-lookup"><span data-stu-id="11273-118">How to Handle Typed Fault Contracts in Orchestrations</span></span>](../core/how-to-handle-typed-fault-contracts-in-orchestrations.md)  
  
-   [<span data-ttu-id="11273-119">Spécification des Actions SOAP pour WCF des adaptateurs d’envoi</span><span class="sxs-lookup"><span data-stu-id="11273-119">Specifying SOAP Actions for WCF Send Adapters</span></span>](../core/specifying-soap-actions-for-wcf-send-adapters.md)