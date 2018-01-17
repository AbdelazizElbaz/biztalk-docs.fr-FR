---
title: "L’importation de certificats à l’aide de l’utilitaire CertWizard | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- certificates, root keys
- certificates, public keys
- certificates, private keys
- importing certificates
- public keys
- private keys
- CertWizard utility
- certificates, importing
- root keys
ms.assetid: 0c54d7ab-69cf-4f4a-b976-6f740a41280b
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 64be28927a49a1fc751870785ff3fc3f55a36cb1
ms.sourcegitcommit: 3fd1c85d9dc2ce7b77da75a5c2087cc48cfcbe50
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/17/2018
---
# <a name="importing-certificates-using-the-certwizard-utility"></a><span data-ttu-id="ee53b-102">L’importation de certificats à l’aide de l’utilitaire CertWizard</span><span class="sxs-lookup"><span data-stu-id="ee53b-102">Importing Certificates Using the CertWizard Utility</span></span>
<span data-ttu-id="ee53b-103">Cette rubrique décrit comment importer un certificat en utilisant l’utilitaire CertWizard, un utilitaire de ligne de commande de pas à pas disponible dans le [!INCLUDE[btsCoName](../../includes/btsconame-md.md)] [!INCLUDE[BTARN_CurrentVersion_FirstRef](../../includes/btarn-currentversion-firstref-md.md)] Kit de développement logiciel.</span><span class="sxs-lookup"><span data-stu-id="ee53b-103">This topic describes how to import a certificate by using CertWizard utility, a step-by-step command-line utility available in the [!INCLUDE[btsCoName](../../includes/btsconame-md.md)][!INCLUDE[BTARN_CurrentVersion_FirstRef](../../includes/btarn-currentversion-firstref-md.md)] SDK.</span></span> <span data-ttu-id="ee53b-104">Cette rubrique décrit l’importation d’un private, public ou clé racine.</span><span class="sxs-lookup"><span data-stu-id="ee53b-104">This topic discusses importing a private, public, or root key.</span></span> <span data-ttu-id="ee53b-105">Elle décrit les commutateurs qui vous permet de configurer le certificat.</span><span class="sxs-lookup"><span data-stu-id="ee53b-105">It describes the switches that you use to configure the certificate.</span></span>  
  
 <span data-ttu-id="ee53b-106">L’utilitaire CertWizard automatise une grande partie des étapes que vous devriez faire manuellement à l’aide de la [!INCLUDE[btsCoName](../../includes/btsconame-md.md)] Management Console (MMC).</span><span class="sxs-lookup"><span data-stu-id="ee53b-106">The CertWizard utility automates many of the steps that you would have to do manually by using the [!INCLUDE[btsCoName](../../includes/btsconame-md.md)] Management Console (MMC).</span></span> <span data-ttu-id="ee53b-107">L’utilitaire CertWizard effectue la **runas** commande pour ouvrir la console MMC comme compte de service hôte.</span><span class="sxs-lookup"><span data-stu-id="ee53b-107">The CertWizard utility performs the **runas** command to open MMC as the host service account.</span></span> <span data-ttu-id="ee53b-108">Si vous n’ajoutez pas une **Useridentity** commutateur, il détecte et utilise le compte de service d’hôte, vous invite à entrer un mot de passe.</span><span class="sxs-lookup"><span data-stu-id="ee53b-108">If you do not add a **Useridentity** switch, it will detect and use the host service account, prompting you for a password.</span></span> <span data-ttu-id="ee53b-109">Il stocke et configure le certificat.</span><span class="sxs-lookup"><span data-stu-id="ee53b-109">It stores and configures the certificate.</span></span>  
  
 <span data-ttu-id="ee53b-110">Vous pouvez importer plusieurs certificats en même temps en créant un fichier de commandes avec plusieurs commandes d’utilitaire CertWizard.</span><span class="sxs-lookup"><span data-stu-id="ee53b-110">You can import multiple certificates at the same time by creating a batch file with multiple CertWizard utility commands.</span></span>  
  
### <a name="to-import-a-private-key"></a><span data-ttu-id="ee53b-111">Pour importer une clé privée</span><span class="sxs-lookup"><span data-stu-id="ee53b-111">To import a private key</span></span>  
  
1.  <span data-ttu-id="ee53b-112">Cliquez sur **Démarrer**, puis sur **Exécuter**, tapez **cmd**, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="ee53b-112">Click **Start**, click **Run**, type **cmd**, and then click **OK**.</span></span>  
  
2.  <span data-ttu-id="ee53b-113">À l’invite de commandes, passez à la [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] dossier SDK à l’aide de MS-DOS **CD** commande, par exemple, tapez **cd C:\Program Files\Microsoft BizTalk \<version\> Accelerator for RosettaNet\SDK** .</span><span class="sxs-lookup"><span data-stu-id="ee53b-113">At the command prompt, move to the [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] SDK folder using the MS-DOS **CD** command, for example, type **cd C:\Program Files\Microsoft BizTalk \<version\> Accelerator for RosettaNet\SDK** .</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="ee53b-114">Pour obtenir de l’utilitaire CertWizard, tapez **CertWizard / ?**</span><span class="sxs-lookup"><span data-stu-id="ee53b-114">For help with the CertWizard utility, type **CertWizard /?**</span></span> <span data-ttu-id="ee53b-115">à l’invite de commandes.</span><span class="sxs-lookup"><span data-stu-id="ee53b-115">at the command prompt.</span></span>  
  
3.  <span data-ttu-id="ee53b-116">À l’invite de commandes, tapez **CertWizard /Privatekey \<nom de fichier\>.pfx**, où \< *nom de fichier*\>.pfx contient le certificat privé.</span><span class="sxs-lookup"><span data-stu-id="ee53b-116">At the command prompt, type **CertWizard /Privatekey \<filename\>.pfx**, where \<*filename*\>.pfx contains the private certificate.</span></span> <span data-ttu-id="ee53b-117">Pour fournir le mot de passe pour le fichier, ajoutez **/Filepassword \<filepassword\>**  à la commande.</span><span class="sxs-lookup"><span data-stu-id="ee53b-117">To provide the password for the file, append **/Filepassword \<filepassword\>** to the command.</span></span>  
  
4.  <span data-ttu-id="ee53b-118">Si vous souhaitez importer le certificat dans un compte spécifique utilisé par l’hôte BizTalk, ajoutez **/Useridentity \<useridentity\> /password \<mot de passe\>**  à la commande.</span><span class="sxs-lookup"><span data-stu-id="ee53b-118">If you want to import the certificate into a specific account used by the BizTalk Host, append **/Useridentity \<useridentity\> /Password \<password\>** to the command.</span></span>  
  
5.  <span data-ttu-id="ee53b-119">Si vous souhaitez désigner une empreinte numérique spécifique au cas où le fichier .pfx contient plusieurs certificats, ajoutez **/overwrite/Thumbprint \<l’empreinte numérique\>**  à la commande.</span><span class="sxs-lookup"><span data-stu-id="ee53b-119">If you want to designate a specific thumbprint in case the .pfx file contains more than one certificate, append **/Thumbprint \<thumbprint\>** to the command.</span></span>  
  
6.  <span data-ttu-id="ee53b-120">Si vous souhaitez configurer l’utilisation du certificat, ajoutez **/Usage** à la commande, puis ajoutez une des valeurs suivantes :</span><span class="sxs-lookup"><span data-stu-id="ee53b-120">If you want to configure the usage of the certificate, append **/Usage** to the command, and then append one of the following values:</span></span>  
  
    -   <span data-ttu-id="ee53b-121">Ajouter **signe** pour ajouter l’empreinte du certificat en tant que le certificat de signature pour le groupe BizTalk.</span><span class="sxs-lookup"><span data-stu-id="ee53b-121">Append **sign** to add the certificate's thumbprint as the signing certificate for the BizTalk Group.</span></span> <span data-ttu-id="ee53b-122">tel que défini dans la boîte de dialogue pour Microsoft BizTalk Server (Local) dans la Console Administration de BizTalk.</span><span class="sxs-lookup"><span data-stu-id="ee53b-122">as set on the dialog box for Microsoft BizTalk Server (Local) in the BizTalk Administration Console.</span></span>  
  
    -   <span data-ttu-id="ee53b-123">Ajouter **déchiffrer** pour ajouter l’empreinte du certificat en tant que le certificat de déchiffrement pour les hôtes BizTalk, tel que défini dans l’onglet certificat des pages de propriétés pour chaque hôte dans la Console Administration de BizTalk.</span><span class="sxs-lookup"><span data-stu-id="ee53b-123">Append **decrypt** to add the certificate's thumbprint as the decryption certificate for the BizTalk Hosts, as set on the certificate tab of the property pages for each host in the BizTalk Administration Console.</span></span>  
  
    -   <span data-ttu-id="ee53b-124">Ajouter **les deux** pour ajouter le certificat de l’empreinte numérique pour les deux BizTalk du groupe de la signature du certificat et le certificat de déchiffrement de l’hôte BizTalk.</span><span class="sxs-lookup"><span data-stu-id="ee53b-124">Append **both** to add the certificate's thumbprint for both the BizTalk Group's signing certificate and the BizTalk Host's decryption certificate.</span></span>  
  
    -   <span data-ttu-id="ee53b-125">Ajouter **aucun** lorsque vous ne souhaitez pas définir la configuration pour le groupe BizTalk ou les hôtes BizTalk.</span><span class="sxs-lookup"><span data-stu-id="ee53b-125">Append **none** when you do not want to set the configuration for the BizTalk Group or the BizTalk Hosts.</span></span>  
  
7.  <span data-ttu-id="ee53b-126">Si vous souhaitez configurer le certificat comme exportable, ajoutez **/Exportable true**.</span><span class="sxs-lookup"><span data-stu-id="ee53b-126">If you want to configure the certificate as exportable, append **/Exportable true**.</span></span> <span data-ttu-id="ee53b-127">Pour définir le certificat comme non exportable, ajoutez **/Exportable false**, qui est le comportement par défaut.</span><span class="sxs-lookup"><span data-stu-id="ee53b-127">To set the certificate as non-exportable, append **/Exportable false**, which is the default behavior.</span></span>  
  
8.  <span data-ttu-id="ee53b-128">Appuyez sur **Entrée**.</span><span class="sxs-lookup"><span data-stu-id="ee53b-128">Press **Enter**.</span></span>  
  
9. <span data-ttu-id="ee53b-129">Si vous n’avez pas tapé un des mots de passe requis dans la commande, l’outil vous invite à entrer pour celle-ci.</span><span class="sxs-lookup"><span data-stu-id="ee53b-129">If you did not type one of the passwords required in the command, the tool prompts you for it.</span></span> <span data-ttu-id="ee53b-130">Tapez le mot de passe, puis appuyez sur **entrée**.</span><span class="sxs-lookup"><span data-stu-id="ee53b-130">Type the password, and then press **Enter**.</span></span>  
  
10. <span data-ttu-id="ee53b-131">Si le fichier contient plusieurs certificats, mais vous n’avez pas tapé une empreinte numérique dans la commande, l’outil affiche les empreintes numériques disponibles et vous invite à sélectionner un.</span><span class="sxs-lookup"><span data-stu-id="ee53b-131">If the file contains multiple certificates, but you did not type a thumbprint in the command, the tool displays the available thumbprints, and prompts you to select one.</span></span> <span data-ttu-id="ee53b-132">Tapez le numéro de l’empreinte numérique que vous souhaitez, puis appuyez sur **entrée**.</span><span class="sxs-lookup"><span data-stu-id="ee53b-132">Type the number of the thumbprint that you want, and then press **Enter**.</span></span>  
  
     <span data-ttu-id="ee53b-133">L’outil importe le certificat dans le magasin de \Personal\Certificates pour l’utilisateur spécifié dans le **/useridentity** basculer.</span><span class="sxs-lookup"><span data-stu-id="ee53b-133">The tool imports the certificate into the \Personal\Certificates store for the user specified in the **/useridentity** switch.</span></span> <span data-ttu-id="ee53b-134">Si vous ne spécifiez pas un utilisateur, l’utilisateur par défaut est l’identité de l’utilisateur pour l’hôte BizTalkServerApplication l’hôte BizTalkServerIsolatedHost.</span><span class="sxs-lookup"><span data-stu-id="ee53b-134">If you do not specify a user, the default user is the user identity for the BizTalkServerApplication and BizTalkServerIsolatedHost hosts.</span></span>  
  
### <a name="to-import-a-public-key"></a><span data-ttu-id="ee53b-135">Pour importer une clé publique</span><span class="sxs-lookup"><span data-stu-id="ee53b-135">To import a public key</span></span>  
  
1.  <span data-ttu-id="ee53b-136">Cliquez sur **Démarrer**, puis sur **Exécuter**, tapez **cmd**, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="ee53b-136">Click **Start**, click **Run**, type **cmd**, and then click **OK**.</span></span>  
  
2.  <span data-ttu-id="ee53b-137">À l’invite de commandes, passez à la [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] dossier SDK à l’aide de MS-DOS **CD** commande, par exemple, tapez **cd C:\Program Files\Microsoft BizTalk \<version\> Accelerator for RosettaNet\SDK**.</span><span class="sxs-lookup"><span data-stu-id="ee53b-137">At the command prompt, move to the [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] SDK folder by using the MS-DOS **CD** command, for example, type **cd C:\Program Files\Microsoft BizTalk \<version\> Accelerator for RosettaNet\SDK**.</span></span>  
  
3.  <span data-ttu-id="ee53b-138">À l’invite de commandes, tapez **/PublicKey de CertWizard \<nom de fichier\>.cer**, où \< *nom de fichier*\>.cer contient le certificat public.</span><span class="sxs-lookup"><span data-stu-id="ee53b-138">At the command prompt, type **CertWizard /Publickey \<filename\>.cer**, where \<*filename*\>.cer contains the public certificate.</span></span>  
  
4.  <span data-ttu-id="ee53b-139">Si vous souhaitez désigner une empreinte numérique du certificat dans le fichier .cer ou .der, ajoutez **/overwrite/Thumbprint \<l’empreinte numérique\>**  à la commande.</span><span class="sxs-lookup"><span data-stu-id="ee53b-139">If you want to designate a thumbprint for the certificate in the .cer or .der file, append **/Thumbprint \<thumbprint\>** to the command.</span></span>  
  
     <span data-ttu-id="ee53b-140">L’outil importe le certificat dans le magasin de \Other People\Certificates de certificats (ordinateur Local) et définit sa configuration.</span><span class="sxs-lookup"><span data-stu-id="ee53b-140">The tool imports the certificate into the Certificates (Local Computer)\Other People\Certificates store, and sets its configuration.</span></span>  
  
### <a name="to-import-a-root-key"></a><span data-ttu-id="ee53b-141">Pour importer une clé racine</span><span class="sxs-lookup"><span data-stu-id="ee53b-141">To import a root key</span></span>  
  
1.  <span data-ttu-id="ee53b-142">Cliquez sur **Démarrer**, puis sur **Exécuter**, tapez **cmd**, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="ee53b-142">Click **Start**, click **Run**, type **cmd**, and then click **OK**.</span></span>  
  
2.  <span data-ttu-id="ee53b-143">À l’invite de commandes, passez à la [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] dossier SDK à l’aide de MS-DOS **CD** commande, par exemple, tapez **cd C:\Program Files\Microsoft BizTalk \<version\> Accelerator for RosettaNet\SDK**.</span><span class="sxs-lookup"><span data-stu-id="ee53b-143">At the command prompt, move to the [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)] SDK folder by using the MS-DOS **CD** command, for example, type **cd C:\Program Files\Microsoft BizTalk \<version\> Accelerator for RosettaNet\SDK**.</span></span>  
  
3.  <span data-ttu-id="ee53b-144">À l’invite de commandes, tapez **CertWizard /Rootkey \<nom de fichier\>.cer**, où \< *nom de fichier*\>.cer contient le certificat racine.</span><span class="sxs-lookup"><span data-stu-id="ee53b-144">At the command prompt, type **CertWizard /Rootkey \<filename\>.cer**, where \<*filename*\>.cer contains the root certificate.</span></span>  
  
4.  <span data-ttu-id="ee53b-145">Si vous souhaitez désigner une empreinte numérique du certificat dans le fichier .cer ou .der, ajoutez **/overwrite/Thumbprint \<l’empreinte numérique\>**  à la commande.</span><span class="sxs-lookup"><span data-stu-id="ee53b-145">If you want to designate a thumbprint for the certificate in the .cer or .der file, append **/Thumbprint \<thumbprint\>** to the command.</span></span>  
  
     <span data-ttu-id="ee53b-146">L’outil importe le certificat dans le magasin de \Trusted Root Certification Authority\Certificates de certificats (ordinateur Local) et définit sa configuration.</span><span class="sxs-lookup"><span data-stu-id="ee53b-146">The tool imports the certificate into the Certificates (Local Computer)\Trusted Root Certification Authority\Certificates store, and sets its configuration.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ee53b-147">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ee53b-147">See Also</span></span>  
 <span data-ttu-id="ee53b-148">[CertWizard](../../adapters-and-accelerators/accelerator-rosettanet/certwizard.md) </span><span class="sxs-lookup"><span data-stu-id="ee53b-148">[CertWizard](../../adapters-and-accelerators/accelerator-rosettanet/certwizard.md) </span></span>  
 [<span data-ttu-id="ee53b-149">Gestion des certificats</span><span class="sxs-lookup"><span data-stu-id="ee53b-149">Managing Certificates</span></span>](../../adapters-and-accelerators/accelerator-rosettanet/managing-certificates1.md)