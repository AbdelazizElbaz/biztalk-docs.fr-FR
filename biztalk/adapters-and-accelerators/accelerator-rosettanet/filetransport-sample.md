---
title: Exemple de FileTransport | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a32c8cbf-0c17-4237-b2a3-9d21faa13496
caps.latest.revision: "11"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 495e4cfe4c9c9b9d7ae16ee58f7831ad5447d37b
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="filetransport-sample"></a><span data-ttu-id="370dc-102">Exemple de FileTransport</span><span class="sxs-lookup"><span data-stu-id="370dc-102">FileTransport Sample</span></span>
<span data-ttu-id="370dc-103">L’exemple FileTransport montre comment configurer [!INCLUDE[btsCoName](../../includes/btsconame-md.md)]® [!INCLUDE[BTARN_CurrentVersion_FirstRef](../../includes/btarn-currentversion-firstref-md.md)] d’utiliser des ports de fichier, au lieu des ports SQL.</span><span class="sxs-lookup"><span data-stu-id="370dc-103">The FileTransport sample demonstrates how to configure [!INCLUDE[btsCoName](../../includes/btsconame-md.md)]® [!INCLUDE[BTARN_CurrentVersion_FirstRef](../../includes/btarn-currentversion-firstref-md.md)] to use File ports, instead of SQL ports.</span></span> <span data-ttu-id="370dc-104">L’exemple FileTransport utilise le Transport FTP (File Protocol) pour envoyer et recevoir des messages, au lieu de HTTP.</span><span class="sxs-lookup"><span data-stu-id="370dc-104">The FileTransport sample uses File Transport Protocol (FTP) to send and receive messages, instead of HTTP.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="370dc-105">Ce document suppose que vous installez [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] test ou démonstration à usage interne uniquement.</span><span class="sxs-lookup"><span data-stu-id="370dc-105">This document assumes that you are installing [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] for internal testing or demonstration purposes only.</span></span> <span data-ttu-id="370dc-106">Il ne pas prescrire n’importe quel compte de sécurité minimale ou configuration.</span><span class="sxs-lookup"><span data-stu-id="370dc-106">It does not prescribe any minimum-security account or set up.</span></span> <span data-ttu-id="370dc-107">Vous devez utiliser un compte qui dispose des autorisations d’administrateur local dans les procédures décrites dans cette rubrique.</span><span class="sxs-lookup"><span data-stu-id="370dc-107">You must use an account that has local administrative permissions throughout the procedures in this topic.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="370dc-108">Cet exemple ne prend pas en charge les pièces jointes de message.</span><span class="sxs-lookup"><span data-stu-id="370dc-108">This sample does not support message attachments.</span></span>  
  
## <a name="filetransport-binding-files"></a><span data-ttu-id="370dc-109">Fichiers de liaison FileTransport</span><span class="sxs-lookup"><span data-stu-id="370dc-109">FileTransport Binding Files</span></span>  
 <span data-ttu-id="370dc-110">L’exemple de FileTransport inclut deux fichiers de liaison.</span><span class="sxs-lookup"><span data-stu-id="370dc-110">The FileTransport sample includes two binding files.</span></span> <span data-ttu-id="370dc-111">Vous pouvez utiliser chacun de ces fichiers de liaison à configurer des ports de fichier pour une utilisation avec une orchestration BTARN.</span><span class="sxs-lookup"><span data-stu-id="370dc-111">You can use each of these binding files to set up File ports for use with a BTARN orchestration.</span></span> <span data-ttu-id="370dc-112">Ces fichiers de liaison se trouvent dans  *\<lecteur >*: \Program Files\Microsoft BizTalk \<version > Accelerator for RosettaNet \SDK\FileTransport.</span><span class="sxs-lookup"><span data-stu-id="370dc-112">These binding files are located in *\<drive>*:\Program Files\Microsoft BizTalk \<version> Accelerator for RosettaNet \SDK\FileTransport.</span></span> <span data-ttu-id="370dc-113">Ouvrez chaque fichier de liaison dans un éditeur tel que le bloc-notes pour afficher les paramètres de l’orchestration, port d’envoi, port de réception et emplacement de réception, comme indiqué ci-dessous.</span><span class="sxs-lookup"><span data-stu-id="370dc-113">Open each binding file in an editor like Notepad to see the settings for the orchestration, send port, receive port, and receive location, as listed below.</span></span>  
  
-   <span data-ttu-id="370dc-114">PrivateInitiatorusingFileDrops.xml</span><span class="sxs-lookup"><span data-stu-id="370dc-114">PrivateInitiatorusingFileDrops.xml</span></span>  
  
    -   <span data-ttu-id="370dc-115">Orchestration : Microsoft.Solutions.BTARN.PrivateInitiator.PrivateInitiatorProcess</span><span class="sxs-lookup"><span data-stu-id="370dc-115">Orchestration: Microsoft.Solutions.BTARN.PrivateInitiator.PrivateInitiatorProcess</span></span>  
  
    -   <span data-ttu-id="370dc-116">Port d’envoi : PrivateInitiator_To_File</span><span class="sxs-lookup"><span data-stu-id="370dc-116">Send port: PrivateInitiator_To_File</span></span>  
  
    -   <span data-ttu-id="370dc-117">Port de réception : File_To_PrivateInitiator</span><span class="sxs-lookup"><span data-stu-id="370dc-117">Receive port: File_To_PrivateInitiator</span></span>  
  
    -   <span data-ttu-id="370dc-118">Emplacement de réception : File_To_PrivateInitiator</span><span class="sxs-lookup"><span data-stu-id="370dc-118">Receive location: File_To_PrivateInitiator</span></span>  
  
-   <span data-ttu-id="370dc-119">PrivateResponderusingFileDrops.xml</span><span class="sxs-lookup"><span data-stu-id="370dc-119">PrivateResponderusingFileDrops.xml</span></span>  
  
    -   <span data-ttu-id="370dc-120">Orchestration : Microsoft.Solutions.BTARN.PrivateResponder.PrivateResponderProcess</span><span class="sxs-lookup"><span data-stu-id="370dc-120">Orchestration: Microsoft.Solutions.BTARN.PrivateResponder.PrivateResponderProcess</span></span>  
  
    -   <span data-ttu-id="370dc-121">Port d’envoi : PrivateResponder_To_File</span><span class="sxs-lookup"><span data-stu-id="370dc-121">Send port: PrivateResponder_To_File</span></span>  
  
    -   <span data-ttu-id="370dc-122">Port de réception : File_To_PrivateResponder</span><span class="sxs-lookup"><span data-stu-id="370dc-122">Receive port: File_To_PrivateResponder</span></span>  
  
    -   <span data-ttu-id="370dc-123">Emplacement de réception : File_To_PrivateResponder</span><span class="sxs-lookup"><span data-stu-id="370dc-123">Receive location: File_To_PrivateResponder</span></span>  
  
 <span data-ttu-id="370dc-124">La procédure suivante décrit comment importer les liaisons à partir des fichiers de liaison à l’aide de la commande BTSTask.</span><span class="sxs-lookup"><span data-stu-id="370dc-124">The following procedure describes how to import the bindings from the binding files using the BTSTask command.</span></span> <span data-ttu-id="370dc-125">Pour plus d’informations, consultez la rubrique « Commande ImportBindings » dans [!INCLUDE[btsBizTalkServer2006r3](../../includes/btsbiztalkserver2006r3-md.md)] aide.</span><span class="sxs-lookup"><span data-stu-id="370dc-125">For more information, see the "ImportBindings Command" topic in [!INCLUDE[btsBizTalkServer2006r3](../../includes/btsbiztalkserver2006r3-md.md)] Help.</span></span>  
  
## <a name="procedure"></a><span data-ttu-id="370dc-126">Procédure</span><span class="sxs-lookup"><span data-stu-id="370dc-126">Procedure</span></span>  
  
#### <a name="to-set-up-btarn-by-using-file-drop-folders"></a><span data-ttu-id="370dc-127">Pour configurer BTARN à l’aide de dossiers de dépôt de fichiers</span><span class="sxs-lookup"><span data-stu-id="370dc-127">To set up BTARN by using file drop folders</span></span>  
  
1.  <span data-ttu-id="370dc-128">Ouvrez l’Explorateur BizTalk.</span><span class="sxs-lookup"><span data-stu-id="370dc-128">Open BizTalk Explorer.</span></span>  
  
2.  <span data-ttu-id="370dc-129">Arrêtez les deux ports d’envoi SQL de LOB, PrivateInitiator_To_LOB et PrivateResponder_To_LOB.</span><span class="sxs-lookup"><span data-stu-id="370dc-129">Stop the two LOB SQL send ports, PrivateInitiator_To_LOB and PrivateResponder_To_LOB.</span></span>  
  
3.  <span data-ttu-id="370dc-130">Désactivez les deux Lob SQL Receive ports, LOB_To_PrivateInitiator et LOB_To_PrivateResponder.</span><span class="sxs-lookup"><span data-stu-id="370dc-130">Disable the two Lob SQL Receive ports, LOB_To_PrivateInitiator and LOB_To_PrivateResponder.</span></span>  
  
4.  <span data-ttu-id="370dc-131">Désinscrire Microsoft.Solutions.BTARN.PrivateResponder.PrivateResponderProcess.</span><span class="sxs-lookup"><span data-stu-id="370dc-131">Unenlist Microsoft.Solutions.BTARN.PrivateResponder.PrivateResponderProcess.</span></span>  
  
5.  <span data-ttu-id="370dc-132">Désinscrire Microsoft.Solutions.BTARN.PrivateInitiator.PrivateInitiatatorProcess.</span><span class="sxs-lookup"><span data-stu-id="370dc-132">Unenlist Microsoft.Solutions.BTARN.PrivateInitiator.PrivateInitiatatorProcess.</span></span>  
  
6.  <span data-ttu-id="370dc-133">Créez un dossier \FileDrops sous le dossier BTARN de C:\Program Files\Microsoft BizTalk \<version > Accelerator for RosettaNet, puis créer la structure de dossiers suivante sous \FileDrops :</span><span class="sxs-lookup"><span data-stu-id="370dc-133">Create a \FileDrops folder under the BTARN folder of C:\Program Files\Microsoft BizTalk \<version> Accelerator for RosettaNet , and then create the following folder structure under \FileDrops:</span></span>  
  
    -   <span data-ttu-id="370dc-134">\PrivateInitiator</span><span class="sxs-lookup"><span data-stu-id="370dc-134">\PrivateInitiator</span></span>  
  
         <span data-ttu-id="370dc-135">\FromLOB</span><span class="sxs-lookup"><span data-stu-id="370dc-135">\FromLOB</span></span>  
  
         <span data-ttu-id="370dc-136">\ToLOB</span><span class="sxs-lookup"><span data-stu-id="370dc-136">\ToLOB</span></span>  
  
    -   <span data-ttu-id="370dc-137">\PrivateResponder</span><span class="sxs-lookup"><span data-stu-id="370dc-137">\PrivateResponder</span></span>  
  
         <span data-ttu-id="370dc-138">\FromLOB</span><span class="sxs-lookup"><span data-stu-id="370dc-138">\FromLOB</span></span>  
  
         <span data-ttu-id="370dc-139">\ToLOB</span><span class="sxs-lookup"><span data-stu-id="370dc-139">\ToLOB</span></span>  
  
7.  <span data-ttu-id="370dc-140">Exécutez la commande suivante (en supposant que BTARN est installé sur le lecteur C:) :</span><span class="sxs-lookup"><span data-stu-id="370dc-140">Run the following command (assuming that BTARN is installed on the C: drive):</span></span>  
  
    ```  
    BTSTask ImportBindings /Source:C:\Program Files\Microsoft BizTalk <version> Accelerator for RosettaNet\SDK\FileTransport\PrivateInitiatorusingFileDrops.xml  
    ```  
  
8.  <span data-ttu-id="370dc-141">Exécutez la commande suivante (en supposant que BTARN est installé sur le lecteur C:) :</span><span class="sxs-lookup"><span data-stu-id="370dc-141">Run the following command (assuming that BTARN is installed on the C: drive):</span></span>  
  
    ```  
    BTSTask ImportBindings /Source:C:\Program Files\Microsoft BizTalk <version> Accelerator for RosettaNet\SDK\FileTransport\PrivateResponderusingFileDrops.xml  
    ```  
  
9. <span data-ttu-id="370dc-142">Démarrer les ports d’envoi : PrivateInitiator_To_File et PrivateResponder_To_File.</span><span class="sxs-lookup"><span data-stu-id="370dc-142">Start the send ports: PrivateInitiator_To_File and PrivateResponder_To_File.</span></span>  
  
10. <span data-ttu-id="370dc-143">Activer les ports de réception : LOB_To_PrivateInitiator et LOB_To_PrivateResponder.</span><span class="sxs-lookup"><span data-stu-id="370dc-143">Enable the receive ports: LOB_To_PrivateInitiator and LOB_To_PrivateResponder.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="370dc-144">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="370dc-144">See Also</span></span>  
 [<span data-ttu-id="370dc-145">Exemples de messagerie</span><span class="sxs-lookup"><span data-stu-id="370dc-145">Messaging Samples</span></span>](../../adapters-and-accelerators/accelerator-rosettanet/messaging-samples.md)