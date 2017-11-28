---
title: "Comment configurer un gestionnaire d’envoi MSMQ | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- MSMQ adapters, send handlers
- configuring [MSMQ adapters], send handlers
- send handlers, MSMQ adapters
ms.assetid: 21917596-f27a-473b-859e-186ab5f4cd94
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: feacaec9d2794cf8806fa5156fe64b7290699faa
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-configure-an-msmq-send-handler"></a><span data-ttu-id="1e602-102">Configuration d'un gestionnaire d'envoi MSMQ</span><span class="sxs-lookup"><span data-stu-id="1e602-102">How to Configure an MSMQ Send Handler</span></span>
<span data-ttu-id="1e602-103">La procédure suivante permet de modifier les variables globales d'un gestionnaire d'envoi MSMQ.</span><span class="sxs-lookup"><span data-stu-id="1e602-103">Use the following procedure to change the global variables for an MSMQ send handler.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="1e602-104">Un seul gestionnaire d'envoi peut être associé à chaque hôte.</span><span class="sxs-lookup"><span data-stu-id="1e602-104">Each host can have only one send handler associated with it.</span></span>  
  
### <a name="to-change-global-variables-for-an-msmq-send-handler-by-using-the-biztalk-server-administration-console"></a><span data-ttu-id="1e602-105">Pour modifier les variables globales d'un gestionnaire d'envoi MSMQ à l'aide de la console Administration de BizTalk Server.</span><span class="sxs-lookup"><span data-stu-id="1e602-105">To change global variables for an MSMQ send handler by using the BizTalk Server Administration console</span></span>  
  
1.  <span data-ttu-id="1e602-106">Dans la console Administration de BizTalk Server, développez **Administration de BizTalk Server**, développez **groupe BizTalk**, développez **paramètres de plateforme**, puis développez  **Adaptateurs**.</span><span class="sxs-lookup"><span data-stu-id="1e602-106">In the BizTalk Server Administration console, expand **BizTalk Server Administration**, expand **BizTalk Group**, expand **Platform Settings**, and then expand **Adapters**.</span></span>  
  
2.  <span data-ttu-id="1e602-107">Dans la liste développée des adaptateurs, cliquez sur **MSMQ**, dans le volet de droite, avec le bouton du Gestionnaire d’envoi que vous souhaitez configurer, puis cliquez sur **propriétés**.</span><span class="sxs-lookup"><span data-stu-id="1e602-107">In the expanded adapter list, click **MSMQ**, in the right pane, right-click the send handler that you want to configure, and then click **Properties**.</span></span>  
  
3.  <span data-ttu-id="1e602-108">Dans le **propriétés du Gestionnaire d’adaptateur** boîte de dialogue le **général** sous l’onglet le **nom d’hôte** , sélectionnez l’hôte avec lequel le Gestionnaire d’envoi est associé et puis cliquez sur **Propriétés**.</span><span class="sxs-lookup"><span data-stu-id="1e602-108">In the **Adapter Handler Properties** dialog box, on the **General** tab, in the **Host Name** list, select the host with which the send handler will be associated, and then click **Properties**.</span></span>  
  
4.  <span data-ttu-id="1e602-109">Dans le **propriétés du Transport MSMQ** boîte de dialogue, entrez une valeur pour **taille de lot**.</span><span class="sxs-lookup"><span data-stu-id="1e602-109">In the **MSMQ Transport Properties** dialog box, enter a value for **Batch Size**.</span></span>  
  
     <span data-ttu-id="1e602-110">Le Gestionnaire d’envoi MSMQ envoie des messages aux files d’attente de destination à l’aide de la **taille de lot** paramètre.</span><span class="sxs-lookup"><span data-stu-id="1e602-110">The MSMQ send handler will send messages to destination queues using the specified **Batch Size** parameter.</span></span> <span data-ttu-id="1e602-111">La valeur par défaut **taille de lot** valeur est 5.</span><span class="sxs-lookup"><span data-stu-id="1e602-111">The default **Batch Size** value is 5.</span></span>  
  
5.  <span data-ttu-id="1e602-112">Cliquez sur **OK** et cliquez sur **OK** à nouveau pour fermer la **propriétés du Gestionnaire d’adaptateur** boîte de dialogue.</span><span class="sxs-lookup"><span data-stu-id="1e602-112">Click **OK** and click **OK** again to close the **Adapter Handler Properties** dialog box.</span></span>