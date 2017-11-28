---
title: "Vue d’ensemble de la création d’une commande RFC dans un SAP à utiliser avec l’adaptateur SAP dans BizTalk | Documents Microsoft"
description: "Créer une demande de changement, RFC destination et envoyer une demande de changement du système SAP - Pack de l’adaptateur BizTalk (LOB)"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 35937183-fc1e-49cd-8a75-8f62effe0013
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 802a2e33b8bc902dc784276ce7c1d9c3f37f3b12
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="create-and-send-an-rfc-in-sap"></a><span data-ttu-id="fdb61-103">Créer et envoyer une demande de changement dans SAP</span><span class="sxs-lookup"><span data-stu-id="fdb61-103">Create and send an RFC in SAP</span></span>
<span data-ttu-id="fdb61-104">Répertorie les principales tâches à effectuer sur le système SAP pour créer une demande de changement.</span><span class="sxs-lookup"><span data-stu-id="fdb61-104">Lists high-level tasks to complete on the SAP system to create an RFC.</span></span> <span data-ttu-id="fdb61-105">Chaque tâche peut impliquer des procédures très détaillées.</span><span class="sxs-lookup"><span data-stu-id="fdb61-105">Each task may involve very detailed procedures.</span></span> <span data-ttu-id="fdb61-106">Par conséquent, nous vous recommandons de contacter votre administrateur SAP pour effectuer ces tâches, ou reportez-vous au Guide de SAP.</span><span class="sxs-lookup"><span data-stu-id="fdb61-106">As a result, we recommend contacting your SAP administrator to complete these tasks, or refer to the SAP guidance.</span></span>  
  
## <a name="create-an-rfc"></a><span data-ttu-id="fdb61-107">Créer une demande de changement</span><span class="sxs-lookup"><span data-stu-id="fdb61-107">Create an RFC</span></span>  
  
1.  <span data-ttu-id="fdb61-108">Démarrez l’interface utilisateur graphique SAP.</span><span class="sxs-lookup"><span data-stu-id="fdb61-108">Start the SAP GUI.</span></span>  
  
2.  <span data-ttu-id="fdb61-109">Accédez à la Transaction SE37 (Générateur de fonction), entrez le nom de la RFC, puis cliquez sur **créer**.</span><span class="sxs-lookup"><span data-stu-id="fdb61-109">Go to Transaction SE37 (Function Builder), enter the RFC name, and click **Create**.</span></span>  
  
3.  <span data-ttu-id="fdb61-110">Entrez un groupe fonction existant sous lequel la demande de modification est créée, une brève description de la RFC, puis cliquez sur **enregistrer**.</span><span class="sxs-lookup"><span data-stu-id="fdb61-110">Enter an existing function group under which the RFC will be created, a short description for the RFC, and click **Save**.</span></span>  
  
4.  <span data-ttu-id="fdb61-111">Dans le **attributs** onglet, sélectionnez le **Remote-Enabled Module** case d’option.</span><span class="sxs-lookup"><span data-stu-id="fdb61-111">In the **Attributes** tab, select the **Remote-Enabled Module** radio button.</span></span>  
  
5.  <span data-ttu-id="fdb61-112">Dans le **importer** , entrez les paramètres d’importation.</span><span class="sxs-lookup"><span data-stu-id="fdb61-112">In the **Import** tab, enter the import parameters.</span></span> <span data-ttu-id="fdb61-113">Ces paramètres sont utilisés pour passer les données externes au module de fonction.</span><span class="sxs-lookup"><span data-stu-id="fdb61-113">These parameters are used for passing the external data to the function module.</span></span>  
  
6.  <span data-ttu-id="fdb61-114">Dans le **exporter** , entrez les paramètres d’exportation.</span><span class="sxs-lookup"><span data-stu-id="fdb61-114">In the **Export** tab, enter the export parameters.</span></span>  
  
7.  <span data-ttu-id="fdb61-115">Dans le **Changing** , entrez les paramètres de modification.</span><span class="sxs-lookup"><span data-stu-id="fdb61-115">In the **Changing** tab, enter the changing parameters.</span></span>  
  
8.  <span data-ttu-id="fdb61-116">Dans le **Tables** , entrez les noms de table.</span><span class="sxs-lookup"><span data-stu-id="fdb61-116">In the **Tables** tab, enter the table names.</span></span>  
  
9. <span data-ttu-id="fdb61-117">Dans le **Exceptions** , entrez les exceptions pour gérer les erreurs.</span><span class="sxs-lookup"><span data-stu-id="fdb61-117">In the **Exceptions** tab, enter the exceptions to handle errors.</span></span>  
  
10. <span data-ttu-id="fdb61-118">Dans le **Code Source** , entrez le code source (logique) pour le document RFC.</span><span class="sxs-lookup"><span data-stu-id="fdb61-118">In the **Source Code** tab, enter the source code (logic) for the RFC.</span></span>  
  
11. <span data-ttu-id="fdb61-119">Cliquez sur le **activer** icône dans la barre d’outils pour activer le module de fonction.</span><span class="sxs-lookup"><span data-stu-id="fdb61-119">Click the **Activate** icon on the toolbar to activate the function module.</span></span>  

## <a name="create-an-rfc-destination"></a><span data-ttu-id="fdb61-120">Créer une destination RFC</span><span class="sxs-lookup"><span data-stu-id="fdb61-120">Create an RFC destination</span></span>  
  
1.  <span data-ttu-id="fdb61-121">Démarrez l’interface utilisateur graphique SAP.</span><span class="sxs-lookup"><span data-stu-id="fdb61-121">Start the SAP GUI.</span></span>  
  
2.  <span data-ttu-id="fdb61-122">Accédez à la Transaction SM59 (afficher et mettre à jour les Destinations RFC).</span><span class="sxs-lookup"><span data-stu-id="fdb61-122">Go to Transaction SM59 (Display and Maintain RFC Destinations).</span></span>  
  
3.  <span data-ttu-id="fdb61-123">Dans la barre de menus, cliquez sur **créer**.</span><span class="sxs-lookup"><span data-stu-id="fdb61-123">From the menu bar, click **Create**.</span></span>  
  
4.  <span data-ttu-id="fdb61-124">Entrez la destination RFC, le type de connexion, la description, puis appuyez sur ENTRÉE.</span><span class="sxs-lookup"><span data-stu-id="fdb61-124">Enter the RFC destination, connection type, description, and then press Enter.</span></span>  
  
5.  <span data-ttu-id="fdb61-125">Sélectionnez le **programme de serveur inscrit** case d’option, entrez l’ID de programme, un hôte de passerelle et un service de passerelle.</span><span class="sxs-lookup"><span data-stu-id="fdb61-125">Select the **Registered Server Program** radio-button, enter the program ID, gateway host, and gateway service.</span></span>  
  
6.  <span data-ttu-id="fdb61-126">Enregistrez la destination RFC.</span><span class="sxs-lookup"><span data-stu-id="fdb61-126">Save the RFC destination.</span></span>  

## <a name="send-an-rfc-from-an-sap-system"></a><span data-ttu-id="fdb61-127">Envoyer une demande de changement d’un système SAP</span><span class="sxs-lookup"><span data-stu-id="fdb61-127">Send an RFC from an SAP system</span></span>  
  
1.  <span data-ttu-id="fdb61-128">Démarrez l’interface utilisateur graphique SAP.</span><span class="sxs-lookup"><span data-stu-id="fdb61-128">Start the SAP GUI.</span></span>  
  
2.  <span data-ttu-id="fdb61-129">Créer un système logique à l’aide de la transaction de BD54.</span><span class="sxs-lookup"><span data-stu-id="fdb61-129">Create a logical system using BD54 transaction.</span></span>  
  
3.  <span data-ttu-id="fdb61-130">Créer une destination RFC dans les connexions TCP/IP à l’aide de la transaction de SM59.</span><span class="sxs-lookup"><span data-stu-id="fdb61-130">Create an RFC destination in TCP/IP connections using SM59 transaction.</span></span>  
  
4.  <span data-ttu-id="fdb61-131">Créer un port à l’aide de la transaction de WE21 et l’attacher à la destination RFC créée dans la dernière étape.</span><span class="sxs-lookup"><span data-stu-id="fdb61-131">Create a port using WE21 transaction and attach it to the RFC destination created in the last step.</span></span>  
  
5.  <span data-ttu-id="fdb61-132">Déclencher une commande RFC à l’aide de SE37.</span><span class="sxs-lookup"><span data-stu-id="fdb61-132">Trigger an RFC by using SE37.</span></span> <span data-ttu-id="fdb61-133">Ce document RFC doit contenir la logique pour effectuer une demande de changement de l’appel à une application externe et puis recevoir une réponse à partir de cette application.</span><span class="sxs-lookup"><span data-stu-id="fdb61-133">This RFC must contain the logic to make an RFC call to an external application and then receive a response from that application.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fdb61-134">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="fdb61-134">See Also</span></span>  
 [<span data-ttu-id="fdb61-135">Exécution de tâches à l’aide de l’interface utilisateur graphique SAP pour les scénarios de l’adaptateur SAP spécifique</span><span class="sxs-lookup"><span data-stu-id="fdb61-135">Performing Tasks Using the SAP GUI for Specific SAP Adapter Scenarios</span></span>](performing-tasks-using-the-sap-gui-for-specific-sap-adapter-scenarios.md)