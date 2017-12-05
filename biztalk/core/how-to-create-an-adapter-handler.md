---
title: "Comment créer un gestionnaire d’adaptateur | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- creating, handlers [adapters]
- handlers [adapters], creating
- adapters, handlers
ms.assetid: 09569417-dce6-473d-891f-6fd12347bcf0
caps.latest.revision: "11"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: e26caf02978006040e52ed3c62e520f51362e2c4
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="how-to-create-an-adapter-handler"></a><span data-ttu-id="23e8f-102">Comment créer un gestionnaire d’adaptateur</span><span class="sxs-lookup"><span data-stu-id="23e8f-102">How to Create an Adapter Handler</span></span>
<span data-ttu-id="23e8f-103">Vous pouvez créer un gestionnaire d'adaptateur d'envoi ou de réception à l'aide de la console Administration de BizTalk Server.</span><span class="sxs-lookup"><span data-stu-id="23e8f-103">You can create a send or receive adapter handler by using the BizTalk Server Administration Console.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="23e8f-104">Vous devez être membre du groupe Administrateurs SSO pour créer un gestionnaire d'adaptateur.</span><span class="sxs-lookup"><span data-stu-id="23e8f-104">You must be a member of the Single Sign-On Administrators group to create an adapter handler.</span></span>  
  
### <a name="to-create-an-adapter-handler"></a><span data-ttu-id="23e8f-105">Pour créer un gestionnaire d'adaptateur</span><span class="sxs-lookup"><span data-stu-id="23e8f-105">To create an adapter handler</span></span>  
  
1.  <span data-ttu-id="23e8f-106">Dans la Console Administration de BizTalk Server, développez **Administration de BizTalk Server**, développez **groupe BizTalk**, développez **paramètres de plateforme**, puis développez  **Adaptateurs**.</span><span class="sxs-lookup"><span data-stu-id="23e8f-106">In the BizTalk Server Administration Console, expand **BizTalk Server Administration**, expand **BizTalk Group**, expand **Platform Settings**, and then expand **Adapters**.</span></span>  
  
2.  <span data-ttu-id="23e8f-107">Dans la liste développée des adaptateurs, cliquez sur la carte pour laquelle vous souhaitez ajouter un envoi ou Gestionnaire de réception, pointez sur **nouveau**, puis cliquez sur **Gestionnaire d’envoi** pour créer un gestionnaire d’envoi ou sur  **Gestionnaire de réception** pour créer un gestionnaire de réception.</span><span class="sxs-lookup"><span data-stu-id="23e8f-107">In the expanded adapter list, right-click the adapter for which you would like to add a send or receive handler, point to **New**, and then click **Send Handler** to create a send handler or click **Receive Handler** to create a receive handler.</span></span>  
  
3.  <span data-ttu-id="23e8f-108">Dans le  **\<nom d’hôte\> propriétés** boîte de dialogue le **général** sous l’onglet du **nom d’hôte** , sélectionnez l’hôte avec lequel l’adaptateur gestionnaire sera associé.</span><span class="sxs-lookup"><span data-stu-id="23e8f-108">In the **\<host name\> Properties** dialog box, on the **General** tab, in the **Host Name** list, select the host with which the adapter handler will be associated.</span></span>  
  
4.  <span data-ttu-id="23e8f-109">Si vous créez un gestionnaire d’envoi de l’adaptateur, sélectionnez l’option à **transformer en gestionnaire par défaut** si vous souhaitez que cette le Gestionnaire d’envoi par défaut pour cette carte.</span><span class="sxs-lookup"><span data-stu-id="23e8f-109">If you are creating an adapter send handler, select the option to **Make this the default handler** if you would like for this to be the default send handler for this adapter.</span></span>  
  
5.  <span data-ttu-id="23e8f-110">Cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="23e8f-110">Click **OK**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="23e8f-111">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="23e8f-111">See Also</span></span>  
 [<span data-ttu-id="23e8f-112">Création et suppression de gestionnaires d’adaptateur</span><span class="sxs-lookup"><span data-stu-id="23e8f-112">Creating and Deleting Adapter Handlers</span></span>](../core/creating-and-deleting-adapter-handlers.md)