---
title: "Étape 4 : Sécurisé Sockets Layer dans IIS | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Secure Socket Layers
- IIS
- double action tutorial, enabling SSL in IIS
- SSL
ms.assetid: 96109294-595a-46ac-974e-33123df79ed5
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 2964b6ac26d6685a1c38b88c5bbf98e8119f3502
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="step-4-enabling-secure-sockets-layer-in-iis"></a><span data-ttu-id="0876c-102">Étape 4 : Sécurisé Sockets Layer dans IIS</span><span class="sxs-lookup"><span data-stu-id="0876c-102">Step 4: Enabling Secure Sockets Layer in IIS</span></span>
<span data-ttu-id="0876c-103">Couche de Sockets sécurisée (SSL) est un protocole conçu pour sécuriser le canal de communication entre un client et un serveur.</span><span class="sxs-lookup"><span data-stu-id="0876c-103">Secure Sockets Layer (SSL) is a protocol designed to secure the communication channel between a client and a server.</span></span> <span data-ttu-id="0876c-104">L’activation de SSL dans Microsoft® Internet Information Services (IIS) 7.5/7.0, les organisations de Contoso et Fabrikam de communiquer à l’aide de l’authentification et le chiffrement pour tous les transferts de données.</span><span class="sxs-lookup"><span data-stu-id="0876c-104">By enabling SSL in Microsoft® Internet Information Services (IIS) 7.5/7.0, the Contoso and Fabrikam organizations communicate using authentication and encryption for all data transfers.</span></span> <span data-ttu-id="0876c-105">Dans cette étape, vous allez apprendre à activer le protocole SSL dans IIS 7.5/7.0.</span><span class="sxs-lookup"><span data-stu-id="0876c-105">In this step, you learn how to enable SSL in IIS 7.5/7.0.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="0876c-106">Vous devez effectuer cette étape sur les ordinateurs de Contoso et Fabrikam.</span><span class="sxs-lookup"><span data-stu-id="0876c-106">You have to perform this step on both the Contoso and Fabrikam computers.</span></span>  
  
### <a name="to-prepare-a-new-server-certificate"></a><span data-ttu-id="0876c-107">Pour préparer un nouveau certificat de serveur</span><span class="sxs-lookup"><span data-stu-id="0876c-107">To prepare a new server certificate</span></span>  
  
1.  <span data-ttu-id="0876c-108">Cliquez sur **Démarrer**, pointez sur **outils d’administration**, puis cliquez sur **Gestionnaire des Services Internet (IIS)**.</span><span class="sxs-lookup"><span data-stu-id="0876c-108">Click **Start**, point to **Administrative Tools**, and then click **Internet Information Services (IIS) Manager**.</span></span>  
  
2.  <span data-ttu-id="0876c-109">Dans le volet gauche de Internet Information Services, développez  **\<**  *Nom_Ordinateur*  **\>**  (*ordinateur local*), développez **Sites Web**, avec le bouton droit **Site Web par défaut**, puis cliquez sur **propriétés**.</span><span class="sxs-lookup"><span data-stu-id="0876c-109">In the Internet Information Services left pane, expand **\<***computer_name***\>** (*local computer*), expand **Web Sites**, right-click **Default Web Site**, and then click **Properties**.</span></span>  
  
3.  <span data-ttu-id="0876c-110">Dans la boîte de dialogue de Sites Web par défaut sur le **sécurité du répertoire** , cliquez sur **certificat de serveur** pour démarrer le **Assistant certificat IIS**.</span><span class="sxs-lookup"><span data-stu-id="0876c-110">In the Default Web Sites dialog box, on the **Directory Security** tab, click **Server Certificate** to start the **IIS Certificate Wizard**.</span></span>  
  
4.  <span data-ttu-id="0876c-111">Sur le **Bienvenue dans l’Assistant certificat de serveur Web** , cliquez sur **suivant**.</span><span class="sxs-lookup"><span data-stu-id="0876c-111">On the **Welcome to the Web Server Certificate Wizard** page, click **Next**.</span></span>  
  
5.  <span data-ttu-id="0876c-112">Sur le **certificat de serveur** page, sélectionnez **créer un nouveau certificat**, puis cliquez sur **suivant**.</span><span class="sxs-lookup"><span data-stu-id="0876c-112">On the **Server Certificate** page, select **Create a new certificate**, and then click **Next**.</span></span>  
  
6.  <span data-ttu-id="0876c-113">Sur le **demande ultérieure ou immédiate** , cliquez sur **suivant**.</span><span class="sxs-lookup"><span data-stu-id="0876c-113">On the **Delayed or immediate request** page, click **Next**.</span></span>  
  
7.  <span data-ttu-id="0876c-114">Sur le **nom et les paramètres de sécurité** , cliquez sur **suivant**, en conservant les valeurs par défaut.</span><span class="sxs-lookup"><span data-stu-id="0876c-114">On the **Name and Security Settings** page, click **Next**, keeping the defaults.</span></span>  
  
8.  <span data-ttu-id="0876c-115">Sur le **informations de l’organisation** page, dans le **organisation** , tapez **Contoso** if sur l’ordinateur Contoso ou **Fabrikam** if sur la Ordinateur Fabrikam, dans le **unité d’organisation** , tapez **Test**, puis cliquez sur **suivant**.</span><span class="sxs-lookup"><span data-stu-id="0876c-115">On the **Organization Information** page, in the **Organization** box, type **Contoso** if on the Contoso computer or **Fabrikam** if on the Fabrikam computer, in the **Organizational unit** box, type **Test**, and then click **Next**.</span></span>  
  
9. <span data-ttu-id="0876c-116">Sur le **nom commun de votre Site** page, dans le **nom commun** zone, tapez le nom de votre ordinateur, puis cliquez sur **suivant**.</span><span class="sxs-lookup"><span data-stu-id="0876c-116">On the **Your Site's Common Name** page, in the **Common name** box, type the name of your computer, and then click **Next**.</span></span>  
  
10. <span data-ttu-id="0876c-117">Sur le **informations géographiques** page, dans le **State/province** , tapez votre département/province, dans le **Ville/localité** zone, tapez votre ville/localité, puis cliquez sur **Suivant**.</span><span class="sxs-lookup"><span data-stu-id="0876c-117">On the **Geographical Information** page, in the **State/province** box, type your state/province, in the **City/locality** box, type your city/locality, and then click **Next**.</span></span>  
  
11. <span data-ttu-id="0876c-118">Sur le **nom du fichier de demande de certificat** page, dans le **nom de fichier** zone, laissez la valeur par défaut **C:\certreq.txt**, puis cliquez sur **suivant**.</span><span class="sxs-lookup"><span data-stu-id="0876c-118">On the **Certificate Request File Name** page, in the **File name** box, leave the default **C:\certreq.txt**, and then click **Next**.</span></span>  
  
12. <span data-ttu-id="0876c-119">Sur le **résumé du fichier de demande** , cliquez sur **suivant**.</span><span class="sxs-lookup"><span data-stu-id="0876c-119">On the **Request File Summary** page, click **Next**.</span></span>  
  
13. <span data-ttu-id="0876c-120">Sur le **fin de l’Assistant certificat de serveur Web** , cliquez sur **Terminer** pour fermer la **Assistant certificat IIS**.</span><span class="sxs-lookup"><span data-stu-id="0876c-120">On the **Completing the Web Server Certificate Wizard** page, click **Finish** to close the **IIS Certificate Wizard**.</span></span>  
  
### <a name="to-generate-a-new-server-certificate"></a><span data-ttu-id="0876c-121">Pour générer un nouveau certificat de serveur</span><span class="sxs-lookup"><span data-stu-id="0876c-121">To generate a new server certificate</span></span>  
  
1.  <span data-ttu-id="0876c-122">Dans Internet Explorer, recherchez et ouvrez http://\<*contoso_machine*\>/CertSrv.</span><span class="sxs-lookup"><span data-stu-id="0876c-122">In Internet Explorer, locate and open http://\<*contoso_machine*\>/CertSrv.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="0876c-123">À l’étape 1, ouvrez http://\<*contoso_machine*\>/CertSrv sur l’ordinateur Contoso ou Fabrikam.</span><span class="sxs-lookup"><span data-stu-id="0876c-123">In step 1, open http://\<*contoso_machine*\>/CertSrv on the Contoso or Fabrikam computer.</span></span>  
  
2.  <span data-ttu-id="0876c-124">Sur le **Microsoft Services Assistant certificat** , cliquez sur **demander un certificat.**</span><span class="sxs-lookup"><span data-stu-id="0876c-124">On the **Microsoft Certificate Services Wizard Welcome** page, click **Request a certificate.**</span></span>  
  
3.  <span data-ttu-id="0876c-125">Sur le **demander un certificat** , cliquez sur **demande de certificat avancée**.</span><span class="sxs-lookup"><span data-stu-id="0876c-125">On the **Request a Certificate** page, click **advanced certificate request**.</span></span>  
  
4.  <span data-ttu-id="0876c-126">Sur le **demande de certificat avancée** , cliquez sur **soumettre une demande de certificat en utilisant un fichier CMC ou PKCS #10 codé en base 64, ou soumettre une demande de renouvellement en utilisant un fichier PKCS #7 codé en base 64**.</span><span class="sxs-lookup"><span data-stu-id="0876c-126">On the **Advanced Certificate Request** page, click **Submit a certificate request by using a base-64-encoded CMC or PKCS #10 file, or submit a renewal request by using a base-64-encoded PKCS #7 file**.</span></span>  
  
5.  <span data-ttu-id="0876c-127">Sur le **soumettre une demande de certificat ou une demande de renouvellement** , cliquez sur **Parcourir pour insérer un fichier**.</span><span class="sxs-lookup"><span data-stu-id="0876c-127">On the **Submit a Certificate Request or Renewal Request** page, click **Browse for a file to insert**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="0876c-128">Si vous recevez une erreur de sécurité lorsque vous cliquez sur le lien, ouvrez le fichier C:\certreq.txt dans le bloc-notes ou un autre éditeur de texte, copiez le contenu du fichier et coller ces informations dans le **demande enregistrée** zone, puis cliquez sur  **Envoyer**.</span><span class="sxs-lookup"><span data-stu-id="0876c-128">If you receive a security error when clicking the link, open the file C:\certreq.txt in Notepad or another text editor, copy the contents of the file and paste that information in the **Saved Request** box, and then click **Submit**.</span></span> <span data-ttu-id="0876c-129">Vous pouvez ensuite accéder à l’étape 10.</span><span class="sxs-lookup"><span data-stu-id="0876c-129">You can then go to step 10.</span></span>  
  
6.  <span data-ttu-id="0876c-130">Cliquez sur **Parcourir** pour ouvrir le **choisir un fichier** boîte de dialogue.</span><span class="sxs-lookup"><span data-stu-id="0876c-130">Click **Browse** to open the **Choose File** dialog box.</span></span>  
  
7.  <span data-ttu-id="0876c-131">Dans le **choisir un fichier** boîte de dialogue, recherchez le  *\<lecteur\>*: \ dossier, sélectionnez le fichier certreq.txt, puis cliquez sur **ouvrir**.</span><span class="sxs-lookup"><span data-stu-id="0876c-131">In the **Choose File** dialog box, locate the *\<drive\>*:\ folder, select the certreq.txt file, and then click **Open**.</span></span>  
  
8.  <span data-ttu-id="0876c-132">Sur le **soumettre une demande de certificat ou une demande de renouvellement** , cliquez sur **en lecture**.</span><span class="sxs-lookup"><span data-stu-id="0876c-132">On the **Submit a Certificate Request or Renewal Request** page, click **Read**.</span></span>  
  
9. <span data-ttu-id="0876c-133">Sur le **soumettre une demande de certificat ou une demande de renouvellement** , cliquez sur **Submit** pour générer le nouveau certificat.</span><span class="sxs-lookup"><span data-stu-id="0876c-133">On the **Submit a Certificate Request or Renewal Request** page, click **Submit** to generate the new certificate.</span></span>  
  
10. <span data-ttu-id="0876c-134">Sur le **délivré** , cliquez sur **télécharger le certificat**.</span><span class="sxs-lookup"><span data-stu-id="0876c-134">On the **Certificate Issued** page, click **Download Certificate**.</span></span>  
  
11. <span data-ttu-id="0876c-135">Dans le **télécharger le fichier** boîte de dialogue, cliquez sur **enregistrer**.</span><span class="sxs-lookup"><span data-stu-id="0876c-135">In the **File Download** dialog box, click **Save**.</span></span>  
  
12. <span data-ttu-id="0876c-136">Dans le **enregistrer en tant que** boîte de dialogue, enregistrez le certificat à \<lecteur\>: \Certs\SSLCert.cer, puis cliquez sur **enregistrer**.</span><span class="sxs-lookup"><span data-stu-id="0876c-136">In the **Save As** dialog box, save the certificate to \<drive\>:\Certs\SSLCert.cer, and then click **Save**.</span></span>  
  
13. <span data-ttu-id="0876c-137">Cliquez sur **fermer** pour fermer la **téléchargement terminé** boîte de dialogue.</span><span class="sxs-lookup"><span data-stu-id="0876c-137">Click **Close** to close the **Download Complete** dialog box.</span></span>  
  
### <a name="to-prepare-a-new-server-certificate-for-iis"></a><span data-ttu-id="0876c-138">Pour préparer un nouveau certificat de serveur IIS</span><span class="sxs-lookup"><span data-stu-id="0876c-138">To Prepare a new Server Certificate for IIS</span></span>  
  
1.  <span data-ttu-id="0876c-139">Cliquez sur **Démarrer**, pointez sur **outils d’administration**, puis cliquez sur **Gestionnaire des Services Internet (IIS)**.</span><span class="sxs-lookup"><span data-stu-id="0876c-139">Click **Start**, point to **Administrative Tools**, and then click **Internet Information Services (IIS) Manager**.</span></span>  
  
2.  <span data-ttu-id="0876c-140">Dans le volet gauche de Internet Information Services, cliquez sur < nom_ordinateur > (ordinateur local), double-cliquez sur **des certificats de serveur** dans le volet droit.</span><span class="sxs-lookup"><span data-stu-id="0876c-140">In the Internet Information Services left pane, click <computer_name> (local computer), double click **Server Certificates** in the right pane.</span></span> <span data-ttu-id="0876c-141">Sélectionnez **créer une demande de certificat** à partir du volet Actions.</span><span class="sxs-lookup"><span data-stu-id="0876c-141">Select **Create Certificate Request** from Actions pane.</span></span>  
  
3.  <span data-ttu-id="0876c-142">Dans la boîte de dialogue Propriétés du nom unique, tapez le nom de l’ordinateur dans le nom commun : zone de texte, de l’organisation :, tapez **Contoso** if sur l’ordinateur Contoso ou **Fabrikam** if sur Fabrikam ordinateur, dans l’unité d’organisation : type de Test, dans la zone Ville/Localité, tapez votre ville/localité, dans la zone État/province, tapez votre département/province, dans la pays/région de liste déroulante, sélectionnez votre pays/région et puis cliquez sur **suivant**.</span><span class="sxs-lookup"><span data-stu-id="0876c-142">In Distinguished Name Properties dialog box type the name of the computer in the Common name: text box, in the Organization: box, type **Contoso** if on the Contoso computer or **Fabrikam** if on the Fabrikam computer, in the Organizational unit: box type Test, in the City/locality box, type your city/locality, in the State/province box, type your state/province, in the Country/region drop down, select your Country/region and then click **Next**.</span></span>  
  
4.  <span data-ttu-id="0876c-143">Dans la boîte de dialogue Propriétés de fournisseur de chiffrement Service, cliquez sur **suivant**.</span><span class="sxs-lookup"><span data-stu-id="0876c-143">In the Cryptographic Service Provider Properties dialog box, click **Next**.</span></span>  
  
5.  <span data-ttu-id="0876c-144">Dans la boîte de dialogue Nom de fichier, spécifiez C:\certreq.txt dans la zone de texte, cliquez sur **Terminer**.</span><span class="sxs-lookup"><span data-stu-id="0876c-144">In the File Name dialog box, specify C:\certreq.txt in the text box, click **Finish**.</span></span>  
  
### <a name="to-generate-a-new-server-certificate-for-iis"></a><span data-ttu-id="0876c-145">Pour générer un nouveau certificat de serveur pour IIS</span><span class="sxs-lookup"><span data-stu-id="0876c-145">To generate a new server certificate for IIS</span></span>  
  
1.  <span data-ttu-id="0876c-146">Dans Internet Explorer, recherchez et ouvrez http://<contoso_machine>/CertSrv.</span><span class="sxs-lookup"><span data-stu-id="0876c-146">In Internet Explorer, locate and open http://<contoso_machine>/CertSrv.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="0876c-147">À l’étape 1, ouvrez http://<contoso_machine>/CertSrv sur l’ordinateur Contoso ou Fabrikam.</span><span class="sxs-lookup"><span data-stu-id="0876c-147">In step 1, open http://<contoso_machine>/CertSrv on the Contoso or Fabrikam computer.</span></span>  
  
2.  <span data-ttu-id="0876c-148">Dans la page Microsoft Services Assistant certificat, cliquez sur **demander un certificat**.</span><span class="sxs-lookup"><span data-stu-id="0876c-148">On the Microsoft Certificate Services Wizard Welcome page, click **Request a certificate**.</span></span>  
  
3.  <span data-ttu-id="0876c-149">Dans la page demander un certificat, cliquez sur **demande de certificat avancée**.</span><span class="sxs-lookup"><span data-stu-id="0876c-149">On the Request a Certificate page, click **Advanced Certificate Request**.</span></span>  
  
4.  <span data-ttu-id="0876c-150">Dans la page de demande de certificat avancée, cliquez sur **soumettre une demande de certificat** en utilisant un fichier CMC ou PKCS #10 codé en base 64, ou soumettre une demande de renouvellement en utilisant un fichier PKCS #7 codé en base 64.</span><span class="sxs-lookup"><span data-stu-id="0876c-150">On the Advanced Certificate Request page, click **Submit a certificate request** by using a base-64-encoded CMC or PKCS #10 file, or submit a renewal request by using a base-64-encoded PKCS #7 file.</span></span>  
  
5.  <span data-ttu-id="0876c-151">Ouvrez le fichier C:\certreq.txt dans le bloc-notes ou un autre éditeur de texte, copiez le contenu du fichier et coller ces informations dans le **demande enregistrée** zone sur l’envoi d’une page de demande de certificat ou une demande de renouvellement, puis cliquez sur **Envoyer**.</span><span class="sxs-lookup"><span data-stu-id="0876c-151">Open the file C:\certreq.txt in Notepad or another text editor, copy the contents of the file and paste that information in the **Saved Request** box on the Submit a Certificate Request or Renewal Request page, and then click **Submit**.</span></span>  
  
6.  <span data-ttu-id="0876c-152">Dans la page certificat émis, cliquez sur **télécharger le certificat**.</span><span class="sxs-lookup"><span data-stu-id="0876c-152">On the Certificate Issued page, click **Download Certificate**.</span></span>  
  
7.  <span data-ttu-id="0876c-153">Dans la boîte de dialogue Téléchargement de fichier, cliquez sur **enregistrer**.</span><span class="sxs-lookup"><span data-stu-id="0876c-153">In the File Download dialog box, click **Save**.</span></span>  
  
8.  <span data-ttu-id="0876c-154">Dans la boîte de dialogue Enregistrer sous, enregistrer le certificat \<lecteur\>: \Certs\SSLCert.cer, puis cliquez sur **enregistrer**.</span><span class="sxs-lookup"><span data-stu-id="0876c-154">In the Save As dialog box, save the certificate to \<drive\>:\Certs\SSLCert.cer, and then click **Save**.</span></span>  
  
### <a name="to-import-the-server-certificate-into-iis"></a><span data-ttu-id="0876c-155">Pour importer le certificat de serveur dans IIS</span><span class="sxs-lookup"><span data-stu-id="0876c-155">To import the server certificate into IIS</span></span>  
  
1.  <span data-ttu-id="0876c-156">Cliquez sur **Démarrer**, pointez sur **outils d’administration**, puis cliquez sur **Gestionnaire des Services Internet (IIS)**.</span><span class="sxs-lookup"><span data-stu-id="0876c-156">Click **Start**, point to **Administrative Tools**, and then click **Internet Information Services (IIS) Manager**.</span></span>  
  
2.  <span data-ttu-id="0876c-157">Dans le volet gauche de Internet Information Services, cliquez sur **(ordinateur local)**, double-cliquez sur **des certificats de serveur** dans le volet droit.</span><span class="sxs-lookup"><span data-stu-id="0876c-157">In the Internet Information Services left pane, click **(local computer)**, double click **Server Certificates** in the right pane.</span></span> <span data-ttu-id="0876c-158">Sélectionnez **demande de certificat complète** dans le volet Actions.</span><span class="sxs-lookup"><span data-stu-id="0876c-158">Select **Complete Certificate Request** from the Actions pane.</span></span>  
  
3.  <span data-ttu-id="0876c-159">Dans le type de boîte de dialogue de réponse de l’autorité spécifier un certificat  **\<lecteur\>: \Certs\SSLCert.cer** dans **nom du fichier contenant la réponse de l’autorité de certification** zone de texte.</span><span class="sxs-lookup"><span data-stu-id="0876c-159">In Specify Certificate Authority Response dialog box type **\<drive\>:\Certs\SSLCert.cer** in **File name containing the certification authority’s response** text box.</span></span> <span data-ttu-id="0876c-160">Dans le type de zone de texte Nom convivial **ContosoSSLCert**.</span><span class="sxs-lookup"><span data-stu-id="0876c-160">In Friendly name text box type **ContosoSSLCert**.</span></span>  
  
### <a name="to-enable-ssl-bindings-for-iis"></a><span data-ttu-id="0876c-161">Pour activer les liaisons SSL pour IIS</span><span class="sxs-lookup"><span data-stu-id="0876c-161">To enable SSL bindings for IIS</span></span>  
  
1.  <span data-ttu-id="0876c-162">Cliquez sur **Démarrer**, pointez sur **outils d’administration**, puis cliquez sur **Gestionnaire des Services Internet (IIS)**.</span><span class="sxs-lookup"><span data-stu-id="0876c-162">Click **Start**, point to **Administrative Tools**, and then click **Internet Information Services (IIS) Manager**.</span></span>  
  
2.  <span data-ttu-id="0876c-163">Dans le volet gauche de Internet Information Services, développez **(ordinateur local)**, développez **Sites**, avec le bouton droit **Site Web par défaut**, puis cliquez sur **modifier Liaisons**.</span><span class="sxs-lookup"><span data-stu-id="0876c-163">In the Internet Information Services left pane, expand **(local computer)**, expand **Sites**, right-click **Default Web Site**, and then click **Edit Bindings**.</span></span>  
  
3.  <span data-ttu-id="0876c-164">Dans la boîte de dialogue liaisons de Site, cliquez sur **ajouter**.</span><span class="sxs-lookup"><span data-stu-id="0876c-164">In Site Bindings dialog box click **Add**.</span></span> <span data-ttu-id="0876c-165">Dans la boîte de dialogue Ajouter la liaison de Site, sélectionnez **https** à partir de la liste déroulante Type, sélectionnez **ContosoSSLCert** à partir de la liste de certificats SSL vers le bas, cliquez sur **OK**, cliquez sur **fermer** .</span><span class="sxs-lookup"><span data-stu-id="0876c-165">In the Add Site Binding dialog box select **https** from Type drop down, select **ContosoSSLCert** from SSL certificate drop down, click **OK**, click **Close**.</span></span>  
  
### <a name="to-import-the-server-certificate-into-iis"></a><span data-ttu-id="0876c-166">Pour importer le certificat de serveur dans IIS</span><span class="sxs-lookup"><span data-stu-id="0876c-166">To import the server certificate into IIS</span></span>  
  
1.  <span data-ttu-id="0876c-167">Cliquez sur **Démarrer**, pointez sur **outils d’administration**, puis cliquez sur **Gestionnaire des Services Internet (IIS)**.</span><span class="sxs-lookup"><span data-stu-id="0876c-167">Click **Start**, point to **Administrative Tools**, and then click **Internet Information Services (IIS) Manager**.</span></span>  
  
2.  <span data-ttu-id="0876c-168">Dans le volet gauche de Internet Information Services, développez  **\<**  *Nom_Ordinateur* \> (*ordinateur local*), développez **Web Sites**, avec le bouton droit **Site Web par défaut**, puis cliquez sur **propriétés**.</span><span class="sxs-lookup"><span data-stu-id="0876c-168">In the Internet Information Services left pane, expand **\<***computer_name*\> (*local computer*), expand **Web Sites**, right-click **Default Web Site**, and then click **Properties**.</span></span>  
  
3.  <span data-ttu-id="0876c-169">Dans la boîte de dialogue Propriétés du Site Web par défaut sur le **sécurité du répertoire** , cliquez sur **certificat de serveur** pour démarrer le **Assistant certificat IIS**.</span><span class="sxs-lookup"><span data-stu-id="0876c-169">In the Default Web Site Properties dialog box, on the **Directory Security** tab, click **Server Certificate** to start the **IIS Certificate Wizard**.</span></span>  
  
4.  <span data-ttu-id="0876c-170">Sur le **Bienvenue dans l’Assistant certificat de serveur Web** , cliquez sur **suivant**.</span><span class="sxs-lookup"><span data-stu-id="0876c-170">On the **Welcome to the Web Server Certificate Wizard** page, click **Next**.</span></span>  
  
5.  <span data-ttu-id="0876c-171">Sur le **demande de certificat en attente** page, sélectionnez **traiter la demande en attente et installer le certificat**, puis cliquez sur **suivant**.</span><span class="sxs-lookup"><span data-stu-id="0876c-171">On the **Pending Certificate Request** page, select **Process the pending request and install the certificate**, and then click **Next**.</span></span>  
  
6.  <span data-ttu-id="0876c-172">Sur le **traiter une demande en attente** page, dans le **chemin d’accès et nom de fichier** , tapez  **\<lecteur\>: \Certs\SSLCert.cer** (ou accédez à ce fichier) puis cliquez sur **suivant**.</span><span class="sxs-lookup"><span data-stu-id="0876c-172">On the **Process a Pending Request** page, in the **Path and file name** box, type **\<drive\>:\Certs\SSLCert.cer** (or browse to that file) and then click **Next**.</span></span>  
  
7.  <span data-ttu-id="0876c-173">Sur le **page Port SSL**, cliquez sur **suivant**.</span><span class="sxs-lookup"><span data-stu-id="0876c-173">On the **SSL Port page**, click **Next**.</span></span>  
  
8.  <span data-ttu-id="0876c-174">Sur le **résumé du certificat** , cliquez sur **suivant**.</span><span class="sxs-lookup"><span data-stu-id="0876c-174">On the **Certificate Summary** page, click **Next**.</span></span>  
  
9. <span data-ttu-id="0876c-175">Sur le **fin de l’Assistant certificat de serveur Web** , cliquez sur **Terminer**.</span><span class="sxs-lookup"><span data-stu-id="0876c-175">On the **Completing the Web Server Certificate Wizard** page, click **Finish**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0876c-176">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="0876c-176">See Also</span></span>  
 [<span data-ttu-id="0876c-177">Création et configuration de la solution Contoso</span><span class="sxs-lookup"><span data-stu-id="0876c-177">Creating and Configuring the Contoso Solution</span></span>](../../adapters-and-accelerators/accelerator-rosettanet/creating-and-configuring-the-contoso-solution.md)