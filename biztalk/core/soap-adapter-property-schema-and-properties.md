---
title: "Schéma de propriété de l’adaptateur SOAP et les propriétés | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- ProxyUsername property [SOAP adapters]
- ClientConnectionTimeout property [SOAP adapters]
- SOAP adapters, properties
- ProxyAddress property [SOAP adapters]
- UserDefined property [SOAP adapters]
- AssemblyName property [SOAP adapters]
- ClientCertificate property [SOAP adapters]
- AffiliateApplicationName property [SOAP adapters]
- schemas, SOAP adapters
- AuthenticationScheme property [SOAP adapters]
- UserName property, SOAP adapters
- UseProxy property [SOAP adapters]
- Password property [SOAP adapters]
- configuring [SOAP adapters], schemas
- UnknownHeaders property [SOAP adapters]
- configuring [SOAP adapters], properties
- UseSoap12 property [SOAP adapters]
- UseHandlerSetting property [SOAP adapters]
- SOAP adapters, schemas
- ProxyPassword property [SOAP adapters]
- UseSSO property [SOAP adapters]
- MethodName property [SOAP adapters]
- ProxyPort property [SOAP adapters]
ms.assetid: b471cf4b-2d87-4aa2-ae4a-f48517fd4c94
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 7a24a9ccfc3a07abe925761fe2d6886646981be9
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="soap-adapter-property-schema-and-properties"></a><span data-ttu-id="7cde3-102">Propriétés et schéma de propriété de l'adaptateur SOAP</span><span class="sxs-lookup"><span data-stu-id="7cde3-102">SOAP Adapter Property Schema and Properties</span></span>
<span data-ttu-id="7cde3-103">Le tableau suivant répertorie les propriétés du schéma de propriété de l'adaptateur SOAP.</span><span class="sxs-lookup"><span data-stu-id="7cde3-103">The following table lists the properties in the SOAP adapter property schema.</span></span>  
  
 <span data-ttu-id="7cde3-104">**Namespace :** http://schemas.microsoft.com/BizTalk/2003/soap-properties</span><span class="sxs-lookup"><span data-stu-id="7cde3-104">**Namespace:** http://schemas.microsoft.com/BizTalk/2003/soap-properties</span></span>  
  
|<span data-ttu-id="7cde3-105">Nom</span><span class="sxs-lookup"><span data-stu-id="7cde3-105">Name</span></span>|<span data-ttu-id="7cde3-106">Type</span><span class="sxs-lookup"><span data-stu-id="7cde3-106">Type</span></span>|<span data-ttu-id="7cde3-107"> Description</span><span class="sxs-lookup"><span data-stu-id="7cde3-107">Description</span></span>|  
|----------|----------|-----------------|  
|<span data-ttu-id="7cde3-108">**Nom de l’assembly**</span><span class="sxs-lookup"><span data-stu-id="7cde3-108">**AssemblyName**</span></span>|<span data-ttu-id="7cde3-109">xs:string</span><span class="sxs-lookup"><span data-stu-id="7cde3-109">xs:string</span></span>|<span data-ttu-id="7cde3-110">Identifie le type .NET et l'assembly qui doivent être chargés et exécutés.</span><span class="sxs-lookup"><span data-stu-id="7cde3-110">Identifies the .NET type and assembly to be loaded and executed.</span></span>|  
|<span data-ttu-id="7cde3-111">**MethodName**</span><span class="sxs-lookup"><span data-stu-id="7cde3-111">**MethodName**</span></span>|<span data-ttu-id="7cde3-112">xs:string</span><span class="sxs-lookup"><span data-stu-id="7cde3-112">xs:string</span></span>|<span data-ttu-id="7cde3-113">Identifie la méthode cible sur l'assembly .NET à appeler.</span><span class="sxs-lookup"><span data-stu-id="7cde3-113">Identifies the target method on the .NET assembly that is to be invoked.</span></span>|  
|<span data-ttu-id="7cde3-114">**Nom d’utilisateur**</span><span class="sxs-lookup"><span data-stu-id="7cde3-114">**Username**</span></span>|<span data-ttu-id="7cde3-115">xs:string</span><span class="sxs-lookup"><span data-stu-id="7cde3-115">xs:string</span></span>|<span data-ttu-id="7cde3-116">Nom d'utilisateur utilisé pour l'authentification sur le serveur.</span><span class="sxs-lookup"><span data-stu-id="7cde3-116">User name to use for authentication with the server.</span></span>|  
|<span data-ttu-id="7cde3-117">**Mot de passe**</span><span class="sxs-lookup"><span data-stu-id="7cde3-117">**Password**</span></span>|<span data-ttu-id="7cde3-118">xs:string</span><span class="sxs-lookup"><span data-stu-id="7cde3-118">xs:string</span></span>|<span data-ttu-id="7cde3-119">Mot de passe de l'utilisateur utilisé pour l'authentification sur le serveur.</span><span class="sxs-lookup"><span data-stu-id="7cde3-119">User password to use for authentication with the server.</span></span>|  
|<span data-ttu-id="7cde3-120">**ClientCertificate**</span><span class="sxs-lookup"><span data-stu-id="7cde3-120">**ClientCertificate**</span></span>|<span data-ttu-id="7cde3-121">xs:string</span><span class="sxs-lookup"><span data-stu-id="7cde3-121">xs:string</span></span>|<span data-ttu-id="7cde3-122">Empreinte du certificat SSL client.</span><span class="sxs-lookup"><span data-stu-id="7cde3-122">Thumbprint of the client SSL certificate.</span></span>|  
|<span data-ttu-id="7cde3-123">**UseProxy**</span><span class="sxs-lookup"><span data-stu-id="7cde3-123">**UseProxy**</span></span>|<span data-ttu-id="7cde3-124">xs:Boolean</span><span class="sxs-lookup"><span data-stu-id="7cde3-124">xs:Boolean</span></span>|<span data-ttu-id="7cde3-125">Indique si l'adaptateur SOAP fait appel ou non à un serveur proxy.</span><span class="sxs-lookup"><span data-stu-id="7cde3-125">Specifies whether the SOAP adapter uses a proxy server.</span></span>|  
|<span data-ttu-id="7cde3-126">**ProxyAddress**</span><span class="sxs-lookup"><span data-stu-id="7cde3-126">**ProxyAddress**</span></span>|<span data-ttu-id="7cde3-127">xs:string</span><span class="sxs-lookup"><span data-stu-id="7cde3-127">xs:string</span></span>|<span data-ttu-id="7cde3-128">Indique l'adresse du serveur proxy.</span><span class="sxs-lookup"><span data-stu-id="7cde3-128">Specifies the proxy server address.</span></span>|  
|<span data-ttu-id="7cde3-129">**ProxyPort**</span><span class="sxs-lookup"><span data-stu-id="7cde3-129">**ProxyPort**</span></span>|<span data-ttu-id="7cde3-130">xs:int</span><span class="sxs-lookup"><span data-stu-id="7cde3-130">xs:int</span></span>|<span data-ttu-id="7cde3-131">Spécifie le port du serveur proxy.</span><span class="sxs-lookup"><span data-stu-id="7cde3-131">Specifies the proxy server port.</span></span>|  
|<span data-ttu-id="7cde3-132">**ProxyUsername**</span><span class="sxs-lookup"><span data-stu-id="7cde3-132">**ProxyUsername**</span></span>|<span data-ttu-id="7cde3-133">xs:string</span><span class="sxs-lookup"><span data-stu-id="7cde3-133">xs:string</span></span>|<span data-ttu-id="7cde3-134">Indique le nom d'utilisateur utilisé pour l'authentification sur le serveur proxy.</span><span class="sxs-lookup"><span data-stu-id="7cde3-134">Specifies the user name for authentication with the proxy server.</span></span>|  
|<span data-ttu-id="7cde3-135">**ProxyPassword**</span><span class="sxs-lookup"><span data-stu-id="7cde3-135">**ProxyPassword**</span></span>|<span data-ttu-id="7cde3-136">xs:string</span><span class="sxs-lookup"><span data-stu-id="7cde3-136">xs:string</span></span>|<span data-ttu-id="7cde3-137">Indique le mot de passe utilisé pour l'authentification sur le serveur proxy.</span><span class="sxs-lookup"><span data-stu-id="7cde3-137">Specifies the user password for authentication with the proxy server.</span></span>|  
|<span data-ttu-id="7cde3-138">**UnknownHeaders**</span><span class="sxs-lookup"><span data-stu-id="7cde3-138">**UnknownHeaders**</span></span>|<span data-ttu-id="7cde3-139">xs:string</span><span class="sxs-lookup"><span data-stu-id="7cde3-139">xs:string</span></span>|<span data-ttu-id="7cde3-140">Indique la liste sérialisée des en-têtes SOAP inconnus.</span><span class="sxs-lookup"><span data-stu-id="7cde3-140">Specifies the serialized list of unknown SOAP headers.</span></span>|  
|<span data-ttu-id="7cde3-141">**AffiliateApplicationName**</span><span class="sxs-lookup"><span data-stu-id="7cde3-141">**AffiliateApplicationName**</span></span>|<span data-ttu-id="7cde3-142">xs:string</span><span class="sxs-lookup"><span data-stu-id="7cde3-142">xs:string</span></span>|<span data-ttu-id="7cde3-143">Définit le nom de l'application associée à utiliser pour l'authentification unique.</span><span class="sxs-lookup"><span data-stu-id="7cde3-143">Defines the name of the affiliate application to use for SSO.</span></span>|  
|<span data-ttu-id="7cde3-144">**AuthenticationScheme**</span><span class="sxs-lookup"><span data-stu-id="7cde3-144">**AuthenticationScheme**</span></span>|<span data-ttu-id="7cde3-145">xs:string</span><span class="sxs-lookup"><span data-stu-id="7cde3-145">xs:string</span></span>|<span data-ttu-id="7cde3-146">Indique le type d'authentification à utiliser avec le serveur de destination.</span><span class="sxs-lookup"><span data-stu-id="7cde3-146">Specifies the type of authentication to use with the destination server.</span></span>|  
|<span data-ttu-id="7cde3-147">**UseSSO**</span><span class="sxs-lookup"><span data-stu-id="7cde3-147">**UseSSO**</span></span>|<span data-ttu-id="7cde3-148">xs:boolean</span><span class="sxs-lookup"><span data-stu-id="7cde3-148">xs:boolean</span></span>|<span data-ttu-id="7cde3-149">Indique si l'adaptateur SOAP utilise l'authentification unique pour le port d'envoi.</span><span class="sxs-lookup"><span data-stu-id="7cde3-149">Specifies whether the SOAP adapter uses SSO for the send port.</span></span>|  
|<span data-ttu-id="7cde3-150">**UseHandlerSetting**</span><span class="sxs-lookup"><span data-stu-id="7cde3-150">**UseHandlerSetting**</span></span>|<span data-ttu-id="7cde3-151">xs:boolean</span><span class="sxs-lookup"><span data-stu-id="7cde3-151">xs:boolean</span></span>|<span data-ttu-id="7cde3-152">Indique si le port d'envoi SOAP utilise la configuration de proxy pour le gestionnaire.</span><span class="sxs-lookup"><span data-stu-id="7cde3-152">Specifies whether the SOAP send port uses the proxy configuration for the handler.</span></span>|  
|<span data-ttu-id="7cde3-153">**ClientConnectionTimeout**</span><span class="sxs-lookup"><span data-stu-id="7cde3-153">**ClientConnectionTimeout**</span></span>|<span data-ttu-id="7cde3-154">xs:int</span><span class="sxs-lookup"><span data-stu-id="7cde3-154">xs:int</span></span>|<span data-ttu-id="7cde3-155">Indique le délai d'attente d'une réponse du serveur.</span><span class="sxs-lookup"><span data-stu-id="7cde3-155">Specifies the time-out period of waiting for a response from the server.</span></span> <span data-ttu-id="7cde3-156">Si la valeur zéro (0), le système calcule le délai d’attente en fonction de la taille du message de demande.</span><span class="sxs-lookup"><span data-stu-id="7cde3-156">If set to zero (0), the system will calculate the time-out based on the request message size.</span></span>|  
|<span data-ttu-id="7cde3-157">**Défini par l’utilisateur**</span><span class="sxs-lookup"><span data-stu-id="7cde3-157">**UserDefined**</span></span>|<span data-ttu-id="7cde3-158">xs:string</span><span class="sxs-lookup"><span data-stu-id="7cde3-158">xs:string</span></span>|<span data-ttu-id="7cde3-159">Spécifie les classes définies par l'utilisateur.</span><span class="sxs-lookup"><span data-stu-id="7cde3-159">Defines user-defined classes.</span></span>|  
|<span data-ttu-id="7cde3-160">**UseSoap12**</span><span class="sxs-lookup"><span data-stu-id="7cde3-160">**UseSoap12**</span></span>|<span data-ttu-id="7cde3-161">xs:boolean</span><span class="sxs-lookup"><span data-stu-id="7cde3-161">xs:boolean</span></span>|<span data-ttu-id="7cde3-162">Indique s'il faut générer un code proxy qui prend en charge le protocole SOAP 1.2.</span><span class="sxs-lookup"><span data-stu-id="7cde3-162">Specifies whether to generate proxy code that supports the SOAP 1.2 protocol.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="7cde3-163">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="7cde3-163">See Also</span></span>  
 [<span data-ttu-id="7cde3-164">Configuration de l’adaptateur SOAP</span><span class="sxs-lookup"><span data-stu-id="7cde3-164">Configuring the SOAP Adapter</span></span>](../core/configuring-the-soap-adapter.md)