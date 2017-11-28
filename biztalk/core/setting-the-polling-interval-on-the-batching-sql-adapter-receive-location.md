---
title: "Emplacement de réception définissant l’intervalle d’interrogation sur l’adaptateur SQL de traitement par lot | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- polling interval [receive adapters]
- SQL adapters, polling interval
- receive locations, polling interval
- SQL adapters, receive locations
- receive locations, SQL adapters
ms.assetid: 9053b20d-145a-4445-b414-c0482cf975a0
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 830cafc89c87ce84048bad8f6e4e9f2feb34f565
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="setting-the-polling-interval-on-the-batching-sql-adapter-receive-location"></a><span data-ttu-id="08ff4-102">Définition de la fréquence d'interrogation de l'emplacement de réception de l'adaptateur SQL de traitement par lot</span><span class="sxs-lookup"><span data-stu-id="08ff4-102">Setting the Polling Interval on the Batching SQL Adapter Receive Location</span></span>
<span data-ttu-id="08ff4-103">Vous pouvez définir l’intervalle d’interrogation sur le traitement par lots de réception de l’adaptateur SQL emplacement (**BatchControlMessageRecvLoc**) différemment sur les ordinateurs de développement et de production.</span><span class="sxs-lookup"><span data-stu-id="08ff4-103">You can set the polling interval on the batching SQL adapter receive location (**BatchControlMessageRecvLoc**) differently on development and production computers.</span></span> <span data-ttu-id="08ff4-104">Pour accélérer l'activation de l'orchestration de traitement par lot d'un accord sur un serveur de développement, Microsoft recommande que vous conserviez la fréquence d'interrogation définie sur la valeur par défaut de 30 secondes.</span><span class="sxs-lookup"><span data-stu-id="08ff4-104">On a development server, Microsoft recommends that you keep the polling interval at the default of 30 seconds, for quick activation of the batching orchestration for an agreement.</span></span> <span data-ttu-id="08ff4-105">Toutefois, sur un serveur de production, la valeur de 30 secondes risque d'affecter les performances.</span><span class="sxs-lookup"><span data-stu-id="08ff4-105">However, on a production server, a setting of 30 seconds may affect performance.</span></span> <span data-ttu-id="08ff4-106">Après avoir activé un lot, vous souhaitez peut-être augmenter la valeur de la fréquence d'interrogation à cinq minutes, par exemple.</span><span class="sxs-lookup"><span data-stu-id="08ff4-106">Once you have activated a batch, you may want to set the polling interval to a higher value, such as five minutes.</span></span>  
  
 <span data-ttu-id="08ff4-107">Pour plus d’informations sur les tiers, consultez [la gestion des Parties](../core/managing-parties.md).</span><span class="sxs-lookup"><span data-stu-id="08ff4-107">For more information about parties, see [Managing Parties](../core/managing-parties.md).</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="08ff4-108">Conditions préalables</span><span class="sxs-lookup"><span data-stu-id="08ff4-108">Prerequisites</span></span>  
 <span data-ttu-id="08ff4-109">Vous devez ouvrir une session en tant que membre du groupe Administrateurs [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="08ff4-109">You must be logged on as a member of the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administrators group.</span></span>  
  
### <a name="to-set-the-polling-interval-on-the-batching-sql-adapter-receive-location"></a><span data-ttu-id="08ff4-110">Pour définir la fréquence d'interrogation de l'emplacement de réception de l'adaptateur SQL de traitement par lot</span><span class="sxs-lookup"><span data-stu-id="08ff4-110">To set the Polling Interval on the Batching SQL Adapter Receive Location</span></span>  
  
1.  <span data-ttu-id="08ff4-111">Dans le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Console d’Administration, cliquez sur **Application EDI BizTalk**, puis cliquez sur **emplacements de réception**.</span><span class="sxs-lookup"><span data-stu-id="08ff4-111">In the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration Console, click **BizTalk EDI Application**, and then click **Receive Locations**.</span></span> <span data-ttu-id="08ff4-112">Avec le bouton droit **BatchControlMessageRecvLoc**, puis cliquez sur **propriétés**.</span><span class="sxs-lookup"><span data-stu-id="08ff4-112">Right-click **BatchControlMessageRecvLoc**, and click **Properties**.</span></span>  
  
2.  <span data-ttu-id="08ff4-113">Dans le **propriétés de l’emplacement de réception** boîte de dialogue le **Transport** , cliquez sur **configurer**.</span><span class="sxs-lookup"><span data-stu-id="08ff4-113">In the **Receive Location Properties** dialog box, in the **Transport** section, click **Configure**.</span></span>  
  
3.  <span data-ttu-id="08ff4-114">Dans le **propriétés du Transport SQL** boîte de dialogue, changez la valeur de **fréquence d’interrogation** à partir de la valeur par défaut « 30 », la valeur souhaitée.</span><span class="sxs-lookup"><span data-stu-id="08ff4-114">In the **SQL Transport Properties** dialog box, change the value for **Polling Interval** from the default value of "30" to the desired value.</span></span> <span data-ttu-id="08ff4-115">Pour un serveur de production, la valeur recommandée est « 5 ».</span><span class="sxs-lookup"><span data-stu-id="08ff4-115">The recommended value for a production server is "5".</span></span>  
  
4.  <span data-ttu-id="08ff4-116">Modifiez la valeur de **unité de mesure de l’interrogation** à partir de la valeur par défaut **secondes** à **Minutes**.</span><span class="sxs-lookup"><span data-stu-id="08ff4-116">Change the value of **Polling Unit of Measure** from the default value of **Seconds** to **Minutes**.</span></span>  
  
5.  <span data-ttu-id="08ff4-117">Cliquez sur **OK**, puis cliquez sur **OK** à nouveau</span><span class="sxs-lookup"><span data-stu-id="08ff4-117">Click **OK**, and then click **OK** again</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="08ff4-118">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="08ff4-118">See Also</span></span>  
 [<span data-ttu-id="08ff4-119">La gestion des Solutions EDI et AS2</span><span class="sxs-lookup"><span data-stu-id="08ff4-119">Managing EDI and AS2 Solutions</span></span>](../core/managing-edi-and-as2-solutions.md)