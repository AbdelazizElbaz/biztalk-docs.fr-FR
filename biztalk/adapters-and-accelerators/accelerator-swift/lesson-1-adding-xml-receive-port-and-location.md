---
title: "Leçon 1 : Ajout de code XML Port de réception et emplacement | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- receive locations, creating
- creating, receive locations
- receive ports, creating
- creating, receive ports
ms.assetid: 252bc080-3820-44cc-8749-715869f3f684
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 186cbb4e021a281ab834f04097f005c2597fbd37
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="lesson-1-adding-xml-receive-port-and-location"></a><span data-ttu-id="86ba4-102">Leçon 1 : Ajout de Port et l’emplacement de réception XML</span><span class="sxs-lookup"><span data-stu-id="86ba4-102">Lesson 1: Adding XML Receive Port and Location</span></span>
<span data-ttu-id="86ba4-103">un port de réception est un groupe logique d'emplacements de réception similaires.</span><span class="sxs-lookup"><span data-stu-id="86ba4-103">A receive port is a logical grouping of similar receive locations.</span></span> <span data-ttu-id="86ba4-104">Un emplacement de réception définit une adresse spécifique (par exemple, un emplacement de fichier ou URL) pour un message entrant et le pipeline est utilisé pour traiter le message.</span><span class="sxs-lookup"><span data-stu-id="86ba4-104">A receive location defines a specific address (such as a URL or file location) for an incoming message and the pipeline that is used to process the message.</span></span>  
  
### <a name="to-add-a-receive-port"></a><span data-ttu-id="86ba4-105">Pour ajouter un port de réception</span><span class="sxs-lookup"><span data-stu-id="86ba4-105">To add a receive port</span></span>  
  
1.  <span data-ttu-id="86ba4-106">Démarrer **Administration de BizTalk Server** console.</span><span class="sxs-lookup"><span data-stu-id="86ba4-106">Start **BizTalk Server Administration** console.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="86ba4-107">La Console Administration de BizTalk Server peut également être ouvert à partir de Visual Studio en cliquant sur **Administration de BizTalk Server** dans les **outils** menu.</span><span class="sxs-lookup"><span data-stu-id="86ba4-107">The BizTalk Server Administration Console can also be opened from within Visual Studio by clicking **BizTalk Server Administration** in the **Tools** menu.</span></span>  
  
2.  <span data-ttu-id="86ba4-108">Dans la Console Administration de BizTalk Server, développez le **Administration de BizTalk Server** nœud, puis le **groupe BizTalk** nœud, puis le **Applications** nœud, puis le **BizTalk Application 1** nœud.</span><span class="sxs-lookup"><span data-stu-id="86ba4-108">In the BizTalk Server Administration Console, expand the **BizTalk Server Administration** node, then the **BizTalk Group** node, then the **Applications** node, and then the **BizTalk Application 1** node.</span></span>  
  
3.  <span data-ttu-id="86ba4-109">Avec le bouton droit **Ports de réception**, pointez sur **nouveau**, puis cliquez sur **Port de réception unidirectionnel**.</span><span class="sxs-lookup"><span data-stu-id="86ba4-109">Right-click **Receive Ports**, point to **New**, and then click **One-Way Receive Port**.</span></span>  
  
4.  <span data-ttu-id="86ba4-110">Dans la boîte de dialogue Propriétés du Port de réception, dans le **nom** , tapez **MT103_XML_ReceivePort**.</span><span class="sxs-lookup"><span data-stu-id="86ba4-110">In the Receive Port Properties dialog box, in the **Name** box, type **MT103_XML_ReceivePort**.</span></span>  
  
5.  <span data-ttu-id="86ba4-111">Cliquez sur **appliquer** à lier le port, puis cliquez sur **OK.**</span><span class="sxs-lookup"><span data-stu-id="86ba4-111">Click **Apply** to bind the port, and then click **OK.**</span></span>  
  
6.  <span data-ttu-id="86ba4-112">Avec le bouton droit **emplacements de réception**, pointez sur **nouveau**, puis cliquez sur **emplacement de réception unidirectionnel**.</span><span class="sxs-lookup"><span data-stu-id="86ba4-112">Right-click **Receive Locations**, point to **New**, and then click **One-way Receive Location**.</span></span>  
  
7.  <span data-ttu-id="86ba4-113">Dans la boîte de dialogue un Port de réception de la sélectionner, cliquez sur **MT103_XML_ReceivePort**, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="86ba4-113">In the Select a Receive Port dialog box, click **MT103_XML_ReceivePort**, and then click **OK**.</span></span>  
  
8.  <span data-ttu-id="86ba4-114">Dans la boîte de dialogue Propriétés de l’emplacement de réception, dans le **nom** , tapez **MT103_XML_ReceiveLocation**.</span><span class="sxs-lookup"><span data-stu-id="86ba4-114">In the Receive Location Properties dialog box, in the **Name** box, type **MT103_XML_ReceiveLocation**.</span></span>  
  
9. <span data-ttu-id="86ba4-115">Dans le **Transport** section, pour le **Type** zone de texte, cliquez sur la liste déroulante et sélectionnez **fichier**.</span><span class="sxs-lookup"><span data-stu-id="86ba4-115">In the **Transport** section, for the **Type** text box, click the drop-down list, and then select **FILE**.</span></span>  
  
10. <span data-ttu-id="86ba4-116">Cliquez sur le **configurer** bouton à droite de la liste déroulante Type.</span><span class="sxs-lookup"><span data-stu-id="86ba4-116">Click the **Configure** button to the right of the Type drop-down list.</span></span>  
  
11. <span data-ttu-id="86ba4-117">Dans la boîte de dialogue Propriétés du Transport FILE, cliquez sur **Parcourir**.</span><span class="sxs-lookup"><span data-stu-id="86ba4-117">In the FILE Transport Properties dialog box, click **Browse**.</span></span> <span data-ttu-id="86ba4-118">Déplacer vers le  **\<lecteur > : \Labs** dossier, puis cliquez sur **créer un nouveau dossier**.</span><span class="sxs-lookup"><span data-stu-id="86ba4-118">Move to the **\<drive>:\Labs** folder, and then click **Make New Folder**.</span></span>  
  
12. <span data-ttu-id="86ba4-119">Dans la boîte de dialogue Rechercher un dossier, créez un **entrant** dossier  **\<lecteur > : \Labs**, puis créez une **XMLFile** dossier dans  **\<lecteur > : \Labs\Inbound**.</span><span class="sxs-lookup"><span data-stu-id="86ba4-119">In the Browse For Folder dialog box, create an **Inbound** folder in **\<drive>:\Labs**, and then create an **XMLFile** folder in **\<drive>:\Labs\Inbound**.</span></span> <span data-ttu-id="86ba4-120">Cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="86ba4-120">Click **OK**.</span></span>  
  
13. <span data-ttu-id="86ba4-121">Dans la boîte de dialogue Propriétés du Transport FILE, vérifiez que  **\*.xml** est entré dans le **masque de fichier** zone, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="86ba4-121">In the FILE Transport Properties dialog box, ensure that **\*.xml** is entered in the **File Mask** box, and then click **OK**.</span></span>  
  
14. <span data-ttu-id="86ba4-122">Dans la boîte de dialogue Propriétés de l’emplacement de réception, vérifiez que **BizTalkServerApplication** est entré pour le **Gestionnaire de réception** boîte.</span><span class="sxs-lookup"><span data-stu-id="86ba4-122">In the Receive Location Properties dialog box, ensure that **BizTalkServerApplication** is entered for the **Receive handler** box.</span></span>  
  
15. <span data-ttu-id="86ba4-123">Pour le **Pipeline de réception** boîte, sélectionnez **XMLReceive** dans la liste déroulante.</span><span class="sxs-lookup"><span data-stu-id="86ba4-123">For the **Receive Pipeline** box, select **XMLReceive** from the drop-down list.</span></span>  
  
16. <span data-ttu-id="86ba4-124">Cliquez sur **appliquer**, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="86ba4-124">Click **Apply**, and then click **OK**.</span></span>  
  
17. <span data-ttu-id="86ba4-125">Dans la Console Administration de BizTalk Server, cliquez sur **emplacements de réception**, avec le bouton droit **MT103_XML_ReceiveLocation**, puis cliquez sur **activer**.</span><span class="sxs-lookup"><span data-stu-id="86ba4-125">In the BizTalk Server Administration Console, click **Receive Locations**, right-click **MT103_XML_ReceiveLocation**, and then click **Enable**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="86ba4-126">Une fois que l’emplacement de réception, BizTalk interroge activement votre dossier de fichiers.</span><span class="sxs-lookup"><span data-stu-id="86ba4-126">After you enable the receive location, BizTalk actively polls your file folder.</span></span>  
  
 <span data-ttu-id="86ba4-127">Passez à [leçon 2 : ajout du Port d’envoi de fichier plat](../../adapters-and-accelerators/accelerator-swift/lesson-2-adding-a-flat-file-send-port.md).</span><span class="sxs-lookup"><span data-stu-id="86ba4-127">Proceed to [Lesson 2: Adding the Flat File Send Port](../../adapters-and-accelerators/accelerator-swift/lesson-2-adding-a-flat-file-send-port.md).</span></span>