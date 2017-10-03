---
title: "Exécution de l’exemple de conservation de l’en-tête JMS MQRFH2 | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 65982dca-77e1-4267-9528-26c59237e9b1
caps.latest.revision: "2"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: ab840ed1d319f8fd50d3a386e0ffc9b349f61b9e
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="running-the-jms-mqrfh2-header-preservation-sample"></a><span data-ttu-id="01d77-102">Exécution de l’exemple de conservation de JMS MQRFH2 en-tête</span><span class="sxs-lookup"><span data-stu-id="01d77-102">Running the JMS MQRFH2 Header Preservation Sample</span></span>
<span data-ttu-id="01d77-103">Cette partie de cet exemple dépose un message dans une file d’attente WebSphere.</span><span class="sxs-lookup"><span data-stu-id="01d77-103">This part of this sample deposits a message into a WebSphere queue.</span></span> <span data-ttu-id="01d77-104">L’architecture ESB récupère ce message et le dépose dans une file d’attente WebSphere sortant.</span><span class="sxs-lookup"><span data-stu-id="01d77-104">The ESB picks up this message and deposits it into an outbound WebSphere queue.</span></span> <span data-ttu-id="01d77-105">Cela montre que les Microsoft BizTalk ESB conservent des en-têtes de RFH2 haute fidélité comme un message transite par BizTalk Server.</span><span class="sxs-lookup"><span data-stu-id="01d77-105">This demonstrates that the ESB and Microsoft BizTalk preserve full-fidelity RFH2 headers as a message travels through BizTalk Server.</span></span>  
  
 <span data-ttu-id="01d77-106">**Pour exécuter l’exemple de conservation de l’en-tête**</span><span class="sxs-lookup"><span data-stu-id="01d77-106">**To run the Header Preservation sample**</span></span>  
  
1.  <span data-ttu-id="01d77-107">Si l’application GlobalBank.ESB n’est pas déjà en cours d’exécution, utilisez la Console Administration de BizTalk pour le démarrer.</span><span class="sxs-lookup"><span data-stu-id="01d77-107">If the GlobalBank.ESB application is not already running, use the BizTalk Administration Console to start it.</span></span>  
  
2.  <span data-ttu-id="01d77-108">Exécutez l’utilitaire IBM RfhUtil, puis sélectionnez le Gestionnaire de file d’attente nommé ESB. JMS. Sample.QueueManager dans la première liste déroulante pour se connecter à ce gestionnaire de file d’attente.</span><span class="sxs-lookup"><span data-stu-id="01d77-108">Run the IBM RfhUtil utility, and then select the queue manager named ESB.JMS.Sample.QueueManager in the first drop-down list to connect to this queue manager.</span></span>  
  
3.  <span data-ttu-id="01d77-109">Dans la deuxième liste déroulante, sélectionnez la file d’attente cible sortant nommé ESB. JMS. EXEMPLE. SENDTOBIZTALK, comme indiqué dans la Figure 1.</span><span class="sxs-lookup"><span data-stu-id="01d77-109">In the second drop-down list, select the target outbound queue named ESB.JMS.SAMPLE.SENDTOBIZTALK, as shown in Figure 1.</span></span>  
  
     <span data-ttu-id="01d77-110">![Gestionnaire de file d’attente](../esb-toolkit/media/ch6-queuemanager.gif "§ 6-QueueManager")</span><span class="sxs-lookup"><span data-stu-id="01d77-110">![Queue Manager](../esb-toolkit/media/ch6-queuemanager.gif "Ch6-QueueManager")</span></span>  
  
     <span data-ttu-id="01d77-111">**Figure 1**</span><span class="sxs-lookup"><span data-stu-id="01d77-111">**Figure 1**</span></span>  
  
     <span data-ttu-id="01d77-112">**Connexion au Gestionnaire de file d’attente et de la file d’attente sortante dans RfhUtil**</span><span class="sxs-lookup"><span data-stu-id="01d77-112">**Connecting to the queue manager and the outbound queue in RfhUtil**</span></span>  
  
4.  <span data-ttu-id="01d77-113">Si la liste déroulante ne contient pas toutes les files d’attente, assurez-vous que le Gestionnaire de file d’attente s’exécute en vérifiant l’élément WebSphere MQ Services, comme indiqué dans la Figure 2.</span><span class="sxs-lookup"><span data-stu-id="01d77-113">If the drop-down list does not contain any queues, make sure that the queue manager is running by checking the WebSphere MQ Services item, as shown in Figure 2.</span></span>  
  
     <span data-ttu-id="01d77-114">![Web sphère](../esb-toolkit/media/ch6-websphere.gif "§ 6-WebSphere")</span><span class="sxs-lookup"><span data-stu-id="01d77-114">![Web Sphere](../esb-toolkit/media/ch6-websphere.gif "Ch6-WebSphere")</span></span>  
  
     <span data-ttu-id="01d77-115">**Figure 2**</span><span class="sxs-lookup"><span data-stu-id="01d77-115">**Figure 2**</span></span>  
  
     <span data-ttu-id="01d77-116">**Vérification que le Gestionnaire de file d’attente est en cours d’exécution dans l’élément WebSphere Services**</span><span class="sxs-lookup"><span data-stu-id="01d77-116">**Checking that the queue manager is running in the WebSphere Services item**</span></span>  
  
5.  <span data-ttu-id="01d77-117">Cliquez sur le **ReadFile** bouton dans l’utilitaire RfhUtil et accédez au fichier de message de test nommé TEST-000128. JMS situé dans le sous-dossier nommé \Source\Samples\JMS\Test\Data\Load\\.</span><span class="sxs-lookup"><span data-stu-id="01d77-117">Click the **ReadFile** button in the RfhUtil utility and navigate to the test message file named TEST-000128.JMS located in the subfolder named \Source\Samples\JMS\Test\Data\Load\\.</span></span> <span data-ttu-id="01d77-118">Ce fichier contient un lot de messages de test 128, mais l’utilitaire charge seul le premier.</span><span class="sxs-lookup"><span data-stu-id="01d77-118">This file contains a batch of 128 test messages, but the utility loads only the first one.</span></span>  
  
6.  <span data-ttu-id="01d77-119">Cliquez sur le **RFH** onglet et assurez-vous que seuls les **JMS** case à cocher est activée.</span><span class="sxs-lookup"><span data-stu-id="01d77-119">Click the **RFH** tab, and then make sure that only the **JMS** check box is selected.</span></span>  
  
7.  <span data-ttu-id="01d77-120">Cliquez sur le **jms** onglet et assurez-vous que le texte sélectionné **répondre à** file d’attente est ESB. JMS. EXEMPLE. DYNAMICQ1 et que le texte sélectionné **file d’attente de Destination** est ESB. JMS. EXEMPLE. DYNAMICQ2.</span><span class="sxs-lookup"><span data-stu-id="01d77-120">Click the **jms** tab, and then make sure that the selected **Reply To** queue is ESB.JMS.SAMPLE.DYNAMICQ1 and that the selected **Destination Queue** is ESB.JMS.SAMPLE.DYNAMICQ2.</span></span>  
  
8.  <span data-ttu-id="01d77-121">Cliquez sur le **principal** onglet, puis cliquez sur le **Q d’écrire** bouton pour écrire le message dans la file d’attente.</span><span class="sxs-lookup"><span data-stu-id="01d77-121">Click the **Main** tab, and then click the **Write Q** button to write the message into the queue.</span></span>  
  
9. <span data-ttu-id="01d77-122">Après un certain délai pendant que l’application s’exécute, le message de sortie ESB apparaît dans l’architecture ESB. JMS. EXEMPLE. DYNAMICQ1 et ESB. JMS. EXEMPLE. DYNAMICQ1 les files d’attente.</span><span class="sxs-lookup"><span data-stu-id="01d77-122">After a delay while the application executes, the ESB output message appears in the ESB.JMS.SAMPLE.DYNAMICQ1 and ESB.JMS.SAMPLE.DYNAMICQ1 queues.</span></span> <span data-ttu-id="01d77-123">Ouvrez l’Explorateur de file d’attente WebSphere et parcourir les files d’attente pour le confirmer.</span><span class="sxs-lookup"><span data-stu-id="01d77-123">Open the WebSphere Queue Explorer and browse the queues to confirm this.</span></span>  
  
10. <span data-ttu-id="01d77-124">Revenez à l’utilitaire RfhUtil et se connecter à des files d’attente pour afficher les messages.</span><span class="sxs-lookup"><span data-stu-id="01d77-124">Go back to the RfhUtil utility and connect to the queues to see the messages.</span></span> <span data-ttu-id="01d77-125">Cliquez sur le **MQMD, RFH,** et **jms** onglets pour vérifier que les valeurs d’entrée et de sortie sont identiques pour le message dans la file d’attente de Destination, et que le message dans la file d’attente de la réponse est identique à l’exception, au lieu d’un message JMS standard, le message est marqué comme « autres ».</span><span class="sxs-lookup"><span data-stu-id="01d77-125">Click the **MQMD, RFH,** and **jms** tabs to verify that the input and output values are unchanged for the message in the Destination Queue, and that the message in the Reply To queue is the same except that, instead of being a standard JMS message, the message is marked as "other".</span></span>