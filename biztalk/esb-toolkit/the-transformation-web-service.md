---
title: Le Service Web de Transformation | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 788bf4a9-a63b-4fd3-93a2-6e34a1464049
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 5abad7a5a7bae3c76fba58ecd92fc3384df5ca25
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="the-transformation-web-service"></a><span data-ttu-id="ee6e1-102">Le Service Web de Transformation</span><span class="sxs-lookup"><span data-stu-id="ee6e1-102">The Transformation Web Service</span></span>
<span data-ttu-id="ee6e1-103">Le service Web de la Transformation permet à des applications externes envoyer un document à une application d’ESB et transformé à l’aide d’un mappage de Microsoft BizTalk déployé.</span><span class="sxs-lookup"><span data-stu-id="ee6e1-103">The Transformation Web service enables external applications to submit a document to an ESB application and have it transformed using a deployed Microsoft BizTalk map.</span></span> <span data-ttu-id="ee6e1-104">Contrairement à l’agent de la transformation, ce service ne pas achemine les messages via la base de données MessageBox de BizTalk.</span><span class="sxs-lookup"><span data-stu-id="ee6e1-104">Unlike the transformation agent, this service does not route messages through the BizTalk Message Box database.</span></span>  
  
 <span data-ttu-id="ee6e1-105">Le [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] contient deux versions de ce service : une version de ASP.NET (ASMX) et une version de Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="ee6e1-105">The [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] contains two versions of this service: an ASP.NET (ASMX) version and a Windows Communication Foundation (WCF) version.</span></span> <span data-ttu-id="ee6e1-106">Les noms de service sont **ESB. TransformServices** et **ESB. TransformServices.WCF**, respectivement, et les services exposent une méthode unique :</span><span class="sxs-lookup"><span data-stu-id="ee6e1-106">The service names are **ESB.TransformServices** and **ESB.TransformServices.WCF**, respectively, and the services expose a single method:</span></span>  
  
-   <span data-ttu-id="ee6e1-107">**Transformation.**</span><span class="sxs-lookup"><span data-stu-id="ee6e1-107">**Transform.**</span></span> <span data-ttu-id="ee6e1-108">Cette méthode prend comme paramètres une **chaîne** qui contient le message à transformer et un **chaîne** qui contient le nom qualifié complet d’un mappage déployé dans BizTalk.</span><span class="sxs-lookup"><span data-stu-id="ee6e1-108">This method takes as parameters a **String** that contains the message to transform and a **String** that contains the fully qualified name of a map deployed in BizTalk.</span></span> <span data-ttu-id="ee6e1-109">La méthode retourne un **chaîne** qui contient le document transformé.</span><span class="sxs-lookup"><span data-stu-id="ee6e1-109">The method returns a **String** that contains the transformed document.</span></span> <span data-ttu-id="ee6e1-110">L’utilisation de paramètres de chaîne réduit le risque de problèmes d’interopérabilité dans un environnement hétérogène ; Toutefois, gardez à l’esprit que cela est un service Web, donc vous devez éviter de l’utiliser pour transformer des documents volumineux (le Service de Transformation dans BizTalk Server est mieux adapté pour les documents volumineux).</span><span class="sxs-lookup"><span data-stu-id="ee6e1-110">The use of string parameters reduces the risk of interoperability issues in a heterogeneous environment; however, keep in mind that this is a Web service, so you should avoid using it to transform large documents (the Transformation Service in BizTalk is better suited for large documents).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="ee6e1-111">Par défaut, les services Web de la Transformation ne sont pas configurés pour exiger SSL Secure Sockets Layer () lors de l’accès par les clients.</span><span class="sxs-lookup"><span data-stu-id="ee6e1-111">By default, the Transformation Web services are not configured to require Secure Sockets Layer (SSL) when accessed by clients.</span></span> <span data-ttu-id="ee6e1-112">Vous devez configurer le service afin qu’il exige SSL pour l’accès client et protéger la connexion entre l’ordinateur hôte du service Web des Internet Information Services (IIS) et votre serveur BizTalk Server à l’aide d’IPSec d’au niveau du réseau et l’accès approprié au niveau des fichiers contrôler les autorisations de liste (ACL).</span><span class="sxs-lookup"><span data-stu-id="ee6e1-112">You should configure the service so that it requires SSL for client access and protect the connection between the Internet Information Services (IIS) Web service host computer and your BizTalk Server using network-level IPSec and appropriate file-level access control list (ACL) permissions.</span></span>