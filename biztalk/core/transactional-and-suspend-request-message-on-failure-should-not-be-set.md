---
title: "L’option transactions &quot;transactionnel&quot; et l’option Gestion d’erreur &quot;suspendre le message de demande en cas d’échec&quot; pas les deux doivent être définies sur false | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: cc6c66cc-6713-4396-b0d4-ac6a0e72164f
caps.latest.revision: "11"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: bf8c47e364fccdb310167e56c6556423c2d4b39d
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="transactions-option-quottransactionalquot-and-the-error-handling-option-quotsuspend-request-message-on-failurequot-should-not-both-be-set-to-false"></a><span data-ttu-id="710b9-102">L’option transactions &quot;transactionnel&quot; et l’option Gestion d’erreur &quot;suspendre le message de demande en cas d’échec&quot; pas les deux doivent être définies sur false</span><span class="sxs-lookup"><span data-stu-id="710b9-102">Transactions option &quot;Transactional&quot; and the error handling option &quot;Suspend request message on failure&quot; should not both be set to false</span></span>
## <a name="details"></a><span data-ttu-id="710b9-103">Détails</span><span class="sxs-lookup"><span data-stu-id="710b9-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="710b9-104">Nom du produit</span><span class="sxs-lookup"><span data-stu-id="710b9-104">Product Name</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|<span data-ttu-id="710b9-105">Version du produit</span><span class="sxs-lookup"><span data-stu-id="710b9-105">Product Version</span></span>|[!INCLUDE[btsWCFVersion](../includes/btswcfversion-md.md)]|  
|<span data-ttu-id="710b9-106">ID d'événement</span><span class="sxs-lookup"><span data-stu-id="710b9-106">Event ID</span></span>|<span data-ttu-id="710b9-107">0</span><span class="sxs-lookup"><span data-stu-id="710b9-107">0</span></span>|  
|<span data-ttu-id="710b9-108">Source de l'événement</span><span class="sxs-lookup"><span data-stu-id="710b9-108">Event Source</span></span>|<span data-ttu-id="710b9-109">0</span><span class="sxs-lookup"><span data-stu-id="710b9-109">0</span></span>|  
|<span data-ttu-id="710b9-110">Composant</span><span class="sxs-lookup"><span data-stu-id="710b9-110">Component</span></span>|<span data-ttu-id="710b9-111">0</span><span class="sxs-lookup"><span data-stu-id="710b9-111">0</span></span>|  
|<span data-ttu-id="710b9-112">Nom symbolique</span><span class="sxs-lookup"><span data-stu-id="710b9-112">Symbolic Name</span></span>|<span data-ttu-id="710b9-113">0</span><span class="sxs-lookup"><span data-stu-id="710b9-113">0</span></span>|  
|<span data-ttu-id="710b9-114">Texte du message</span><span class="sxs-lookup"><span data-stu-id="710b9-114">Message Text</span></span>|<span data-ttu-id="710b9-115">L'option des transactions « Transactionnel » et l'option de gestion des erreurs « Suspendre le message de requête en cas d'échec » ne doivent pas être toutes deux définies sur False, faute de quoi des messages pourraient être perdus.</span><span class="sxs-lookup"><span data-stu-id="710b9-115">The transactions option "Transactional" and the error handling option "Suspend request message on failure" should not both be set to false since message loss may occur.</span></span> <span data-ttu-id="710b9-116">Définissez une ou les deux options à la valeur true.</span><span class="sxs-lookup"><span data-stu-id="710b9-116">Please set one or both options to true.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="710b9-117">Explication</span><span class="sxs-lookup"><span data-stu-id="710b9-117">Explanation</span></span>  
 <span data-ttu-id="710b9-118">Dans l’adaptateur WCF-NetMsmq, les options **transactionnel** et **suspendre le message de demande en cas d’échec** pas les deux doivent être définies sur false (désactivé).</span><span class="sxs-lookup"><span data-stu-id="710b9-118">In the WCF-NetMsmq adapter, the options **Transactional** and **Suspend request message on failure** should not both be set to false (unchecked).</span></span> <span data-ttu-id="710b9-119">Une perte de message peut se produire si l'envoi du message ayant échoué n'a pas été annulé en tant que transaction, alors que le message n'a pas été suspendu ni stocké dans la base de données MessageBox.</span><span class="sxs-lookup"><span data-stu-id="710b9-119">Message loss may occur if the failed message submission does not roll back as a transaction, while the message is not suspended and stored in the Message Box.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="710b9-120">Action de l'utilisateur</span><span class="sxs-lookup"><span data-stu-id="710b9-120">User Action</span></span>  
 <span data-ttu-id="710b9-121">La procédure suivante permet de vérifier les paramètres de l'adaptateur.</span><span class="sxs-lookup"><span data-stu-id="710b9-121">Use the following procedure to verify adapter settings.</span></span>  
  
#### <a name="to-verify-adapter-settings"></a><span data-ttu-id="710b9-122">Pour vérifier les paramètres de l'adaptateur</span><span class="sxs-lookup"><span data-stu-id="710b9-122">To verify adapter settings</span></span>  
  
1.  <span data-ttu-id="710b9-123">Cliquez sur **Démarrer**, cliquez sur **tous les programmes**, cliquez sur [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], puis cliquez sur **Administration de BizTalk Server**.</span><span class="sxs-lookup"><span data-stu-id="710b9-123">Click **Start**, click **All Programs**, click [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], and click **BizTalk Server Administration**.</span></span>  
  
2.  <span data-ttu-id="710b9-124">Dans la racine de la Console, développez [!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)], développez **groupe BizTalk**, développez **Applications**.</span><span class="sxs-lookup"><span data-stu-id="710b9-124">In the Console Root, expand [!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)], expand **BizTalk Group**, and expand  **Applications**.</span></span>  
  
3.  <span data-ttu-id="710b9-125">Recherchez votre application, puis recherchez votre transport.</span><span class="sxs-lookup"><span data-stu-id="710b9-125">Locate your application and then locate your transport.</span></span>  
  
4.  <span data-ttu-id="710b9-126">Cliquez avec le bouton droit sur le nom du transport.</span><span class="sxs-lookup"><span data-stu-id="710b9-126">Right-click the transport name.</span></span>  
  
5.  <span data-ttu-id="710b9-127">Cliquez sur **Propriétés**.</span><span class="sxs-lookup"><span data-stu-id="710b9-127">Click **Properties**.</span></span>  
  
6.  <span data-ttu-id="710b9-128">Dans le port **Type** , sélectionnez le port approprié.</span><span class="sxs-lookup"><span data-stu-id="710b9-128">In the port **Type** list, select the correct port.</span></span>  
  
7.  <span data-ttu-id="710b9-129">Cliquez sur **configurer**.</span><span class="sxs-lookup"><span data-stu-id="710b9-129">Click **Configure**.</span></span>  
  
8.  <span data-ttu-id="710b9-130">Dans le **propriétés du Transport WCF-NetMsmq** boîte de dialogue, cliquez sur le **liaison** onglet.</span><span class="sxs-lookup"><span data-stu-id="710b9-130">In the **WCF-NetMsmq Transport Properties** dialog box, click the **Binding** tab.</span></span>  
  
9. <span data-ttu-id="710b9-131">Dans le **Transactions** section, déterminez si **transactionnel** est activée.</span><span class="sxs-lookup"><span data-stu-id="710b9-131">In the **Transactions** section, determine if **Transactional** is checked.</span></span>  
  
10. <span data-ttu-id="710b9-132">Cliquez sur le **Messages** onglet.</span><span class="sxs-lookup"><span data-stu-id="710b9-132">Click the **Messages** tab.</span></span>  
  
11. <span data-ttu-id="710b9-133">Déterminer si **suspendre le message de demande en cas d’échec** est activée.</span><span class="sxs-lookup"><span data-stu-id="710b9-133">Determine if **Suspend request message on failure** is checked.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="710b9-134">Ces étapes s'appliquent uniquement aux emplacements de réception.</span><span class="sxs-lookup"><span data-stu-id="710b9-134">These steps only apply to receive locations.</span></span>