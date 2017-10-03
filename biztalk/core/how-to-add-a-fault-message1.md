---
title: "L’ajout d’une erreur Message1 | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- exceptions, adding messages
- fault messages, adding
- adding, fault messages
- faults, adding messages
ms.assetid: 9d21de6b-c1a5-46e9-a9dc-d6aa7b5fe34b
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 87ef85460f6ca6aea046ef9efff60fd198664cd1
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-add-a-fault-message"></a><span data-ttu-id="4bf4d-102">Ajout d'un message d'erreur</span><span class="sxs-lookup"><span data-stu-id="4bf4d-102">How to Add a Fault Message</span></span>
<span data-ttu-id="4bf4d-103">Lorsque vous avez commencé par créer le port menant au système principal, il contenait une demande et une réponse.</span><span class="sxs-lookup"><span data-stu-id="4bf4d-103">When you first created the port to the back-end system, it contained a request and a response.</span></span> <span data-ttu-id="4bf4d-104">Vous devez ajouter une erreur pour capturer l'exception.</span><span class="sxs-lookup"><span data-stu-id="4bf4d-104">You must add a fault to capture the exception.</span></span>  
  
### <a name="to-add-a-fault-message"></a><span data-ttu-id="4bf4d-105">Pour ajouter un message d'erreur</span><span class="sxs-lookup"><span data-stu-id="4bf4d-105">To add a fault message</span></span>  
  
1.  <span data-ttu-id="4bf4d-106">Avec le bouton droit **opération de Port**, puis sélectionnez un **nouveau Message d’erreur**.</span><span class="sxs-lookup"><span data-stu-id="4bf4d-106">Right-click **Port Operation**, and then select a **New Fault Message**.</span></span>  
  
     <span data-ttu-id="4bf4d-107">A **erreur** apparaît sous le **demande et réponse** dans le port.</span><span class="sxs-lookup"><span data-stu-id="4bf4d-107">A **Fault** appears under the **Request and Response** in the port.</span></span>  
  
2.  <span data-ttu-id="4bf4d-108">Sur le **Vue Orchestration** de l’écran, cliquez sur **Messages**, puis sélectionnez **nouveau Message**.</span><span class="sxs-lookup"><span data-stu-id="4bf4d-108">On the **Orchestration View** screen, right-click **Messages**, and then select **New Message**.</span></span>  
  
     <span data-ttu-id="4bf4d-109">Ceci crée le message Message_3, que vous pouvez affecter spécifiquement à l'erreur.</span><span class="sxs-lookup"><span data-stu-id="4bf4d-109">This creates Message_3, which you can assign specifically to the fault.</span></span>  
  
3.  <span data-ttu-id="4bf4d-110">Avec le bouton droit **Message_3** pour accéder à la **propriétés** fenêtre.</span><span class="sxs-lookup"><span data-stu-id="4bf4d-110">Right-click **Message_3** to access the **Properties** window.</span></span>  
  
    1.  <span data-ttu-id="4bf4d-111">Définir le **Type de Message**.</span><span class="sxs-lookup"><span data-stu-id="4bf4d-111">Set the **Message Type**.</span></span>  
  
    2.  <span data-ttu-id="4bf4d-112">Sélectionnez **schéma**, puis sélectionnez à partir de **assembly de référence**.</span><span class="sxs-lookup"><span data-stu-id="4bf4d-112">Select **Schema**, and then select from **ref assembly**.</span></span>  
  
         <span data-ttu-id="4bf4d-113">Cette opération ouvre une **sélectionner le Type d’artefact** fenêtre.</span><span class="sxs-lookup"><span data-stu-id="4bf4d-113">This opens a **Select Artifact Type** window.</span></span>  
  
    3.  <span data-ttu-id="4bf4d-114">Faites défiler vers le bas et sélectionnez l'erreur complète.</span><span class="sxs-lookup"><span data-stu-id="4bf4d-114">Scroll down and select the fully qualified fault.</span></span>  
  
         <span data-ttu-id="4bf4d-115">Le nom est **BTS. SOAP_Envelope_1__1.fault**.</span><span class="sxs-lookup"><span data-stu-id="4bf4d-115">The name is **BTS.SOAP_Envelope_1__1.fault**.</span></span> <span data-ttu-id="4bf4d-116">Cliquez sur **OK** pour accepter la sélection et fermer la fenêtre.</span><span class="sxs-lookup"><span data-stu-id="4bf4d-116">Click **OK** to accept the selection and close the window.</span></span>  
  
4.  <span data-ttu-id="4bf4d-117">Avec le bouton droit le **erreur** pour accéder à la **propriétés** fenêtre.</span><span class="sxs-lookup"><span data-stu-id="4bf4d-117">Right-click the **Fault** to access the **Properties** window.</span></span>  
  
    1.  <span data-ttu-id="4bf4d-118">Définir le **Type de Message**.</span><span class="sxs-lookup"><span data-stu-id="4bf4d-118">Set the **Message Type**.</span></span>  
  
    2.  <span data-ttu-id="4bf4d-119">Sélectionnez **schéma** puis sélectionnez à partir de **ref** assembly.</span><span class="sxs-lookup"><span data-stu-id="4bf4d-119">Select **Schema** and then select from **ref** assembly.</span></span>  
  
         <span data-ttu-id="4bf4d-120">Cette opération ouvre une **sélectionner le Type d’artefact** fenêtre.</span><span class="sxs-lookup"><span data-stu-id="4bf4d-120">This opens a **Select Artifact Type** window.</span></span>  
  
    3.  <span data-ttu-id="4bf4d-121">Faites défiler vers le bas et sélectionnez l'erreur complète.</span><span class="sxs-lookup"><span data-stu-id="4bf4d-121">Scroll down and select the fully qualified fault.</span></span>  
  
         <span data-ttu-id="4bf4d-122">Le nom est **BTS. SOAP_Envelope_1__1.fault**.</span><span class="sxs-lookup"><span data-stu-id="4bf4d-122">The name is **BTS.SOAP_Envelope_1__1.fault**.</span></span>  
  
    4.  <span data-ttu-id="4bf4d-123">Cliquez sur **OK** pour accepter la sélection et fermer la fenêtre.</span><span class="sxs-lookup"><span data-stu-id="4bf4d-123">Click **OK** to accept the selection and close the window.</span></span>  
  
         ![](../core/media/siebeladapter-17-exceptionhandling-addscope.gif "SiebelAdapter_17_ExceptionHandling_AddScope")  
  
5.  <span data-ttu-id="4bf4d-124">Une fois l'erreur nommée, vous définissez ce nom sur le type d'objet d'exception de CatchException.</span><span class="sxs-lookup"><span data-stu-id="4bf4d-124">After the fault is named, you will set this name to the CatchException's exception object type.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4bf4d-125">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="4bf4d-125">See Also</span></span>  
 [<span data-ttu-id="4bf4d-126">À l’aide de la gestion des exceptions de BizTalk Server</span><span class="sxs-lookup"><span data-stu-id="4bf4d-126">Using BizTalk Server Exception Handling</span></span>](../core/using-biztalk-server-exception-handling2.md)