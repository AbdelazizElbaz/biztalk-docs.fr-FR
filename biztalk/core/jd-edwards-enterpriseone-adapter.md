---
title: Adaptateur JD Edwards EnterpriseOne | Documents Microsoft
description: "Installer, parcourez les didacticiels, découvrez l’architecture, utiliser la sécurité de l’authentification unique, créer vos applications, importez le fichier de liaison et ajouter la gestion des exceptions lors de l’utilisation de l’adaptateur BizTalk pour J.D. Edwards EnterpriseOne dans BizTalk Server"
ms.custom: 
ms.date: 10/18/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 97f0f87a-59c3-4503-8da6-d6967dab820a
caps.latest.revision: "12"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 9e1d82cafd20e8c86fbbf7daa42304ecb95c9aee
ms.sourcegitcommit: dd7c54feab783ae2f8fe75873363fe9ffc77cd66
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/07/2017
---
# <a name="jd-edwards-enterpriseone-adapter"></a><span data-ttu-id="7e7e9-104">Adaptateur JD Edwards EnterpriseOne</span><span class="sxs-lookup"><span data-stu-id="7e7e9-104">JD Edwards EnterpriseOne Adapter</span></span>
<span data-ttu-id="7e7e9-105">Adaptateur Microsoft BizTalk pour J.D.</span><span class="sxs-lookup"><span data-stu-id="7e7e9-105">Microsoft BizTalk Adapter for J.D.</span></span> <span data-ttu-id="7e7e9-106">Edwards EnterpriseOne permet d’utiliser les fonctions commerciales de JD Edwards EnterpriseOne dans BizTalk Server.</span><span class="sxs-lookup"><span data-stu-id="7e7e9-106">Edwards EnterpriseOne enables you to use JD Edwards EnterpriseOne business functions within BizTalk Server.</span></span> <span data-ttu-id="7e7e9-107">Les sections suivantes décrivent la configuration de l'adaptateur pour accéder à des informations spécifiques à JD Edwards EnterpriseOne.</span><span class="sxs-lookup"><span data-stu-id="7e7e9-107">The following sections discuss setting up the adapter to access JD Edwards EnterpriseOne-specific information.</span></span>  
  
## <a name="get-started"></a><span data-ttu-id="7e7e9-108">Prise en main</span><span class="sxs-lookup"><span data-stu-id="7e7e9-108">Get started</span></span>
<span data-ttu-id="7e7e9-109">[Prise en main](../core/getting-started-with-biztalk-adapter-for-jd-edwards-enterpriseone.md) répertorie les étapes pour installer l’adaptateur et des didacticiels pas à pas.</span><span class="sxs-lookup"><span data-stu-id="7e7e9-109">[Get started](../core/getting-started-with-biztalk-adapter-for-jd-edwards-enterpriseone.md) lists the steps to install the adapter, and step through some tutorials.</span></span>

## <a name="architecture"></a><span data-ttu-id="7e7e9-110">Architecture</span><span class="sxs-lookup"><span data-stu-id="7e7e9-110">Architecture</span></span>
<span data-ttu-id="7e7e9-111">[Architecture](../core/architecture-of-biztalk-adapter-for-jd-edwards-enterpriseone.md) décrit la conception et d’exécuter les éléments lors de la carte.</span><span class="sxs-lookup"><span data-stu-id="7e7e9-111">[Architecture](../core/architecture-of-biztalk-adapter-for-jd-edwards-enterpriseone.md) describes the design time and run time elements of the adapter.</span></span>

## <a name="security"></a><span data-ttu-id="7e7e9-112">Sécurité</span><span class="sxs-lookup"><span data-stu-id="7e7e9-112">Security</span></span>
<span data-ttu-id="7e7e9-113">[Sécurité](../core/security-in-biztalk-adapter-for-jd-edwards-enterpriseone.md) implique l’utilisation d’Enterprise Single Sign-on (SSO) dans BizTalk Server pour sécuriser vos applications qui utilisent cet adaptateur.</span><span class="sxs-lookup"><span data-stu-id="7e7e9-113">[Security](../core/security-in-biztalk-adapter-for-jd-edwards-enterpriseone.md) involves using Enterprise Single Sign-on (SSO) within BizTalk Serer to secure your applications that use this adapter.</span></span>

## <a name="create-the-artifacts"></a><span data-ttu-id="7e7e9-114">Créer les artefacts</span><span class="sxs-lookup"><span data-stu-id="7e7e9-114">Create the artifacts</span></span>
<span data-ttu-id="7e7e9-115">[Créer les artefacts de l’application](../core/developing-applications2.md) vous montre comment ajouter les artefacts dans la console Administration de BizTalk et dans Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="7e7e9-115">[Create the application artifacts](../core/developing-applications2.md) shows you how to add the artifacts in BizTalk Administration, and in Visual Studio.</span></span> <span data-ttu-id="7e7e9-116">Il montre également comment utiliser les propriétés de contexte de message dans une orchestration.</span><span class="sxs-lookup"><span data-stu-id="7e7e9-116">It also shows how to use message context properties in an orchestration.</span></span>

## <a name="import-your-app"></a><span data-ttu-id="7e7e9-117">Importez votre application</span><span class="sxs-lookup"><span data-stu-id="7e7e9-117">Import your app</span></span>
<span data-ttu-id="7e7e9-118">[Déploiement de votre application](../core/deploying-biztalk-adapter-for-jd-edwards-enterpriseone.md) explique comment importer le fichier de liaison de votre application dans la console Administration de BizTalk et dépasse les limitations.</span><span class="sxs-lookup"><span data-stu-id="7e7e9-118">[Deploying your application](../core/deploying-biztalk-adapter-for-jd-edwards-enterpriseone.md) discusses how to import your application binding file into BizTalk Administration, and goes over any limitations.</span></span> 

## <a name="exception-handling"></a><span data-ttu-id="7e7e9-119">Gestion des exceptions</span><span class="sxs-lookup"><span data-stu-id="7e7e9-119">Exception handling</span></span>
<span data-ttu-id="7e7e9-120">[Exceptions BizTalk Server](../core/using-biztalk-server-exception-handling3.md) fournit des conseils sur l’ajout de formes différentes à votre orchestration pour gérer les exceptions.</span><span class="sxs-lookup"><span data-stu-id="7e7e9-120">[BizTalk Server Exception Handling](../core/using-biztalk-server-exception-handling3.md) provides guidance on adding different shapes to your orchestration to handle exceptions.</span></span>

## <a name="troubleshooting"></a><span data-ttu-id="7e7e9-121">Dépannage</span><span class="sxs-lookup"><span data-stu-id="7e7e9-121">Troubleshooting</span></span>
<span data-ttu-id="7e7e9-122">[Dépanner l’adaptateur](../core/troubleshooting-jd-edwards-enterpriseone.md) décrit quelques erreurs courantes et les situations et traite le suivi d’événements pour Windows.</span><span class="sxs-lookup"><span data-stu-id="7e7e9-122">[Troubleshoot the adapter](../core/troubleshooting-jd-edwards-enterpriseone.md) describes some common errors and situations, and discusses Event Tracing for Windows.</span></span>

## <a name="reference"></a><span data-ttu-id="7e7e9-123">Référence</span><span class="sxs-lookup"><span data-stu-id="7e7e9-123">Reference</span></span>
<span data-ttu-id="7e7e9-124">[Informations techniques de référence](../core/technical-reference6.md) inclut des exemples de fichiers et des exemples de types de données utilisées par cet adaptateur.</span><span class="sxs-lookup"><span data-stu-id="7e7e9-124">[Technical reference](../core/technical-reference6.md) includes sample files and sample data types used by this adapter.</span></span>

## <a name="ui-reference"></a><span data-ttu-id="7e7e9-125">référence de l'interface utilisateur</span><span class="sxs-lookup"><span data-stu-id="7e7e9-125">UI reference</span></span>
<span data-ttu-id="7e7e9-126">[Référence à l’interface](../core/ui-reference-for-biztalk-adapter-for-jd-edwards-enterpriseone.md) fournit des détails sur les boîtes de dialogue et Assistants utilisés par cet adaptateur.</span><span class="sxs-lookup"><span data-stu-id="7e7e9-126">[UI reference](../core/ui-reference-for-biztalk-adapter-for-jd-edwards-enterpriseone.md) provides details on the dialog boxes and wizards used by this adapter.</span></span> 