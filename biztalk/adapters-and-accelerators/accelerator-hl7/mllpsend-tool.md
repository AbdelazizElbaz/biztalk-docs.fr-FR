---
title: Outil de MllpSend | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- MllpSend tool
- MLLP-encoded messages, receive adapters
- MLLP-encoded messages, MllpSend tool
ms.assetid: b1723d52-4909-4543-8215-4f73802b6c4f
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: a15da306f61cb4297d9ba8cdc036035310474d8e
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="mllpsend-tool"></a><span data-ttu-id="74e83-102">Outil de MllpSend</span><span class="sxs-lookup"><span data-stu-id="74e83-102">MllpSend Tool</span></span>
<span data-ttu-id="74e83-103">Vous pouvez utiliser l’outil MllpSend pour envoyer l’emplacement de réception de données à un MLLP.</span><span class="sxs-lookup"><span data-stu-id="74e83-103">You can use the MllpSend tool to send data to an MLLP receive location.</span></span>  
  
 <span data-ttu-id="74e83-104">Vous installez cet outil via le [!INCLUDE[HL7_CurrentVersion_FirstRef](../../includes/hl7-currentversion-firstref-md.md)] procédure d’installation personnalisée.</span><span class="sxs-lookup"><span data-stu-id="74e83-104">You install this tool through the [!INCLUDE[HL7_CurrentVersion_FirstRef](../../includes/hl7-currentversion-firstref-md.md)] Custom installation procedure.</span></span> <span data-ttu-id="74e83-105">Si vous avez effectué une installation par défaut pour installer BTAHL7, vous devez exécuter une installation personnalisée et installer les outils de test pour ce didacticiel fonctionne correctement.</span><span class="sxs-lookup"><span data-stu-id="74e83-105">If you performed a Typical installation to install BTAHL7, then you must run a Custom installation and install the test tools in order for this tutorial to work correctly.</span></span> <span data-ttu-id="74e83-106">Sur l’écran d’installation personnalisée, sélectionnez **outil de Test MLLP** à partir de la **adaptateur** dossier, puis sélectionnez **Instances Test** à partir de la **artefacts** dossier.</span><span class="sxs-lookup"><span data-stu-id="74e83-106">At the Custom Setup screen, select **MLLP Test Tool** from the **Adapter** folder, and select **Test Instances** from the **Artifacts** folder.</span></span> <span data-ttu-id="74e83-107">Pour plus d’informations, consultez [installation personnalisée](http://msdn.microsoft.com/library/e55c86e1-af63-49ba-8510-d177e1b96692).</span><span class="sxs-lookup"><span data-stu-id="74e83-107">For more information, see [Performing a Custom Installation](http://msdn.microsoft.com/library/e55c86e1-af63-49ba-8510-d177e1b96692).</span></span>  
  
 <span data-ttu-id="74e83-108">Le programme d’installation BTAHL7 installe cet outil dans  *\<lecteur >*: \Program Files\Microsoft BizTalk \<version > Accelerator for HL7\SDK\MLLP utilitaires.</span><span class="sxs-lookup"><span data-stu-id="74e83-108">BTAHL7 setup installs this tool in *\<drive>*:\Program Files\Microsoft BizTalk \<version> Accelerator for HL7\SDK\MLLP Utilities.</span></span>  
  
 <span data-ttu-id="74e83-109">Vous utilisez cet outil dans le [didacticiel de bout en bout](../../adapters-and-accelerators/accelerator-hl7/end-to-end-tutorial1.md), le [didacticiel Interrogative](../../adapters-and-accelerators/accelerator-hl7/interrogative-tutorial.md), le [didacticiel de traitement par lot](../../adapters-and-accelerators/accelerator-hl7/batching-tutorial.md)et le [didacticiel enrichissement de Message](../../adapters-and-accelerators/accelerator-hl7/message-enrichment-tutorial.md).</span><span class="sxs-lookup"><span data-stu-id="74e83-109">You use this tool in the [End-to-End Tutorial](../../adapters-and-accelerators/accelerator-hl7/end-to-end-tutorial1.md), the [Interrogative Tutorial](../../adapters-and-accelerators/accelerator-hl7/interrogative-tutorial.md), the [Batching Tutorial](../../adapters-and-accelerators/accelerator-hl7/batching-tutorial.md), and the [Message Enrichment Tutorial](../../adapters-and-accelerators/accelerator-hl7/message-enrichment-tutorial.md).</span></span> <span data-ttu-id="74e83-110">Si vous avez installé [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] via l’installation par défaut et vous n’avez pas installé le Testtools MLLP (y compris MllpSend et MllpReceive), vous ne serez pas en mesure de tester vos résultats du didacticiels.</span><span class="sxs-lookup"><span data-stu-id="74e83-110">If you installed [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] through the default installation, and have not installed the MLLP Testtools (including MllpSend and MllpReceive), you will not be able to test your tutorial results.</span></span>  
  
## <a name="tool-usage"></a><span data-ttu-id="74e83-111">Utilisation de l’outil</span><span class="sxs-lookup"><span data-stu-id="74e83-111">Tool Usage</span></span>  
 <span data-ttu-id="74e83-112">Voici la syntaxe à qu'utiliser pour appeler cet outil de ligne de commande :</span><span class="sxs-lookup"><span data-stu-id="74e83-112">The following shows the syntax you use to invoke this command-line tool:</span></span>  
  
```  
mllpsend.exe [/?] [/I <IP>] [/P <PORT>] [/TWOWAY] [/REPEAT <n>] [/F <FILENAME> | "TEXT"] /SB nn /EB nn /CR nn  
```  
  
 <span data-ttu-id="74e83-113">Le tableau suivant décrit chaque partie de la syntaxe de que l’outil MllpSend utilise.</span><span class="sxs-lookup"><span data-stu-id="74e83-113">The following table describes each part of the syntax the MllpSend tool uses.</span></span>  
  
|<span data-ttu-id="74e83-114">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="74e83-114">Syntax</span></span>|<span data-ttu-id="74e83-115"> Description</span><span class="sxs-lookup"><span data-stu-id="74e83-115">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="74e83-116">**/?**</span><span class="sxs-lookup"><span data-stu-id="74e83-116">**/?**</span></span>|<span data-ttu-id="74e83-117">Affiche l’aide dans la fenêtre d’invite de commandes.</span><span class="sxs-lookup"><span data-stu-id="74e83-117">Displays Help in the Command Prompt window.</span></span>|  
|<span data-ttu-id="74e83-118">**/I \<IP >**</span><span class="sxs-lookup"><span data-stu-id="74e83-118">**/I \<IP>**</span></span>|<span data-ttu-id="74e83-119">Indique l’adresse de destination.</span><span class="sxs-lookup"><span data-stu-id="74e83-119">Denotes the address to send to.</span></span> <span data-ttu-id="74e83-120">La valeur par défaut est localhost.</span><span class="sxs-lookup"><span data-stu-id="74e83-120">The default value is localhost.</span></span>|  
|<span data-ttu-id="74e83-121">**/P \<PORT >**</span><span class="sxs-lookup"><span data-stu-id="74e83-121">**/P \<PORT>**</span></span>|<span data-ttu-id="74e83-122">Indique le numéro de port de destination.</span><span class="sxs-lookup"><span data-stu-id="74e83-122">Denotes the port number to send to.</span></span> <span data-ttu-id="74e83-123">La valeur par défaut est **11000**.</span><span class="sxs-lookup"><span data-stu-id="74e83-123">The default value is **11000**.</span></span>|  
|<span data-ttu-id="74e83-124">**/F**</span><span class="sxs-lookup"><span data-stu-id="74e83-124">**/F**</span></span>|<span data-ttu-id="74e83-125">Envoie le contenu du fichier du nom de fichier.</span><span class="sxs-lookup"><span data-stu-id="74e83-125">Sends content of the file FILENAME.</span></span>|  
|<span data-ttu-id="74e83-126">**/ RÉPÉTITION\<n>**</span><span class="sxs-lookup"><span data-stu-id="74e83-126">**/REPEAT \<n>**</span></span>|<span data-ttu-id="74e83-127">Envoie le message même  *n*  fois.</span><span class="sxs-lookup"><span data-stu-id="74e83-127">Sends the same message *n* times.</span></span> <span data-ttu-id="74e83-128">Les caractères de wrapper seront appliquées à chaque message.</span><span class="sxs-lookup"><span data-stu-id="74e83-128">The wrapper characters will be applied to each message.</span></span>|  
|<span data-ttu-id="74e83-129">**/ TWOWAY (BIDIRECTIONNEL).**</span><span class="sxs-lookup"><span data-stu-id="74e83-129">**/TWOWAY**</span></span>|<span data-ttu-id="74e83-130">L’expéditeur attend une réponse du récepteur.</span><span class="sxs-lookup"><span data-stu-id="74e83-130">The sender will wait for a response from the receiver.</span></span> <span data-ttu-id="74e83-131">Service bus et EB doivent être spécifiés.</span><span class="sxs-lookup"><span data-stu-id="74e83-131">SB and EB need to be specified.</span></span> <span data-ttu-id="74e83-132">CR est facultative.</span><span class="sxs-lookup"><span data-stu-id="74e83-132">CR is optional.</span></span> <span data-ttu-id="74e83-133">En mode de fichier, la réponse est stockée dans le fichier. RÉPONSE.</span><span class="sxs-lookup"><span data-stu-id="74e83-133">In File mode, the response is stored in the file FILE.RESPONSE.</span></span>|  
|<span data-ttu-id="74e83-134">**/ SB**</span><span class="sxs-lookup"><span data-stu-id="74e83-134">**/SB**</span></span>|<span data-ttu-id="74e83-135">Définit la valeur ASCII de l’octet de délimiteur Démarrer de bloc.</span><span class="sxs-lookup"><span data-stu-id="74e83-135">Sets the ASCII value of the Start Block Delimiter Byte.</span></span> <span data-ttu-id="74e83-136">La valeur par défaut est none.</span><span class="sxs-lookup"><span data-stu-id="74e83-136">The default is none.</span></span>|  
|<span data-ttu-id="74e83-137">**/EB**</span><span class="sxs-lookup"><span data-stu-id="74e83-137">**/EB**</span></span>|<span data-ttu-id="74e83-138">Définit la valeur ASCII de l’octet de délimiteur de bloc de fin.</span><span class="sxs-lookup"><span data-stu-id="74e83-138">Sets the ASCII value of the End Block Delimiter Byte.</span></span> <span data-ttu-id="74e83-139">La valeur par défaut est none.</span><span class="sxs-lookup"><span data-stu-id="74e83-139">The default is none.</span></span>|  
|<span data-ttu-id="74e83-140">**/CR**</span><span class="sxs-lookup"><span data-stu-id="74e83-140">**/CR**</span></span>|<span data-ttu-id="74e83-141">Définit la valeur ASCII de l’octet le délimiteur de retour chariot.</span><span class="sxs-lookup"><span data-stu-id="74e83-141">Sets the ASCII value of the Carriage Return Delimiter Byte.</span></span> <span data-ttu-id="74e83-142">La valeur par défaut est none.</span><span class="sxs-lookup"><span data-stu-id="74e83-142">The default is none.</span></span>|  
  
## <a name="examples-of-tool-use"></a><span data-ttu-id="74e83-143">Exemples d’utilisation de l’outil</span><span class="sxs-lookup"><span data-stu-id="74e83-143">Examples of Tool Use</span></span>  
 <span data-ttu-id="74e83-144">Les exemples suivants montrent comment vous pouvez utiliser l’outil MllpSend.</span><span class="sxs-lookup"><span data-stu-id="74e83-144">The following examples demonstrate how you can use the MllpSend tool.</span></span>  
  
 <span data-ttu-id="74e83-145">**Exemple 1.**</span><span class="sxs-lookup"><span data-stu-id="74e83-145">**Example 1.**</span></span> <span data-ttu-id="74e83-146">Vous pouvez utiliser la commande suivante pour envoyer un message à une carte à sens unique à l’écoute sur le port 13000 sur le serveur « myserver ».</span><span class="sxs-lookup"><span data-stu-id="74e83-146">You can use the following command to send a message to a one-way adapter listening on port 13000 on server "myserver".</span></span> <span data-ttu-id="74e83-147">Les valeurs ASCII de caractères wrapper sont SB 11, EB 28 et CR 13.</span><span class="sxs-lookup"><span data-stu-id="74e83-147">The ASCII values of the wrapper characters are SB 11, EB 28, and CR 13.</span></span>  
  
```  
mllpsend.exe /I myserver /P 13000 /SB 11 /EB 28 /CR 13 "A short message"  
```  
  
 <span data-ttu-id="74e83-148">**Exemple 2.**</span><span class="sxs-lookup"><span data-stu-id="74e83-148">**Example 2.**</span></span> <span data-ttu-id="74e83-149">Vous pouvez utiliser la commande suivante pour envoyer un message de 100 fois à une carte bidirectionnelle à l’écoute sur le port 11000 sur le serveur « localhost ».</span><span class="sxs-lookup"><span data-stu-id="74e83-149">You can use the following command to send a message 100 times to a two-way adapter listening on port 11000 on server "localhost".</span></span> <span data-ttu-id="74e83-150">Les valeurs ASCII de caractères wrapper sont SB 11, EB 28 et CR 13.</span><span class="sxs-lookup"><span data-stu-id="74e83-150">The ASCII values of the wrapper characters are SB 11, EB 28, and CR 13.</span></span>  
  
```  
mllpsend.exe /SB 11 /EB 28 /CR 13 /TWOWAY /REPEAT 100 "A short message"  
```  
  
## <a name="see-also"></a><span data-ttu-id="74e83-151">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="74e83-151">See Also</span></span>  
 [<span data-ttu-id="74e83-152">Utilitaires</span><span class="sxs-lookup"><span data-stu-id="74e83-152">Utilities</span></span>](../../adapters-and-accelerators/accelerator-hl7/utilities2.md)