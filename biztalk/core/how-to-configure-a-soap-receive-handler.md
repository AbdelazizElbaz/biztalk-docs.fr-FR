---
title: "Pour configurer un protocole SOAP Gestionnaire de réception | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- configuring [SOAP adapters], receive handlers
- SOAP adapters, receive handlers
- receive handlers, SOAP adapters
ms.assetid: e1174381-f36c-4131-83b7-26bfa879802e
caps.latest.revision: "12"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 4054635a8ffa4e019f7db9513e5e20e997f7e291
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-configure-a-soap-receive-handler"></a><span data-ttu-id="64964-102">Pour configurer les Gestionnaire de réception SOAP</span><span class="sxs-lookup"><span data-stu-id="64964-102">How to Configure a SOAP Receive Handler</span></span>
<span data-ttu-id="64964-103">Vous pouvez configurer les paramètres du gestionnaire de réception SOAP à l'aide de la console Administration de BizTalk Server.</span><span class="sxs-lookup"><span data-stu-id="64964-103">You can configure the SOAP receive handler settings by using the BizTalk Server Administration Console.</span></span> <span data-ttu-id="64964-104">Dans ce cas, il n'est pas nécessaire de définir les propriétés de remplacement de gestionnaire dans BizTalk Explorer.</span><span class="sxs-lookup"><span data-stu-id="64964-104">If you configure the adapter using the BizTalk Server Administration Console, the handler override properties do not need to be set in BizTalk Explorer.</span></span>  
  
### <a name="to-change-global-variables-for-the-soap-receive-handler"></a><span data-ttu-id="64964-105">Pour modifier des variables globales du gestionnaire de réception SOAP</span><span class="sxs-lookup"><span data-stu-id="64964-105">To change global variables for the SOAP receive handler</span></span>  
  
1.  <span data-ttu-id="64964-106">Dans la Console Administration de BizTalk Server, développez [!INCLUDE[btsBizTalkServer2006r3ui](../includes/btsbiztalkserver2006r3ui-md.md)] **Administration**, développez **groupe BizTalk**, développez **paramètres de plateforme**, puis développez  **Adaptateurs**.</span><span class="sxs-lookup"><span data-stu-id="64964-106">In the BizTalk Server Administration Console, expand [!INCLUDE[btsBizTalkServer2006r3ui](../includes/btsbiztalkserver2006r3ui-md.md)] **Administration**, expand **BizTalk Group**, expand **Platform Settings**, and then expand **Adapters**.</span></span>  
  
2.  <span data-ttu-id="64964-107">Dans la liste développée des adaptateurs, cliquez sur **SOAP**, dans le volet de droite, avec le bouton du Gestionnaire de réception que vous souhaitez configurer, puis cliquez sur **propriétés**.</span><span class="sxs-lookup"><span data-stu-id="64964-107">In the expanded adapter list, click **SOAP**, in the right pane, right-click the receive handler that you want to configure, and then click **Properties**.</span></span>  
  
3.  <span data-ttu-id="64964-108">Dans le **propriétés du Gestionnaire d’adaptateur** boîte de dialogue le **général** sous l’onglet le **nom d’hôte** , sélectionnez l’hôte auquel le Gestionnaire de réception sera associé, puis Cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="64964-108">In the **Adapter Handler Properties** dialog box, on the **General** tab, in the **Host Name** list, select the host with which the receive handler will be associated, and then click **OK**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="64964-109">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="64964-109">See Also</span></span>  
 <span data-ttu-id="64964-110">[Configuration de l’adaptateur SOAP](../core/configuring-the-soap-adapter.md) </span><span class="sxs-lookup"><span data-stu-id="64964-110">[Configuring the SOAP Adapter](../core/configuring-the-soap-adapter.md) </span></span>  
 [<span data-ttu-id="64964-111">Utilisation de Services Web</span><span class="sxs-lookup"><span data-stu-id="64964-111">Consuming Web Services</span></span>](../core/consuming-web-services.md)