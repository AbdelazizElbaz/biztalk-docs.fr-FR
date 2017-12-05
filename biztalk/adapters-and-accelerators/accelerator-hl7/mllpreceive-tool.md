---
title: Outil de MllpReceive | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- MLLP-encoded messages, send adapters
- MllpReceive tool
- MLLP-encoded messages, MllpReceive tool
ms.assetid: 7069444b-1412-40bf-b567-fa86f76cd007
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: e990c49a221653289619a33c30100accc3c68d6e
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="mllpreceive-tool"></a><span data-ttu-id="23e30-102">Outil de MllpReceive</span><span class="sxs-lookup"><span data-stu-id="23e30-102">MllpReceive Tool</span></span>
<span data-ttu-id="23e30-103">Vous pouvez utiliser l’outil MllpReceive pour recevoir des données à partir d’un port d’envoi MLLP.</span><span class="sxs-lookup"><span data-stu-id="23e30-103">You can use the MllpReceive tool to receive data from an MLLP send port.</span></span>  
  
 <span data-ttu-id="23e30-104">Vous installez cet outil via le [!INCLUDE[HL7_CurrentVersion_FirstRef](../../includes/hl7-currentversion-firstref-md.md)] procédure d’installation personnalisée.</span><span class="sxs-lookup"><span data-stu-id="23e30-104">You install this tool through the [!INCLUDE[HL7_CurrentVersion_FirstRef](../../includes/hl7-currentversion-firstref-md.md)] Custom installation procedure.</span></span> <span data-ttu-id="23e30-105">Si vous avez effectué une installation par défaut pour installer BTAHL7, vous devez exécuter une installation personnalisée et installer les outils de test pour ce didacticiel fonctionne correctement.</span><span class="sxs-lookup"><span data-stu-id="23e30-105">If you performed a Typical installation to install BTAHL7, then you must run a Custom installation and install the test tools in order for this tutorial to work correctly.</span></span> <span data-ttu-id="23e30-106">Sur l’écran d’installation personnalisée, sélectionnez **outil de Test MLLP** à partir de la **adaptateur** dossier, puis sélectionnez **Instances Test** à partir de la **artefacts** dossier.</span><span class="sxs-lookup"><span data-stu-id="23e30-106">At the Custom Setup screen, select **MLLP Test Tool** from the **Adapter** folder, and select **Test Instances** from the **Artifacts** folder.</span></span> <span data-ttu-id="23e30-107">Pour plus d’informations, consultez [installation personnalisée](http://msdn.microsoft.com/library/e55c86e1-af63-49ba-8510-d177e1b96692).</span><span class="sxs-lookup"><span data-stu-id="23e30-107">For more information, see [Performing a Custom Installation](http://msdn.microsoft.com/library/e55c86e1-af63-49ba-8510-d177e1b96692).</span></span>  
  
 <span data-ttu-id="23e30-108">Le programme d’installation BTAHL7 installe cet outil dans  *\<lecteur\>*: \Program Files\Microsoft BizTalk \<version\> Accelerator for HL7\SDK\MLLP utilitaires.</span><span class="sxs-lookup"><span data-stu-id="23e30-108">BTAHL7 setup installs this tool in *\<drive\>*:\Program Files\Microsoft BizTalk \<version\> Accelerator for HL7\SDK\MLLP Utilities.</span></span>  
  
 <span data-ttu-id="23e30-109">Vous utilisez cet outil dans le [didacticiel de bout en bout](../../adapters-and-accelerators/accelerator-hl7/end-to-end-tutorial1.md), le [didacticiel Interrogative](../../adapters-and-accelerators/accelerator-hl7/interrogative-tutorial.md), le [didacticiel de traitement par lot](../../adapters-and-accelerators/accelerator-hl7/batching-tutorial.md)et le [didacticiel enrichissement de Message](../../adapters-and-accelerators/accelerator-hl7/message-enrichment-tutorial.md).</span><span class="sxs-lookup"><span data-stu-id="23e30-109">You use this tool in the [End-to-End Tutorial](../../adapters-and-accelerators/accelerator-hl7/end-to-end-tutorial1.md), the [Interrogative Tutorial](../../adapters-and-accelerators/accelerator-hl7/interrogative-tutorial.md), the [Batching Tutorial](../../adapters-and-accelerators/accelerator-hl7/batching-tutorial.md), and the [Message Enrichment Tutorial](../../adapters-and-accelerators/accelerator-hl7/message-enrichment-tutorial.md).</span></span> <span data-ttu-id="23e30-110">Si vous avez installé [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] via l’installation par défaut et vous n’avez pas installé l’outil MLLPTest (y compris MllpReceive et MllpSend), vous ne serez pas en mesure de tester vos résultats du didacticiels.</span><span class="sxs-lookup"><span data-stu-id="23e30-110">If you installed [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] through the default installation, and have not installed the MLLPTest tool (including MllpReceive and MllpSend), you will not be able to test your tutorial results.</span></span>  
  
## <a name="tool-usage"></a><span data-ttu-id="23e30-111">Utilisation de l’outil</span><span class="sxs-lookup"><span data-stu-id="23e30-111">Tool Usage</span></span>  
 <span data-ttu-id="23e30-112">Voici la syntaxe à qu'utiliser pour appeler cet outil de ligne de commande :</span><span class="sxs-lookup"><span data-stu-id="23e30-112">The following shows the syntax you use to invoke this command-line tool:</span></span>  
  
```  
mllpreceive.exe [/?] [/I <IP>] [/P <PORT>] [/SPLIT] [/D <DIRECTORY>] [/STATICACK "ACKTEXT" | /HL7ACK <FILENAME>] /SB nn /EB nn /CR nn  
```  
  
 <span data-ttu-id="23e30-113">Le tableau suivant décrit chaque partie de la syntaxe de que l’outil MllpReceive utilise.</span><span class="sxs-lookup"><span data-stu-id="23e30-113">The following table describes each part of the syntax the MllpReceive tool uses.</span></span>  
  
|<span data-ttu-id="23e30-114">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="23e30-114">Syntax</span></span>|<span data-ttu-id="23e30-115">Signification</span><span class="sxs-lookup"><span data-stu-id="23e30-115">Meaning</span></span>|  
|------------|-------------|  
|<span data-ttu-id="23e30-116">/?</span><span class="sxs-lookup"><span data-stu-id="23e30-116">/?</span></span>|<span data-ttu-id="23e30-117">Affiche cette aide.</span><span class="sxs-lookup"><span data-stu-id="23e30-117">Displays this help.</span></span>|  
|<span data-ttu-id="23e30-118">/I \<IP\></span><span class="sxs-lookup"><span data-stu-id="23e30-118">/I \<IP\></span></span>|<span data-ttu-id="23e30-119">Indique l’adresse de manière à écouter.</span><span class="sxs-lookup"><span data-stu-id="23e30-119">Denotes the address to listen to.</span></span> <span data-ttu-id="23e30-120">La valeur par défaut est disponible de toutes les adresses IP.</span><span class="sxs-lookup"><span data-stu-id="23e30-120">The default is all available IPs.</span></span>|  
|<span data-ttu-id="23e30-121">/P \<PORT\></span><span class="sxs-lookup"><span data-stu-id="23e30-121">/P \<PORT\></span></span>|<span data-ttu-id="23e30-122">Indique le numéro de port pour écouter.</span><span class="sxs-lookup"><span data-stu-id="23e30-122">Denotes the port number to listen to.</span></span> <span data-ttu-id="23e30-123">La valeur par défaut est 12000.</span><span class="sxs-lookup"><span data-stu-id="23e30-123">The default value is 12000.</span></span>|  
|<span data-ttu-id="23e30-124">/D \<ACTIVE\></span><span class="sxs-lookup"><span data-stu-id="23e30-124">/D \<DIRECTORY\></span></span>|<span data-ttu-id="23e30-125">Stocke le reçu tous les messages dans le répertoire \<active\>.</span><span class="sxs-lookup"><span data-stu-id="23e30-125">Stores all received message(s) in the directory in \<DIRECTORY\>.</span></span> <span data-ttu-id="23e30-126">Si vous ne spécifiez pas \<répertoire\>, le répertoire par défaut est % Temp%.</span><span class="sxs-lookup"><span data-stu-id="23e30-126">If you do not specify \<DIRECTORY\>, the default directory is %TEMP%.</span></span>|  
|<span data-ttu-id="23e30-127">/ FRACTIONNEMENT</span><span class="sxs-lookup"><span data-stu-id="23e30-127">/SPLIT</span></span>|<span data-ttu-id="23e30-128">Fractionne les données reçues en messages distincts selon les délimiteurs.</span><span class="sxs-lookup"><span data-stu-id="23e30-128">Splits the received data into separate messages based on the delimiters.</span></span> <span data-ttu-id="23e30-129">Service bus et EB sont requis.</span><span class="sxs-lookup"><span data-stu-id="23e30-129">SB and EB are required.</span></span> <span data-ttu-id="23e30-130">CR est facultative.</span><span class="sxs-lookup"><span data-stu-id="23e30-130">CR is optional.</span></span>|  
|<span data-ttu-id="23e30-131">/ STATICACK</span><span class="sxs-lookup"><span data-stu-id="23e30-131">/STATICACK</span></span>|<span data-ttu-id="23e30-132">L’accusé de réception statique renvoyé à l’expéditeur.</span><span class="sxs-lookup"><span data-stu-id="23e30-132">The static acknowledgment returned to the sender.</span></span> <span data-ttu-id="23e30-133">Mode fractionné appliquera.</span><span class="sxs-lookup"><span data-stu-id="23e30-133">Will enforce SPLIT mode.</span></span>|  
|<span data-ttu-id="23e30-134">/ HL7ACK</span><span class="sxs-lookup"><span data-stu-id="23e30-134">/HL7ACK</span></span>|<span data-ttu-id="23e30-135">L’accusé de réception HL7 renvoyé à l’expéditeur.</span><span class="sxs-lookup"><span data-stu-id="23e30-135">The HL7 acknowledgment returned to the sender.</span></span> <span data-ttu-id="23e30-136">Nom de fichier indique le nom du fichier contenant les accusés de réception HL7.</span><span class="sxs-lookup"><span data-stu-id="23e30-136">FILENAME denotes the name of the file containing the HL7 ACK.</span></span> <span data-ttu-id="23e30-137">Mode fractionné appliquera.</span><span class="sxs-lookup"><span data-stu-id="23e30-137">Will enforce SPLIT mode.</span></span>|  
|<span data-ttu-id="23e30-138">/ SB</span><span class="sxs-lookup"><span data-stu-id="23e30-138">/SB</span></span>|<span data-ttu-id="23e30-139">Définit la valeur ASCII de démarrer un octet de séparateur de bloc.</span><span class="sxs-lookup"><span data-stu-id="23e30-139">Sets the ASCII value of Start Block Delimiter Byte.</span></span> <span data-ttu-id="23e30-140">La valeur par défaut est none.</span><span class="sxs-lookup"><span data-stu-id="23e30-140">The default is none.</span></span>|  
|<span data-ttu-id="23e30-141">/EB</span><span class="sxs-lookup"><span data-stu-id="23e30-141">/EB</span></span>|<span data-ttu-id="23e30-142">Définit la valeur ASCII d’octet de délimiteur de bloc de fin.</span><span class="sxs-lookup"><span data-stu-id="23e30-142">Sets the ASCII value of End Block Delimiter Byte.</span></span> <span data-ttu-id="23e30-143">La valeur par défaut est none.</span><span class="sxs-lookup"><span data-stu-id="23e30-143">The default is none.</span></span>|  
|<span data-ttu-id="23e30-144">/CR</span><span class="sxs-lookup"><span data-stu-id="23e30-144">/CR</span></span>|<span data-ttu-id="23e30-145">Définit la valeur ASCII d’octet de séparateur retour chariot.</span><span class="sxs-lookup"><span data-stu-id="23e30-145">Sets the ASCII value of Carriage Return Delimiter Byte.</span></span> <span data-ttu-id="23e30-146">La valeur par défaut est none.</span><span class="sxs-lookup"><span data-stu-id="23e30-146">The default is none.</span></span>|  
  
## <a name="example-of-tool-use"></a><span data-ttu-id="23e30-147">Exemple d’utilisation de l’outil</span><span class="sxs-lookup"><span data-stu-id="23e30-147">Example of Tool Use</span></span>  
 <span data-ttu-id="23e30-148">Vous pouvez utiliser la commande suivante pour écouter le port 10000 sur localhost et enregistrer des messages pour séparer les fichiers dans C:\TEMP :</span><span class="sxs-lookup"><span data-stu-id="23e30-148">You can use the following command to listen to port 10000 on localhost, and save messages to separate files on C:\TEMP:</span></span>  
  
```  
mllpreceive.exe /P 10000 /SPLIT /SB 11 /EB 28 /CR 13 /D C:\TEMP  
```  
  
## <a name="see-also"></a><span data-ttu-id="23e30-149">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="23e30-149">See Also</span></span>  
 [<span data-ttu-id="23e30-150">Utilitaires</span><span class="sxs-lookup"><span data-stu-id="23e30-150">Utilities</span></span>](../../adapters-and-accelerators/accelerator-hl7/utilities2.md)