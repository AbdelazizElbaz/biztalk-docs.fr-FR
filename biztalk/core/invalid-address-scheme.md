---
title: "Schéma d’adresse non valide | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0b059289-654e-40d6-a092-2a685e6e10f7
caps.latest.revision: "17"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 385f3aca555f18599887897f6b60144070f252a2
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="invalid-address-scheme"></a><span data-ttu-id="3bba7-102">Schéma d'adresse non valide</span><span class="sxs-lookup"><span data-stu-id="3bba7-102">Invalid address scheme</span></span>
## <a name="details"></a><span data-ttu-id="3bba7-103">Détails</span><span class="sxs-lookup"><span data-stu-id="3bba7-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="3bba7-104">Nom du produit</span><span class="sxs-lookup"><span data-stu-id="3bba7-104">Product Name</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|<span data-ttu-id="3bba7-105">Version du produit</span><span class="sxs-lookup"><span data-stu-id="3bba7-105">Product Version</span></span>|[!INCLUDE[btsWCFVersion](../includes/btswcfversion-md.md)]|  
|<span data-ttu-id="3bba7-106">ID d'événement</span><span class="sxs-lookup"><span data-stu-id="3bba7-106">Event ID</span></span>|<span data-ttu-id="3bba7-107">000</span><span class="sxs-lookup"><span data-stu-id="3bba7-107">000</span></span>|  
|<span data-ttu-id="3bba7-108">Source de l'événement</span><span class="sxs-lookup"><span data-stu-id="3bba7-108">Event Source</span></span>|<span data-ttu-id="3bba7-109">0</span><span class="sxs-lookup"><span data-stu-id="3bba7-109">0</span></span>|  
|<span data-ttu-id="3bba7-110">Composant</span><span class="sxs-lookup"><span data-stu-id="3bba7-110">Component</span></span>|<span data-ttu-id="3bba7-111">0</span><span class="sxs-lookup"><span data-stu-id="3bba7-111">0</span></span>|  
|<span data-ttu-id="3bba7-112">Nom symbolique</span><span class="sxs-lookup"><span data-stu-id="3bba7-112">Symbolic Name</span></span>|<span data-ttu-id="3bba7-113">0</span><span class="sxs-lookup"><span data-stu-id="3bba7-113">0</span></span>|  
|<span data-ttu-id="3bba7-114">Texte du message</span><span class="sxs-lookup"><span data-stu-id="3bba7-114">Message Text</span></span>|<span data-ttu-id="3bba7-115">Schéma d'adresse non valide ; schéma « {0} » attendu.</span><span class="sxs-lookup"><span data-stu-id="3bba7-115">Invalid address scheme; expecting "{0}" scheme.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="3bba7-116">Explication</span><span class="sxs-lookup"><span data-stu-id="3bba7-116">Explanation</span></span>  
 <span data-ttu-id="3bba7-117">Le schéma de protocole fourni ne correspond pas au type défini par votre liaison de transport.</span><span class="sxs-lookup"><span data-stu-id="3bba7-117">You provided a protocol scheme that does not match the type defined by your transport binding.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="3bba7-118">Action de l'utilisateur</span><span class="sxs-lookup"><span data-stu-id="3bba7-118">User Action</span></span>  
 <span data-ttu-id="3bba7-119">Pour résoudre cette erreur, procédez comme suit :</span><span class="sxs-lookup"><span data-stu-id="3bba7-119">To resolve this error, do the following:</span></span>  
  
1.  <span data-ttu-id="3bba7-120">Cliquez sur **Démarrer**, cliquez sur **tous les programmes**, cliquez sur **Microsoft [!INCLUDE[btsBizTalkServer2006r3ui](../includes/btsbiztalkserver2006r3ui-md.md)]** , puis cliquez sur **Administration de BizTalk Server**.</span><span class="sxs-lookup"><span data-stu-id="3bba7-120">Click **Start**, click **All Programs**, click **Microsoft [!INCLUDE[btsBizTalkServer2006r3ui](../includes/btsbiztalkserver2006r3ui-md.md)]**, and click **BizTalk Server Administration**.</span></span>  
  
2.  <span data-ttu-id="3bba7-121">Dans la racine de la Console, développez **Administration de BizTalk Server**, développez **groupe BizTalk**, développez **Applications**.</span><span class="sxs-lookup"><span data-stu-id="3bba7-121">In the Console Root, expand  **BizTalk Server Administration**, expand **BizTalk Group**, and expand  **Applications**.</span></span>  
  
3.  <span data-ttu-id="3bba7-122">Recherchez votre application, puis recherchez votre transport.</span><span class="sxs-lookup"><span data-stu-id="3bba7-122">Locate your application and then locate your transport.</span></span>  
  
4.  <span data-ttu-id="3bba7-123">Cliquez avec le bouton droit sur le nom du transport.</span><span class="sxs-lookup"><span data-stu-id="3bba7-123">Right-click the transport name.</span></span>  
  
5.  <span data-ttu-id="3bba7-124">Cliquez sur **Propriétés**.</span><span class="sxs-lookup"><span data-stu-id="3bba7-124">Click **Properties**.</span></span>  
  
6.  <span data-ttu-id="3bba7-125">Dans le port **Type** , sélectionnez le port approprié.</span><span class="sxs-lookup"><span data-stu-id="3bba7-125">In the port **Type** list, select the correct port.</span></span>  
  
7.  <span data-ttu-id="3bba7-126">Cliquez sur **configurer**.</span><span class="sxs-lookup"><span data-stu-id="3bba7-126">Click **Configure**.</span></span>  
  
8.  <span data-ttu-id="3bba7-127">Dans le **WCF [***type de transport***] propriétés du Transport** boîte de dialogue, cliquez sur le **général** onglet.</span><span class="sxs-lookup"><span data-stu-id="3bba7-127">In the **WCF [***transport type***] Transport Properties** dialog box, click the **General** tab.</span></span>  
  
9. <span data-ttu-id="3bba7-128">Dans le **adresse (URI)** texte zone, assurez-vous que la valeur d’adresse correspond au type de l’adaptateur WCF qui est utilisé.</span><span class="sxs-lookup"><span data-stu-id="3bba7-128">In the **Address (URI)** text box, ensure that address value matches the type of the WCF adapter that is being used.</span></span>  
  
 <span data-ttu-id="3bba7-129">En outre, si vous utilisez l’adaptateur WCF-Custom avec un type de liaison fournie par le système, vérifiez la valeur de la **Type de liaison** liste sur le **liaison** onglet. Si le **Type de liaison** est configuré pour **customBinding**, l’adresse doit correspondre à l’élément de liaison de transport répertoriée dans le **Type de liaison** liste sur le **Liaison** onglet.</span><span class="sxs-lookup"><span data-stu-id="3bba7-129">Also, if you use the WCF-Custom adapter with a system-provided binding type, check the value of the **Binding Type** list on the **Binding** tab. If the **Binding Type** is configured to **customBinding**, the address should match the transport binding element listed in the **Binding Type** list on the **Binding** tab.</span></span>