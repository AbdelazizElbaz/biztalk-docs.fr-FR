---
title: "Pour configurer un MSMQ Gestionnaire de réception | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- receive handlers, MSMQ adapters
- configuring [MSMQ adapters], receive handlers
- MSMQ adapters, receive handlers
ms.assetid: d6d82098-3a73-44e2-80d5-143f77e919cc
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 6f34e1b3f399c93bd92aa9c4e07f6e0082d25204
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-configure-an-msmq-receive-handler"></a><span data-ttu-id="d69f4-102">Comment configurer un gestionnaire de réception MSMQ</span><span class="sxs-lookup"><span data-stu-id="d69f4-102">How to Configure an MSMQ Receive Handler</span></span>
<span data-ttu-id="d69f4-103">Utilisez la procédure suivante pour changer l'hôte auquel le gestionnaire de réception MSMQ est associé.</span><span class="sxs-lookup"><span data-stu-id="d69f4-103">Use the following procedure to change the host with which the MSMQ receive handler is associated.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="d69f4-104">Chaque hôte ne peut être associé qu'à un seul gestionnaire de réception.</span><span class="sxs-lookup"><span data-stu-id="d69f4-104">Each host can associate with only one receive handler.</span></span>  
  
### <a name="to-change-the-host-with-which-the-msmq-receive-handler-is-associated"></a><span data-ttu-id="d69f4-105">Pour changer l'hôte auquel le gestionnaire de réception MSMQ est associé</span><span class="sxs-lookup"><span data-stu-id="d69f4-105">To change the host with which the MSMQ receive handler is associated</span></span>  
  
1.  <span data-ttu-id="d69f4-106">Dans la console Administration de BizTalk Server, développez **Administration de BizTalk Server**, développez **groupe BizTalk**, développez **paramètres de plateforme**, puis développez  **Adaptateurs**.</span><span class="sxs-lookup"><span data-stu-id="d69f4-106">In the BizTalk Server Administration console, expand **BizTalk Server Administration**, expand **BizTalk Group**, expand **Platform Settings**, and then expand **Adapters**.</span></span>  
  
2.  <span data-ttu-id="d69f4-107">Dans la liste développée des adaptateurs, cliquez sur **MSMQ**, dans le volet de droite, avec le bouton du Gestionnaire de réception que vous souhaitez configurer, puis cliquez sur **propriétés**.</span><span class="sxs-lookup"><span data-stu-id="d69f4-107">In the expanded adapter list, click **MSMQ**, in the right pane, right-click the receive handler that you want to configure, and then click **Properties**.</span></span>  
  
3.  <span data-ttu-id="d69f4-108">Dans le **propriétés du Gestionnaire d’adaptateur** boîte de dialogue le **général** sous l’onglet du **nom d’hôte** , sélectionnez l’hôte avec lequel associer le Gestionnaire de réception.</span><span class="sxs-lookup"><span data-stu-id="d69f4-108">In the **Adapter Handler Properties** dialog box, on the **General** tab, in the **Host Name** list, select the host with which the receive handler will be associated.</span></span>  
  
4.  <span data-ttu-id="d69f4-109">Cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="d69f4-109">Click **OK**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d69f4-110">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d69f4-110">See Also</span></span>  
 [<span data-ttu-id="d69f4-111">Configuration de l’adaptateur MSMQ</span><span class="sxs-lookup"><span data-stu-id="d69f4-111">Configuring the MSMQ Adapter</span></span>](../core/configuring-the-msmq-adapter.md)