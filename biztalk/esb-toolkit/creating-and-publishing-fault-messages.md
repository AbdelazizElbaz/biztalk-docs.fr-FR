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
# <a name="creating-and-publishing-fault-messages"></a>Création et la publication des Messages d’erreur
Pour vous aider à comprendre comment utiliser les fonctionnalités de l’infrastructure de gestion des exceptions pour gérer des exceptions, cette section présente un scénario courant en fonction de l’envoi d’un message à une application d’ESB.  
  
 Le scénario est composé d’un utilisateur d’envoyer une facture pour le système. Au cours du traitement de la facture dans une orchestration, le moteur de règles d’entreprise BizTalk lève une exception d’application, car une partie des données est incorrecte. Le processus d’entreprise doit intercepter l’exception, envoyer le message incriminé à une autre personne ou le système peut corriger le message, puis renvoyez le message pour le traitement.  
  
 Lorsque vous utilisez la fonctionnalité d’ESB Échec de l’Orchestration Exception routage, les étapes du processus sont les suivants :  
  
1.  Détecte l’erreur de code dans le Gestionnaire d’exceptions et crée un message d’erreur en appelant le **CreateFaultMessage** méthode, comme indiqué dans l’exemple de code suivant.  
  
    ```csharp  
    // Create fault exception message.  
    faultMsg = Microsoft.Practices.ESB.ExceptionHandling.ExceptionMgmt.CreateFaultMessage();  
    ```  
  
2.  Le mécanisme d’Exception de ESB insère automatiquement la description de l’erreur dans le contexte de message d’erreur (par exemple, « le moteur de règles d’entreprise a levé une division par zéro lors du traitement de la stratégie LoanProcessing. »).  
  
3.  Le mécanisme d’Exception de ESB automatiquement promeut les propriétés spécifiques à l’échec et les propriétés spécifiques à l’application dans le contexte de message d’erreur et définit les valeurs à partir de l’environnement actuel. Ces propriétés sont les suivantes :  
  
    -   **Application** (remplies automatiquement)  
  
    -   **DateTime** (et rempli automatiquement comme valeur UTC)  
  
    -   **Description** (remplies automatiquement, le message d’exception)  
  
    -   **ErrorType** (remplies automatiquement, le type d’exception)  
  
    -   **MachineName** (remplies automatiquement, le nom du serveur)  
  
    -   **Étendue** (remplies automatiquement, la forme étendue qui contient le Gestionnaire d’exceptions en cours)  
  
    -   **ServiceName** (remplies automatiquement, le nom de l’orchestration)  
  
    -   **ServiceInstanceID**(remplies automatiquement : l’ID d’instance d’orchestration en tant que GUID)  
  
4.  Le code dans le Gestionnaire d’exceptions définit d’autres propriétés du message d’erreur en fonction des besoins, comme indiqué dans l’exemple de code suivant.  
  
    ```csharp  
    // Set fault message properties.  
    faultMsg.Body.FailureCategory = "MessageBuild";  
    faultMsg.Body.FaultCode = 1000;  
    faultMsg.Body.FaultDescription = "Some error occurred";  
    faultMsg.Body.FaultSeverity =  
       Microsoft.Practices.ESB.ExceptionHandling.FaultSeverity.Severe;  
    ```  
  
5.  Le mécanisme d’Exception de ESB sérialise automatiquement actuel **Exception** objet dans le message d’erreur.  
  
6.  Si vous le souhaitez, le code dans le Gestionnaire d’exceptions peut ajouter des messages d’orchestration en cours pour le message d’erreur ESB à l’aide du **AddMessage (faultMsg, messageToAdd)** (méthode). Cette méthode sérialise et stocke le message, y compris toutes les propriétés de contexte, comme indiqué dans l’exemple de code suivant.  
  
    ```csharp  
    // Add other current orchestration messages to the fault message.  
    Microsoft.Practices.ESB.ExceptionHandling.ExceptionMgmt.AddMessage(  
                                faultMsg, approvedRequestMsg);  
    Microsoft.Practices.ESB.ExceptionHandling.ExceptionMgmt.AddMessage(  
                                faultMsg, DeniedRequestMsg, @"c:\temp");  
    ```  
  
7.  Code dans le Gestionnaire d’exceptions publie le message d’erreur ESB dans la base de données de la boîte de Message à l’aide d’un port à liaison directe.  
  
8.  Si la publication aboutit, les événements suivants se produisent :  
  
    -   Abonnements de port d’orchestration ou d’envoi peuvent traiter le message d’erreur ESB et extraire des messages ajoutés, avec leurs valeurs de propriété de contexte.  
  
    -   Un gestionnaire d’exceptions global (un port d’envoi) publie automatiquement le message d’erreur ESB dans le portail de gestion ESB.