---
title: "Exécution des Tests de composant de Namespace | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 13768608-ade6-44c0-897f-d417c3408302
caps.latest.revision: "2"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: a0ae865e91fd6ff796cb870c71840bde8a95831e
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="running-the-namespace-component-tests"></a><span data-ttu-id="c1ba0-102">Exécution des Tests de composant de Namespace</span><span class="sxs-lookup"><span data-stu-id="c1ba0-102">Running the Namespace Component Tests</span></span>
<span data-ttu-id="c1ba0-103">La procédure suivante montre comment vous pouvez exécuter les quatre scénarios de test de la [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] exemple de composant de Namespace.</span><span class="sxs-lookup"><span data-stu-id="c1ba0-103">The following procedure shows how you can run all four of the test scenarios for the [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] Namespace Component sample.</span></span>  
  
 <span data-ttu-id="c1ba0-104">**Pour exécuter le composant Namespace exemples de scénarios de test**</span><span class="sxs-lookup"><span data-stu-id="c1ba0-104">**To run the Namespace Component sample test scenarios**</span></span>  
  
1.  <span data-ttu-id="c1ba0-105">Avant d’exécuter cet exemple pour la première fois, assurez-vous que la réception emplacement et envoyer une URL de port pointant vers les sous-dossiers appropriés dans les fichiers de distribution source.</span><span class="sxs-lookup"><span data-stu-id="c1ba0-105">Before you run this sample for the first time, make sure that the receive location and send port URL point to the appropriate subfolders in the source distribution files.</span></span> <span data-ttu-id="c1ba0-106">Spécifiez le sous-dossier \Source\Samples\Namespace\Test\Filedrop\In pour l’emplacement de réception et le sous-dossier \Source\Samples\Namespace\Test\Filedrop\Out pour l’URL de port d’envoi.</span><span class="sxs-lookup"><span data-stu-id="c1ba0-106">Specify the subfolder \Source\Samples\Namespace\Test\Filedrop\In for the receive location and the subfolder \Source\Samples\Namespace\Test\Filedrop\Out for the send port URL.</span></span>  
  
2.  <span data-ttu-id="c1ba0-107">Si l’application GlobalBank.ESB n’est pas déjà en cours d’exécution, utilisez la Console d’Administration Microsoft BizTalk pour le démarrer.</span><span class="sxs-lookup"><span data-stu-id="c1ba0-107">If the GlobalBank.ESB application is not already running, use the Microsoft BizTalk Administration Console to start it.</span></span>  
  
3.  <span data-ttu-id="c1ba0-108">Faites une copie du fichier nommé TEST_Add_to_PassThrough.0000.ns.xml (situé dans le sous-dossier \Source\Samples\Namespace\Test\Data\ de votre dossier d’installation ESB) et renommez la copie en supprimant le préfixe « TEST_ ».</span><span class="sxs-lookup"><span data-stu-id="c1ba0-108">Make a copy of the file named TEST_Add_to_PassThrough.0000.ns.xml (located in the \Source\Samples\Namespace\Test\Data\ subfolder of your ESB installation folder), and rename the copy by removing the "TEST_" prefix.</span></span>  
  
4.  <span data-ttu-id="c1ba0-109">Copiez le fichier renommé dans le sous-dossier \Source\Samples\Namespace\Test\Filedrop\In.</span><span class="sxs-lookup"><span data-stu-id="c1ba0-109">Copy the renamed file into the \Source\Samples\Namespace\Test\Filedrop\In subfolder.</span></span>  
  
5.  <span data-ttu-id="c1ba0-110">Récupère le message, l’architecture ESB ajoute un espace de noms et dépose le message mis à jour dans le sous-dossier \Source\Samples\Namespace\Test\Filedrop\Out.</span><span class="sxs-lookup"><span data-stu-id="c1ba0-110">The ESB picks up the message, adds a namespace to it, and drops the updated message into the \Source\Samples\Namespace\Test\Filedrop\Out subfolder.</span></span> <span data-ttu-id="c1ba0-111">Ouvrez l’entrée et de sortie des fichiers dans un éditeur de texte pour voir l’effet de ce test.</span><span class="sxs-lookup"><span data-stu-id="c1ba0-111">Open the input and output files in a text editor to see the effect of this test.</span></span>  
  
6.  <span data-ttu-id="c1ba0-112">Maintenant, exécutez le deuxième test.</span><span class="sxs-lookup"><span data-stu-id="c1ba0-112">Now run the second test.</span></span> <span data-ttu-id="c1ba0-113">Faites une copie du fichier nommé TEST_Add_to_Remove.0000.ns.xml et renommez-la en supprimant le préfixe « TEST_ ».</span><span class="sxs-lookup"><span data-stu-id="c1ba0-113">Make a copy of the file named TEST_Add_to_Remove.0000.ns.xml and rename it by removing the "TEST_" prefix.</span></span>  
  
7.  <span data-ttu-id="c1ba0-114">Copiez le fichier renommé dans le sous-dossier \Source\Samples\Namespace\Test\Filedrop\In.</span><span class="sxs-lookup"><span data-stu-id="c1ba0-114">Copy the renamed file into the \Source\Samples\Namespace\Test\Filedrop\In subfolder.</span></span>  
  
8.  <span data-ttu-id="c1ba0-115">L’architecture ESB récupère le message lui ajoute un espace de noms, supprime le nouvel espace de noms et dépose le message mis à jour dans le sous-dossier \Source\Samples\Namespace\Test\Filedrop\Out.</span><span class="sxs-lookup"><span data-stu-id="c1ba0-115">The ESB picks up the message, adds a namespace to it, removes the new namespace, and drops the updated message into the \Source\Samples\Namespace\Test\Filedrop\Out subfolder.</span></span> <span data-ttu-id="c1ba0-116">Ouvrez l’entrée et de sortie des fichiers dans un éditeur de texte pour voir l’effet de ce test.</span><span class="sxs-lookup"><span data-stu-id="c1ba0-116">Open the input and output files in a text editor to see the effect of this test.</span></span>  
  
9. <span data-ttu-id="c1ba0-117">Maintenant exécuter le test de tiers.</span><span class="sxs-lookup"><span data-stu-id="c1ba0-117">Now run the third test.</span></span> <span data-ttu-id="c1ba0-118">Faites une copie du fichier nommé TEST_PassThrough_to_Remove.0000.ns.xml et renommez-la en supprimant le préfixe « TEST_ ».</span><span class="sxs-lookup"><span data-stu-id="c1ba0-118">Make a copy of the file named TEST_PassThrough_to_Remove.0000.ns.xml and rename it by removing the "TEST_" prefix.</span></span>  
  
10. <span data-ttu-id="c1ba0-119">Copiez le fichier renommé dans le sous-dossier \Source\Samples\Namespace\Test\Filedrop\In.</span><span class="sxs-lookup"><span data-stu-id="c1ba0-119">Copy the renamed file into the \Source\Samples\Namespace\Test\Filedrop\In subfolder.</span></span>  
  
11. <span data-ttu-id="c1ba0-120">L’architecture ESB récupère le message, supprime l’espace de noms existant et dépose le message mis à jour dans le sous-dossier \Source\Samples\Namespace\Test\Filedrop\Out.</span><span class="sxs-lookup"><span data-stu-id="c1ba0-120">The ESB picks up the message, removes the existing namespace, and drops the updated message into the \Source\Samples\Namespace\Test\Filedrop\Out subfolder.</span></span> <span data-ttu-id="c1ba0-121">Ouvrez l’entrée et de sortie des fichiers dans un éditeur de texte pour voir l’effet de ce test.</span><span class="sxs-lookup"><span data-stu-id="c1ba0-121">Open the input and output files in a text editor to see the effect of this test.</span></span>  
  
12. <span data-ttu-id="c1ba0-122">Enfin, exécutez la quatrième de tests.</span><span class="sxs-lookup"><span data-stu-id="c1ba0-122">Finally, run the fourth test.</span></span> <span data-ttu-id="c1ba0-123">Faites une copie du fichier nommé TEST_AddViaExtraction_to_PassThrough.0000.ns.xml et renommez-la en supprimant le préfixe « TEST_ ».</span><span class="sxs-lookup"><span data-stu-id="c1ba0-123">Make a copy of the file named TEST_AddViaExtraction_to_PassThrough.0000.ns.xml and rename it by removing the "TEST_" prefix.</span></span>  
  
13. <span data-ttu-id="c1ba0-124">Copiez le fichier renommé dans le sous-dossier \Source\Samples\Namespace\Test\Filedrop\In.</span><span class="sxs-lookup"><span data-stu-id="c1ba0-124">Copy the renamed file into the \Source\Samples\Namespace\Test\Filedrop\In subfolder.</span></span>  
  
14. <span data-ttu-id="c1ba0-125">Récupère le message de l’architecture ESB, extrait l’élément spécifié dans le **ExtractionNodeXPath** propriété, crée un message à partir de cet élément avec les valeurs de l’espace de noms spécifié et dépose le message mis à jour dans le \Source\Samples\ Namespace\Test\Filedrop\Out sous-dossier.</span><span class="sxs-lookup"><span data-stu-id="c1ba0-125">The ESB picks up the message, extracts the element specified in the **ExtractionNodeXPath** property, creates a message from this element with the specified namespace values, and drops the updated message into the \Source\Samples\Namespace\Test\Filedrop\Out subfolder.</span></span> <span data-ttu-id="c1ba0-126">Ouvrez l’entrée et de sortie des fichiers dans un éditeur de texte pour voir l’effet de ce test.</span><span class="sxs-lookup"><span data-stu-id="c1ba0-126">Open the input and output files in a text editor to see the effect of this test.</span></span>