---
title: "L’accès à la propriété en-tête en cours d’exécution à partir d’un exemple d’Orchestration | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 2059eb2c-50a3-4618-a6ec-faa1a9e5d368
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: d2ddbb2ea7ef978c0e5eae07835d5a9c1320bbc2
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="running-the-header-property-access-from-an-orchestration-sample"></a><span data-ttu-id="ce7c5-102">L’accès à la propriété en-tête en cours d’exécution à partir d’un exemple d’Orchestration</span><span class="sxs-lookup"><span data-stu-id="ce7c5-102">Running the Header Property Access from an Orchestration Sample</span></span>
<span data-ttu-id="ce7c5-103">Cette partie de l’exemple illustre comment l’architecture ESB promeut les métadonnées d’en-tête JMS dans les propriétés de contexte de message, qui a accès au code et des composants dans les orchestrations dans Microsoft BizTalk.</span><span class="sxs-lookup"><span data-stu-id="ce7c5-103">This part of the sample demonstrates how the ESB promotes JMS header metadata into message context properties, which code and components in orchestrations within Microsoft BizTalk can access.</span></span> <span data-ttu-id="ce7c5-104">L’exemple inclut un pipeline de réception qui contient une instance du composant ESB JMS qui promeut les métadonnées d’en-tête JMS dans les propriétés de contexte de message.</span><span class="sxs-lookup"><span data-stu-id="ce7c5-104">The sample includes a receive pipeline that contains an instance of the ESB JMS component that promotes JMS header metadata into message context properties.</span></span>  
  
 <span data-ttu-id="ce7c5-105">Le port de réception transmet le message à une orchestration nommée JMSRouter qui Récupère le nom de la file d’attente affecté par l’utilitaire RfhUtil (et envoyés dans les métadonnées de l’en-tête) à partir des propriétés de contexte du message.</span><span class="sxs-lookup"><span data-stu-id="ce7c5-105">The receive port passes the message to an orchestration named JMSRouter that retrieves the queue name assigned by the RfhUtil utility (and sent in the header metadata) from the context properties of the message.</span></span> <span data-ttu-id="ce7c5-106">L’orchestration affecte ce nom de file d’attente pour un port d’envoi dynamique et envoie le message à ce port.</span><span class="sxs-lookup"><span data-stu-id="ce7c5-106">The orchestration assigns this queue name to a dynamic send port and sends the message to that port.</span></span>  
  
 <span data-ttu-id="ce7c5-107">Un pipeline d’envoi pour le port contient une instance du composant ESB JMS rétrograde les propriétés de contexte de message dans les métadonnées d’en-tête JMS.</span><span class="sxs-lookup"><span data-stu-id="ce7c5-107">A send pipeline for the port contains an instance of the ESB JMS component that demotes the message context properties into the JMS header metadata.</span></span>  
  
 <span data-ttu-id="ce7c5-108">**Pour exécuter l’exemple d’accès à la propriété en-tête**</span><span class="sxs-lookup"><span data-stu-id="ce7c5-108">**To run the Header Property Access sample**</span></span>  
  
1.  <span data-ttu-id="ce7c5-109">Si l’application GlobalBank.ESB n’est pas déjà en cours d’exécution, utilisez la Console Administration de BizTalk pour le démarrer.</span><span class="sxs-lookup"><span data-stu-id="ce7c5-109">If the GlobalBank.ESB application is not already running, use the BizTalk Administration Console to start it.</span></span>  
  
2.  <span data-ttu-id="ce7c5-110">Exécutez l’utilitaire IBM RfhUtil ; Sélectionnez le Gestionnaire de file d’attente nommé ESB. JMS. Sample.QueueManager dans la première liste déroulante pour se connecter à ce gestionnaire de file d’attente, comme dans 1 partie de cet exemple.</span><span class="sxs-lookup"><span data-stu-id="ce7c5-110">Run the IBM RfhUtil utility; select the queue manager named ESB.JMS.Sample.QueueManager in the first drop-down list to connect to this queue manager, as in Part 1 of this sample.</span></span>  
  
3.  <span data-ttu-id="ce7c5-111">Dans la deuxième liste déroulante, sélectionnez la file d’attente cible sortant nommé ESB. JMS. EXEMPLE. SENDTOBIZTALK.</span><span class="sxs-lookup"><span data-stu-id="ce7c5-111">In the second drop-down list, select the target outbound queue named ESB.JMS.SAMPLE.SENDTOBIZTALK.</span></span>  
  
4.  <span data-ttu-id="ce7c5-112">Cliquez sur le **ReadFile** bouton dans l’utilitaire RfhUtil et cliquez sur le fichier de message de test nommé TEST-000128. JMS situé dans le sous-dossier nommé \Source\Samples\JMS\Test\Data\Load\\.</span><span class="sxs-lookup"><span data-stu-id="ce7c5-112">Click the **ReadFile** button in the RfhUtil utility, and then navigate to the test message file named TEST-000128.JMS located in the subfolder named \Source\Samples\JMS\Test\Data\Load\\.</span></span> <span data-ttu-id="ce7c5-113">Ce fichier contient un lot de messages de test 128, mais l’utilitaire charge seul le premier.</span><span class="sxs-lookup"><span data-stu-id="ce7c5-113">This file contains a batch of 128 test messages, but the utility loads only the first one.</span></span>  
  
5.  <span data-ttu-id="ce7c5-114">Cliquez sur le **RFH** onglet et assurez-vous que seuls les **JMS** case à cocher est activée.</span><span class="sxs-lookup"><span data-stu-id="ce7c5-114">Click the **RFH** tab, and then make sure that only the **JMS** check box is selected.</span></span>  
  
6.  <span data-ttu-id="ce7c5-115">Cliquez sur le **jms** onglet et assurez-vous que le texte sélectionné **répondre à** file d’attente est ESB. JMS. EXEMPLE. RÉPONSE et que le texte sélectionné **file d’attente de Destination** est ESB. JMS. EXEMPLE. DYNAMICQ2.</span><span class="sxs-lookup"><span data-stu-id="ce7c5-115">Click the **jms** tab, and then make sure that the selected **Reply To** queue is ESB.JMS.SAMPLE.REPLY and that the selected **Destination Queue** is ESB.JMS.SAMPLE.DYNAMICQ2.</span></span>  
  
7.  <span data-ttu-id="ce7c5-116">Cliquez sur le **principal** onglet, puis cliquez sur le **Q d’écrire** bouton pour écrire le message dans la file d’attente.</span><span class="sxs-lookup"><span data-stu-id="ce7c5-116">Click the **Main** tab, and then click the **Write Q** button to write the message into the queue.</span></span>  
  
8.  <span data-ttu-id="ce7c5-117">Après un certain délai pendant que l’application s’exécute, le message de sortie ESB apparaît dans l’architecture ESB. JMS. EXEMPLE. File d’attente de DYNAMICQ2.</span><span class="sxs-lookup"><span data-stu-id="ce7c5-117">After a delay while the application executes, the ESB output message appears in the ESB.JMS.SAMPLE.DYNAMICQ2 queue.</span></span> <span data-ttu-id="ce7c5-118">Ouvrez l’Explorateur de file d’attente WebSphere et parcourir les files d’attente pour le confirmer.</span><span class="sxs-lookup"><span data-stu-id="ce7c5-118">Open the WebSphere Queue Explorer and browse the queues to confirm this.</span></span>  
  
## <a name="how-the-sample-works"></a><span data-ttu-id="ce7c5-119">Fonctionne de l’exemple</span><span class="sxs-lookup"><span data-stu-id="ce7c5-119">How the Sample Works</span></span>  
 <span data-ttu-id="ce7c5-120">À l’intérieur de l’orchestration, code peut accéder aux valeurs qui étaient dans les en-têtes JMS en chargeant le message dans une **XmlDocument** de l’instance, comme indiqué dans le code suivant.</span><span class="sxs-lookup"><span data-stu-id="ce7c5-120">Inside the orchestration, code can access the values that were in the JMS headers by loading the message into an **XmlDocument** instance, as shown in the following code.</span></span>  
  
```csharp  
if (null != InboundMsg(  
    Microsoft.Practices.ESB.JMS.Schemas.Property.MQRFH2_NameValueData))  
{     
  jmsInfo.LoadXml(InboundMsg(  
     Microsoft.Practices.ESB.JMS.Schemas.Property.MQRFH2_NameValueData));  
  if (null != jmsInfo)  
  {  
    if (null != jmsInfo.SelectSingleNode("//Dst"))  
    {  
      xElement = jmsInfo.SelectSingleNode("//Dst");  
      destinationQueue = xElement.InnerText.ToUpper(  
                         System.Globalization.CultureInfo.CurrentCulture);  
    }  
    if (null != jmsInfo.SelectSingleNode("//Rto"))  
    {  
      xElement = jmsInfo.SelectSingleNode("//Rto");  
      replyToQueue = xElement.InnerText.ToUpper(  
                     System.Globalization.CultureInfo.CurrentCulture);  
    }  
  }  
}  
```  
  
 <span data-ttu-id="ce7c5-121">En outre, le code peut accéder à toutes les propriétés de contexte MQMD du message.</span><span class="sxs-lookup"><span data-stu-id="ce7c5-121">In addition, the code can access all of the MQMD context properties of the message.</span></span>