---
title: "Création et publication de Messages d’erreur | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: cc7ba1d9-b647-4cba-a3dc-4400505ff51f
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 57833cefedcf53b7355c17cf97d429d2eb988819
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="creating-and-publishing-fault-messages"></a><span data-ttu-id="bf8a3-102">Création et la publication des Messages d’erreur</span><span class="sxs-lookup"><span data-stu-id="bf8a3-102">Creating and Publishing Fault Messages</span></span>
<span data-ttu-id="bf8a3-103">Pour vous aider à comprendre comment utiliser les fonctionnalités de l’infrastructure de gestion des exceptions pour gérer des exceptions, cette section présente un scénario courant en fonction de l’envoi d’un message à une application d’ESB.</span><span class="sxs-lookup"><span data-stu-id="bf8a3-103">To help you understand how to use the features of the Exception Management Framework to manage exceptions, this section presents a common scenario based on the submission of a message to an ESB application.</span></span>  
  
 <span data-ttu-id="bf8a3-104">Le scénario est composé d’un utilisateur d’envoyer une facture pour le système.</span><span class="sxs-lookup"><span data-stu-id="bf8a3-104">The scenario consists of a user submitting an invoice to the system.</span></span> <span data-ttu-id="bf8a3-105">Au cours du traitement de la facture dans une orchestration, le moteur de règles d’entreprise BizTalk lève une exception d’application, car une partie des données est incorrecte.</span><span class="sxs-lookup"><span data-stu-id="bf8a3-105">During the course of processing the invoice in an orchestration, the BizTalk Business Rules Engine throws an application exception because some part of the data is incorrect.</span></span> <span data-ttu-id="bf8a3-106">Le processus d’entreprise doit intercepter l’exception, envoyer le message incriminé à une autre personne ou le système peut corriger le message, puis renvoyez le message pour le traitement.</span><span class="sxs-lookup"><span data-stu-id="bf8a3-106">The business process should catch the exception, send the offending message to another person or system that can correct the message, and then resubmit the message for processing.</span></span>  
  
 <span data-ttu-id="bf8a3-107">Lorsque vous utilisez la fonctionnalité d’ESB Échec de l’Orchestration Exception routage, les étapes du processus sont les suivants :</span><span class="sxs-lookup"><span data-stu-id="bf8a3-107">When using the ESB Failed Orchestration Exception Routing feature, the process steps are the following:</span></span>  
  
1.  <span data-ttu-id="bf8a3-108">Détecte l’erreur de code dans le Gestionnaire d’exceptions et crée un message d’erreur en appelant le **CreateFaultMessage** méthode, comme indiqué dans l’exemple de code suivant.</span><span class="sxs-lookup"><span data-stu-id="bf8a3-108">Code in the exception handler detects the error and creates a fault message by calling the **CreateFaultMessage** method, as shown in the following code example.</span></span>  
  
    ```csharp  
    // Create fault exception message.  
    faultMsg = Microsoft.Practices.ESB.ExceptionHandling.ExceptionMgmt.CreateFaultMessage();  
    ```  
  
2.  <span data-ttu-id="bf8a3-109">Le mécanisme d’Exception de ESB insère automatiquement la description de l’erreur dans le contexte de message d’erreur (par exemple, « le moteur de règles d’entreprise a levé une division par zéro lors du traitement de la stratégie LoanProcessing. »).</span><span class="sxs-lookup"><span data-stu-id="bf8a3-109">The ESB Exception mechanism automatically inserts the error description into the fault message context (for example, "The Business Rules Engine threw a divide by zero error while processing the LoanProcessing policy.").</span></span>  
  
3.  <span data-ttu-id="bf8a3-110">Le mécanisme d’Exception de ESB automatiquement promeut les propriétés spécifiques à l’échec et les propriétés spécifiques à l’application dans le contexte de message d’erreur et définit les valeurs à partir de l’environnement actuel.</span><span class="sxs-lookup"><span data-stu-id="bf8a3-110">The ESB Exception mechanism automatically promotes failure-specific properties and application-specific properties into the fault message context and sets the values from the current environment.</span></span> <span data-ttu-id="bf8a3-111">Ces propriétés sont les suivantes :</span><span class="sxs-lookup"><span data-stu-id="bf8a3-111">These properties are the following:</span></span>  
  
    -   <span data-ttu-id="bf8a3-112">**Application** (remplies automatiquement)</span><span class="sxs-lookup"><span data-stu-id="bf8a3-112">**Application** (auto-populated)</span></span>  
  
    -   <span data-ttu-id="bf8a3-113">**DateTime** (et rempli automatiquement comme valeur UTC)</span><span class="sxs-lookup"><span data-stu-id="bf8a3-113">**DateTime** (auto-populated as a UTC value)</span></span>  
  
    -   <span data-ttu-id="bf8a3-114">**Description** (remplies automatiquement, le message d’exception)</span><span class="sxs-lookup"><span data-stu-id="bf8a3-114">**Description** (auto-populated—the exception message)</span></span>  
  
    -   <span data-ttu-id="bf8a3-115">**ErrorType** (remplies automatiquement, le type d’exception)</span><span class="sxs-lookup"><span data-stu-id="bf8a3-115">**ErrorType** (auto-populated—the exception type)</span></span>  
  
    -   <span data-ttu-id="bf8a3-116">**MachineName** (remplies automatiquement, le nom du serveur)</span><span class="sxs-lookup"><span data-stu-id="bf8a3-116">**MachineName** (auto-populated—the current server name)</span></span>  
  
    -   <span data-ttu-id="bf8a3-117">**Étendue** (remplies automatiquement, la forme étendue qui contient le Gestionnaire d’exceptions en cours)</span><span class="sxs-lookup"><span data-stu-id="bf8a3-117">**Scope** (auto-populated—the Scope shape that contains the current exception handler)</span></span>  
  
    -   <span data-ttu-id="bf8a3-118">**ServiceName** (remplies automatiquement, le nom de l’orchestration)</span><span class="sxs-lookup"><span data-stu-id="bf8a3-118">**ServiceName** (auto-populated—the orchestration name)</span></span>  
  
    -   <span data-ttu-id="bf8a3-119">**ServiceInstanceID**(remplies automatiquement : l’ID d’instance d’orchestration en tant que GUID)</span><span class="sxs-lookup"><span data-stu-id="bf8a3-119">**ServiceInstanceID**(auto-populated—the orchestration instance ID as a GUID)</span></span>  
  
4.  <span data-ttu-id="bf8a3-120">Le code dans le Gestionnaire d’exceptions définit d’autres propriétés du message d’erreur en fonction des besoins, comme indiqué dans l’exemple de code suivant.</span><span class="sxs-lookup"><span data-stu-id="bf8a3-120">Code in the exception handler sets other properties of the fault message as required, as shown in the following code example.</span></span>  
  
    ```csharp  
    // Set fault message properties.  
    faultMsg.Body.FailureCategory = "MessageBuild";  
    faultMsg.Body.FaultCode = 1000;  
    faultMsg.Body.FaultDescription = "Some error occurred";  
    faultMsg.Body.FaultSeverity =  
       Microsoft.Practices.ESB.ExceptionHandling.FaultSeverity.Severe;  
    ```  
  
5.  <span data-ttu-id="bf8a3-121">Le mécanisme d’Exception de ESB sérialise automatiquement actuel **Exception** objet dans le message d’erreur.</span><span class="sxs-lookup"><span data-stu-id="bf8a3-121">The ESB Exception mechanism automatically serializes the current **Exception** object into the fault message.</span></span>  
  
6.  <span data-ttu-id="bf8a3-122">Si vous le souhaitez, le code dans le Gestionnaire d’exceptions peut ajouter des messages d’orchestration en cours pour le message d’erreur ESB à l’aide du **AddMessage (faultMsg, messageToAdd)** (méthode).</span><span class="sxs-lookup"><span data-stu-id="bf8a3-122">Optionally, code in the exception handler can add current orchestration messages to the ESB fault message using the **AddMessage(faultMsg, messageToAdd)** method.</span></span> <span data-ttu-id="bf8a3-123">Cette méthode sérialise et stocke le message, y compris toutes les propriétés de contexte, comme indiqué dans l’exemple de code suivant.</span><span class="sxs-lookup"><span data-stu-id="bf8a3-123">This method serializes and persists the message, including all the context properties, as shown in the following code example.</span></span>  
  
    ```csharp  
    // Add other current orchestration messages to the fault message.  
    Microsoft.Practices.ESB.ExceptionHandling.ExceptionMgmt.AddMessage(  
                                faultMsg, approvedRequestMsg);  
    Microsoft.Practices.ESB.ExceptionHandling.ExceptionMgmt.AddMessage(  
                                faultMsg, DeniedRequestMsg, @"c:\temp");  
    ```  
  
7.  <span data-ttu-id="bf8a3-124">Code dans le Gestionnaire d’exceptions publie le message d’erreur ESB dans la base de données de la boîte de Message à l’aide d’un port à liaison directe.</span><span class="sxs-lookup"><span data-stu-id="bf8a3-124">Code in the exception handler publishes the ESB fault message to the Message Box database using a direct bound port.</span></span>  
  
8.  <span data-ttu-id="bf8a3-125">Si la publication aboutit, les événements suivants se produisent :</span><span class="sxs-lookup"><span data-stu-id="bf8a3-125">If publishing succeeds, the following events occur:</span></span>  
  
    -   <span data-ttu-id="bf8a3-126">Abonnements de port d’orchestration ou d’envoi peuvent traiter le message d’erreur ESB et extraire des messages ajoutés, avec leurs valeurs de propriété de contexte.</span><span class="sxs-lookup"><span data-stu-id="bf8a3-126">Orchestration or send port subscriptions can process the ESB fault message and extract any added messages, complete with their context property values.</span></span>  
  
    -   <span data-ttu-id="bf8a3-127">Un gestionnaire d’exceptions global (un port d’envoi) publie automatiquement le message d’erreur ESB dans le portail de gestion ESB.</span><span class="sxs-lookup"><span data-stu-id="bf8a3-127">A global exception handler (a send port) automatically publishes the ESB fault message to the ESB Management Portal.</span></span>