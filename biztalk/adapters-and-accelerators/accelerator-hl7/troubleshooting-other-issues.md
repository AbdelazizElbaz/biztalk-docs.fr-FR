---
title: "Résolution d’autres problèmes | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: troubleshooting
ms.assetid: 1f115f64-45ce-445d-ab18-092f4a6a232c
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 796482df7234e2699b5b9bd3d1c12f6e98ccb923
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="troubleshooting-other-issues"></a><span data-ttu-id="36149-102">Résolution d’autres problèmes</span><span class="sxs-lookup"><span data-stu-id="36149-102">Troubleshooting Other Issues</span></span>
<span data-ttu-id="36149-103">Autres problèmes liés à des adresses [!INCLUDE[btsCoName](../../includes/btsconame-md.md)] [!INCLUDE[HL7_CurrentVersion_FirstRef](../../includes/hl7-currentversion-firstref-md.md)].</span><span class="sxs-lookup"><span data-stu-id="36149-103">Addresses other issues related to [!INCLUDE[btsCoName](../../includes/btsconame-md.md)] [!INCLUDE[HL7_CurrentVersion_FirstRef](../../includes/hl7-currentversion-firstref-md.md)].</span></span>  
  
## <a name="message-rejected-by-the-btahl7-engine"></a><span data-ttu-id="36149-104">Message rejeté par le moteur de BTAHL7</span><span class="sxs-lookup"><span data-stu-id="36149-104">Message rejected by the BTAHL7 engine</span></span>  
  
### <a name="symptom"></a><span data-ttu-id="36149-105">Symptôme</span><span class="sxs-lookup"><span data-stu-id="36149-105">Symptom</span></span>  
 <span data-ttu-id="36149-106">Les messages sont rejetés aléatoirement par le moteur de messagerie.</span><span class="sxs-lookup"><span data-stu-id="36149-106">Messages are randomly rejected by the message engine.</span></span>  
  
<span data-ttu-id="36149-107">**Cause possible** : selon la norme HL7, valeurs d’énumération pour la table 0338 contient la valeur « L & I ».</span><span class="sxs-lookup"><span data-stu-id="36149-107">**Possible Cause** : According to the HL7 standard, enumeration values for table 0338 contains the "L&I" value.</span></span> <span data-ttu-id="36149-108">6 de champ du segment PRA peut contenir cette valeur.</span><span class="sxs-lookup"><span data-stu-id="36149-108">Field 6 of the PRA segment may contain this value.</span></span> <span data-ttu-id="36149-109">Étant donné que [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] traite le caractère « & » comme un délimiteur, le message est rejeté.</span><span class="sxs-lookup"><span data-stu-id="36149-109">Since [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] treats the "&" character as a delimiter, the message is rejected.</span></span>  
  
<span data-ttu-id="36149-110">**Résolution** : il existe trois solutions possibles pour résoudre ce problème :</span><span class="sxs-lookup"><span data-stu-id="36149-110">**Resolution** : There are three potential resolutions for this issue:</span></span>  
  
1.  <span data-ttu-id="36149-111">Dans l’instance de message, gérer le caractère « & » via une séquence d’échappement, telles que l’utilisation de la combinaison de caractères L\T\I.</span><span class="sxs-lookup"><span data-stu-id="36149-111">In the message instance, handle the "&" character through an escape sequence, such as using the character combination L\T\I.</span></span>  
  
2.  <span data-ttu-id="36149-112">Ajouter une valeur d’énumération de « LI » à PRA 6 dans le schéma et utiliser à la place de cette valeur dans l’instance de message.</span><span class="sxs-lookup"><span data-stu-id="36149-112">Add an enumeration value of "LI" at PRA 6 in the schema and use this value instead in the message instance.</span></span>  
  
3.  <span data-ttu-id="36149-113">Utilisez un séparateur de sous-composant complètement différentes dans où MSH2 a été ; Toutefois, cette solution ne peut pas être pratique, en fonction de votre environnement.</span><span class="sxs-lookup"><span data-stu-id="36149-113">Use a completely different subcomponent separator in MSH2; however, this particular solution may not be practical depending upon your environment.</span></span>  
  
## <a name="cannot-edit-the-hl7-schema-using-visual-studio"></a><span data-ttu-id="36149-114">Impossible de modifier le schéma HL7 à l’aide de Visual Studio</span><span class="sxs-lookup"><span data-stu-id="36149-114">Cannot edit the HL7 schema using Visual Studio</span></span>  
  
### <a name="symptom"></a><span data-ttu-id="36149-115">Symptôme</span><span class="sxs-lookup"><span data-stu-id="36149-115">Symptom</span></span>  
 <span data-ttu-id="36149-116">Impossible de modifier le schéma HL7 avec [!INCLUDE[btsCoName](../../includes/btsconame-md.md)] [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="36149-116">Cannot edit the HL7 schema using [!INCLUDE[btsCoName](../../includes/btsconame-md.md)][!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)].</span></span>  
  
<span data-ttu-id="36149-117">**Cause possible** : [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)] ne prend pas en charge certains schémas HL7.</span><span class="sxs-lookup"><span data-stu-id="36149-117">**Possible Cause** : [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)] does not support some HL7 schemas.</span></span>  
  
<span data-ttu-id="36149-118">**Résolution** : utiliser les autres éditeurs, tels que [!INCLUDE[btsCoName](../../includes/btsconame-md.md)] le bloc-notes, pour modifier les schémas HL7.</span><span class="sxs-lookup"><span data-stu-id="36149-118">**Resolution** : Use other editors, such as [!INCLUDE[btsCoName](../../includes/btsconame-md.md)] Notepad, to edit HL7 schemas.</span></span>  
  
## <a name="message-handling-fails-with-no-errors-logged"></a><span data-ttu-id="36149-119">Échec de la gestion des messages sans erreur connecté</span><span class="sxs-lookup"><span data-stu-id="36149-119">Message handling fails with no errors logged</span></span>  
  
### <a name="symptom"></a><span data-ttu-id="36149-120">Symptôme</span><span class="sxs-lookup"><span data-stu-id="36149-120">Symptom</span></span>  
 <span data-ttu-id="36149-121">Le système traite les messages sans enregistrer les messages d’erreur ou de placer les messages dans la file d’attente de message suspendu.</span><span class="sxs-lookup"><span data-stu-id="36149-121">The system processes messages without logging error messages or placing messages in the suspended message queue.</span></span>  
  
<span data-ttu-id="36149-122">**Cause possible** : le **HeaderSpecType** et **DocumentSpecType** les valeurs de propriété respectent la casse.</span><span class="sxs-lookup"><span data-stu-id="36149-122">**Possible Cause** : The **HeaderSpecType** and **DocumentSpecType** property values are case-sensitive.</span></span> <span data-ttu-id="36149-123">Lorsque vous déployez vos pipelines, une erreur typographique dans ces noms peut entraîner des messages d’erreur de manipulation et de supprimée sans erreur connecté.</span><span class="sxs-lookup"><span data-stu-id="36149-123">When you deploy your pipelines, a typographical error in these names can cause messages to be mishandled and dropped with no errors logged.</span></span>  
  
<span data-ttu-id="36149-124">**Résolution** : observer le respect de la casse lors de l’utilisation du **HeaderSpecType** et **DocumentSpecType** les noms de valeurs de propriété.</span><span class="sxs-lookup"><span data-stu-id="36149-124">**Resolution** : Observe case-sensitivity when using the **HeaderSpecType** and **DocumentSpecType** property value names.</span></span>  
  
## <a name="message-header-fields-are-not-validated-correctly"></a><span data-ttu-id="36149-125">Champs d’en-tête de message ne sont pas validés correctement</span><span class="sxs-lookup"><span data-stu-id="36149-125">Message header fields are not validated correctly</span></span>  
  
### <a name="symptom"></a><span data-ttu-id="36149-126">Symptôme</span><span class="sxs-lookup"><span data-stu-id="36149-126">Symptom</span></span>  
 <span data-ttu-id="36149-127">Échec de la validation d’un champ d’en-tête.</span><span class="sxs-lookup"><span data-stu-id="36149-127">Validation of a header field failed.</span></span>  
  
 <span data-ttu-id="36149-128">Raison : Le [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] sérialiseur validé une propriété promue, pas la propriété de contexte de champ d’en-tête réelle.</span><span class="sxs-lookup"><span data-stu-id="36149-128">Reason: The [!INCLUDE[btaBTAHL71.3abbrevnonumber](../../includes/btabtahl71-3abbrevnonumber-md.md)] serializer validated a promoted property, not the actual header-field context property.</span></span>  
  
<span data-ttu-id="36149-129">**Cause possible** : une modification s’est produite à la propriété promue correspondant à l’en-tête via une orchestration ou un mappage.</span><span class="sxs-lookup"><span data-stu-id="36149-129">**Possible Cause** : A change occurred to the promoted property corresponding to the header through an orchestration or a map.</span></span>  
  
<span data-ttu-id="36149-130">**Résolution** : les propriétés de contexte de message, en-têtes MSH1, où MSH2 a été et MSH5 {1-3} devoir être mis à jour afin qu’ils soient synchronisés avec les données.</span><span class="sxs-lookup"><span data-stu-id="36149-130">**Resolution** : The context properties of message headers MSH1, MSH2, and MSH5{1-3} need to be updated so that they are in synchronization with the data.</span></span>  
  
## <a name="the-mllp-adapter-is-not-removed-during-uninstall"></a><span data-ttu-id="36149-131">L’adaptateur MLLP n’est pas supprimé lors de la désinstallation</span><span class="sxs-lookup"><span data-stu-id="36149-131">The MLLP adapter is not removed during uninstall</span></span>  
  
### <a name="symptom"></a><span data-ttu-id="36149-132">Symptôme</span><span class="sxs-lookup"><span data-stu-id="36149-132">Symptom</span></span>  
 <span data-ttu-id="36149-133">Le programme d’installation BTAHL7 n’a pas supprimé l’adaptateur MLLP lors de la désinstallation de BTAHL7.</span><span class="sxs-lookup"><span data-stu-id="36149-133">The BTAHL7 setup program did not remove the MLLP adapter during uninstallation of BTAHL7.</span></span>  
  
<span data-ttu-id="36149-134">**Cause possible** : il y a un port de réception emplacement ou d’envoi avec un type de transport de MLLP.</span><span class="sxs-lookup"><span data-stu-id="36149-134">**Possible Cause** : There was a receive location or send port with a transport type of MLLP.</span></span> <span data-ttu-id="36149-135">Le programme d’installation BTAHL7 ne peut pas supprimer l’adaptateur MLLP si elle est référencée dans un des projets BizTalk Server.</span><span class="sxs-lookup"><span data-stu-id="36149-135">BTAHL7 setup cannot remove the MLLP adapter if it is being referenced in any of the BizTalk Server projects.</span></span>  
  
<span data-ttu-id="36149-136">**Résolution** : à l’issue de la désinstallation de BTAHL7, procédez comme suit :</span><span class="sxs-lookup"><span data-stu-id="36149-136">**Resolution** : After uninstallation of BTAHL7 has completed, do the following:</span></span>  
  
1.  <span data-ttu-id="36149-137">Dans la Console Administration de BizTalk Server, supprimez tous les emplacements de réception et ports d’envoi qui ont un type de transport de MLLP, ou modifier le type de transport, les emplacements de réception ou ports d’envoi à un autre type.</span><span class="sxs-lookup"><span data-stu-id="36149-137">In the BizTalk Server Administration Console, remove all receive locations and send ports that have a transport type of MLLP, or change the transport type of the receive locations or send ports to another type.</span></span>  
  
2.  <span data-ttu-id="36149-138">Dans la Console d’Administration, supprimez l’adaptateur MLLP.</span><span class="sxs-lookup"><span data-stu-id="36149-138">In the Administration Console, delete the MLLP adapter.</span></span>  
  
3.  <span data-ttu-id="36149-139">Redémarrez l’instance d’hôte.</span><span class="sxs-lookup"><span data-stu-id="36149-139">Restart the host instance.</span></span>  
  
## <a name="btahl7-cannot-be-uninstalled-if-biztalk-server-has-already-been-uninstalled"></a><span data-ttu-id="36149-140">BTAHL7 ne peut pas être désinstallé si BizTalk Server a déjà été désinstallé</span><span class="sxs-lookup"><span data-stu-id="36149-140">BTAHL7 cannot be uninstalled if BizTalk Server has already been uninstalled</span></span>  
  
### <a name="symptom"></a><span data-ttu-id="36149-141">Symptôme</span><span class="sxs-lookup"><span data-stu-id="36149-141">Symptom</span></span>  
 <span data-ttu-id="36149-142">Désinstallation [!INCLUDE[HL7_CurrentVersion_abbrev](../../includes/hl7-currentversion-abbrev-md.md)] entraîne l’erreur suivante :</span><span class="sxs-lookup"><span data-stu-id="36149-142">Uninstalling [!INCLUDE[HL7_CurrentVersion_abbrev](../../includes/hl7-currentversion-abbrev-md.md)] results in the following error:</span></span>  
  
`A network error while attempting to read from file C:\Windows\Installer\Microsoft BizTalk <version\> Accelerator for HL7.msi`
  
<span data-ttu-id="36149-143">**Cause possible** : [!INCLUDE[btsBizTalkServerNoVersion_md](../../includes/btsbiztalkservernoversion-md.md)] a été désinstallée avant la désinstallation de [!INCLUDE[HL7_CurrentVersion_abbrev](../../includes/hl7-currentversion-abbrev-md.md)] a été tentée.</span><span class="sxs-lookup"><span data-stu-id="36149-143">**Possible Cause** : [!INCLUDE[btsBizTalkServerNoVersion_md](../../includes/btsbiztalkservernoversion-md.md)] was uninstalled before uninstallation of [!INCLUDE[HL7_CurrentVersion_abbrev](../../includes/hl7-currentversion-abbrev-md.md)] was attempted.</span></span> <span data-ttu-id="36149-144">Vous devez désinstaller [!INCLUDE[HL7_CurrentVersion_abbrev](../../includes/hl7-currentversion-abbrev-md.md)] avant de désinstaller [!INCLUDE[btsBizTalkServerNoVersion_md](../../includes/btsbiztalkservernoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="36149-144">You must uninstall [!INCLUDE[HL7_CurrentVersion_abbrev](../../includes/hl7-currentversion-abbrev-md.md)] before uninstalling [!INCLUDE[btsBizTalkServerNoVersion_md](../../includes/btsbiztalkservernoversion-md.md)].</span></span>  
  
<span data-ttu-id="36149-145">**Résolution** : Réinstallez [!INCLUDE[btsBizTalkServerNoVersion_md](../../includes/btsbiztalkservernoversion-md.md)], puis désinstallez [!INCLUDE[HL7_CurrentVersion_abbrev](../../includes/hl7-currentversion-abbrev-md.md)], puis désinstallez [!INCLUDE[btsBizTalkServerNoVersion_md](../../includes/btsbiztalkservernoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="36149-145">**Resolution** : Reinstall [!INCLUDE[btsBizTalkServerNoVersion_md](../../includes/btsbiztalkservernoversion-md.md)], then uninstall [!INCLUDE[HL7_CurrentVersion_abbrev](../../includes/hl7-currentversion-abbrev-md.md)], and then uninstall [!INCLUDE[btsBizTalkServerNoVersion_md](../../includes/btsbiztalkservernoversion-md.md)].</span></span>  
  
## <a name="messages-are-still-sent-after-the-applicable-mllp-send-port-has-been-stopped"></a><span data-ttu-id="36149-146">Les messages sont toujours envoyés une fois que le port d’envoi MLLP applicable a été arrêté.</span><span class="sxs-lookup"><span data-stu-id="36149-146">Messages are still sent after the applicable MLLP send port has been stopped</span></span>  
  
### <a name="symptom"></a><span data-ttu-id="36149-147">Symptôme</span><span class="sxs-lookup"><span data-stu-id="36149-147">Symptom</span></span>  
 <span data-ttu-id="36149-148">Après avoir arrêter un MLLP port d’envoi, les messages qui sont envoyées via ce port d’envoi n’arrêtez pas, mais continuer à envoyer.</span><span class="sxs-lookup"><span data-stu-id="36149-148">After you stop an MLLP send port, the messages that are sent through that send port do not stop, but continue to be sent.</span></span>  
  
<span data-ttu-id="36149-149">**Cause possible** : lorsque vous arrêtez un port d’envoi, la connexion reste établie jusqu'à ce qu’il soit supprimé par l’arrêt de l’hôte BizTalk.</span><span class="sxs-lookup"><span data-stu-id="36149-149">**Possible Cause** : When you stop a send port, the connection remains established until it is removed by stopping the BizTalk host.</span></span> <span data-ttu-id="36149-150">Par conséquent, les messages sont envoyés encore une fois que le port d’envoi a été arrêté.</span><span class="sxs-lookup"><span data-stu-id="36149-150">As a result, messages are still sent after the send port has been stopped.</span></span> <span data-ttu-id="36149-151">Cela se produit, car Biztalk Server n’appelle pas dans l’adaptateur MLLP au cours de démarrage ou d’arrêt du port d’envoi.</span><span class="sxs-lookup"><span data-stu-id="36149-151">This occurs because Biztalk Server does not call into the MLLP adapter during start or stop of the send port.</span></span> <span data-ttu-id="36149-152">BizTalk Server appelle l’adaptateur MLLP uniquement pendant le démarrage et arrêt du service hôte.</span><span class="sxs-lookup"><span data-stu-id="36149-152">BizTalk Server calls into the MLLP adapter only during the start and stop of the host service.</span></span>  
  
<span data-ttu-id="36149-153">**Résolution** : vous pouvez supprimer la transmission de connexion et d’arrêter des messages par l’arrêt de l’instance d’hôte qui est le Gestionnaire d’envoi pour le port d’envoi que vous avez arrêtés.</span><span class="sxs-lookup"><span data-stu-id="36149-153">**Resolution** : You can remove the connection and stop transmission of messages by stopping the host instance that is the send handler for the send port that you stopped.</span></span> <span data-ttu-id="36149-154">Toutefois, l’arrêt de cette instance d’hôte peut affecter les autres messages que vous ne souhaitez pas arrêter.</span><span class="sxs-lookup"><span data-stu-id="36149-154">However, stopping that host instance might affect other messages that you do not want to stop.</span></span> <span data-ttu-id="36149-155">Si vous savez que c’est le cas, vous devez configurer le port d’envoi différemment lorsque vous la créez.</span><span class="sxs-lookup"><span data-stu-id="36149-155">If you know that this is the case, you should configure the send port differently when you create it.</span></span> <span data-ttu-id="36149-156">Vous devez créer une autre instance de l’hôte pour servir le Gestionnaire d’envoi pour seulement ce port d’envoi MLLP (ou un sous-ensemble de vos ports d’envoi).</span><span class="sxs-lookup"><span data-stu-id="36149-156">You should create another host instance to serve as the send handler for only this MLLP send port (or a subset of your send ports).</span></span> <span data-ttu-id="36149-157">Vous pouvez ensuite arrêter la transmission des messages à partir de ce port d’envoi par l’arrêt de cette instance d’hôte.</span><span class="sxs-lookup"><span data-stu-id="36149-157">You can then stop transmission of messages from this send port by stopping this host instance.</span></span> <span data-ttu-id="36149-158">Cela affectera puis pas la transmission d’autres messages d’autres ports d’envoi qui utilisent d’autres gestionnaires d’envoi.</span><span class="sxs-lookup"><span data-stu-id="36149-158">This will then not affect transmission of other messages on other send ports that use other send handlers.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="36149-159">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="36149-159">See Also</span></span>  
 [<span data-ttu-id="36149-160">Problèmes connus et dépannage dans HL7</span><span class="sxs-lookup"><span data-stu-id="36149-160">Troubleshooting and known issues in HL7</span></span>](../../adapters-and-accelerators/accelerator-hl7/troubleshooting-and-known-issues-in-hl7.md)