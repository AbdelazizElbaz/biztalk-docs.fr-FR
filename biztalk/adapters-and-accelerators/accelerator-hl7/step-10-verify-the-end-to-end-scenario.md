---
title: "Étape 10 : Vérifier que le scénario de bout en bout | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: end-to-end tutorial, verifying solution
ms.assetid: 24b74ba6-e303-4ab1-8a93-25a430e4894d
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: d38f137625554bd689477964e3a969142eca0658
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="step-10-verify-the-end-to-end-scenario"></a><span data-ttu-id="1f206-102">Étape 10 : Vérifier que le scénario de bout en bout</span><span class="sxs-lookup"><span data-stu-id="1f206-102">Step 10: Verify the End-to-End Scenario</span></span>
<span data-ttu-id="1f206-103">Dans cette étape, vous vérifiez le scénario de bout en bout pour ce didacticiel.</span><span class="sxs-lookup"><span data-stu-id="1f206-103">In this step, you verify the end-to-end scenario for this tutorial.</span></span>  
  
### <a name="to-verify-the-end-to-end-tutorial-scenario"></a><span data-ttu-id="1f206-104">Pour vérifier le scénario de didacticiel de bout en bout</span><span class="sxs-lookup"><span data-stu-id="1f206-104">To verify the end-to-end tutorial scenario</span></span>  
  
1.  <span data-ttu-id="1f206-105">Cliquez sur **Démarrer**, pointez sur **programmes**, pointez sur **Accessoires**, puis cliquez sur **invite de commandes**.</span><span class="sxs-lookup"><span data-stu-id="1f206-105">Click **Start**, point to **Programs**, point to **Accessories**, and then click **Command Prompt**.</span></span>  
  
2.  <span data-ttu-id="1f206-106">Dans la fenêtre d’invite de commandes, accédez à  **\<* lecteur*\>: \Program Files\Microsoft BizTalk \<version\> Accelerator for HL7\SDK\MLLP Utilitaires **, puis appuyez sur **entrée**.</span><span class="sxs-lookup"><span data-stu-id="1f206-106">In the Command Prompt window, move to **\<*drive*\>:\Program Files\Microsoft BizTalk \<version\> Accelerator for HL7\SDK\MLLP Utilities**, and then press **Enter**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="1f206-107">Si vous ne trouvez pas un dossier MLLP utilitaires sous le dossier du Kit de développement logiciel, les outils de test MLLP ne peuvent pas être installés.</span><span class="sxs-lookup"><span data-stu-id="1f206-107">If you cannot find an MLLP Utilities folder under the SDK folder, the MLLP test tools may not be installed.</span></span> <span data-ttu-id="1f206-108">Ouvrez le panneau de configuration, puis ouvrez **Ajout / Suppression de programmes**.</span><span class="sxs-lookup"><span data-stu-id="1f206-108">Open the Control Panel, and then open **Add or Remove Programs**.</span></span> <span data-ttu-id="1f206-109">Sélectionnez **Microsoft BizTalk \<version\> Accelerator pour HL7**, puis sélectionnez **modification**.</span><span class="sxs-lookup"><span data-stu-id="1f206-109">Select **Microsoft BizTalk \<version\> Accelerator for HL7**, and then select **Change**.</span></span> <span data-ttu-id="1f206-110">Dans l’Assistant d’installation BTAHL7, sélectionnez **modifier**.</span><span class="sxs-lookup"><span data-stu-id="1f206-110">In the BTAHL7 setup wizard, select **Modify**.</span></span> <span data-ttu-id="1f206-111">Développez le **carte** dossier pour voir si le **outil de Test MLLP** a été installé.</span><span class="sxs-lookup"><span data-stu-id="1f206-111">Expand the **Adapter** folder to see whether the **MLLP Test Tool** has been installed.</span></span> <span data-ttu-id="1f206-112">Si ce n’est pas le cas, installez-le.</span><span class="sxs-lookup"><span data-stu-id="1f206-112">If not, install it.</span></span>  
  
3.  <span data-ttu-id="1f206-113">Dans la fenêtre d’invite de commandes, tapez **mllpreceive /p 14000**, puis appuyez sur **entrée**.</span><span class="sxs-lookup"><span data-stu-id="1f206-113">In the Command Prompt window, type **mllpreceive /p 14000**, and then press **Enter**.</span></span> <span data-ttu-id="1f206-114">Cela exécute l’application d’écouteur MLLP écouter le port 14000 et en spécifiant les caractères EB, service bus et CR par défaut du message MLLP et affiche tous les messages reçus à l’écran.</span><span class="sxs-lookup"><span data-stu-id="1f206-114">This runs the MLLP listener application listening to port 14000 and specifying the default EB, SB, and CR characters of the MLLP message, and displays any messages received to the screen.</span></span>  
  
4.  <span data-ttu-id="1f206-115">Démarrez une invite de commandes supplémentaire en cliquant sur **Démarrer**, pointez sur **programmes**, pointez sur **Accessoires**, puis cliquez sur **l’invite de commandes**.</span><span class="sxs-lookup"><span data-stu-id="1f206-115">Start an additional command prompt by clicking **Start**, point to **Programs**, point to **Accessories**, and then click **Command Prompt**.</span></span>  
  
5.  <span data-ttu-id="1f206-116">Dans la deuxième fenêtre d’invite de commandes, accédez à  **\<* lecteur*\>: \Program Files\Microsoft BizTalk \<version\> Accelerator for HL7\SDK\ MLLP utilitaires **, puis appuyez sur **entrée**.</span><span class="sxs-lookup"><span data-stu-id="1f206-116">In the second Command Prompt window, move to **\<*drive*\>:\Program Files\Microsoft BizTalk \<version\> Accelerator for HL7\SDK\MLLP Utilities**, and then press **Enter**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="1f206-117">L’étape suivante envoie le message.</span><span class="sxs-lookup"><span data-stu-id="1f206-117">The following step sends the message.</span></span>  
  
6.  <span data-ttu-id="1f206-118">Dans la fenêtre d’invite de commandes, tapez  **mllpsend/SB 11 /EB 28 /CR 13 /f «\<*lecteur*\>: \Program Files\Microsoft BizTalk \<version\> Accelerator for HL7\SDK\End en bout Tutorial\ADT^A03.txt »**, où \<* lecteur* \> est la lettre de lecteur de votre installation.</span><span class="sxs-lookup"><span data-stu-id="1f206-118">In the Command Prompt window, type **mllpsend /SB 11 /EB 28 /CR 13 /f "\<*drive*\>:\Program Files\Microsoft BizTalk \<version\> Accelerator for HL7\SDK\End-to-End Tutorial\ADT^A03.txt"**, where \<*drive*\> is your installation drive letter.</span></span> <span data-ttu-id="1f206-119">Appuyez sur **Entrée**.</span><span class="sxs-lookup"><span data-stu-id="1f206-119">Press **Enter**.</span></span>  
  
7.  <span data-ttu-id="1f206-120">Vérifiez que vous disposez les résultats suivants :</span><span class="sxs-lookup"><span data-stu-id="1f206-120">Verify that you have the following results:</span></span>  
  
    -   <span data-ttu-id="1f206-121">L’application du récepteur MLLP doit afficher un message.</span><span class="sxs-lookup"><span data-stu-id="1f206-121">The MLLP listener application should display a message.</span></span> <span data-ttu-id="1f206-122">La première ligne du message doit avoir les valeurs suivantes :</span><span class="sxs-lookup"><span data-stu-id="1f206-122">The first line of the message should have the following values:</span></span>  
  
        ```  
        MSH|^~\&|BTAHL7^IE^UUID|MCM|HI^System^GUID||199601121005||ADT^A04|000001|P|2.4|||SU|NE  
        ```  
  
    -   <span data-ttu-id="1f206-123">Un message s’affiche dans \< *lecteur*\>: \Program Files\Microsoft BizTalk \<version\> Accelerator for HL7\SDK\End en bout Tutorial\Tutorial_sendMsg_RX.</span><span class="sxs-lookup"><span data-stu-id="1f206-123">A message appears in \<*drive*\>:\Program Files\Microsoft BizTalk \<version\> Accelerator for HL7\SDK\End-to-End Tutorial\Tutorial_sendMsg_RX.</span></span> <span data-ttu-id="1f206-124">Ce message doit être le même que le message affiché par l’application d’écouteur MLLP.</span><span class="sxs-lookup"><span data-stu-id="1f206-124">This message should be the same as the message shown by the MLLP listener application.</span></span> <span data-ttu-id="1f206-125">Vérifiez que la première ligne du message a les mêmes valeurs de message comme suit.</span><span class="sxs-lookup"><span data-stu-id="1f206-125">Verify that the first line of the message has the same message values as follows.</span></span> <span data-ttu-id="1f206-126">Notez que les valeurs pour MSH3 un nd MSH5 dans le code suivant correspondent les valeurs que vous avez spécifié pour le Tutorial_RXSystem :</span><span class="sxs-lookup"><span data-stu-id="1f206-126">Note that the values for MSH3 a nd MSH5 in the following code match the values you specified for the Tutorial_RXSystem:</span></span>  
  
        ```  
        MSH|^~\&|BTAHL7|MCM|Tutorial_RXSystem||199601121005||ADT^A03|000001|P|2.3.1  
        ```  
  
    -   <span data-ttu-id="1f206-127">Deux messages s’affichent dans \< *lecteur*\>: \Program Files\Microsoft BizTalk \<version\> Accelerator for HL7\SDK\End en bout Tutorial\Tutorial_sendAck_ADT.</span><span class="sxs-lookup"><span data-stu-id="1f206-127">Two messages appear in \<*drive*\>:\Program Files\Microsoft BizTalk \<version\> Accelerator for HL7\SDK\End-to-End Tutorial\Tutorial_sendAck_ADT.</span></span> <span data-ttu-id="1f206-128">Un de ces messages est un accusé de réception application ; l’autre est un accusé de réception de la validation.</span><span class="sxs-lookup"><span data-stu-id="1f206-128">One of these messages is an application acknowledgment; the other is a commit acknowledgment.</span></span> <span data-ttu-id="1f206-129">L’accusé de réception d’application doit avoir le contenu suivant :</span><span class="sxs-lookup"><span data-stu-id="1f206-129">The application acknowledgment should have the following content:</span></span>  
  
        ```  
        MSH|^~\&|BTAHL7InterfaceEngine||Tutorial_ADTSystem|MCM|<datetime>||ACK^A03^ACK|000001|P|2.3.1|||AL  
        MSA|AA|000001  
        ```  
  
    -   <span data-ttu-id="1f206-130">L’accusé de réception de validation doit avoir le contenu suivant :</span><span class="sxs-lookup"><span data-stu-id="1f206-130">The commit acknowledgment should have the following content:</span></span>  
  
        ```  
        MSH|^~\&|BTAHL7InterfaceEngine||Tutorial_ADTSystem|MCM|<datetime>||ACK^A03^ACK|100000|P|2.3.1  
        MSA|CA|000001  
        ```  
  
    > [!NOTE]
    >  <span data-ttu-id="1f206-131">Si les messages ne s’affichent pas correctement, utilisez l’outil de contrôle d’intégrité et l’activité de suivi du fonctionnement (HAT) pour résoudre l’erreur.</span><span class="sxs-lookup"><span data-stu-id="1f206-131">If the messages do not appear correctly, use the Health and Activity Tracking (HAT) tool to troubleshoot the error.</span></span>  
  
 <span data-ttu-id="1f206-132">Félicitations !</span><span class="sxs-lookup"><span data-stu-id="1f206-132">Congratulations!</span></span> <span data-ttu-id="1f206-133">Vous avez terminé le didacticiel de bout en bout BTAHL7.</span><span class="sxs-lookup"><span data-stu-id="1f206-133">You have successfully completed the BTAHL7 End-to-End Tutorial.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1f206-134">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="1f206-134">See Also</span></span>  
 [<span data-ttu-id="1f206-135">Didacticiel de bout en bout</span><span class="sxs-lookup"><span data-stu-id="1f206-135">End-to-End Tutorial</span></span>](../../adapters-and-accelerators/accelerator-hl7/end-to-end-tutorial1.md)