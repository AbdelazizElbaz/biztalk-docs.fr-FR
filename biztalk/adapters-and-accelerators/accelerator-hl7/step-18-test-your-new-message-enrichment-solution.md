---
title: "Étape 18 : Tester votre nouvelle Solution d’enrichissement de Message | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: message enrichment tutorial, testing solution
ms.assetid: 233fbf79-0ab1-4064-b828-6bbbb56cbec2
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: ca2716a5d05292f105798cf394cd05bac1104c4b
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="step-18-test-your-new-message-enrichment-solution"></a><span data-ttu-id="6e36a-102">Étape 18 : Tester votre nouvelle Solution d’enrichissement de Message</span><span class="sxs-lookup"><span data-stu-id="6e36a-102">Step 18: Test Your New Message Enrichment Solution</span></span>
<span data-ttu-id="6e36a-103">Dans cette étape, vous testez votre solution à l’aide de l’application WSClient pour envoyer un message à [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] et de voir si l’application MLLPReceive reçoit un message au format HL7 comme prévu.</span><span class="sxs-lookup"><span data-stu-id="6e36a-103">In this step, you test your solution by using the WSClient application to send a message to [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] and seeing if the MLLPReceive application receives an HL7-formatted message as expected.</span></span>  
  
### <a name="to-test-your-solution"></a><span data-ttu-id="6e36a-104">Pour tester votre solution</span><span class="sxs-lookup"><span data-stu-id="6e36a-104">To test your solution</span></span>  
  
1.  <span data-ttu-id="6e36a-105">Ouvrez une invite de commandes.</span><span class="sxs-lookup"><span data-stu-id="6e36a-105">Open a command prompt.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="6e36a-106">Étape 2 nécessite que vous avez installé l’outil de Test de MLLP à l’aide de la procédure d’installation personnalisée.</span><span class="sxs-lookup"><span data-stu-id="6e36a-106">Step 2 requires that you have installed the MLLP Test tool using the custom installation procedure.</span></span> <span data-ttu-id="6e36a-107">Si les utilitaires \MLLP répertoire contenant MllpReceive.exe et MllpSend.exe n’existe pas sur votre ordinateur, installez-les en effectuant une installation personnalisée.</span><span class="sxs-lookup"><span data-stu-id="6e36a-107">If the \MLLP Utilities directory containing MllpReceive.exe and MllpSend.exe does not exist on your computer, install them by performing a custom installation.</span></span> <span data-ttu-id="6e36a-108">Pour plus d’informations, consultez [installation personnalisée](http://msdn.microsoft.com/library/e55c86e1-af63-49ba-8510-d177e1b96692).</span><span class="sxs-lookup"><span data-stu-id="6e36a-108">For information, see [Performing a Custom Installation](http://msdn.microsoft.com/library/e55c86e1-af63-49ba-8510-d177e1b96692).</span></span>  
  
2.  <span data-ttu-id="6e36a-109">À l’invite de commandes, tapez  **cd \<* lecteur*> : \Program Files\Microsoft BizTalk \<version > Accelerator HL7\SDK\MLLP utilitaires ** (où \< *lecteur*> est la lettre de lecteur de votre installation), puis appuyez sur **entrée**.</span><span class="sxs-lookup"><span data-stu-id="6e36a-109">At the command prompt, type **cd \<*drive*>:\Program Files\Microsoft BizTalk \<version> Accelerator for HL7\SDK\MLLP Utilities** (where \<*drive*> is your installation drive letter), and then press **Enter**.</span></span>  
  
3.  <span data-ttu-id="6e36a-110">À l’invite de commandes, tapez **mllpreceive /p 11000 /eb 11/SB 28 /cr 13**, puis appuyez sur **entrée**.</span><span class="sxs-lookup"><span data-stu-id="6e36a-110">At the command prompt, type **mllpreceive /p 11000 /eb 11 /sb 28 /cr 13**, and then press **Enter**.</span></span> <span data-ttu-id="6e36a-111">Cela exécute l’application d’écouteur MLLP à l’écoute sur le port 11000 et en spécifiant les caractères EB, service bus et CR par défaut du message MLLP et affiche tous les messages reçus à l’écran.</span><span class="sxs-lookup"><span data-stu-id="6e36a-111">This runs the MLLP listener application listening to port 11000 and specifying the default EB, SB, and CR characters of the MLLP message, and displays any messages received to the screen.</span></span>  
  
4.  <span data-ttu-id="6e36a-112">Ouvrez une deuxième invite de commandes.</span><span class="sxs-lookup"><span data-stu-id="6e36a-112">Open a second command prompt.</span></span>  
  
5.  <span data-ttu-id="6e36a-113">À l’invite de commandes, tapez  **cd \<* lecteur*> : \Tutorial\WSClient\bin\Debug**, puis appuyez sur **entrée**.</span><span class="sxs-lookup"><span data-stu-id="6e36a-113">At the command prompt, type **cd \<*drive*>:\Tutorial\WSClient\bin\Debug**, and then press **Enter**.</span></span>  
  
6.  <span data-ttu-id="6e36a-114">À l’invite de commandes, tapez **wsclient Jean henry 123456789**, puis appuyez sur **entrée**.</span><span class="sxs-lookup"><span data-stu-id="6e36a-114">At the command prompt, type **wsclient john henry smith 123456789**, and then press **Enter**.</span></span> <span data-ttu-id="6e36a-115">Il envoie un message au service Web qui contient un exemple de message avec un nom de patient de Henry de John Smith et un numéro de sécurité sociale exemple 123456789.</span><span class="sxs-lookup"><span data-stu-id="6e36a-115">This sends a message to the Web service that contains a sample message with a patient name of John Henry Smith and a sample social security number of 123456789.</span></span>  
  
7.  <span data-ttu-id="6e36a-116">Après un court instant, l’application MLLPReceive affiche le message entrant MLLP.</span><span class="sxs-lookup"><span data-stu-id="6e36a-116">After a short pause, the MLLPReceive application displays the incoming MLLP message.</span></span> <span data-ttu-id="6e36a-117">Le message doit ressembler à ce qui suit :</span><span class="sxs-lookup"><span data-stu-id="6e36a-117">The message should look similar to the following:</span></span>  
  
    ```  
    MSH|^~\&|TestTrailing^Delimiters|srcFac^srcFacUid|dstApp^dstAppUid|dstFac^dstFacUid|200307092343|sec|ADT^A04|msgid2134|P|2.2PID|||123456789||smith^john  
    ```  
  
     <span data-ttu-id="6e36a-118">Si vous ne recevez pas de réponse après quelques minutes, vérifiez le journal des événements pour les erreurs et commencez le dépannage.</span><span class="sxs-lookup"><span data-stu-id="6e36a-118">If you do not receive a response after a few minutes, you should check the Application event log for any errors and begin troubleshooting.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6e36a-119">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="6e36a-119">See Also</span></span>  
 [<span data-ttu-id="6e36a-120">Didacticiel d’enrichissement de message</span><span class="sxs-lookup"><span data-stu-id="6e36a-120">Message Enrichment Tutorial</span></span>](../../adapters-and-accelerators/accelerator-hl7/message-enrichment-tutorial.md)