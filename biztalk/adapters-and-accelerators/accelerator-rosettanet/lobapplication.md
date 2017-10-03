---
title: LOBApplication | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- trading partners, submitting actions
- LOBs, submitting actions
- LOBApplication utility
- trading partners, response messages
- LOBs, LOBApplication utility
- LOBs, response messages
ms.assetid: ad5986af-4175-49cd-806b-04e1fde63f55
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: ed2dc02911ad8ce78e3657c78ad1150d96b4f4f9
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="lobapplication"></a><span data-ttu-id="acf2d-102">LOBApplication</span><span class="sxs-lookup"><span data-stu-id="acf2d-102">LOBApplication</span></span>
<span data-ttu-id="acf2d-103">Vous utilisez l’utilitaire LOBApplication pour envoyer un message d’action ou d’une réponse à un partenaire commercial, en simulant un programme de bureau de métier (LOB) réels.</span><span class="sxs-lookup"><span data-stu-id="acf2d-103">You use the LOBApplication utility to submit an action or response message to a trading partner, simulating an actual line-of-business (LOB) desktop program.</span></span>  
  
 [!INCLUDE[btsCoName](../../includes/btsconame-md.md)]<span data-ttu-id="acf2d-104">® [!INCLUDE[BTARN_CurrentVersion_FirstRef](../../includes/btarn-currentversion-firstref-md.md)] fournit des exemples de messages dans la \< *lecteur*> \Program Files\Microsoft BizTalk \<version > Accelerator for RosettaNet\SDK\LOBApplication\SampleInstances dossier.</span><span class="sxs-lookup"><span data-stu-id="acf2d-104">® [!INCLUDE[BTARN_CurrentVersion_FirstRef](../../includes/btarn-currentversion-firstref-md.md)] provides sample messages in the \<*drive*>\Program Files\Microsoft BizTalk \<version> Accelerator for RosettaNet\SDK\LOBApplication\SampleInstances folder.</span></span>  
  
## <a name="location-in-sdk"></a><span data-ttu-id="acf2d-105">Emplacement dans le kit de développement logiciel (SDK)</span><span class="sxs-lookup"><span data-stu-id="acf2d-105">Location in SDK</span></span>  
 <span data-ttu-id="acf2d-106">\<*lecteur*> \Program Files\Microsoft BizTalk \<version > Accelerator for RosettaNet\SDK\LOBApplication</span><span class="sxs-lookup"><span data-stu-id="acf2d-106">\<*drive*>\Program Files\Microsoft BizTalk \<version> Accelerator for RosettaNet\SDK\LOBApplication</span></span>  
  
## <a name="running-lobapplication"></a><span data-ttu-id="acf2d-107">LOBApplication en cours d’exécution</span><span class="sxs-lookup"><span data-stu-id="acf2d-107">Running LOBApplication</span></span>  
  
#### <a name="to-run-lobapplication"></a><span data-ttu-id="acf2d-108">Pour exécuter LOBApplication</span><span class="sxs-lookup"><span data-stu-id="acf2d-108">To run LOBApplication</span></span>  
  
1.  <span data-ttu-id="acf2d-109">Dans l’Explorateur Windows, accédez à \< *lecteur*> \Program Files\Microsoft BizTalk \<version > Accelerator for RosettaNet\SDK\\.</span><span class="sxs-lookup"><span data-stu-id="acf2d-109">In Windows Explorer, move to \<*drive*>\Program Files\Microsoft BizTalk \<version> Accelerator for RosettaNet\SDK\\.</span></span>  
  
2.  <span data-ttu-id="acf2d-110">Double-cliquez sur **LOBApplication.exe**, puis appuyez sur ENTRÉE.</span><span class="sxs-lookup"><span data-stu-id="acf2d-110">Double-click **LOBApplication.exe**, and then press ENTER.</span></span>  
  
     <span data-ttu-id="acf2d-111">Les pages qui suivent vous invitent à entrer les informations requises pour exécuter l’utilitaire.</span><span class="sxs-lookup"><span data-stu-id="acf2d-111">The pages that follow prompt you for the information that is required to run the utility.</span></span>  
  
## <a name="syntax-for-lobapplication"></a><span data-ttu-id="acf2d-112">Syntaxe de LOBApplication</span><span class="sxs-lookup"><span data-stu-id="acf2d-112">Syntax for LOBApplication</span></span>  
 <span data-ttu-id="acf2d-113">Utilisez le **Proxy d’Application LOB** page pour spécifier les noms de page d’accueil et les partenaires, les propriétés de processus PIP (Partner Interface) et les propriétés de message pour le message envoyé par l’utilitaire LOBApplication.</span><span class="sxs-lookup"><span data-stu-id="acf2d-113">Use the **LOB Application Proxy** page to specify home and partner names, Partner Interface Process (PIP) properties, and message properties for the message sent by the LOBApplication utility.</span></span>  
  
 <span data-ttu-id="acf2d-114">Le tableau suivant décrit l’utilisation de chaque champ sur la **Proxy d’Application LOB** page.</span><span class="sxs-lookup"><span data-stu-id="acf2d-114">The following table describes how to use each field on the **LOB Application Proxy** page.</span></span>  
  
|<span data-ttu-id="acf2d-115">Utiliser</span><span class="sxs-lookup"><span data-stu-id="acf2d-115">Use this</span></span>|<span data-ttu-id="acf2d-116">Pour effectuer cette opération</span><span class="sxs-lookup"><span data-stu-id="acf2d-116">To do this</span></span>|  
|--------------|----------------|  
|<span data-ttu-id="acf2d-117">**Nom du profil de base**</span><span class="sxs-lookup"><span data-stu-id="acf2d-117">**Home Profile Name**</span></span>|<span data-ttu-id="acf2d-118">Tapez le nom de l’organisation d’origine (tiers de la source).</span><span class="sxs-lookup"><span data-stu-id="acf2d-118">Type the name of the home organization (source party).</span></span>|  
|<span data-ttu-id="acf2d-119">**Nom du partenaire commercial**</span><span class="sxs-lookup"><span data-stu-id="acf2d-119">**Trading Partner Name**</span></span>|<span data-ttu-id="acf2d-120">Tapez le nom du partenaire commercial (tiers de destination).</span><span class="sxs-lookup"><span data-stu-id="acf2d-120">Type the name of the trading partner (destination party).</span></span>|  
|<span data-ttu-id="acf2d-121">**Nom du PIP**</span><span class="sxs-lookup"><span data-stu-id="acf2d-121">**PIP Name**</span></span>|<span data-ttu-id="acf2d-122">Tapez le code de l’affichage du PIP, par exemple, type **3A2**.</span><span class="sxs-lookup"><span data-stu-id="acf2d-122">Type the display code of the PIP, for example, type **3A2**.</span></span> <span data-ttu-id="acf2d-123">Cette valeur respecte la casse.</span><span class="sxs-lookup"><span data-stu-id="acf2d-123">This value is case-sensitive.</span></span>|  
|<span data-ttu-id="acf2d-124">**Version PIP**</span><span class="sxs-lookup"><span data-stu-id="acf2d-124">**PIP Version**</span></span>|<span data-ttu-id="acf2d-125">Type de la version du PIP, par exemple, type **V02.00**.</span><span class="sxs-lookup"><span data-stu-id="acf2d-125">Type the version of the PIP, for example, type **V02.00**.</span></span> <span data-ttu-id="acf2d-126">Cette valeur respecte la casse.</span><span class="sxs-lookup"><span data-stu-id="acf2d-126">This value is case-sensitive.</span></span>|  
|<span data-ttu-id="acf2d-127">**ID d’Instance PIP** (facultatif)</span><span class="sxs-lookup"><span data-stu-id="acf2d-127">**PIP Instance ID** (optional)</span></span>|<span data-ttu-id="acf2d-128">Tapez un ID d’instance alphanumériques pour le PIP, par exemple, tapez **STD_3A2_V02.02**.</span><span class="sxs-lookup"><span data-stu-id="acf2d-128">Type an alphanumeric instance ID for the PIP, for example, type **STD_3A2_V02.02**.</span></span> <span data-ttu-id="acf2d-129">Évitez les caractères spéciaux.</span><span class="sxs-lookup"><span data-stu-id="acf2d-129">Avoid special characters.</span></span> <span data-ttu-id="acf2d-130">L’ID doit être unique par partenaire et par code PIP.</span><span class="sxs-lookup"><span data-stu-id="acf2d-130">The ID should be unique per partner and per PIP code.</span></span> <span data-ttu-id="acf2d-131">Pour les messages qui sont marqués comme messages d’action, si l’ID d’Instance est vide, l’utilitaire LOBApplication utilise une valeur HUID générée pour l’ID d’Instance PIP.</span><span class="sxs-lookup"><span data-stu-id="acf2d-131">For messages that are marked as action messages, if the Instance ID is empty, the LOBApplication utility uses a generated HUID value for the PIP Instance ID.</span></span> <span data-ttu-id="acf2d-132">**Remarque :** lorsque vous sélectionnez **réponse** dans les **Message catégorie**, vous devez taper l’ID d’Instance PIP dans ce champ.</span><span class="sxs-lookup"><span data-stu-id="acf2d-132">**Note:**  When you select **Response** in the **Message Category**, you must type the PIP Instance ID in this field.</span></span>|  
|<span data-ttu-id="acf2d-133">**Nom de fichier**</span><span class="sxs-lookup"><span data-stu-id="acf2d-133">**File Name**</span></span>|<span data-ttu-id="acf2d-134">Cliquez sur le bouton de sélection (...), accédez au dossier qui contient le fichier d’instance PIP, puis cliquez sur le fichier d’instance PIP.</span><span class="sxs-lookup"><span data-stu-id="acf2d-134">Click the ellipsis button (...), go to the folder that contains the PIP instance file, and then click the PIP instance file.</span></span>|  
|<span data-ttu-id="acf2d-135">**Catégorie de message**</span><span class="sxs-lookup"><span data-stu-id="acf2d-135">**Message Category**</span></span>|<span data-ttu-id="acf2d-136">Sélectionnez le type de message (**Action** ou **réponse**).</span><span class="sxs-lookup"><span data-stu-id="acf2d-136">Select the type of message (**Action** or **Response**).</span></span>|  
|<span data-ttu-id="acf2d-137">**Pièces jointes**</span><span class="sxs-lookup"><span data-stu-id="acf2d-137">**Attachments**</span></span>|<span data-ttu-id="acf2d-138">Cliquez sur **ajouter**, accédez au dossier qui contient le fichier de pièce jointe, puis cliquez sur **ouvrir**.</span><span class="sxs-lookup"><span data-stu-id="acf2d-138">Click **Add**, move to the folder that contains the attachment file, and then click **Open**.</span></span>|  
|<span data-ttu-id="acf2d-139">**Envoyer le Message**</span><span class="sxs-lookup"><span data-stu-id="acf2d-139">**Submit Message**</span></span>|<span data-ttu-id="acf2d-140">Cliquez ici pour envoyer le message.</span><span class="sxs-lookup"><span data-stu-id="acf2d-140">Click to send the message.</span></span>|  
|<span data-ttu-id="acf2d-141">**État**</span><span class="sxs-lookup"><span data-stu-id="acf2d-141">**Status**</span></span>|<span data-ttu-id="acf2d-142">Lire l’état de l’action dans ce champ.</span><span class="sxs-lookup"><span data-stu-id="acf2d-142">Read the status of the action in this field.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="acf2d-143">Notes</span><span class="sxs-lookup"><span data-stu-id="acf2d-143">Remarks</span></span>  
 <span data-ttu-id="acf2d-144">L’utilitaire LOBApplication crée un message avec les propriétés spécifiées et l’envoie au partenaire commercial.</span><span class="sxs-lookup"><span data-stu-id="acf2d-144">The LOBApplication utility creates a message with the properties specified, and sends it to the trading partner.</span></span> <span data-ttu-id="acf2d-145">Cet utilitaire écrit les données de contenu de service dans le message à la base de données BTARNDATA, dans la table MessageFromLOB.</span><span class="sxs-lookup"><span data-stu-id="acf2d-145">This utility writes the service content data in the message to the BTARNDATA database, in the MessageFromLOB table.</span></span> <span data-ttu-id="acf2d-146">Il simule l’envoi d’un message d’action.</span><span class="sxs-lookup"><span data-stu-id="acf2d-146">This utility simulates sending an action message.</span></span>  
  
 <span data-ttu-id="acf2d-147">Les exemples de messages dans le dossier SampleInstances sous le dossier LOBApplication dans le [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] SDK sont préconfigurés à assumer les identificateurs d’entreprise Global (GBIs) suivants : 123456789 pour l’organisation d’origine et 987654321 pour le partenaire organisation.</span><span class="sxs-lookup"><span data-stu-id="acf2d-147">The sample messages in the SampleInstances folder under the LOBApplication folder in the [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] SDK are preconfigured to assume the following Global Business Identifiers (GBIs): 123456789 for the home organization and 987654321 for the partner organization.</span></span> <span data-ttu-id="acf2d-148">Vous devez modifier les exemples de messages dans un éditeur de texte à utiliser d’autres GBIs.</span><span class="sxs-lookup"><span data-stu-id="acf2d-148">You must change the sample messages in a text editor to use other GBIs.</span></span>  
  
 <span data-ttu-id="acf2d-149">Vous utilisez l’utilitaire LOBApplication pour simuler un programme de bureau métier-envoi d’un message.</span><span class="sxs-lookup"><span data-stu-id="acf2d-149">You use the LOBApplication utility to simulate a line-of-business desktop program submitting a message.</span></span> <span data-ttu-id="acf2d-150">Vous utilisez l’utilitaire LOBWebApplication pour simuler une application Web de métier-envoi d’un message.</span><span class="sxs-lookup"><span data-stu-id="acf2d-150">You use the LOBWebApplication utility to simulate a line-of-business Web application submitting a message.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="acf2d-151">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="acf2d-151">See Also</span></span>  
 <span data-ttu-id="acf2d-152">[Utilitaires](../../adapters-and-accelerators/accelerator-rosettanet/utilities1.md) </span><span class="sxs-lookup"><span data-stu-id="acf2d-152">[Utilities](../../adapters-and-accelerators/accelerator-rosettanet/utilities1.md) </span></span>  
 [<span data-ttu-id="acf2d-153">LOBWebApplication</span><span class="sxs-lookup"><span data-stu-id="acf2d-153">LOBWebApplication</span></span>](../../adapters-and-accelerators/accelerator-rosettanet/lobwebapplication.md)