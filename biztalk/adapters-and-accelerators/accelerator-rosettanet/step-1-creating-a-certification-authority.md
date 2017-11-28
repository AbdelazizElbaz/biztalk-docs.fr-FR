---
title: "Étape 1 : Création d’une autorité de Certification | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- certificates, creating
- double action tutorial, creating certificates
- creating, certificates
ms.assetid: b6ecd534-6b03-4336-8337-33ec18a0802a
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: d94a2b02b654983701323703edcc1b3ba3fcca13
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="step-1-creating-a-certification-authority"></a><span data-ttu-id="38fbe-102">Étape 1 : Création d’une autorité de Certification</span><span class="sxs-lookup"><span data-stu-id="38fbe-102">Step 1: Creating a Certification Authority</span></span>
<span data-ttu-id="38fbe-103">Dans cette rubrique, vous installez les Services de certificats [!INCLUDE[btsWinNoVersion](../../includes/btswinnoversion-md.md)] composant.</span><span class="sxs-lookup"><span data-stu-id="38fbe-103">In this topic, you install the Certificate Services [!INCLUDE[btsWinNoVersion](../../includes/btswinnoversion-md.md)] component.</span></span> <span data-ttu-id="38fbe-104">Il permet de générer les certificats que vous devez promouvoir une communication sécurisée entre les organisations de Contoso et Fabrikam.</span><span class="sxs-lookup"><span data-stu-id="38fbe-104">You use it to generate the certificates that you need to promote secure communication between the Contoso and Fabrikam organizations.</span></span> <span data-ttu-id="38fbe-105">Chaque partenaire commercial aura un certificat de chiffrement privé pour la communication et un certificat de signature privée à des fins d’identification.</span><span class="sxs-lookup"><span data-stu-id="38fbe-105">Each trading partner will have a private encryption certificate for communication and a private signature certificate for identification purposes.</span></span> <span data-ttu-id="38fbe-106">En outre, les partenaires partagent leurs certificats de clé publique entre eux pour promouvoir une communication sécurisée lors de l’implémentation de la 3A2 processus PIP (Partner Interface).</span><span class="sxs-lookup"><span data-stu-id="38fbe-106">Additionally, the partners will share their public key certificates with each other to promote secure communication when implementing the 3A2 Partner Interface Process (PIP).</span></span>  
  
### <a name="to-install-the-certificate-server"></a><span data-ttu-id="38fbe-107">Pour installer le certificat de serveur</span><span class="sxs-lookup"><span data-stu-id="38fbe-107">To install the certificate server</span></span>  
  
1.  <span data-ttu-id="38fbe-108">Cliquez sur **Démarrer**, pointez sur **paramètres**, puis cliquez sur **le panneau de configuration**.</span><span class="sxs-lookup"><span data-stu-id="38fbe-108">Click **Start**, point to **Settings**, and then click **Control Panel**.</span></span> <span data-ttu-id="38fbe-109">Double-cliquez sur **ajouter ou supprimer des programmes**.</span><span class="sxs-lookup"><span data-stu-id="38fbe-109">Double-click **Add or Remove Programs**.</span></span>  
  
2.  <span data-ttu-id="38fbe-110">Dans le **Ajout / Suppression de programmes** boîte de dialogue, cliquez sur **ajouter/supprimer des composants Windows**.</span><span class="sxs-lookup"><span data-stu-id="38fbe-110">In the **Add or Remove Programs** dialog box, click **Add/Remove Windows Components**.</span></span>  
  
3.  <span data-ttu-id="38fbe-111">Sur le **Assistant Composants de Windows** page, dans le **composants** section, sélectionnez **les Services de certificats**, cliquez sur **Oui**, puis cliquez sur **Suivant** pour démarrer l’Assistant Configuration de composants.</span><span class="sxs-lookup"><span data-stu-id="38fbe-111">On the **Windows Components Wizard** page, in the **Components** section, select **Certificate Services**, click **Yes**, and then click **Next** to start the Configuring Components Wizard.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="38fbe-112">Si le **ServicesWindows de certificats** composant est déjà activée, ignorez le reste de cette procédure.</span><span class="sxs-lookup"><span data-stu-id="38fbe-112">If the **Certificates ServicesWindows** component is already selected, skip the rest of this procedure.</span></span>  
  
4.  <span data-ttu-id="38fbe-113">Sur le **Type d’autorité de certification** , assurez-vous que **autorité racine autonome** est sélectionné, puis cliquez sur **suivant**.</span><span class="sxs-lookup"><span data-stu-id="38fbe-113">On the **CA Type** page, make sure that **Stand-alone root CA** is selected, and then click **Next**.</span></span>  
  
5.  <span data-ttu-id="38fbe-114">Sur le **les informations d’identification autorité de certification** page, dans le **nom commun de cette autorité de certification** , tapez **Contoso-FabrikamCA**, puis cliquez sur **suivant**.</span><span class="sxs-lookup"><span data-stu-id="38fbe-114">On the **CA Identifying Information** page, in the **Common name for this CA** box, type **Contoso-FabrikamCA**, and then click **Next**.</span></span>  
  
6.  <span data-ttu-id="38fbe-115">Sur le **paramètres de base de données de certificat** page, laissez les valeurs par défaut, puis cliquez sur **suivant**.</span><span class="sxs-lookup"><span data-stu-id="38fbe-115">On the **Certificate Database Settings** page, leave the defaults, and then click **Next**.</span></span>  
  
7.  <span data-ttu-id="38fbe-116">Cliquez sur **Oui** lorsque l’Assistant vous invite à arrêter les Internet Information Services (IIS).</span><span class="sxs-lookup"><span data-stu-id="38fbe-116">Click **Yes** when the wizard prompts you to stop Internet Information Services (IIS).</span></span>  
  
8.  <span data-ttu-id="38fbe-117">Cliquez sur **Oui** si le **Assistant Composants de configuration** vous invite à activer Active Server Pages.</span><span class="sxs-lookup"><span data-stu-id="38fbe-117">Click **Yes** if the **Configuring Components Wizard** prompts you to enable Active Server Pages.</span></span>  
  
9. <span data-ttu-id="38fbe-118">Cliquez sur **Terminer** pour fermer la **Assistant Composants de Windows**.</span><span class="sxs-lookup"><span data-stu-id="38fbe-118">Click **Finish** to close the **Windows Components Wizard**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="38fbe-119">Vous devez uniquement utiliser un seul ordinateur en tant que l’autorité de Certification.</span><span class="sxs-lookup"><span data-stu-id="38fbe-119">You only have to use one computer as the Certification Authority.</span></span> <span data-ttu-id="38fbe-120">Il est inutile de répéter cette procédure sur le deuxième ordinateur.</span><span class="sxs-lookup"><span data-stu-id="38fbe-120">You do not have to repeat this step on the second computer.</span></span> <span data-ttu-id="38fbe-121">Ce didacticiel utilise l’ordinateur Contoso en tant que l’autorité de Certification.</span><span class="sxs-lookup"><span data-stu-id="38fbe-121">This tutorial uses the Contoso computer as the Certification Authority.</span></span>  
  
### <a name="to-install-a-root-certification-authority-ca-for-windows-server-2008"></a><span data-ttu-id="38fbe-122">Pour installer une autorité de Certification (CA) racine pour Windows Server 2008</span><span class="sxs-lookup"><span data-stu-id="38fbe-122">To install a root Certification Authority (CA) for Windows Server 2008</span></span>  
  
1.  <span data-ttu-id="38fbe-123">Ouvrez le Gestionnaire de serveur, cliquez sur **ajouter des rôles** dans des rôles, cliquez sur **suivant**, puis cliquez sur **certificat Active Directory** Services case à cocher.</span><span class="sxs-lookup"><span data-stu-id="38fbe-123">Open Server Manager, click **Add Roles** in Roles, click **Next**, and click **Active Directory Certificate** Services check box.</span></span> <span data-ttu-id="38fbe-124">Cliquez sur **suivant** à deux reprises.</span><span class="sxs-lookup"><span data-stu-id="38fbe-124">Click **Next** twice.</span></span>  
  
2.  <span data-ttu-id="38fbe-125">Dans la page Sélectionner les Services de rôle, cliquez sur **autorité de Certification et inscription de l’autorité de Certification via le Web**.</span><span class="sxs-lookup"><span data-stu-id="38fbe-125">On the Select Role Services page, click **Certification Authority and Certification Authority Web Enrollment**.</span></span> <span data-ttu-id="38fbe-126">Cliquez sur **Suivant**.</span><span class="sxs-lookup"><span data-stu-id="38fbe-126">Click **Next**.</span></span>  
  
3.  <span data-ttu-id="38fbe-127">Dans la page spécifier le Type d’installation, cliquez sur **autonome**.</span><span class="sxs-lookup"><span data-stu-id="38fbe-127">On the Specify Setup Type page, click **Standalone**.</span></span> <span data-ttu-id="38fbe-128">Cliquez sur **Suivant**.</span><span class="sxs-lookup"><span data-stu-id="38fbe-128">Click **Next**.</span></span>  
  
4.  <span data-ttu-id="38fbe-129">Dans la page spécifier le Type autorité de certification, cliquez sur l’autorité de certification racine.</span><span class="sxs-lookup"><span data-stu-id="38fbe-129">On the Specify CA Type page, click Root CA.</span></span> <span data-ttu-id="38fbe-130">Cliquez sur **Suivant**.</span><span class="sxs-lookup"><span data-stu-id="38fbe-130">Click **Next**.</span></span>  
  
5.  <span data-ttu-id="38fbe-131">Dans la page Configurer la clé privée, cliquez sur Créer une nouvelle clé privée.</span><span class="sxs-lookup"><span data-stu-id="38fbe-131">On the Set Up Private Key page, click Create a new private key.</span></span> <span data-ttu-id="38fbe-132">Cliquez sur **Suivant**.</span><span class="sxs-lookup"><span data-stu-id="38fbe-132">Click **Next**.</span></span>  
  
6.  <span data-ttu-id="38fbe-133">Sur la cryptographie configurer pour la page de l’autorité de certification.</span><span class="sxs-lookup"><span data-stu-id="38fbe-133">On the Configure Cryptography for CA page.</span></span> <span data-ttu-id="38fbe-134">Cliquez sur **Suivant**.</span><span class="sxs-lookup"><span data-stu-id="38fbe-134">Click **Next**.</span></span>  
  
7.  <span data-ttu-id="38fbe-135">Configurer des nom d’autorité de certification, dans la zone Nom commun de cette autorité de certification, tapez Contoso-FabrikamCA, puis cliquez sur **suivant**.</span><span class="sxs-lookup"><span data-stu-id="38fbe-135">On Configure CA Name, in the Common name for this CA box, type Contoso-FabrikamCA, and then click **Next**.</span></span>  
  
8.  <span data-ttu-id="38fbe-136">Dans la page Définir la période de validité, cliquez sur **suivant**.</span><span class="sxs-lookup"><span data-stu-id="38fbe-136">On the Set Validity Period page, click **Next**.</span></span>  
  
9. <span data-ttu-id="38fbe-137">Dans la page Configuration de base de données de certificat, cliquez sur **suivant**.</span><span class="sxs-lookup"><span data-stu-id="38fbe-137">On the Configure Certificate Database page, Click **Next**.</span></span>  
  
10. <span data-ttu-id="38fbe-138">Dans la page Confirmer les Options d’Installation, cliquez sur **installer**.</span><span class="sxs-lookup"><span data-stu-id="38fbe-138">On the Confirm Installation Options page, click **Install**.</span></span>  
  
### <a name="configuring-the-web-site-for-the-ca-to-use-https-authentication"></a><span data-ttu-id="38fbe-139">Configuration du site Web de l’autorité de certification à utiliser l’authentification HTTPS</span><span class="sxs-lookup"><span data-stu-id="38fbe-139">Configuring the Web site for the CA to use HTTPS authentication</span></span>  
  
1.  <span data-ttu-id="38fbe-140">Sur l’ordinateur que vous avez utilisé comme l’autorité de Certification, cliquez sur Démarrer, pointez sur tous les programmes, pointez sur Outils d’administration, puis cliquez sur Gestionnaire des Services Internet (IIS).</span><span class="sxs-lookup"><span data-stu-id="38fbe-140">On the computer you used as the Certification Authority, click Start, point to All Programs, point to Administrative Tools, and then click Internet Information Services (IIS) Manager.</span></span>  
  
2.  <span data-ttu-id="38fbe-141">Dans la boîte de dialogue Gestionnaire des Services Internet (IIS), cliquez droit **Site Web par défaut et sélectionnez Modifier les liaisons...**</span><span class="sxs-lookup"><span data-stu-id="38fbe-141">In the Internet Information Services (IIS) Manager dialog box, right click **Default Web Site and select Edit Bindings…**</span></span> <span data-ttu-id="38fbe-142">dans le menu contextuel.</span><span class="sxs-lookup"><span data-stu-id="38fbe-142">from the popup menu.</span></span>  
  
3.  <span data-ttu-id="38fbe-143">Dans la boîte de dialogue liaisons de Site, cliquez sur **ajouter**.</span><span class="sxs-lookup"><span data-stu-id="38fbe-143">In Site Bindings dialog box click **Add**.</span></span>  
  
4.  <span data-ttu-id="38fbe-144">Dans la boîte de dialogue Ajouter une liaison de Site, sélectionnez **https** dans la liste déroulante Type, sélectionnez le certificat à partir de **certificat SSL** liste déroulante et cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="38fbe-144">In Add Site Binding dialog box select **https** in Type drop down, select the certificate from **SSL certificate** drop down and click **OK**.</span></span>  
  
5.  <span data-ttu-id="38fbe-145">Cliquez sur **fermer** pour fermer les liaisons du Site...</span><span class="sxs-lookup"><span data-stu-id="38fbe-145">Click **Close** to close the Site Bindings…</span></span> <span data-ttu-id="38fbe-146">boîte de dialogue.</span><span class="sxs-lookup"><span data-stu-id="38fbe-146">dialog box.</span></span>  
  
### <a name="to-download-the-ca-certificate"></a><span data-ttu-id="38fbe-147">Pour télécharger le certificat d’autorité de certification</span><span class="sxs-lookup"><span data-stu-id="38fbe-147">To download the CA certificate</span></span>  
  
1.  <span data-ttu-id="38fbe-148">Dans Internet Explorer, recherchez et ouvrez http://<contoso_computername>/certsrv/Default.asp.</span><span class="sxs-lookup"><span data-stu-id="38fbe-148">In Internet Explorer, locate and open http://<contoso_computername>/certsrv/Default.asp.</span></span>  
  
2.  <span data-ttu-id="38fbe-149">Dans la page Default.asp, cliquez sur **télécharger un certificat autorité de certification, chaîne de certificats ou la liste de révocation**.</span><span class="sxs-lookup"><span data-stu-id="38fbe-149">On the Default.asp page, click **Download a CA certificate, certificate chain, or CRL**.</span></span>  
  
3.  <span data-ttu-id="38fbe-150">Assurez-vous que **actuel [Contoso-FabrikamCA]** est sélectionné dans le **certificat d’autorité de certification** liste, puis cliquez sur **télécharger le certificat de CA**.</span><span class="sxs-lookup"><span data-stu-id="38fbe-150">Make sure that **Current[Contoso-FabrikamCA]** is selected in the **CA Certificate** list, and then click **Download CA Certificate**.</span></span>  
  
4.  <span data-ttu-id="38fbe-151">Enregistrez le certificat sur C:\Certs\Contoso-FabrikamCA.cer sur l’ordinateur Fabrikam et Contoso.</span><span class="sxs-lookup"><span data-stu-id="38fbe-151">Save the certificate to C:\Certs\Contoso-FabrikamCA.cer on both the Contoso and the Fabrikam computer.</span></span>  
  
### <a name="to-import-the-ca-certificate-to-the-trusted-root-certification-authorities-store"></a><span data-ttu-id="38fbe-152">Pour importer le certificat d’autorité de certification dans le magasin d’autorités de Certification racines de confiance</span><span class="sxs-lookup"><span data-stu-id="38fbe-152">To import the CA certificate to the Trusted Root Certification Authorities store</span></span>  
  
1.  <span data-ttu-id="38fbe-153">Cliquez sur **Démarrer**, puis sur **Exécuter**, tapez **cmd**, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="38fbe-153">Click **Start**, click **Run**, type **cmd**, and then click **OK**.</span></span>  
  
2.  <span data-ttu-id="38fbe-154">À l’invite de commandes, accédez au  **\<lecteur > : \Program Files\MicrosoftBizTalk \<version > Accelerator for RosettaNet\SDK**, puis appuyez sur **entrée**.</span><span class="sxs-lookup"><span data-stu-id="38fbe-154">At the command prompt, move to **\<drive>:\Program Files\MicrosoftBizTalk \<version> Accelerator for RosettaNet\SDK**, and then press **Enter**.</span></span>  
  
3.  <span data-ttu-id="38fbe-155">À l’invite de commandes, tapez **CertWizard /Rootkey »\<lecteur > : \Certs\Contoso-FabrikamCA.cer «**, puis appuyez sur **entrée**.</span><span class="sxs-lookup"><span data-stu-id="38fbe-155">At the command prompt, type **CertWizard /Rootkey "\<drive>:\Certs\Contoso-FabrikamCA.cer"**, and then press **Enter**.</span></span>  
  
    > [!IMPORTANT]
    >  <span data-ttu-id="38fbe-156">Effectuez cette procédure sur les ordinateurs de Contoso et Fabrikam.</span><span class="sxs-lookup"><span data-stu-id="38fbe-156">Perform this procedure on both the Contoso and Fabrikam computers.</span></span>  
  
### <a name="to-enable-automatic-certificate-issuing"></a><span data-ttu-id="38fbe-157">Pour activer l’émission de certificat automatique</span><span class="sxs-lookup"><span data-stu-id="38fbe-157">To enable automatic certificate issuing</span></span>  
  
1.  <span data-ttu-id="38fbe-158">Sur l’ordinateur que vous avez utilisé comme l’autorité de Certification, cliquez sur **Démarrer**, pointez sur **programmes**, pointez sur **outils d’administration**, puis cliquez sur  **Autorité de certification**.</span><span class="sxs-lookup"><span data-stu-id="38fbe-158">On the computer you used as the Certification Authority, click **Start**, point to **Programs**, point to **Administrative Tools**, and then click **Certification Authority**.</span></span>  
  
2.  <span data-ttu-id="38fbe-159">Dans la boîte de dialogue Autorité de Certification, cliquez sur **Contoso-FabrikamCA**, puis cliquez sur **propriétés**.</span><span class="sxs-lookup"><span data-stu-id="38fbe-159">In the Certification Authority dialog box, right-click **Contoso-FabrikamCA**, and then click **Properties**.</span></span>  
  
3.  <span data-ttu-id="38fbe-160">Dans la boîte de dialogue Propriétés de Contoso-FabrikamCA sur la **Module de stratégie** , cliquez sur **propriétés**.</span><span class="sxs-lookup"><span data-stu-id="38fbe-160">In the Contoso-FabrikamCA Properties dialog box, on the **Policy Module** tab, click **Properties**.</span></span>  
  
4.  <span data-ttu-id="38fbe-161">Dans la boîte de dialogue Propriétés, sélectionnez **suivre les paramètres dans le modèle de certificat**, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="38fbe-161">In the Properties dialog box, select **Follow the settings in the certificate template**, and then click **OK**.</span></span>  
  
5.  <span data-ttu-id="38fbe-162">Cliquez sur **OK** pour fermer la boîte de dialogue FabrikamCA de Contoso.</span><span class="sxs-lookup"><span data-stu-id="38fbe-162">Click **OK** to close the Contoso-FabrikamCA dialog box.</span></span>  
  
6.  <span data-ttu-id="38fbe-163">Fermez la boîte de dialogue Autorité de Certification.</span><span class="sxs-lookup"><span data-stu-id="38fbe-163">Close the Certification Authority dialog box.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="38fbe-164">En activant l’émission automatique de certificats, les Services de certificats automatise la procédure d’émission des certificats.</span><span class="sxs-lookup"><span data-stu-id="38fbe-164">By enabling automatic certificate issuing, Certificate Services automates the certificate issuing procedure.</span></span> <span data-ttu-id="38fbe-165">Vous devez redémarrer les Services de certificats pour appliquer cette modification.</span><span class="sxs-lookup"><span data-stu-id="38fbe-165">You will have to restart Certificate Services to apply this change.</span></span>  
    >   
    >  <span data-ttu-id="38fbe-166">Vous devrez peut-être installer le certificat racine Contoso-FabrikamCA.cer dans les autorités de Certification de racine User\Trusted actuel.</span><span class="sxs-lookup"><span data-stu-id="38fbe-166">You may need to install the Root Certificate Contoso-FabrikamCA.cer in the Current User\Trusted Root Certification authorities.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="38fbe-167">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="38fbe-167">See Also</span></span>  
 [<span data-ttu-id="38fbe-168">Étape 2 : Création publiques et privées des certificats</span><span class="sxs-lookup"><span data-stu-id="38fbe-168">Step 2: Creating Public and Private Certificates</span></span>](../../adapters-and-accelerators/accelerator-rosettanet/step-2-creating-public-and-private-certificates.md)