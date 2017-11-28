---
title: Le Service Web de gestion des exceptions | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: dfe6ebdf-9b92-40c7-93fb-afd6c5f68aaa
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: eb8d8f3439e3b99d118e2932d0a158113ec51be2
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="the-exception-handling-web-service"></a><span data-ttu-id="a7e00-102">Le Service Web de gestion des exceptions</span><span class="sxs-lookup"><span data-stu-id="a7e00-102">The Exception Handling Web Service</span></span>
<span data-ttu-id="a7e00-103">Le service Web de gestion des exceptions accepte un message d’erreur et le publie dans le portail d’Exception ESB.</span><span class="sxs-lookup"><span data-stu-id="a7e00-103">The Exception Handling Web service accepts a fault message and publishes it to the ESB Exception Portal.</span></span> <span data-ttu-id="a7e00-104">Une application cliente peut créer des messages d’exception et les envoyer à l’architecture ESB, où tout gestionnaire configuré pour ce type d’exception ou un gestionnaire générique, peut traiter l’exception.</span><span class="sxs-lookup"><span data-stu-id="a7e00-104">A client application can create exception messages and submit them to the ESB, where any handler configured for that exception type, or a generic handler, can process the exception.</span></span> <span data-ttu-id="a7e00-105">Le principal avantage de ce service est qu’il permet d’entités en dehors d’une application ESB devant être inclus dans le mécanisme de gestion des exceptions de ESB.</span><span class="sxs-lookup"><span data-stu-id="a7e00-105">The major benefit of this service is that it allows entities outside an ESB application to participate in the ESB exception handling mechanism.</span></span>  
  
 <span data-ttu-id="a7e00-106">Le [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] contient deux versions de ce service : une version de ASP.NET (ASMX) et une version de Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="a7e00-106">The [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] contains two versions of this service: an ASP.NET (ASMX) version and a Windows Communication Foundation (WCF) version.</span></span> <span data-ttu-id="a7e00-107">Les noms de service sont **ESB. ExceptionHandlingServices** et **ESB. ExceptionHandlingServices.WCF**, respectivement, et les services exposent une méthode unique :</span><span class="sxs-lookup"><span data-stu-id="a7e00-107">The service names are **ESB.ExceptionHandlingServices** and **ESB.ExceptionHandlingServices.WCF**, respectively, and the services expose a single method:</span></span>  
  
-   <span data-ttu-id="a7e00-108">**SubmitFault**.</span><span class="sxs-lookup"><span data-stu-id="a7e00-108">**SubmitFault**.</span></span> <span data-ttu-id="a7e00-109">Cette méthode prend une instance de la **FaultMessage** classe et n’a aucune valeur de retour.</span><span class="sxs-lookup"><span data-stu-id="a7e00-109">This method takes an instance of the **FaultMessage** class and has no return value.</span></span>  
  
 <span data-ttu-id="a7e00-110">Pour plus d’informations sur la façon dont le mécanisme de gestion des exceptions fonctionnement, consultez [à l’aide de gestion des exceptions ESB](../esb-toolkit/using-esb-exception-management.md).</span><span class="sxs-lookup"><span data-stu-id="a7e00-110">For information about the way the exception handling mechanism works, see [Using ESB Exception Management](../esb-toolkit/using-esb-exception-management.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="a7e00-111">Par défaut, les services Web de la gestion des exceptions ne sont pas configurés pour exiger SSL Secure Sockets Layer () lors de l’accès par les clients.</span><span class="sxs-lookup"><span data-stu-id="a7e00-111">By default, the Exception Handling Web services are not configured to require Secure Sockets Layer (SSL) when accessed by clients.</span></span> <span data-ttu-id="a7e00-112">Vous devez configurer le service afin qu’il exige SSL pour l’accès client et protéger la connexion entre l’ordinateur hôte du service Web des Internet Information Services (IIS) et le serveur qui héberge le **ESBExceptions** base de données à l’aide d’IPSec d’au niveau du réseau et les autorisations de liste (ACL) de contrôle de l’accès approprié au niveau du fichier.</span><span class="sxs-lookup"><span data-stu-id="a7e00-112">You should configure the service so that it requires SSL for client access and protect the connection between the Internet Information Services (IIS) Web service host computer and the server that hosts the **ESBExceptions** database using network-level IPSec and appropriate file-level access control list (ACL) permissions.</span></span>