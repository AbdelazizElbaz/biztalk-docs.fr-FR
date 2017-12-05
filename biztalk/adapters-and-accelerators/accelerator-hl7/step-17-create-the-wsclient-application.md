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
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="step-17-create-the-wsclient-application"></a><span data-ttu-id="65586-102">Étape 17 : Créer l’Application WSClient</span><span class="sxs-lookup"><span data-stu-id="65586-102">Step 17: Create the WSClient Application</span></span>
<span data-ttu-id="65586-103">WSClient.exe (client de service Web) est une application console écrite en [!INCLUDE[btsVCSharp](../../includes/btsvcsharp-md.md)] qui montre comment envoyer des données à l’orchestration que vous avez publiée en tant qu’un service Web dans les étapes précédentes.</span><span class="sxs-lookup"><span data-stu-id="65586-103">WSClient.exe (Web service client) is a console application written in [!INCLUDE[btsVCSharp](../../includes/btsvcsharp-md.md)] that illustrates how to send data to the orchestration that you published as a Web service in the previous steps.</span></span> <span data-ttu-id="65586-104">L’application WSClient accepte quatre paramètres dans l’ordre d’entrée : patient prénom, deuxième prénom, nom et dernier numéro de sécurité sociale, respectivement.</span><span class="sxs-lookup"><span data-stu-id="65586-104">The WSClient application accepts four input parameters in order: patient first name, middle name, last name, and social security number, respectively.</span></span> <span data-ttu-id="65586-105">Pour envoyer des informations sur les patients à votre service Web, utilisez la syntaxe de ligne de commande suivante :</span><span class="sxs-lookup"><span data-stu-id="65586-105">To send patient information to your Web service, use the following command line syntax:</span></span>  
  
```  
wsclient john henry smith 123456789  
```  
  
### <a name="to-create-the-wsclient-application"></a><span data-ttu-id="65586-106">Pour créer l’application WSClient</span><span class="sxs-lookup"><span data-stu-id="65586-106">To create the WSClient application</span></span>  
  
1.  <span data-ttu-id="65586-107">Dans l’Explorateur de solutions, cliquez sur **Solution 'BTAHL7V22Common'**, cliquez sur **ajouter**, puis cliquez sur **nouveau projet**.</span><span class="sxs-lookup"><span data-stu-id="65586-107">In Solution Explorer, right-click **Solution 'BTAHL7V22Common'**, click **Add**, and then click **New Project**.</span></span>  
  
2.  <span data-ttu-id="65586-108">Dans le **ajouter un nouveau projet** boîte de dialogue le **Types de projets** volet, cliquez sur **Visual C#** et dans le **modèles** volet, cliquez sur **Application console**.</span><span class="sxs-lookup"><span data-stu-id="65586-108">In the **Add New Project** dialog box, in the **Project Types** pane, click **Visual C#** and in the **Templates** pane, click **Console Application**.</span></span>  
  
3.  <span data-ttu-id="65586-109">Dans le **nom** , tapez **WSClient**.</span><span class="sxs-lookup"><span data-stu-id="65586-109">In the **Name** field, type **WSClient**.</span></span> <span data-ttu-id="65586-110">Dans le **emplacement** champ, accédez à  **\<* lecteur*\>: \Tutorial**, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="65586-110">In the **Location** field, browse to **\<*drive*\>:\Tutorial**, and then click **OK**.</span></span> <span data-ttu-id="65586-111">L’Explorateur de solutions ajoute WSClient à l’arborescence, et le fichier Program.cs s’affiche.</span><span class="sxs-lookup"><span data-stu-id="65586-111">Solution Explorer adds WSClient to the tree, and the Program.cs file appears.</span></span>  
  
4.  <span data-ttu-id="65586-112">Dans l’Explorateur de solutions, cliquez sur **WSClient**, puis cliquez sur **ajouter une référence Web**.</span><span class="sxs-lookup"><span data-stu-id="65586-112">In Solution Explorer, right-click **WSClient**, and then click **Add Web Reference**.</span></span>  
  
5.  <span data-ttu-id="65586-113">Dans la boîte de dialogue Ajouter une référence Web, cliquez sur **services Web sur l’ordinateur local**.</span><span class="sxs-lookup"><span data-stu-id="65586-113">In the Add Web Reference dialog box, click **Web services on the local machine**.</span></span> <span data-ttu-id="65586-114">L’ordinateur local recherche dans les services Web disponibles, puis les affiche dans une liste.</span><span class="sxs-lookup"><span data-stu-id="65586-114">The local computer searches for available Web services, and then displays them in a list.</span></span>  
  
6.  <span data-ttu-id="65586-115">Dans la liste des Services Web sur l’ordinateur Local, cliquez sur **BTAHL7_Project_Doorbell_Orchestration_SOAPReceivePort**, cliquez sur **Operation_1**, puis cliquez sur **ajouter une référence**.</span><span class="sxs-lookup"><span data-stu-id="65586-115">In the list of Web Services on the Local Machine, click **BTAHL7_Project_Doorbell_Orchestration_SOAPReceivePort**, click **Operation_1**, and then click **Add Reference**.</span></span>  
  
7.  <span data-ttu-id="65586-116">Double-cliquez sur le fichier Program.cs.</span><span class="sxs-lookup"><span data-stu-id="65586-116">Double-click Program.cs.</span></span>  
  
8.  <span data-ttu-id="65586-117">Copiez le code suivant et collez-le dans la fenêtre de Program.cs :</span><span class="sxs-lookup"><span data-stu-id="65586-117">Copy the following code and then paste it into the Program.cs window:</span></span>  
  
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
  
9. <span data-ttu-id="65586-118">Dans l’Explorateur de solutions, cliquez sur **WSClient**, puis cliquez sur **Build**.</span><span class="sxs-lookup"><span data-stu-id="65586-118">In Solution Explorer, right-click **WSClient**, and then click **Build**.</span></span> <span data-ttu-id="65586-119">Vérifiez qu’un message de réussite s’affiche dans la fenêtre Sortie.</span><span class="sxs-lookup"><span data-stu-id="65586-119">Ensure that a success message appears in the output window.</span></span> <span data-ttu-id="65586-120">Si aucun message de réussite s’affiche, résoudre les problèmes **WSClient**.</span><span class="sxs-lookup"><span data-stu-id="65586-120">If no success message appears, troubleshoot **WSClient**.</span></span> [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]<span data-ttu-id="65586-121">place une copie du fichier exécutable, WSClient.exe, dans le \< *lecteur*\>: \Tutorial\WSClient\bin\Debug dossier.</span><span class="sxs-lookup"><span data-stu-id="65586-121"> places a copy of the executable, WSClient.exe, into the \<*drive*\>:\Tutorial\WSClient\bin\Debug folder.</span></span>  
  
 <span data-ttu-id="65586-122">Passez à [étape 18 : tester votre nouvelle Solution d’enrichissement de Message](../../adapters-and-accelerators/accelerator-hl7/step-18-test-your-new-message-enrichment-solution.md).</span><span class="sxs-lookup"><span data-stu-id="65586-122">Proceed to [Step 18: Test Your New Message Enrichment Solution](../../adapters-and-accelerators/accelerator-hl7/step-18-test-your-new-message-enrichment-solution.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="65586-123">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="65586-123">See Also</span></span>  
 [<span data-ttu-id="65586-124">Didacticiel sur l’enrichissement des messages</span><span class="sxs-lookup"><span data-stu-id="65586-124">Message Enrichment Tutorial</span></span>](../../adapters-and-accelerators/accelerator-hl7/message-enrichment-tutorial.md)