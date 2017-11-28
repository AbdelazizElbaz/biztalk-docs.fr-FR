---
title: "Exécute le bloc charger l’exemple de routage basé sur le contenu | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 7e981567-7c6c-4c13-bd5b-597efdd3fb50
caps.latest.revision: "2"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 36c5348563cc52c31b14dbceddf35bdb3d5d94cb
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="running-the-bulk-load-content-based-routing-sample"></a><span data-ttu-id="bf147-102">La charge en fonction du contenu routage échantillon global en cours d’exécution</span><span class="sxs-lookup"><span data-stu-id="bf147-102">Running the Bulk Load Content-Based Routing Sample</span></span>
<span data-ttu-id="bf147-103">Cette partie de l’exemple illustre une file d’attente des messages que les Microsoft BizTalk ESB achemine vers les files d’attente de destination différent en fonction du nom de la file d’attente spécifié dans chaque message de chargement en masse.</span><span class="sxs-lookup"><span data-stu-id="bf147-103">This part of the sample demonstrates bulk loading a queue with messages that the ESB and Microsoft BizTalk will route to different destination queues based on the queue name specified in each message.</span></span> <span data-ttu-id="bf147-104">Il utilise les fonctionnalités de l’exemple que vous avez vu dans les parties précédentes.</span><span class="sxs-lookup"><span data-stu-id="bf147-104">It uses the features of the sample that you have seen in the previous two parts.</span></span>  
  
 <span data-ttu-id="bf147-105">**Pour exécuter l’exemple d’accès en fonction du contenu de chargement en masse de routage**</span><span class="sxs-lookup"><span data-stu-id="bf147-105">**To run the Bulk Load Content-based Routing Access sample**</span></span>  
  
1.  <span data-ttu-id="bf147-106">Si l’application GlobalBank.ESB n’est pas déjà en cours d’exécution, utilisez la Console Administration de BizTalk pour le démarrer.</span><span class="sxs-lookup"><span data-stu-id="bf147-106">If the GlobalBank.ESB application is not already running, use the BizTalk Administration Console to start it.</span></span>  
  
2.  <span data-ttu-id="bf147-107">Exécutez l’utilitaire IBM RfhUtil, puis sélectionnez le Gestionnaire de file d’attente nommé ESB. JMS. Sample.QueueManager dans la première liste déroulante pour se connecter à ce gestionnaire de file d’attente, comme dans les 2 partie de cet exemple.</span><span class="sxs-lookup"><span data-stu-id="bf147-107">Run the IBM RfhUtil utility, and then select the queue manager named ESB.JMS.Sample.QueueManager in the first drop-down list to connect to this queue manager, as in Part 2 of this sample.</span></span>  
  
3.  <span data-ttu-id="bf147-108">Dans la deuxième liste déroulante, sélectionnez la file d’attente cible sortant nommé ESB. JMS. EXEMPLE. SENDTOBIZTALK, comme dans les 2 partie de cet exemple.</span><span class="sxs-lookup"><span data-stu-id="bf147-108">In the second drop-down list, select the target outbound queue named ESB.JMS.SAMPLE.SENDTOBIZTALK, as in Part 2 of this sample.</span></span>  
  
4.  <span data-ttu-id="bf147-109">Cliquez sur le **charge Q** bouton dans l’utilitaire RfhUtil et cliquez sur le fichier de message de test nommé TEST-000128. JMS situé dans le sous-dossier nommé \Source\Samples\JMS\Test\Data\Load\\.</span><span class="sxs-lookup"><span data-stu-id="bf147-109">Click the **Load Q** button in the RfhUtil utility, and then navigate to the test message file named TEST-000128.JMS located in the subfolder named \Source\Samples\JMS\Test\Data\Load\\.</span></span> <span data-ttu-id="bf147-110">Ce fichier contient un lot de messages test 128 que l’exemple va envoyer à l’architecture ESB.</span><span class="sxs-lookup"><span data-stu-id="bf147-110">This file contains a batch of 128 test messages that the sample will send to the ESB.</span></span>  
  
5.  <span data-ttu-id="bf147-111">Dans le **charge** boîte de dialogue, laissez toutes les valeurs définies à leurs valeurs par défaut.</span><span class="sxs-lookup"><span data-stu-id="bf147-111">In the **Load** dialog box, leave all values set to their default values.</span></span>  
  
6.  <span data-ttu-id="bf147-112">Dans le **charge** boîte de dialogue, cliquez sur **OK** pour ajouter tous les messages à la file d’attente d’entrée.</span><span class="sxs-lookup"><span data-stu-id="bf147-112">In the **Load** dialog box, click **OK** to add all the messages to the input queue.</span></span>  
  
7.  <span data-ttu-id="bf147-113">Après un certain délai pendant que l’application s’exécute, les messages de sortie ESB apparaissent dans les files d’attente de destination différentes, en fonction des valeurs dans leurs en-têtes JMS.</span><span class="sxs-lookup"><span data-stu-id="bf147-113">After a delay while the application executes, the ESB output messages appear in various destination queues, depending on the values in their JMS headers.</span></span> <span data-ttu-id="bf147-114">Toutefois, tous les spécifient la même réponse à file d’attente, pour toutes les réponses apparaissent dans l’architecture ESB. JMS. EXEMPLE. File d’attente de la réponse.</span><span class="sxs-lookup"><span data-stu-id="bf147-114">However, all specify the same Reply To queue, so all the replies appear in the ESB.JMS.SAMPLE.REPLY queue.</span></span> <span data-ttu-id="bf147-115">Ouvrez l’Explorateur de file d’attente WebSphere et parcourir les files d’attente pour le confirmer.</span><span class="sxs-lookup"><span data-stu-id="bf147-115">Open the WebSphere Queue Explorer and browse the queues to confirm this.</span></span>