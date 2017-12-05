---
title: "Étape 2 : Création publics et privés certificats | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- double action tutorial, creating certificates
- public certificates
- certificates, public certificates
- creating, certificates
- private certificates
ms.assetid: 0a925d89-03d9-41fe-907b-85a6ae42362a
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 7c26765b19c868dbb78d3924069b60161827312c
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="step-2-creating-public-and-private-certificates"></a><span data-ttu-id="b2e80-102">Étape 2 : Création publiques et privées des certificats</span><span class="sxs-lookup"><span data-stu-id="b2e80-102">Step 2: Creating Public and Private Certificates</span></span>
<span data-ttu-id="b2e80-103">Dans cette étape, vous utilisez l’autorité de Certification créé dans [étape 1 : création d’une autorité de Certification &#91; RN3 &#93; ](../../adapters-and-accelerators/accelerator-rosettanet/step-1-creating-a-certification-authority.md) pour générer les certificats publics et privés qui utilisent des organisations Contoso et Fabrikam.</span><span class="sxs-lookup"><span data-stu-id="b2e80-103">In this step, you use the Certification Authority created in [Step 1: Creating a Certification Authority &#91;RN3&#93;](../../adapters-and-accelerators/accelerator-rosettanet/step-1-creating-a-certification-authority.md) to generate the public and private certificates that the Contoso and Fabrikam organizations use.</span></span>  
  
### <a name="to-generate-the-contoso-and-fabrikam-encryption-certificates"></a><span data-ttu-id="b2e80-104">Pour générer les certificats de chiffrement de Contoso et Fabrikam</span><span class="sxs-lookup"><span data-stu-id="b2e80-104">To generate the Contoso and Fabrikam encryption certificates</span></span>  
  
1.  <span data-ttu-id="b2e80-105">Sur l’ordinateur que vous avez utilisé comme l’autorité de Certification, dans Internet Explorer, recherchez et ouvrez http://<contoso_computername>/certsrv.</span><span class="sxs-lookup"><span data-stu-id="b2e80-105">On the computer you used as the Certification Authority, in Internet Explorer, locate and open http://<contoso_computername>/certsrv.</span></span>  
  
2.  <span data-ttu-id="b2e80-106">Sur le **Bienvenue** , cliquez sur **demander un certificat**.</span><span class="sxs-lookup"><span data-stu-id="b2e80-106">On the **Welcome** page, click **Request a certificate**.</span></span>  
  
3.  <span data-ttu-id="b2e80-107">Sur le **demander un certificat** , cliquez sur **demande de certificat avancée**.</span><span class="sxs-lookup"><span data-stu-id="b2e80-107">On the **Request a Certificate** page, click **advanced certificate request**.</span></span>  
  
4.  <span data-ttu-id="b2e80-108">Sur le **demande de certificat avancée** , cliquez sur **créer et soumettre une demande à cette autorité de certification**.</span><span class="sxs-lookup"><span data-stu-id="b2e80-108">On the **Advanced Certificate Request** page, click **Create and submit a request to this CA**.</span></span>  
  
5.  <span data-ttu-id="b2e80-109">Sur le **demande de certificat avancée** page, procédez comme suit :</span><span class="sxs-lookup"><span data-stu-id="b2e80-109">On the **Advanced Certificate Request** page, do the following:</span></span>  
  
    |<span data-ttu-id="b2e80-110">Utiliser</span><span class="sxs-lookup"><span data-stu-id="b2e80-110">Use this</span></span>|<span data-ttu-id="b2e80-111">Pour effectuer cette opération</span><span class="sxs-lookup"><span data-stu-id="b2e80-111">To do this</span></span>|  
    |--------------|----------------|  
    |<span data-ttu-id="b2e80-112">**Nom**</span><span class="sxs-lookup"><span data-stu-id="b2e80-112">**Name**</span></span>|<span data-ttu-id="b2e80-113">Type **Fabrikam chiffrement**.</span><span class="sxs-lookup"><span data-stu-id="b2e80-113">Type **Fabrikam Encryption**.</span></span>|  
    |<span data-ttu-id="b2e80-114">**Courrier électronique**</span><span class="sxs-lookup"><span data-stu-id="b2e80-114">**E-Mail**</span></span>|<span data-ttu-id="b2e80-115">Type  **jdoe@fabrikam.com** .</span><span class="sxs-lookup"><span data-stu-id="b2e80-115">Type **jdoe@fabrikam.com**.</span></span>|  
    |<span data-ttu-id="b2e80-116">**Company**</span><span class="sxs-lookup"><span data-stu-id="b2e80-116">**Company**</span></span>|<span data-ttu-id="b2e80-117">Type **Fabrikam**.</span><span class="sxs-lookup"><span data-stu-id="b2e80-117">Type **Fabrikam**.</span></span>|  
    |<span data-ttu-id="b2e80-118">**Service**</span><span class="sxs-lookup"><span data-stu-id="b2e80-118">**Department**</span></span>|<span data-ttu-id="b2e80-119">Type **Test**.</span><span class="sxs-lookup"><span data-stu-id="b2e80-119">Type **Test**.</span></span>|  
    |<span data-ttu-id="b2e80-120">**Ville**</span><span class="sxs-lookup"><span data-stu-id="b2e80-120">**City**</span></span>|<span data-ttu-id="b2e80-121">Type **Test**.</span><span class="sxs-lookup"><span data-stu-id="b2e80-121">Type **Test**.</span></span>|  
    |<span data-ttu-id="b2e80-122">**État**</span><span class="sxs-lookup"><span data-stu-id="b2e80-122">**State**</span></span>|<span data-ttu-id="b2e80-123">Type **Test**.</span><span class="sxs-lookup"><span data-stu-id="b2e80-123">Type **Test**.</span></span>|  
    |<span data-ttu-id="b2e80-124">**Pays/région**</span><span class="sxs-lookup"><span data-stu-id="b2e80-124">**Country/Region**</span></span>|<span data-ttu-id="b2e80-125">Type **US**.</span><span class="sxs-lookup"><span data-stu-id="b2e80-125">Type **US**.</span></span>|  
    |<span data-ttu-id="b2e80-126">**Type de certificat nécessaire**</span><span class="sxs-lookup"><span data-stu-id="b2e80-126">**Type of Certificate Needed**</span></span>|<span data-ttu-id="b2e80-127">Sélectionnez **certificat de Protection de courrier électronique** à partir de la zone de liste déroulante.</span><span class="sxs-lookup"><span data-stu-id="b2e80-127">Select **E-Mail Protection Certificate** from the drop down list.</span></span>|  
    |<span data-ttu-id="b2e80-128">**Utilisation de la clé**</span><span class="sxs-lookup"><span data-stu-id="b2e80-128">**Key Usage**</span></span>|<span data-ttu-id="b2e80-129">Sélectionnez le **Exchange** option.</span><span class="sxs-lookup"><span data-stu-id="b2e80-129">Select the **Exchange** option.</span></span>|  
    |<span data-ttu-id="b2e80-130">**Options de clé supplémentaires**</span><span class="sxs-lookup"><span data-stu-id="b2e80-130">**Additional Key Options**</span></span>|<span data-ttu-id="b2e80-131">Activez les options suivantes :</span><span class="sxs-lookup"><span data-stu-id="b2e80-131">Place a check in the following options:</span></span><br /><br /> <span data-ttu-id="b2e80-132">-   **Marquer les clés comme étant exportables**</span><span class="sxs-lookup"><span data-stu-id="b2e80-132">-   **Mark keys as exportable**</span></span><br /><span data-ttu-id="b2e80-133">-   **Stocker le certificat dans le magasin de certificats ordinateur local**</span><span class="sxs-lookup"><span data-stu-id="b2e80-133">-   **Store certificate in the local computer certificate store**</span></span>|  
    |<span data-ttu-id="b2e80-134">**Nom convivial**</span><span class="sxs-lookup"><span data-stu-id="b2e80-134">**Friendly Name**</span></span>|<span data-ttu-id="b2e80-135">Type **Fabrikam chiffrement**.</span><span class="sxs-lookup"><span data-stu-id="b2e80-135">Type **Fabrikam Encryption**.</span></span>|  
  
6.  <span data-ttu-id="b2e80-136">Cliquez sur **Submit**, puis cliquez sur **Oui** dans **Confirmation d’accès au Web** boîte de dialogue.</span><span class="sxs-lookup"><span data-stu-id="b2e80-136">Click **Submit**, and then click **Yes** in **Web Access Confirmation** dialog box.</span></span>  
  
7.  <span data-ttu-id="b2e80-137">Sur le **délivré** , cliquez sur **installer ce certificat**.</span><span class="sxs-lookup"><span data-stu-id="b2e80-137">On the **Certificate Issued** page, click **Install this certificate**.</span></span>  
  
8.  <span data-ttu-id="b2e80-138">Répétez les étapes 1 à 7, en modifiant les informations contenues dans le **nom** zone le **Information d’identification** section et le **nom convivial** boîte à **Contoso Chiffrement**.</span><span class="sxs-lookup"><span data-stu-id="b2e80-138">Repeat steps 1-7, changing the information in the **Name** box in the **Identifying Information** section and the **Friendly Name** box to **Contoso Encryption**.</span></span>  
  
### <a name="to-generate-the-contoso-and-fabrikam-signing-certificates"></a><span data-ttu-id="b2e80-139">Pour générer de Contoso et Fabrikam des certificats de signature</span><span class="sxs-lookup"><span data-stu-id="b2e80-139">To generate the Contoso and Fabrikam Signing Certificates</span></span>  
  
1.  <span data-ttu-id="b2e80-140">Dans Internet Explorer, recherchez et ouvrez http://<contoso_computername>/certsrv.</span><span class="sxs-lookup"><span data-stu-id="b2e80-140">In Internet Explorer, locate and open http://<contoso_computername>/certsrv.</span></span>  
  
2.  <span data-ttu-id="b2e80-141">Sur le **Bienvenue** , cliquez sur **demander un certificat**.</span><span class="sxs-lookup"><span data-stu-id="b2e80-141">On the **Welcome** page, click **Request a certificate**.</span></span>  
  
3.  <span data-ttu-id="b2e80-142">Sur le **demander un certificat** , cliquez sur **demande de certificat avancée**.</span><span class="sxs-lookup"><span data-stu-id="b2e80-142">On the **Request a Certificate** page, click **advanced certificate request**.</span></span>  
  
4.  <span data-ttu-id="b2e80-143">Sur le **demande de certificat avancée** , cliquez sur **créer et soumettre une demande à cette autorité de certification**.</span><span class="sxs-lookup"><span data-stu-id="b2e80-143">On the **Advanced Certificate Request** page, click **Create and submit a request to this CA**.</span></span>  
  
5.  <span data-ttu-id="b2e80-144">Sur le **demande de certificat avancée** page, procédez comme suit :</span><span class="sxs-lookup"><span data-stu-id="b2e80-144">On the **Advanced Certificate Request** page, do the following:</span></span>  
  
    |<span data-ttu-id="b2e80-145">Utiliser</span><span class="sxs-lookup"><span data-stu-id="b2e80-145">Use this</span></span>|<span data-ttu-id="b2e80-146">Pour effectuer cette opération</span><span class="sxs-lookup"><span data-stu-id="b2e80-146">To do this</span></span>|  
    |--------------|----------------|  
    |<span data-ttu-id="b2e80-147">**Nom**</span><span class="sxs-lookup"><span data-stu-id="b2e80-147">**Name**</span></span>|<span data-ttu-id="b2e80-148">Type **Fabrikam Signature**.</span><span class="sxs-lookup"><span data-stu-id="b2e80-148">Type **Fabrikam Signature**.</span></span>|  
    |<span data-ttu-id="b2e80-149">**Courrier électronique**</span><span class="sxs-lookup"><span data-stu-id="b2e80-149">**E-Mail**</span></span>|<span data-ttu-id="b2e80-150">Type  **jdoe@fabrikam.com** .</span><span class="sxs-lookup"><span data-stu-id="b2e80-150">Type **jdoe@fabrikam.com**.</span></span>|  
    |<span data-ttu-id="b2e80-151">**Company**</span><span class="sxs-lookup"><span data-stu-id="b2e80-151">**Company**</span></span>|<span data-ttu-id="b2e80-152">Type **Fabrikam**.</span><span class="sxs-lookup"><span data-stu-id="b2e80-152">Type **Fabrikam**.</span></span>|  
    |<span data-ttu-id="b2e80-153">**Service**</span><span class="sxs-lookup"><span data-stu-id="b2e80-153">**Department**</span></span>|<span data-ttu-id="b2e80-154">Type **Test**.</span><span class="sxs-lookup"><span data-stu-id="b2e80-154">Type **Test**.</span></span>|  
    |<span data-ttu-id="b2e80-155">**Ville**</span><span class="sxs-lookup"><span data-stu-id="b2e80-155">**City**</span></span>|<span data-ttu-id="b2e80-156">Type **Test**.</span><span class="sxs-lookup"><span data-stu-id="b2e80-156">Type **Test**.</span></span>|  
    |<span data-ttu-id="b2e80-157">**État**</span><span class="sxs-lookup"><span data-stu-id="b2e80-157">**State**</span></span>|<span data-ttu-id="b2e80-158">Type **Test**.</span><span class="sxs-lookup"><span data-stu-id="b2e80-158">Type **Test**.</span></span>|  
    |<span data-ttu-id="b2e80-159">**Pays/région**</span><span class="sxs-lookup"><span data-stu-id="b2e80-159">**Country/Region**</span></span>|<span data-ttu-id="b2e80-160">Type **US**.</span><span class="sxs-lookup"><span data-stu-id="b2e80-160">Type **US**.</span></span>|  
    |<span data-ttu-id="b2e80-161">**Type de certificat nécessaire**</span><span class="sxs-lookup"><span data-stu-id="b2e80-161">**Type of Certificate Needed**</span></span>|<span data-ttu-id="b2e80-162">Sélectionnez **certificat de Protection de courrier électronique**contre la zone de liste déroulante.</span><span class="sxs-lookup"><span data-stu-id="b2e80-162">Select **E-Mail Protection Certificate**.from the drop down list.</span></span>|  
    |<span data-ttu-id="b2e80-163">**Utilisation de la clé**</span><span class="sxs-lookup"><span data-stu-id="b2e80-163">**Key Usage**</span></span>|<span data-ttu-id="b2e80-164">Sélectionnez le **Signature** option.</span><span class="sxs-lookup"><span data-stu-id="b2e80-164">Select the **Signature** option.</span></span>|  
    |<span data-ttu-id="b2e80-165">**Options de clé supplémentaires**</span><span class="sxs-lookup"><span data-stu-id="b2e80-165">**Additional Key Options**</span></span>|<span data-ttu-id="b2e80-166">Activez les options suivantes :</span><span class="sxs-lookup"><span data-stu-id="b2e80-166">Place a check in the following options:</span></span><br /><br /> <span data-ttu-id="b2e80-167">-   **Marquer les clés comme étant exportables**</span><span class="sxs-lookup"><span data-stu-id="b2e80-167">-   **Mark keys as exportable**</span></span><br /><span data-ttu-id="b2e80-168">-   **Stocker le certificat dans le magasin de certificats ordinateur local**</span><span class="sxs-lookup"><span data-stu-id="b2e80-168">-   **Store certificate in the local computer certificate store**</span></span>|  
    |<span data-ttu-id="b2e80-169">**Nom convivial**</span><span class="sxs-lookup"><span data-stu-id="b2e80-169">**Friendly Name**</span></span>|<span data-ttu-id="b2e80-170">Type **Fabrikam Signature**.</span><span class="sxs-lookup"><span data-stu-id="b2e80-170">Type **Fabrikam Signature**.</span></span>|  
  
6.  <span data-ttu-id="b2e80-171">Cliquez sur **Submit**, puis cliquez sur **Oui** lorsque vous êtes invité à la demande de certificat.</span><span class="sxs-lookup"><span data-stu-id="b2e80-171">Click **Submit**, and then click **Yes** when asked to request the certificate.</span></span>  
  
7.  <span data-ttu-id="b2e80-172">Sur le **délivré** , cliquez sur **installer ce certificat**.</span><span class="sxs-lookup"><span data-stu-id="b2e80-172">On the **Certificate Issued** page, click **Install this certificate**.</span></span>  
  
8.  <span data-ttu-id="b2e80-173">Répétez les étapes 1 à 7, en modifiant les informations contenues dans le **nom** zone le **Information d’identification** section et le **nom convivial** boîte à **Contoso Signature**.</span><span class="sxs-lookup"><span data-stu-id="b2e80-173">Repeat steps 1-7, changing the information in the **Name** box in the **Identifying Information** section and the **Friendly Name** box to **Contoso Signature**.</span></span>  
  
### <a name="to-generate-private-certificates-for-the-encryption-and-signature-certificates"></a><span data-ttu-id="b2e80-174">Pour générer les certificats privés pour les certificats de chiffrement et de Signature</span><span class="sxs-lookup"><span data-stu-id="b2e80-174">To generate private certificates for the Encryption and Signature certificates</span></span>  
  
1.  <span data-ttu-id="b2e80-175">Cliquez sur **Démarrer**, cliquez sur **exécuter**, type **MMC**, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="b2e80-175">Click **Start**, click **Run**, type **MMC**, and then click **OK**.</span></span>  
  
2.  <span data-ttu-id="b2e80-176">Dans la fenêtre Console1, sur le **fichier** menu, cliquez sur **ajouter/supprimer un composant logiciel enfichable**.</span><span class="sxs-lookup"><span data-stu-id="b2e80-176">In the Console1 window, on the **File** menu, click **Add/Remove Snap-in**.</span></span>  
  
3.  <span data-ttu-id="b2e80-177">Dans la boîte de dialogue Ajouter/supprimer un composant logiciel enfichable sur le **autonome** , cliquez sur **ajouter**.</span><span class="sxs-lookup"><span data-stu-id="b2e80-177">In the Add/Remove Snap-in dialog box, on the **Standalone** tab, click **Add**.</span></span>  
  
4.  <span data-ttu-id="b2e80-178">Dans la boîte de dialogue Ajouter Standalone Snap-in, sélectionnez le **certificats** -composant logiciel enfichable à partir de la **enfichables Standalone** liste, puis cliquez sur **ajouter**.</span><span class="sxs-lookup"><span data-stu-id="b2e80-178">In the Add Standalone Snap-in dialog box, select the **Certificates** snap-in from the **Available Standalone Snap-ins** list, and then click **Add**.</span></span>  
  
5.  <span data-ttu-id="b2e80-179">Dans la boîte de dialogue composant logiciel enfichable Certificats, sélectionnez **mon compte d’utilisateur**, puis cliquez sur **suivant**.</span><span class="sxs-lookup"><span data-stu-id="b2e80-179">In the Certificates snap-in dialog box, select **My user account**, and then click **Next**.</span></span>  
  
6.  <span data-ttu-id="b2e80-180">Dans la boîte de dialogue Sélectionner un ordinateur, cliquez sur **Terminer**.</span><span class="sxs-lookup"><span data-stu-id="b2e80-180">In the Select Computer dialog box, click **Finish**.</span></span>  
  
7.  <span data-ttu-id="b2e80-181">Dans la boîte de dialogue Ajouter Standalone Snap-in, cliquez sur **fermer**.</span><span class="sxs-lookup"><span data-stu-id="b2e80-181">In the Add Standalone Snap-in dialog box, click **Close**.</span></span>  
  
8.  <span data-ttu-id="b2e80-182">Dans la boîte de dialogue Ajouter/supprimer un composant logiciel enfichable, cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="b2e80-182">In the Add/Remove Snap-in dialog box, click **OK**.</span></span>  
  
9. <span data-ttu-id="b2e80-183">Dans la fenêtre Console1, développez **certificats (ordinateur Local)**, développez **personnel**, puis cliquez sur **certificats**.</span><span class="sxs-lookup"><span data-stu-id="b2e80-183">In the Console1 window, expand **Certificates (Local Computer)**, expand **Personal**, and then click **Certificates**.</span></span>  
  
10. <span data-ttu-id="b2e80-184">Dans le volet droit, cliquez sur le **Fabrikam chiffrement** de certificat, pointez sur **toutes les tâches**, puis cliquez sur **exporter**.</span><span class="sxs-lookup"><span data-stu-id="b2e80-184">In the right pane, right-click the **Fabrikam Encryption** certificate, point to **All Tasks**, and then click **Export**.</span></span>  
  
11. <span data-ttu-id="b2e80-185">Dans la page **Bienvenue dans l'Assistant Exportation du certificat** , cliquez sur **Suivant**.</span><span class="sxs-lookup"><span data-stu-id="b2e80-185">On the **Welcome to the Certificate Export Wizard** page, click **Next**.</span></span>  
  
12. <span data-ttu-id="b2e80-186">Sur le **exporter la clé privée** page, sélectionnez **Oui, exporter la clé privée**, puis cliquez sur **suivant**.</span><span class="sxs-lookup"><span data-stu-id="b2e80-186">On the **Export Private Key** page, select **Yes, export the private key**, and then click **Next**.</span></span>  
  
13. <span data-ttu-id="b2e80-187">Sur le **Format de fichier d’exportation** , assurez-vous que **Personal Information Exchange** est la seule option sélectionnée, puis cliquez sur **suivant**.</span><span class="sxs-lookup"><span data-stu-id="b2e80-187">On the **Export File Format** page, make sure that **Personal Information Exchange** is the only option selected, and then click **Next**.</span></span>  
  
14. <span data-ttu-id="b2e80-188">Sur le **mot de passe** page, dans le **mot de passe** et **confirmer le mot de passe** zones, tapez **mysecret**, puis cliquez sur **suivant** .</span><span class="sxs-lookup"><span data-stu-id="b2e80-188">On the **Password** page, in the **Password** and **Confirm Password** boxes, type **mysecret**, and then click **Next**.</span></span>  
  
15. <span data-ttu-id="b2e80-189">Sur le **fichier à exporter** , cliquez sur **Parcourir**.</span><span class="sxs-lookup"><span data-stu-id="b2e80-189">On the **File To Export** page, click **Browse**.</span></span>  
  
16. <span data-ttu-id="b2e80-190">Dans le **enregistrer en tant que** boîte de dialogue Enregistrer le certificat en utilisant le chemin d’accès du fichier  *\<lecteur\>*: \Certs\Fabrikam privé Encryption.pfx.</span><span class="sxs-lookup"><span data-stu-id="b2e80-190">In the **Save As** dialog box, save the certificate using the file path *\<drive\>*:\Certs\Fabrikam Private Encryption.pfx.</span></span>  
  
17. <span data-ttu-id="b2e80-191">Sur le **fichier à exporter** , cliquez sur **suivant**.</span><span class="sxs-lookup"><span data-stu-id="b2e80-191">On the **File to Export** page, click **Next**.</span></span>  
  
18. <span data-ttu-id="b2e80-192">Sur le **fin de l’Assistant Exportation de certificat** , cliquez sur **Terminer**.</span><span class="sxs-lookup"><span data-stu-id="b2e80-192">On the **Completing the Certificate Export Wizard** page, click **Finish**.</span></span>  
  
19. <span data-ttu-id="b2e80-193">Dans le menu contextuel Assistant Exportation de certificat indiquant la réussite de l’exportation, cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="b2e80-193">In the Certificate Export Wizard popup indicating a successful export, click **OK**.</span></span>  
  
20. <span data-ttu-id="b2e80-194">Répétez les étapes 10 à 19 pour le certificat de Signature de Fabrikam en utilisant le nom de fichier Signature.pfx de Fabrikam privé.</span><span class="sxs-lookup"><span data-stu-id="b2e80-194">Repeat steps 10-19 for the Fabrikam Signature certificate using the file name Fabrikam Private Signature.pfx.</span></span>  
  
21. <span data-ttu-id="b2e80-195">Répétez les étapes 10 à 19 pour les certificats de Signature de Contoso et le chiffrement Contoso en utilisant les noms de fichiers Contoso privé Signature.pfx et Contoso privé Encryption.pfx, respectivement.</span><span class="sxs-lookup"><span data-stu-id="b2e80-195">Repeat steps 10-19 for the Contoso Signature and Contoso Encryption certificates using the file names Contoso Private Signature.pfx and Contoso Private Encryption.pfx, respectively.</span></span>  
  
### <a name="to-generate-public-certificates-for-the-encryption-and-signature-certificates"></a><span data-ttu-id="b2e80-196">Pour générer les certificats publics pour les certificats de chiffrement et de Signature</span><span class="sxs-lookup"><span data-stu-id="b2e80-196">To generate public certificates for the Encryption and Signature certificates</span></span>  
  
1.  <span data-ttu-id="b2e80-197">Dans la fenêtre Console1, développez **certificats-utilisateur actuel**, développez **personnel**, puis cliquez sur **certificats**.</span><span class="sxs-lookup"><span data-stu-id="b2e80-197">In the Console1 window, expand **Certificates – Current User**, expand **Personal**, and then click **Certificates**.</span></span>  
  
2.  <span data-ttu-id="b2e80-198">Avec le bouton droit le **Fabrikam chiffrement** de certificat, pointez sur **toutes les tâches**, puis cliquez sur **exporter**.</span><span class="sxs-lookup"><span data-stu-id="b2e80-198">Right-click the **Fabrikam Encryption** certificate, point to **All Tasks**, and then click **Export**.</span></span>  
  
3.  <span data-ttu-id="b2e80-199">Dans la page **Bienvenue dans l'Assistant Exportation du certificat** , cliquez sur **Suivant**.</span><span class="sxs-lookup"><span data-stu-id="b2e80-199">On the **Welcome to the Certificate Export Wizard** page, click **Next**.</span></span>  
  
4.  <span data-ttu-id="b2e80-200">Sur le **exporter la clé privée** page, sélectionnez **non, ne pas exporter de la clé privée**, puis cliquez sur **suivant**.</span><span class="sxs-lookup"><span data-stu-id="b2e80-200">On the **Export Private Key** page, select **No, do not export the private key**, and then click **Next**.</span></span>  
  
5.  <span data-ttu-id="b2e80-201">Sur le **Format de fichier d’exportation** , cliquez sur **suivant**.</span><span class="sxs-lookup"><span data-stu-id="b2e80-201">On the **Export File Format** page, click **Next**.</span></span>  
  
6.  <span data-ttu-id="b2e80-202">Sur le **fichier à exporter** , cliquez sur **Parcourir**.</span><span class="sxs-lookup"><span data-stu-id="b2e80-202">On the **File To Export** page, click **Browse**.</span></span>  
  
7.  <span data-ttu-id="b2e80-203">Dans la boîte de dialogue Enregistrer sous, entrez  **\<lecteur\>: \Certs** pour **enregistrer dans**, **Encryption.cer Public de Fabrikam** comme **nom de fichier** , et  **\*.cer** pour **enregistrer en tant que type**, puis cliquez sur **enregistrer**.</span><span class="sxs-lookup"><span data-stu-id="b2e80-203">In the Save As dialog box, enter **\<drive\>:\Certs** for **Save in**, **Fabrikam Public Encryption.cer** as **File name**, and **\*.cer** for **Save as type**, and then click **Save**.</span></span>  
  
8.  <span data-ttu-id="b2e80-204">Sur le **fichier à exporter** , cliquez sur **suivant**.</span><span class="sxs-lookup"><span data-stu-id="b2e80-204">On the **File to Export** page, click **Next**.</span></span>  
  
9. <span data-ttu-id="b2e80-205">Sur le **fin de l’Assistant Exportation de certificat** , cliquez sur **Terminer**.</span><span class="sxs-lookup"><span data-stu-id="b2e80-205">On the **Completing the Certificate Export Wizard** page, click **Finish**.</span></span>  
  
10. <span data-ttu-id="b2e80-206">Dans le menu contextuel Assistant Exportation de certificat indiquant la réussite de l’exportation, cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="b2e80-206">In the Certificate Export Wizard popup indicating a successful export, click **OK**.</span></span>  
  
11. <span data-ttu-id="b2e80-207">Répétez les étapes 1 à 9 pour le certificat de Signature de Fabrikam en utilisant le nom de fichier Signature.cer Public de Fabrikam.</span><span class="sxs-lookup"><span data-stu-id="b2e80-207">Repeat steps 1-9 for the Fabrikam Signature certificate using the file name Fabrikam Public Signature.cer.</span></span>  
  
12. <span data-ttu-id="b2e80-208">Répétez les étapes 1 à 9 pour les certificats de Signature de Contoso et le chiffrement Contoso en utilisant les noms de fichiers Signature.cer publics de Contoso et Encryption.cer publics de Contoso, respectivement.</span><span class="sxs-lookup"><span data-stu-id="b2e80-208">Repeat steps 1-9 for the Contoso Signature and Contoso Encryption certificates using the file names Contoso Public Signature.cer and Contoso Public Encryption.cer, respectively.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b2e80-209">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b2e80-209">See Also</span></span>  
 [<span data-ttu-id="b2e80-210">Étape 3 : Importation de certificats publics et privés</span><span class="sxs-lookup"><span data-stu-id="b2e80-210">Step 3: Importing Public and Private Certificates</span></span>](../../adapters-and-accelerators/accelerator-rosettanet/step-3-importing-public-and-private-certificates.md)