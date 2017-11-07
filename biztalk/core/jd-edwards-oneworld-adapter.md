---
title: Adaptateur JD Edwards OneWorld | Documents Microsoft
description: "Installer, parcourez les didacticiels, découvrez l’architecture, utiliser la sécurité de l’authentification unique, créer vos applications, importez le fichier de liaison et ajouter la gestion des exceptions lors de l’utilisation de l’adaptateur BizTalk pour J.D. Edwards OneWorld dans BizTalk Server"
ms.custom: 
ms.date: 10/18/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 5df8cd89-d9df-41ca-9a2c-b9d7fbcd06f2
caps.latest.revision: "14"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 9bde93503bff679faf2717edefb386aa2f43fc3e
ms.sourcegitcommit: dd7c54feab783ae2f8fe75873363fe9ffc77cd66
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/07/2017
---
# <a name="jd-edwards-oneworld-adapter"></a><span data-ttu-id="1c2e9-104">Adaptateur JD Edwards OneWorld</span><span class="sxs-lookup"><span data-stu-id="1c2e9-104">JD Edwards OneWorld Adapter</span></span>
<span data-ttu-id="1c2e9-105">L'adaptateur Microsoft BizTalk pour JD Edwards OneWorld vous permet d'utiliser les fonctions commerciales de JD Edwards OneWorld avec BizTalk Server.</span><span class="sxs-lookup"><span data-stu-id="1c2e9-105">Microsoft BizTalk Adapter for JD Edwards OneWorld enables you to use JD Edwards OneWorld business functions within BizTalk Server.</span></span> <span data-ttu-id="1c2e9-106">Les sections suivantes décrivent la configuration de l'adaptateur BizTalk pour JD Edwards OneWorld pour accéder aux informations spécifiques à JD Edwards OneWorld.</span><span class="sxs-lookup"><span data-stu-id="1c2e9-106">The following sections discuss setting up BizTalk Adapter for JD Edwards OneWorld to access JD Edwards OneWorld-specific information.</span></span>  
  
## <a name="get-started"></a><span data-ttu-id="1c2e9-107">Prise en main</span><span class="sxs-lookup"><span data-stu-id="1c2e9-107">Get started</span></span> 
<span data-ttu-id="1c2e9-108">[Prise en main](../core/getting-started-with-biztalk-adapter-for-jd-edwards-oneworld.md) répertorie les étapes pour installer l’adaptateur et parcourir un didacticiel.</span><span class="sxs-lookup"><span data-stu-id="1c2e9-108">[Get started](../core/getting-started-with-biztalk-adapter-for-jd-edwards-oneworld.md) lists the steps to install the adapter, and step through a tutorial.</span></span>

## <a name="architecture"></a><span data-ttu-id="1c2e9-109">Architecture</span><span class="sxs-lookup"><span data-stu-id="1c2e9-109">Architecture</span></span>
<span data-ttu-id="1c2e9-110">[Architecture](../core/planning-and-architecture17.md) des détails de l’adaptateur de fonctionne de la façon dont les fonctions et les instances sont regroupées au moment du design et moment de l’exécution, limitations lors de l’interrogation et la récupération des listes et l’utilisation des éléments de commandes multiples avec cette carte.</span><span class="sxs-lookup"><span data-stu-id="1c2e9-110">[Architecture](../core/planning-and-architecture17.md) details how the adapter works, how instances and functions are pooled at design time and run time, limitations when  querying and retrieving lists, and using multi-order items with this adapter.</span></span>

## <a name="security"></a><span data-ttu-id="1c2e9-111">Sécurité</span><span class="sxs-lookup"><span data-stu-id="1c2e9-111">Security</span></span>
<span data-ttu-id="1c2e9-112">[Sécurité de l’adaptateur BizTalk pour JD Edwards OneWorld](../core/security-in-biztalk-adapter-for-jd-edwards-oneworld.md) implique l’utilisation d’Enterprise Single Sign-on (SSO) dans BizTalk Server pour sécuriser vos applications qui utilisent cet adaptateur.</span><span class="sxs-lookup"><span data-stu-id="1c2e9-112">[Security in BizTalk Adapter for JD Edwards OneWorld](../core/security-in-biztalk-adapter-for-jd-edwards-oneworld.md) involves using Enterprise Single Sign-on (SSO) within BizTalk Serer to secure your applications that use this adapter.</span></span>

## <a name="create-the-artifacts"></a><span data-ttu-id="1c2e9-113">Créer les artefacts</span><span class="sxs-lookup"><span data-stu-id="1c2e9-113">Create the artifacts</span></span>
<span data-ttu-id="1c2e9-114">[Créer les artefacts de l’application](../core/developing-applications3.md) vous montre comment ajouter les artefacts dans la console Administration de BizTalk et dans Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="1c2e9-114">[Create the application artifacts](../core/developing-applications3.md) shows you how to add the artifacts in BizTalk Administration, and in Visual Studio.</span></span> <span data-ttu-id="1c2e9-115">Il montre également comment utiliser les propriétés de contexte de message dans une orchestration.</span><span class="sxs-lookup"><span data-stu-id="1c2e9-115">It also shows how to use message context properties in an orchestration.</span></span>

## <a name="import-your-app"></a><span data-ttu-id="1c2e9-116">Importez votre application</span><span class="sxs-lookup"><span data-stu-id="1c2e9-116">Import your app</span></span>
<span data-ttu-id="1c2e9-117">[Déploiement de l’adaptateur BizTalk pour JD Edwards OneWorld](../core/deploying-biztalk-adapter-for-jd-edwards-oneworld.md) explique comment importer le fichier de liaison de votre application dans la console Administration de BizTalk et dépasse les limitations.</span><span class="sxs-lookup"><span data-stu-id="1c2e9-117">[Deploying BizTalk Adapter for JD Edwards OneWorld](../core/deploying-biztalk-adapter-for-jd-edwards-oneworld.md) discusses how to import your application binding file into BizTalk Administration, and goes over the limitations.</span></span> 

## <a name="exception-handling"></a><span data-ttu-id="1c2e9-118">Gestion des exceptions</span><span class="sxs-lookup"><span data-stu-id="1c2e9-118">Exception handling</span></span> 
<span data-ttu-id="1c2e9-119">[La gestion des exceptions de BizTalk Server](../core/using-biztalk-server-exception-handling1.md) fournit des conseils sur la mise à jour le fichier jdearglist.txt et l’ajout de formes différentes à votre orchestration pour gérer les exceptions.</span><span class="sxs-lookup"><span data-stu-id="1c2e9-119">[BizTalk Server exception handling](../core/using-biztalk-server-exception-handling1.md) provides guidance on updating the jdearglist.txt file, and adding different shapes to your orchestration to handle exceptions.</span></span>

## <a name="troubleshooting"></a><span data-ttu-id="1c2e9-120">Dépannage</span><span class="sxs-lookup"><span data-stu-id="1c2e9-120">Troubleshooting</span></span>
<span data-ttu-id="1c2e9-121">[Résolution des problèmes](../core/troubleshooting-jd-edwards-oneworld.md) décrit quelques erreurs courantes et les situations et traite le suivi d’événements pour Windows.</span><span class="sxs-lookup"><span data-stu-id="1c2e9-121">[Troubleshooting](../core/troubleshooting-jd-edwards-oneworld.md) describes some common errors and situations, and discusses Event Tracing for Windows.</span></span>

## <a name="data-types"></a><span data-ttu-id="1c2e9-122">Types de données</span><span class="sxs-lookup"><span data-stu-id="1c2e9-122">Data Types</span></span>
<span data-ttu-id="1c2e9-123">[Annexe : Les Types de données](../core/appendix-a-data-types.md) répertorie les types de données exemple utilisées par cet adaptateur.</span><span class="sxs-lookup"><span data-stu-id="1c2e9-123">[Appendix: Data Types](../core/appendix-a-data-types.md) lists the sample data types used by this adapter.</span></span>

## <a name="ui-reference"></a><span data-ttu-id="1c2e9-124">référence de l'interface utilisateur</span><span class="sxs-lookup"><span data-stu-id="1c2e9-124">UI reference</span></span>
<span data-ttu-id="1c2e9-125">[Référence de l’interface utilisateur de l’adaptateur BizTalk pour JDE OneWorld](../core/ui-reference-for-biztalk-adapter-for-jde-oneworld.md) fournit des détails sur les boîtes de dialogue et Assistants utilisés par cet adaptateur.</span><span class="sxs-lookup"><span data-stu-id="1c2e9-125">[UI Reference for BizTalk Adapter for JDE OneWorld](../core/ui-reference-for-biztalk-adapter-for-jde-oneworld.md) provides details on the dialog boxes and wizards used by this adapter.</span></span> 