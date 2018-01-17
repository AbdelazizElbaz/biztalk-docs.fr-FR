---
title: "Étape 17 : Créer l’Application WSClient | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- WSClient application
- message enrichment tutorial, WSClient application
- creating, WSClient application
ms.assetid: 2849cd4c-30d0-47ab-8161-fab379d5a548
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 54eff7c2a455d9f1129bb40d83c002bac92841bd
ms.sourcegitcommit: 3fd1c85d9dc2ce7b77da75a5c2087cc48cfcbe50
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/17/2018
---
# <a name="step-17-create-the-wsclient-application"></a>Étape 17 : Créer l’Application WSClient
WSClient.exe (client de service Web) est une application console écrite en [!INCLUDE[btsVCSharp](../../includes/btsvcsharp-md.md)] qui montre comment envoyer des données à l’orchestration que vous avez publiée en tant qu’un service Web dans les étapes précédentes. L’application WSClient accepte quatre paramètres dans l’ordre d’entrée : patient prénom, deuxième prénom, nom et dernier numéro de sécurité sociale, respectivement. Pour envoyer des informations sur les patients à votre service Web, utilisez la syntaxe de ligne de commande suivante :  
  
```  
wsclient john henry smith 123456789  
```  
  
### <a name="to-create-the-wsclient-application"></a>Pour créer l’application WSClient  
  
1.  Dans l’Explorateur de solutions, cliquez sur **Solution 'BTAHL7V22Common'**, cliquez sur **ajouter**, puis cliquez sur **nouveau projet**.  
  
2.  Dans le **ajouter un nouveau projet** boîte de dialogue le **Types de projets** volet, cliquez sur **Visual C#** et dans le **modèles** volet, cliquez sur **Application console**.  
  
3.  Dans le **nom** , tapez **WSClient**. Dans le **emplacement** champ, accédez à  **\< *lecteur*\>: \Tutorial**, puis cliquez sur **OK**. L’Explorateur de solutions ajoute WSClient à l’arborescence, et le fichier Program.cs s’affiche.  
  
4.  Dans l’Explorateur de solutions, cliquez sur **WSClient**, puis cliquez sur **ajouter une référence Web**.  
  
5.  Dans la boîte de dialogue Ajouter une référence Web, cliquez sur **services Web sur l’ordinateur local**. L’ordinateur local recherche dans les services Web disponibles, puis les affiche dans une liste.  
  
6.  Dans la liste des Services Web sur l’ordinateur Local, cliquez sur **BTAHL7_Project_Doorbell_Orchestration_SOAPReceivePort**, cliquez sur **Operation_1**, puis cliquez sur **ajouter une référence**.  
  
7.  Double-cliquez sur le fichier Program.cs.  
  
8.  Copiez le code suivant et collez-le dans la fenêtre de Program.cs :  
  
    ```  
    using System;  
  
    namespace WSClient  
    {  
       class Class1  
       {  
          [STAThread]  
          static void Main(string[] args)  
          {  
             try   
             {  
                localhost.DoorbellRoot req=new WSClient.localhost.DoorbellRoot();  
                req.FirstName=args[0];  
                req.MiddleName=args[1];  
                req.LastName=args[2];  
                req.SSN=args[3];  
                localhost.BTAHL7_Project_Doorbell_Orchestration_SOAPReceivePort sp=new WSClient.localhost.BTAHL7_Project_Doorbell_Orchestration_SOAPReceivePort();  
                sp.Operation_1(req);  
             }  
             catch (Exception ex)  
             {  
                Console.WriteLine(ex.Message);  
             }  
          }  
       }  
    }  
    ```  
  
9. Dans l’Explorateur de solutions, cliquez sur **WSClient**, puis cliquez sur **Build**. Vérifiez qu’un message de réussite s’affiche dans la fenêtre Sortie. Si aucun message de réussite s’affiche, résoudre les problèmes **WSClient**. [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]place une copie du fichier exécutable, WSClient.exe, dans le \< *lecteur*\>: \Tutorial\WSClient\bin\Debug dossier.  
  
 Passez à [étape 18 : tester votre nouvelle Solution d’enrichissement de Message](../../adapters-and-accelerators/accelerator-hl7/step-18-test-your-new-message-enrichment-solution.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Didacticiel sur l’enrichissement des messages](../../adapters-and-accelerators/accelerator-hl7/message-enrichment-tutorial.md)