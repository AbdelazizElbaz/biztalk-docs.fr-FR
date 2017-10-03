---
title: "Comment créer des Ports d’envoi pour JD Edwards OneWorld | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- creating send ports
- send ports, creating
ms.assetid: 858425ef-bdb7-4d2d-90ca-b3655e389749
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: fc77fd72171983ab2fbc7de42ddf36d770d045c6
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-create-send-ports-for-jd-edwards-oneworld"></a><span data-ttu-id="c1a32-102">Création de ports d'envoi pour JD Edwards OneWorld</span><span class="sxs-lookup"><span data-stu-id="c1a32-102">How to Create Send Ports for JD Edwards OneWorld</span></span>
<span data-ttu-id="c1a32-103">La procédure suivante permet de créer un port d'envoi.</span><span class="sxs-lookup"><span data-stu-id="c1a32-103">Use the following procedure to create a send port.</span></span>  
  
### <a name="to-create-a-send-port"></a><span data-ttu-id="c1a32-104">Pour créer un port d’envoi</span><span class="sxs-lookup"><span data-stu-id="c1a32-104">To create a send port</span></span>  
  
1.  <span data-ttu-id="c1a32-105">Dans la Console Administration de BizTalk Server, développez **Administration de BizTalk Server**, développez **groupe BizTalk**, développez **Applications**, puis accédez à la application requise.</span><span class="sxs-lookup"><span data-stu-id="c1a32-105">In the BizTalk Server Administration Console, expand **BizTalk Server Administration**, expand **BizTalk Group**, expand **Applications**, and then navigate to the required application.</span></span>  
  
2.  <span data-ttu-id="c1a32-106">Avec le bouton droit **Ports d’envoi**, pointez sur **nouveau**, puis cliquez sur **Port d’envoi statique avec sollicitation-réponse**.</span><span class="sxs-lookup"><span data-stu-id="c1a32-106">Right-click **Send Ports**, point to **New**, and then click **Static Solicit-Response Send Port**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="c1a32-107">Vous pouvez également utiliser **Port statique unidirectionnel**.</span><span class="sxs-lookup"><span data-stu-id="c1a32-107">You can also use **Static One-Way Port**.</span></span>  
  
3.  <span data-ttu-id="c1a32-108">Dans le **propriétés de Port d’envoi** boîte de dialogue le **nom** , tapez le nom du port d’envoi (par exemple, tapez **SendToJDE**.)</span><span class="sxs-lookup"><span data-stu-id="c1a32-108">In the **Send Port Properties** dialog box, in the **Name** field, type a send port name (for example, type **SendToJDE**.)</span></span>  
  
4.  <span data-ttu-id="c1a32-109">Dans le **Type** la liste déroulante, sélectionnez **JDEOneWorld**.</span><span class="sxs-lookup"><span data-stu-id="c1a32-109">In the **Type** drop-down list, select **JDEOneWorld**.</span></span>  
  
5.  <span data-ttu-id="c1a32-110">Dans le **URI** liste déroulante, sélectionnez le Gestionnaire d’envoi.</span><span class="sxs-lookup"><span data-stu-id="c1a32-110">In the **URI** drop-down list, select the send handler.</span></span>  
  
6.  <span data-ttu-id="c1a32-111">Cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="c1a32-111">Click **OK**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c1a32-112">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="c1a32-112">See Also</span></span>  
 [<span data-ttu-id="c1a32-113">Création de gestionnaires de JD Edwards OneWorld envoi</span><span class="sxs-lookup"><span data-stu-id="c1a32-113">Creating JD Edwards OneWorld Send Handlers</span></span>](../core/creating-jd-edwards-oneworld-send-handlers.md)