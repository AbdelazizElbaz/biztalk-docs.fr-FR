---
title: "L’adaptateur TIBCO Enterprise Message Service | Documents Microsoft"
description: "Installer, parcourez les didacticiels, découvrez l’architecture, utiliser la sécurité de l’authentification unique, créer vos applications, importez le fichier de liaison et ajouter la gestion des exceptions lors de l’utilisation de l’adaptateur BizTalk pour TIBCO EMS dans BizTalk Server"
ms.custom: 
ms.date: 10/23/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 362556d2-295c-4496-a429-ad7ecc44db76
caps.latest.revision: "15"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 988c7993dd407cb90e267e713a3195f897de9ceb
ms.sourcegitcommit: dd7c54feab783ae2f8fe75873363fe9ffc77cd66
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/07/2017
---
# <a name="tibco-enterprise-message-service-adapter"></a><span data-ttu-id="c2622-103">Adaptateur TIBCO Enterprise Message Service</span><span class="sxs-lookup"><span data-stu-id="c2622-103">TIBCO Enterprise Message Service Adapter</span></span>
<span data-ttu-id="c2622-104">L’adaptateur Microsoft BizTalk pour TIBCO Enterprise Message Service vous permet de publier et s’abonner à des files d’attente et aux rubriques gérées par TIBCO EMS à l’aide de btsBizTalkServerNoVersion.</span><span class="sxs-lookup"><span data-stu-id="c2622-104">Microsoft BizTalk Adapter for TIBCO Enterprise Message Service enables you to publish and subscribe to queues and topics managed by TIBCO EMS using btsBizTalkServerNoVersion.</span></span>  <span data-ttu-id="c2622-105">Les sections suivantes décrivent la prise en main, créer des applications et bien plus encore.</span><span class="sxs-lookup"><span data-stu-id="c2622-105">The following sections discuss getting started, creating applications, and more.</span></span>  
   
## <a name="get-started"></a><span data-ttu-id="c2622-106">Prise en main</span><span class="sxs-lookup"><span data-stu-id="c2622-106">Get started</span></span>
<span data-ttu-id="c2622-107">[Prise en main](../core/getting-started-with-biztalk-adapter-for-tibco-enterprise-message-service.md) décrit les fonctionnalités de la carte, l’installation de l’adaptateur et inclut des didacticiels.</span><span class="sxs-lookup"><span data-stu-id="c2622-107">[Get started](../core/getting-started-with-biztalk-adapter-for-tibco-enterprise-message-service.md) describes adapter features, installing the adapter, and includes some tutorials.</span></span>

## <a name="architecture"></a><span data-ttu-id="c2622-108">Architecture</span><span class="sxs-lookup"><span data-stu-id="c2622-108">Architecture</span></span>
<span data-ttu-id="c2622-109">[Architecture](../core/planning-and-architecture16.md) décrit comment l’adaptateur fonctionne, fournit quelques exigences supplémentaires et répertorie les restrictions.</span><span class="sxs-lookup"><span data-stu-id="c2622-109">[Architecture](../core/planning-and-architecture16.md) describes how the adapter works, provides some additional requirements, and lists any limitations.</span></span>

## <a name="security"></a><span data-ttu-id="c2622-110">Sécurité</span><span class="sxs-lookup"><span data-stu-id="c2622-110">Security</span></span>
<span data-ttu-id="c2622-111">[Sécurité](../core/security-in-biztalk-adapter-for-tibco-ems.md) implique l’utilisation d’Enterprise Single Sign-on (SSO) dans BizTalk Server pour sécuriser vos applications qui utilisent cet adaptateur.</span><span class="sxs-lookup"><span data-stu-id="c2622-111">[Security](../core/security-in-biztalk-adapter-for-tibco-ems.md) involves using Enterprise Single Sign-on (SSO) within BizTalk Serer to secure your applications that use this adapter.</span></span>

## <a name="create-the-artifacts"></a><span data-ttu-id="c2622-112">Créer les artefacts</span><span class="sxs-lookup"><span data-stu-id="c2622-112">Create the artifacts</span></span>
<span data-ttu-id="c2622-113">[Créer les artefacts de l’application](../core/developing-applications5.md) répertorie les étapes pour générer des schémas, de créer l’envoi et de recevoir des artefacts utilisés par cet adaptateur et comment utiliser les propriétés de contexte d’une orchestration.</span><span class="sxs-lookup"><span data-stu-id="c2622-113">[Create the application artifacts](../core/developing-applications5.md) lists the steps to generate schemas, create the send and receive artifacts used by this adapter, and how to use the message context properties within an orchestration.</span></span>

## <a name="import-apps"></a><span data-ttu-id="c2622-114">Importer des applications</span><span class="sxs-lookup"><span data-stu-id="c2622-114">Import apps</span></span>
<span data-ttu-id="c2622-115">[Importer des liaisons](../core/deploying-biztalk-adapter-for-tibco-enterprise-message-service.md) explique comment importer le fichier de liaison de votre application dans la console Administration de BizTalk et dépasse les limitations.</span><span class="sxs-lookup"><span data-stu-id="c2622-115">[Import bindings](../core/deploying-biztalk-adapter-for-tibco-enterprise-message-service.md) discusses how to import your application binding file into BizTalk Administration, and goes over any limitations.</span></span> 

## <a name="handle-exceptions"></a><span data-ttu-id="c2622-116">Gestion des exceptions</span><span class="sxs-lookup"><span data-stu-id="c2622-116">Handle exceptions</span></span>
<span data-ttu-id="c2622-117">[Utiliser des exceptions BizTalk Server](../core/using-biztalk-server-exception-handling5.md) fournit des conseils sur l’ajout de formes différentes à votre orchestration pour gérer les exceptions.</span><span class="sxs-lookup"><span data-stu-id="c2622-117">[Use BizTalk Server Exception Handling](../core/using-biztalk-server-exception-handling5.md) provides guidance on adding different shapes to your orchestration to handle exceptions.</span></span>

## <a name="troubleshooting"></a><span data-ttu-id="c2622-118">Dépannage</span><span class="sxs-lookup"><span data-stu-id="c2622-118">Troubleshooting</span></span>
 <span data-ttu-id="c2622-119">[Résolution des problèmes](../core/troubleshooting-tibco-enterprise-message-service.md) décrit quelques erreurs courantes et les situations et traite le suivi d’événements pour Windows.</span><span class="sxs-lookup"><span data-stu-id="c2622-119">[Troubleshooting](../core/troubleshooting-tibco-enterprise-message-service.md) describes some common errors and situations, and discusses Event Tracing for Windows.</span></span>