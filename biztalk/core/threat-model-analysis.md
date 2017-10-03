---
title: "Analyse du modèle de menace | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- TMA, about TMA
- TMA
- TMA, procedure steps
ms.assetid: dfbf46aa-0a35-4925-8718-df8591efc279
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 06f5de73434d2c3a7bf67e659c6566b530b38aeb
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="threat-model-analysis"></a><span data-ttu-id="7426e-102">Analyse du modèle des menaces</span><span class="sxs-lookup"><span data-stu-id="7426e-102">Threat Model Analysis</span></span>
<span data-ttu-id="7426e-103">Une analyse du modèle des menaces est une analyse qui aide à déterminer les risques de sécurité liés à un produit, une application, un réseau ou un environnement, et l'origine des attaques.</span><span class="sxs-lookup"><span data-stu-id="7426e-103">A threat model analysis (TMA) is an analysis that helps determine the security risks posed to a product, application, network, or environment, and how attacks can show up.</span></span> <span data-ttu-id="7426e-104">L'objectif est de déterminer les menaces nécessitant une prévention et la manière de les prévenir.</span><span class="sxs-lookup"><span data-stu-id="7426e-104">The goal is to determine which threats require mitigation and how to mitigate them.</span></span>  
  
 <span data-ttu-id="7426e-105">Cette section fournit des informations très détaillées sur le processus d'analyse du modèle des menaces.</span><span class="sxs-lookup"><span data-stu-id="7426e-105">This section provides high-level information about the TMA process.</span></span> <span data-ttu-id="7426e-106">Pour plus d’informations, consultez le chapitre 4 de *Writing Secure Code, Second edition*, de Michael Howard et David LeBlanc.</span><span class="sxs-lookup"><span data-stu-id="7426e-106">For more information, see Chapter 4 of *Writing Secure Code, Second edition*, by Michael Howard and David LeBlanc.</span></span>  
  
 <span data-ttu-id="7426e-107">Les avantages d'une analyse du modèle des menaces sont notamment :</span><span class="sxs-lookup"><span data-stu-id="7426e-107">Some of the benefits of a TMA are:</span></span>  
  
-   <span data-ttu-id="7426e-108">Fournit une meilleure compréhension de votre application</span><span class="sxs-lookup"><span data-stu-id="7426e-108">Provides a better understanding of your application</span></span>  
  
-   <span data-ttu-id="7426e-109">Vous aide à trouver des bogues</span><span class="sxs-lookup"><span data-stu-id="7426e-109">Helps you find bugs</span></span>  
  
-   <span data-ttu-id="7426e-110">Peut aider les nouveaux membres de l'équipe à comprendre l'application en détail</span><span class="sxs-lookup"><span data-stu-id="7426e-110">Can help new team members understand the application in detail</span></span>  
  
-   <span data-ttu-id="7426e-111">Contient des informations importantes pour les autres équipes qui améliorent votre application</span><span class="sxs-lookup"><span data-stu-id="7426e-111">Contains important information for other teams that build on your application</span></span>  
  
-   <span data-ttu-id="7426e-112">Utile pour les testeurs</span><span class="sxs-lookup"><span data-stu-id="7426e-112">Useful for testers</span></span>  
  
 <span data-ttu-id="7426e-113">Les étapes détaillées à suivre pour effectuer une analyse du modèle des menaces sont les suivantes :</span><span class="sxs-lookup"><span data-stu-id="7426e-113">The high-level steps to perform a TMA are:</span></span>  
  
-   <span data-ttu-id="7426e-114">Étape 1.</span><span class="sxs-lookup"><span data-stu-id="7426e-114">Step 1.</span></span> <span data-ttu-id="7426e-115">Collecter les informations générales</span><span class="sxs-lookup"><span data-stu-id="7426e-115">Collect Background Information</span></span>  
  
-   <span data-ttu-id="7426e-116">Étape 2.</span><span class="sxs-lookup"><span data-stu-id="7426e-116">Step 2.</span></span> <span data-ttu-id="7426e-117">Créer et analyser le modèle de menace</span><span class="sxs-lookup"><span data-stu-id="7426e-117">Create and Analyze the Threat Model</span></span>  
  
-   <span data-ttu-id="7426e-118">Étape 3.</span><span class="sxs-lookup"><span data-stu-id="7426e-118">Step 3.</span></span> <span data-ttu-id="7426e-119">Examen des menaces</span><span class="sxs-lookup"><span data-stu-id="7426e-119">Review Threats</span></span>  
  
-   <span data-ttu-id="7426e-120">Étape 4.</span><span class="sxs-lookup"><span data-stu-id="7426e-120">Step 4.</span></span> <span data-ttu-id="7426e-121">Identifier les Technologies et Techniques de prévention</span><span class="sxs-lookup"><span data-stu-id="7426e-121">Identify Mitigation Techniques and Technologies</span></span>  
  
-   <span data-ttu-id="7426e-122">Étape 5.</span><span class="sxs-lookup"><span data-stu-id="7426e-122">Step 5.</span></span> <span data-ttu-id="7426e-123">Modèle de sécurité et des considérations relatives au déploiement de document</span><span class="sxs-lookup"><span data-stu-id="7426e-123">Document Security Model and Deployment Considerations</span></span>  
  
-   <span data-ttu-id="7426e-124">Étape 6.</span><span class="sxs-lookup"><span data-stu-id="7426e-124">Step 6.</span></span> <span data-ttu-id="7426e-125">Implémenter et tester les préventions</span><span class="sxs-lookup"><span data-stu-id="7426e-125">Implement and Test Mitigations</span></span>  
  
-   <span data-ttu-id="7426e-126">Étape 7.</span><span class="sxs-lookup"><span data-stu-id="7426e-126">Step 7.</span></span> <span data-ttu-id="7426e-127">Conserver le modèle des menaces synchronisé avec la conception</span><span class="sxs-lookup"><span data-stu-id="7426e-127">Keep the Threat Model in Sync with Design</span></span>  
  
## <a name="step-1-collect-background-information"></a><span data-ttu-id="7426e-128">Étape 1.</span><span class="sxs-lookup"><span data-stu-id="7426e-128">Step 1.</span></span> <span data-ttu-id="7426e-129">Collecter les informations générales</span><span class="sxs-lookup"><span data-stu-id="7426e-129">Collect Background Information</span></span>  
 <span data-ttu-id="7426e-130">Pour préparer une analyse du modèle des menaces réussie, vous devez recueillir des informations générales.</span><span class="sxs-lookup"><span data-stu-id="7426e-130">To prepare for a successful TMA, you have to collect some background information.</span></span> <span data-ttu-id="7426e-131">Elles permettent d'analyser votre environnement cible (une application, un programme ou l'infrastructure entière) comme suit :</span><span class="sxs-lookup"><span data-stu-id="7426e-131">It is useful to analyze your target environment (an application, program, or the whole infrastructure) as follows:</span></span>  
  
-   <span data-ttu-id="7426e-132">Identification des scénarios de cas d'utilisation.</span><span class="sxs-lookup"><span data-stu-id="7426e-132">Identify use-case scenarios.</span></span> <span data-ttu-id="7426e-133">Pour chaque scénario de cas d'utilisation pour votre environnement cible, identifiez la manière dont vous pensez que votre entreprise utilise l'environnement cible et toutes limitations ou restrictions liées à ce dernier.</span><span class="sxs-lookup"><span data-stu-id="7426e-133">For each use-case scenario for your target environment, identify how you expect your company to use the target environment, and any limitations or restrictions on the target environment.</span></span> <span data-ttu-id="7426e-134">Ces informations permettent de définir l'étendue de la discussion sur le modèle des menaces et fournissent des pointeurs aux ressources (actifs de valeur de votre entreprise, tels que des données et des ordinateurs) et des points d'entrée.</span><span class="sxs-lookup"><span data-stu-id="7426e-134">This information helps define the scope of the threat model discussion, and provides pointers to assets (anything of value to your company, such as data and computers) and entry points.</span></span>  
  
-   <span data-ttu-id="7426e-135">Création d'un diagramme de flux de données pour chaque scénario.</span><span class="sxs-lookup"><span data-stu-id="7426e-135">Create a data flow diagram (DFD) for each scenario.</span></span> <span data-ttu-id="7426e-136">Assurez-vous d'être suffisamment précis pour comprendre vos menaces.</span><span class="sxs-lookup"><span data-stu-id="7426e-136">Make sure that you go deep enough to understand your threats.</span></span>  
  
-   <span data-ttu-id="7426e-137">Détermination des limites et de l'étendue de l'environnement cible.</span><span class="sxs-lookup"><span data-stu-id="7426e-137">Determine the boundaries and scope of the target environment.</span></span>  
  
-   <span data-ttu-id="7426e-138">Compréhension des limites entre les composants approuvés et non approuvés.</span><span class="sxs-lookup"><span data-stu-id="7426e-138">Understand the boundaries between trusted and untrusted components.</span></span>  
  
-   <span data-ttu-id="7426e-139">Compréhension du modèle de configuration et d'administration pour chaque composant.</span><span class="sxs-lookup"><span data-stu-id="7426e-139">Understand the configuration and administration model for each component.</span></span>  
  
-   <span data-ttu-id="7426e-140">Création d'une liste de dépendances externes.</span><span class="sxs-lookup"><span data-stu-id="7426e-140">Create a list of external dependencies.</span></span>  
  
-   <span data-ttu-id="7426e-141">Création d'une liste d'hypothèses sur les autres composants dont dépend chaque composant.</span><span class="sxs-lookup"><span data-stu-id="7426e-141">Create a list of assumptions about other components on which each component depends.</span></span> <span data-ttu-id="7426e-142">Cela permet de valider des hypothèses entre composants, des éléments d'action et des éléments de suivi avec d'autres équipes.</span><span class="sxs-lookup"><span data-stu-id="7426e-142">This helps validate cross-component assumptions, action items, and follow-up items with other teams.</span></span>  
  
## <a name="step-2-create-and-analyze-the-threat-model"></a><span data-ttu-id="7426e-143">Étape 2.</span><span class="sxs-lookup"><span data-stu-id="7426e-143">Step 2.</span></span> <span data-ttu-id="7426e-144">Créer et analyser le modèle de menace</span><span class="sxs-lookup"><span data-stu-id="7426e-144">Create and Analyze the Threat Model</span></span>  
 <span data-ttu-id="7426e-145">Après avoir recueilli des informations générales, vous devez organiser une ou plusieurs réunions sur le modèle des menaces.</span><span class="sxs-lookup"><span data-stu-id="7426e-145">After you collect the background information, you should have a threat model meeting or meetings.</span></span> <span data-ttu-id="7426e-146">Assurez-vous qu'au moins un membre de chaque étape de développement est présent (par exemple, responsable de programme, développeur et testeur).</span><span class="sxs-lookup"><span data-stu-id="7426e-146">Make sure that at least one member of each development discipline (for example, program managers, developers, and testers) is at the meeting.</span></span> <span data-ttu-id="7426e-147">Veillez à rappeler aux participants que le but de la réunion est de trouver des menaces et non de les prévenir.</span><span class="sxs-lookup"><span data-stu-id="7426e-147">Make sure that you remind the attendees that the goal of the meeting is to find threats, not to fix them.</span></span> <span data-ttu-id="7426e-148">Au cours de la réunion sur le modèle des menaces, procédez comme suit :</span><span class="sxs-lookup"><span data-stu-id="7426e-148">During the threat model meeting, do the following:</span></span>  
  
-   <span data-ttu-id="7426e-149">Examinez le diagramme de flux de données pour chaque cas d'utilisation.</span><span class="sxs-lookup"><span data-stu-id="7426e-149">Examine the DFD for each use case.</span></span> <span data-ttu-id="7426e-150">Pour chaque cas d'utilisation, identifiez :</span><span class="sxs-lookup"><span data-stu-id="7426e-150">For each use case identify:</span></span>  
  
    -   <span data-ttu-id="7426e-151">Points d'entrée</span><span class="sxs-lookup"><span data-stu-id="7426e-151">Entry points</span></span>  
  
    -   <span data-ttu-id="7426e-152">Limites de confiance</span><span class="sxs-lookup"><span data-stu-id="7426e-152">Trust boundaries</span></span>  
  
    -   <span data-ttu-id="7426e-153">Flux de données du point d'entrée à l'emplacement de repos final (et inversement)</span><span class="sxs-lookup"><span data-stu-id="7426e-153">Flow of data from entry point to final resting location (and back)</span></span>  
  
-   <span data-ttu-id="7426e-154">Notez les actifs impliqués.</span><span class="sxs-lookup"><span data-stu-id="7426e-154">Note the assets involved.</span></span>  
  
-   <span data-ttu-id="7426e-155">Discutez chaque DFD et recherche les menaces dans les catégories suivantes pour toutes les entrées du diagramme : **S**urpation identifier, **T**ion des données, **R**épudiation, **I**la divulgation d’informations, **D**éni de service, et **E**lévation de privilèges.</span><span class="sxs-lookup"><span data-stu-id="7426e-155">Discuss each DFD, and look for threats in the following categories for all entries in the DFD: **S**poofing identify, **T**ampering with data, **R**epudiation, **I**nformation disclosure, **D**enial of service, and **E**levation of privileges.</span></span>  
  
-   <span data-ttu-id="7426e-156">Créez une liste des menaces identifiées.</span><span class="sxs-lookup"><span data-stu-id="7426e-156">Create a list of the identified threats.</span></span> <span data-ttu-id="7426e-157">Nous recommandons que cette liste inclue un titre, une brève description (y compris des arborescences de menaces), les ressources, le ou les impacts, le risque, les techniques de prévention, l'état de prévention et un numéro de bogue.</span><span class="sxs-lookup"><span data-stu-id="7426e-157">We recommend that this list include the following: title, brief description (including threat trees), asset (asset), impact(s), risk, mitigation techniques, mitigation status, and a bug number.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="7426e-158">Vous pouvez ajouter le risque, les techniques de prévention et l'état de prévention lorsque vous passez en revue les menaces.</span><span class="sxs-lookup"><span data-stu-id="7426e-158">You can add risk, mitigation techniques, and mitigation status as you review the threats.</span></span> <span data-ttu-id="7426e-159">Ne consacrez pas trop de temps à ces domaines pendant la réunion sur le modèle des menaces.</span><span class="sxs-lookup"><span data-stu-id="7426e-159">Do not spend too much time in these areas during the threat model meeting.</span></span>  
  
## <a name="step-3-review-threats"></a><span data-ttu-id="7426e-160">Étape 3.</span><span class="sxs-lookup"><span data-stu-id="7426e-160">Step 3.</span></span> <span data-ttu-id="7426e-161">Examen des menaces</span><span class="sxs-lookup"><span data-stu-id="7426e-161">Review Threats</span></span>  
 <span data-ttu-id="7426e-162">Une fois que vous avez identifié les menaces pour votre environnement, vous devez classer le risque de chaque menace et déterminer la manière dont vous voulez répondre à chaque menace.</span><span class="sxs-lookup"><span data-stu-id="7426e-162">After you have identified the threats to your environment, you must rank the risk of each threat and determine how you want to respond to each threat.</span></span> <span data-ttu-id="7426e-163">Vous pouvez le faire grâce à des réunions d'équipe supplémentaires ou par courrier électronique.</span><span class="sxs-lookup"><span data-stu-id="7426e-163">You can do this with additional team meetings or through e-mail.</span></span> <span data-ttu-id="7426e-164">Vous pouvez utiliser les catégories d’effet suivantes pour calculer l’exposition aux risques : **D**égâts potentiels, **R**eproductibilité, **E**xploitabilité, **un**tteinte des utilisateurs et **D**étectabilité.</span><span class="sxs-lookup"><span data-stu-id="7426e-164">You can use the following effect categories to calculate risk exposure: **D**amage potential, **R**eproducibility, **E**xploitability, **A**ffected users, and **D**iscoverability.</span></span>  
  
 <span data-ttu-id="7426e-165">Une fois que vous avez une liste des menaces pour votre environnement cible classée par risque, vous devez déterminer la manière dont vous répondrez à chaque menace.</span><span class="sxs-lookup"><span data-stu-id="7426e-165">After you have a list of the threats to your target environment prioritized by risk, you must determine how you will respond to each threat.</span></span> <span data-ttu-id="7426e-166">Votre réponse peut être de ne rien faire (rarement un bon choix), de prévenir les utilisateurs du problème potentiel, de supprimer le problème ou de le résoudre.</span><span class="sxs-lookup"><span data-stu-id="7426e-166">Your response can be to do nothing (rarely a good choice), warn users about the potential problem, remove the problem, or fix the problem.</span></span>  
  
## <a name="step-4-identify-mitigation-techniques-and-technologies"></a><span data-ttu-id="7426e-167">Étape 4.</span><span class="sxs-lookup"><span data-stu-id="7426e-167">Step 4.</span></span> <span data-ttu-id="7426e-168">Identifier les Technologies et Techniques de prévention</span><span class="sxs-lookup"><span data-stu-id="7426e-168">Identify Mitigation Techniques and Technologies</span></span>  
 <span data-ttu-id="7426e-169">Une fois que vous avez identifié les menaces à prévenir, vous devez déterminer les techniques de prévention disponibles pour chaque menace et la technologie la plus appropriée pour réduire l'effet de chaque menace.</span><span class="sxs-lookup"><span data-stu-id="7426e-169">After you identify which threats you will fix, you must determine the available mitigation techniques for each threat, and the most appropriate technology to reduce the effect of each threat.</span></span>  
  
 <span data-ttu-id="7426e-170">Par exemple, en fonction des détails de votre environnement cible, vous pouvez réduire l'effet des menaces de falsification des données en utilisant des techniques d'autorisation.</span><span class="sxs-lookup"><span data-stu-id="7426e-170">For example, depending on the details of your target environment, you can reduce the effect of data-tamper threats by using authorization techniques.</span></span> <span data-ttu-id="7426e-171">Vous devez alors déterminer la technologie d'autorisation appropriée à utiliser (par exemple, listes de contrôle d'accès discrétionnaire, autorisations ou restrictions d'IP).</span><span class="sxs-lookup"><span data-stu-id="7426e-171">You then have to determine the appropriate authorization technology to use (for example, discretionary access control lists (DACLs), permissions, or IP restrictions).</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="7426e-172">Lorsque vous évaluez les techniques et technologies de prévention à utiliser, vous devez considérer ce qui est approprié pour votre entreprise, ainsi que toute stratégie d'entreprise pouvant affecter la technique de prévention à choisir.</span><span class="sxs-lookup"><span data-stu-id="7426e-172">When you evaluate mitigation techniques and technologies to use, you must consider what makes business sense for your company, and any policies your company has that might affect the mitigation technique to choose.</span></span>  
  
 <span data-ttu-id="7426e-173">Après avoir terminé l'analyse du modèle des menaces, procédez comme suit :</span><span class="sxs-lookup"><span data-stu-id="7426e-173">After you complete the TMA, do the following:</span></span>  
  
-   <span data-ttu-id="7426e-174">Documentez le modèle de sécurité et les considérations relatives au déploiement.</span><span class="sxs-lookup"><span data-stu-id="7426e-174">Document the security model and deployment considerations</span></span>  
  
-   <span data-ttu-id="7426e-175">Mettez en œuvre et testez les préventions.</span><span class="sxs-lookup"><span data-stu-id="7426e-175">Implement and test mitigations</span></span>  
  
-   <span data-ttu-id="7426e-176">Conservez le modèle des menaces synchronisé avec la conception.</span><span class="sxs-lookup"><span data-stu-id="7426e-176">Keep the threat model synchronized with design</span></span>  
  
## <a name="step-5-document-security-model-and-deployment-considerations"></a><span data-ttu-id="7426e-177">Étape 5.</span><span class="sxs-lookup"><span data-stu-id="7426e-177">Step 5.</span></span> <span data-ttu-id="7426e-178">Modèle de sécurité et des considérations relatives au déploiement de document</span><span class="sxs-lookup"><span data-stu-id="7426e-178">Document Security Model and Deployment Considerations</span></span>  
 <span data-ttu-id="7426e-179">Il est important de documenter ce que vous avez découvert lors de l'analyse du modèle des menaces et comment vous avez décidé de réduire l'effet des menaces pour votre environnement cible.</span><span class="sxs-lookup"><span data-stu-id="7426e-179">It is valuable to document what you discover during the TMA and how you decide to reduce the effect of the threats to your target environment.</span></span> <span data-ttu-id="7426e-180">Cette documentation peut être utile pour le personnel de l'assurance qualité, du test, du support technique et du back-office.</span><span class="sxs-lookup"><span data-stu-id="7426e-180">This documentation can be useful to quality assurance (QA), test, support, and operations personnel.</span></span> <span data-ttu-id="7426e-181">Incluez des informations sur d'autres applications qui interagissent ou assurent l'interface avec votre environnement cible, ainsi que les recommandations et les exigences en matière de pare-feu et de topologie.</span><span class="sxs-lookup"><span data-stu-id="7426e-181">Include information about other applications that interact or interface with your target environment, and the firewall and topology recommendations and requirements.</span></span>  
  
## <a name="step-6-implement-and-test-mitigations"></a><span data-ttu-id="7426e-182">Étape 6.</span><span class="sxs-lookup"><span data-stu-id="7426e-182">Step 6.</span></span> <span data-ttu-id="7426e-183">Implémenter et tester les préventions</span><span class="sxs-lookup"><span data-stu-id="7426e-183">Implement and Test Mitigations</span></span>  
 <span data-ttu-id="7426e-184">Lorsque votre équipe est prête à prévenir les menaces identifiées lors de l'analyse du modèle des menaces, veillez à utiliser des listes de vérification de développement et de déploiement pour suivre le code sécurisé et les normes de déploiement permettant de minimiser l'introduction de nouvelles menaces.</span><span class="sxs-lookup"><span data-stu-id="7426e-184">When your team is ready to fix threats identified during the TMA, make sure you use development and deployment checklists to follow secure code and deployment standards that will help minimize the introduction of new threats.</span></span>  
  
 <span data-ttu-id="7426e-185">Une fois que vous avez implémenté une prévention, veillez à la tester pour vous assurer qu'elle offre le niveau de protection souhaité contre la menace.</span><span class="sxs-lookup"><span data-stu-id="7426e-185">After you implement a mitigation, make sure you test it to make sure it provides the level of protection that you want for the threat.</span></span>  
  
## <a name="step-7-keep-the-threat-model-in-sync-with-design"></a><span data-ttu-id="7426e-186">Étape 7.</span><span class="sxs-lookup"><span data-stu-id="7426e-186">Step 7.</span></span> <span data-ttu-id="7426e-187">Conserver le modèle des menaces synchronisé avec la conception</span><span class="sxs-lookup"><span data-stu-id="7426e-187">Keep the Threat Model in Sync with Design</span></span>  
 <span data-ttu-id="7426e-188">Lorsque vous ajoutez de nouvelles applications, de nouveaux serveurs ou autres éléments à votre environnement, veillez à revoir vos conclusions de l'analyse du modèle des menaces et à procéder à d'autres analyses pour chaque nouvelle fonctionnalité.</span><span class="sxs-lookup"><span data-stu-id="7426e-188">As you add new applications, servers, and other elements to your environment, make sure that you revisit the findings of the threat model analysis and do TMAs for any new functionality.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7426e-189">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="7426e-189">See Also</span></span>  
<span data-ttu-id="7426e-190">[Études de cas de sécurité pour les petites et moyennes entreprises](../core/security-case-studies-for-small-to-medium-sized-companies.md) </span><span class="sxs-lookup"><span data-stu-id="7426e-190">[Security Case Studies for Small to Medium-Sized Companies](../core/security-case-studies-for-small-to-medium-sized-companies.md) </span></span>  
 [<span data-ttu-id="7426e-191">Exemples de scénarios d’analyse du modèle</span><span class="sxs-lookup"><span data-stu-id="7426e-191">Sample Scenarios for Threat Model Analysis</span></span>](../core/sample-scenarios-for-threat-model-analysis.md)