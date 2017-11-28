---
title: Comment configurer la forme attente | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Delay shape [Orchestration Designer], configuring
- Delay shape [Orchestration Designer]
- Delay shape [Orchestration Designer], timeouts
- Delay shape [Orchestration Designer], about Delay shape
- configuring [Orchestration Designer], Delay shapes
ms.assetid: 727be28d-932a-41d5-af3f-3ee6f7129a17
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 0b76448398facd3af7f3b9712491f9895ffb406d
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-configure-the-delay-shape"></a><span data-ttu-id="9ee7b-102">Configuration de la forme Attente</span><span class="sxs-lookup"><span data-stu-id="9ee7b-102">How to Configure the Delay Shape</span></span>
![](../core/media/ebiz-orch-delay.gif "ebiz_orch_delay")  
<span data-ttu-id="9ee7b-103">Forme Attente</span><span class="sxs-lookup"><span data-stu-id="9ee7b-103">Delay shape</span></span>  
  
 <span data-ttu-id="9ee7b-104">Il existe deux façons de spécifier le délai d’attente pour un **délai**:</span><span class="sxs-lookup"><span data-stu-id="9ee7b-104">There are two ways to specify the timeout for a **Delay**:</span></span>  
  
-   <span data-ttu-id="9ee7b-105">Vous pouvez utiliser **System.DateTime**, ce qui entraîne l’orchestration en attente jusqu'à la date et heure est atteinte.</span><span class="sxs-lookup"><span data-stu-id="9ee7b-105">You can use **System.DateTime**, which causes your orchestration to pause until the specified date and time is reached.</span></span>  
  
     <span data-ttu-id="9ee7b-106">System.DateTime.UtcNow.AddSeconds(60)</span><span class="sxs-lookup"><span data-stu-id="9ee7b-106">System.DateTime.UtcNow.AddSeconds(60)</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="9ee7b-107">Retards doivent être exprimées en temps universel coordonné (UTC) lors de l’utilisation **DateTime**.</span><span class="sxs-lookup"><span data-stu-id="9ee7b-107">Delays must be expressed in Coordinated Universal Time (UTC) when using **DateTime**.</span></span>  
  
-   <span data-ttu-id="9ee7b-108">Vous pouvez utiliser **System.TimeSpan**, ce qui entraîne l’orchestration en attente pendant la durée spécifiée.</span><span class="sxs-lookup"><span data-stu-id="9ee7b-108">You can use **System.TimeSpan**, which causes your orchestration to pause for the specified length of time.</span></span>  
  
     <span data-ttu-id="9ee7b-109">System.TimeSpan(0, 1, 0)</span><span class="sxs-lookup"><span data-stu-id="9ee7b-109">System.TimeSpan(0, 1, 0)</span></span>  
  
 <span data-ttu-id="9ee7b-110">Si votre **délai** forme se trouve dans un **écouter** forme, vous n’avez pas besoin d’ajouter un point-virgule à la fin de l’expression.</span><span class="sxs-lookup"><span data-stu-id="9ee7b-110">If your **Delay** shape is inside a **Listen** shape, you do not need to add a semicolon at the end of the expression.</span></span>  
  
 <span data-ttu-id="9ee7b-111">Pour plus d’informations sur **System.DateTime** et **System.TimeSpan**, consultez « Structure DateTime » et « TimeSpan Structure » dans la [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] Collection combinée.</span><span class="sxs-lookup"><span data-stu-id="9ee7b-111">For more information about **System.DateTime** and **System.TimeSpan**, see "DateTime Structure" and "TimeSpan Structure" in the [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] Combined Collection.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="9ee7b-112">Dans un environnement à plusieurs ordinateurs installation où [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] et SQL Server sont installés sur des ordinateurs séparés, la **délai** forme peut prendre fin plus tôt que prévu en raison du temps sur [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] et [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] ordinateurs ne sont pas synchronisées.</span><span class="sxs-lookup"><span data-stu-id="9ee7b-112">In a multiple machines installation environment where [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] and SQL Server are installed on separated machines, the **Delay** shape may end earlier than expected because of the times on [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] and [!INCLUDE[btsSQLServerNoVersion](../includes/btssqlservernoversion-md.md)] machines are unsynchronized.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="9ee7b-113">Condition de stress, le délai d’expiration spécifié dans le **délai** forme peut se produire plus tard que ce que vous avez spécifié.</span><span class="sxs-lookup"><span data-stu-id="9ee7b-113">Under the stress condition, the timeout specified in the **Delay** shape may occur later than what you have specified.</span></span> <span data-ttu-id="9ee7b-114">Ceci est dû à la pénurie de threads constatée en condition de stress.</span><span class="sxs-lookup"><span data-stu-id="9ee7b-114">This is because of the thread starvation under the stress condition.</span></span>  
  
### <a name="to-configure-a-delay-shape"></a><span data-ttu-id="9ee7b-115">Pour configurer une forme Attente</span><span class="sxs-lookup"><span data-stu-id="9ee7b-115">To configure a Delay shape</span></span>  
  
1.  <span data-ttu-id="9ee7b-116">Si l’éditeur d’Expression BizTalk n’est pas visible, cliquez sur le **délai** mettre en forme et cliquez sur **modifier le délai**, ou dans la fenêtre Propriétés, cliquez sur le **points de suspension** ( **...** ) bouton pour le **Expression** propriété.</span><span class="sxs-lookup"><span data-stu-id="9ee7b-116">If BizTalk Expression Editor is not visible, right-click the **Delay** shape and click **Edit Delay**, or in the Properties window, click the **Ellipsis** (**...**) button for the **Expression** property.</span></span>  
  
2.  <span data-ttu-id="9ee7b-117">Dans Éditeur d’Expression BizTalk, créez une expression qui retourne un **System.DateTime** objet ou un **System.TimeSpan** objet.</span><span class="sxs-lookup"><span data-stu-id="9ee7b-117">In BizTalk Expression Editor, create an expression that returns a **System.DateTime** object or a **System.TimeSpan** object.</span></span> <span data-ttu-id="9ee7b-118">Pour plus d’informations, consultez [spécifications et Limitations pour les Expressions](../core/requirements-and-limitations-for-expressions.md).</span><span class="sxs-lookup"><span data-stu-id="9ee7b-118">For more information, see [Requirements and Limitations for Expressions](../core/requirements-and-limitations-for-expressions.md).</span></span>