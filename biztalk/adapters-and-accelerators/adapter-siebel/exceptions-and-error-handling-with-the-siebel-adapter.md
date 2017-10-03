---
title: "Exceptions et gestion des erreurs avec l’adaptateur Siebel | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- error handling, troubleshooting
- exceptions, troubleshooting
- troubleshooting, exceptions and error handling
ms.assetid: d46e908f-0715-43e2-879b-f5d0beb9bc64
caps.latest.revision: "5"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 743e2a0f03e35282c24a506ff37e9d774f0b7505
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="exceptions-and-error-handling-with-the-siebel-adapter"></a><span data-ttu-id="fa8db-102">Exceptions et gestion des erreurs avec l’adaptateur Siebel</span><span class="sxs-lookup"><span data-stu-id="fa8db-102">Exceptions and Error Handling with the Siebel adapter</span></span>
## <a name="exception-list"></a><span data-ttu-id="fa8db-103">Liste des exceptions</span><span class="sxs-lookup"><span data-stu-id="fa8db-103">Exception list</span></span>
<span data-ttu-id="fa8db-104">Les exceptions levées par le [!INCLUDE[adaptersiebel](../../includes/adaptersiebel-md.md)].</span><span class="sxs-lookup"><span data-stu-id="fa8db-104">The exceptions thrown by the [!INCLUDE[adaptersiebel](../../includes/adaptersiebel-md.md)].</span></span> <span data-ttu-id="fa8db-105">Il peuvent contenir :</span><span class="sxs-lookup"><span data-stu-id="fa8db-105">These can contain:</span></span>  
  
-   <span data-ttu-id="fa8db-106">Une exception interne qui est une exception levée système par le .NET Framework</span><span class="sxs-lookup"><span data-stu-id="fa8db-106">An inner exception, which is a system exception that the .NET Framework throws</span></span>  
  
-   <span data-ttu-id="fa8db-107">Une exception levée LOB par la bibliothèque cliente LOB.</span><span class="sxs-lookup"><span data-stu-id="fa8db-107">An LOB exception that the LOB client library throws.</span></span>  
  
 <span data-ttu-id="fa8db-108">Pour plus d’informations sur l’exception interne, reportez-vous à la documentation de .NET Framework ou Siebel respectif.</span><span class="sxs-lookup"><span data-stu-id="fa8db-108">For more information about the inner exception, refer to the respective .NET Framework or Siebel documentation.</span></span> <span data-ttu-id="fa8db-109">L’exception contient également un message d’erreur détaillé qui vous aide à résoudre le problème.</span><span class="sxs-lookup"><span data-stu-id="fa8db-109">The exception also contains a detailed error message that helps in resolving the problem.</span></span> <span data-ttu-id="fa8db-110">Notez que la liste des exceptions mentionnées ici n’est pas complet.</span><span class="sxs-lookup"><span data-stu-id="fa8db-110">Note that the list of exceptions mentioned here is not comprehensive.</span></span>  
  
|<span data-ttu-id="fa8db-111">Exception</span><span class="sxs-lookup"><span data-stu-id="fa8db-111">Exception</span></span>|<span data-ttu-id="fa8db-112">Erreur de Cause possible/Description</span><span class="sxs-lookup"><span data-stu-id="fa8db-112">Possible Cause/Error Description</span></span>|  
|---------------|---------------------------------------|  
|<span data-ttu-id="fa8db-113">ConnectionException</span><span class="sxs-lookup"><span data-stu-id="fa8db-113">ConnectionException</span></span>|<span data-ttu-id="fa8db-114">L’adaptateur lève cette exception s’il est impossible d’établir une connexion ou fermez une connexion existante à un système Siebel.</span><span class="sxs-lookup"><span data-stu-id="fa8db-114">The adapter throws this exception if it is unable to establish a connection or close an existing connection to a Siebel system.</span></span>|  
|<span data-ttu-id="fa8db-115">CredentialsException</span><span class="sxs-lookup"><span data-stu-id="fa8db-115">CredentialsException</span></span>|<span data-ttu-id="fa8db-116">L’adaptateur lève cette exception si le client de l’adaptateur ne spécifie pas un nom d’utilisateur ou le mot de passe pour se connecter à un système Siebel.</span><span class="sxs-lookup"><span data-stu-id="fa8db-116">The adapter throws this exception if the adapter client does not specify a user name or password to connect to a Siebel system.</span></span>|  
|<span data-ttu-id="fa8db-117">MetadataException</span><span class="sxs-lookup"><span data-stu-id="fa8db-117">MetadataException</span></span>|<span data-ttu-id="fa8db-118">L’adaptateur lève cette exception en cas d’échec récupérer des métadonnées pour les artefacts de Siebel.</span><span class="sxs-lookup"><span data-stu-id="fa8db-118">The adapter throws this exception if it fails to retrieve metadata for Siebel artifacts.</span></span>|  
|<span data-ttu-id="fa8db-119">XmlReaderParsingException</span><span class="sxs-lookup"><span data-stu-id="fa8db-119">XmlReaderParsingException</span></span>|<span data-ttu-id="fa8db-120">L’adaptateur lève cette exception si les informations d’entrée fournies par les clients de la carte pour appeler une opération dans le système Siebel, est incomplète ou incorrecte.</span><span class="sxs-lookup"><span data-stu-id="fa8db-120">The adapter throws this exception if the input information provided by the adapter clients to invoke an operation in the Siebel system, is either incomplete or incorrect.</span></span>|  
|<span data-ttu-id="fa8db-121">XmlReaderGenerationException</span><span class="sxs-lookup"><span data-stu-id="fa8db-121">XmlReaderGenerationException</span></span>|<span data-ttu-id="fa8db-122">L’adaptateur lève cette exception s’il est impossible de générer la sortie d’une opération exécutée dans un système Siebel.</span><span class="sxs-lookup"><span data-stu-id="fa8db-122">The adapter throws this exception if it is unable to generate output for an operation executed in a Siebel system.</span></span>|  
|<span data-ttu-id="fa8db-123">TargetSystemException</span><span class="sxs-lookup"><span data-stu-id="fa8db-123">TargetSystemException</span></span>|<span data-ttu-id="fa8db-124">L’adaptateur lève cette exception si l’API COM Siebel, que l’adaptateur utilise pour interagir avec le système Siebel, lève une exception.</span><span class="sxs-lookup"><span data-stu-id="fa8db-124">The adapter throws this exception if the Siebel COM API, which the adapter uses to interface with the Siebel system, throws an exception.</span></span> <span data-ttu-id="fa8db-125">L’exception interne contient l’exception levée par l’API de COM Siebel.</span><span class="sxs-lookup"><span data-stu-id="fa8db-125">The inner exception contains the exception thrown by the Siebel COM API.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="fa8db-126">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="fa8db-126">See Also</span></span>  
 <span data-ttu-id="fa8db-127">[Comprendre l’adaptateur BizTalk pour Siebel eBusiness Applications](../../adapters-and-accelerators/adapter-siebel/understand-biztalk-adapter-for-siebel-ebusiness-applications.md) </span><span class="sxs-lookup"><span data-stu-id="fa8db-127">[Understand BizTalk Adapter for Siebel eBusiness Applications](../../adapters-and-accelerators/adapter-siebel/understand-biztalk-adapter-for-siebel-ebusiness-applications.md) </span></span>  
[<span data-ttu-id="fa8db-128">Dépanner l’adaptateur Siebel</span><span class="sxs-lookup"><span data-stu-id="fa8db-128">Troubleshoot the Siebel adapter</span></span>](../../adapters-and-accelerators/adapter-siebel/troubleshoot-the-siebel-adapter.md)