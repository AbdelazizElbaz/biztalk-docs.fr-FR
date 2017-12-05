---
title: CertWizard | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- certificates, CertWizard utility
- CertWizard utility
- certificates, importing
ms.assetid: beeab3c0-d7b1-4bb9-8b19-f79b049d5aa1
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: ea106299a734f79506823ca4a6951a3dad367553
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="certwizard"></a><span data-ttu-id="fee57-102">CertWizard</span><span class="sxs-lookup"><span data-stu-id="fee57-102">CertWizard</span></span>
<span data-ttu-id="fee57-103">L’utilitaire CertWizard permet d’importer un certificat à partir d’un fichier .pfx ou .cer dans un magasin privé ou public pour une utilisation avec [!INCLUDE[btsCoName](../../includes/btsconame-md.md)]® [!INCLUDE[BTARN_CurrentVersion_FirstRef](../../includes/btarn-currentversion-firstref-md.md)].</span><span class="sxs-lookup"><span data-stu-id="fee57-103">You use the CertWizard utility to import a certificate from a .pfx or .cer file into a private or public store for use with [!INCLUDE[btsCoName](../../includes/btsconame-md.md)]® [!INCLUDE[BTARN_CurrentVersion_FirstRef](../../includes/btarn-currentversion-firstref-md.md)].</span></span>  
  
## <a name="location-in-sdk"></a><span data-ttu-id="fee57-104">Emplacement dans le kit de développement logiciel (SDK)</span><span class="sxs-lookup"><span data-stu-id="fee57-104">Location in SDK</span></span>  
 <span data-ttu-id="fee57-105">\<*lecteur*\>\Program Files\\ [!INCLUDE[btsCoName](../../includes/btsconame-md.md)] BizTalk \<version\> Accelerator for RosettaNet\SDK\\</span><span class="sxs-lookup"><span data-stu-id="fee57-105">\<*drive*\>\Program Files\\[!INCLUDE[btsCoName](../../includes/btsconame-md.md)] BizTalk \<version\> Accelerator for RosettaNet\SDK\\</span></span>  
  
## <a name="running-certwizard"></a><span data-ttu-id="fee57-106">CertWizard en cours d’exécution</span><span class="sxs-lookup"><span data-stu-id="fee57-106">Running CertWizard</span></span>  
  
#### <a name="to-run-certwizard"></a><span data-ttu-id="fee57-107">Pour exécuter CertWizard</span><span class="sxs-lookup"><span data-stu-id="fee57-107">To run CertWizard</span></span>  
  
1.  <span data-ttu-id="fee57-108">Ouvrez une invite de commandes.</span><span class="sxs-lookup"><span data-stu-id="fee57-108">Open a command prompt.</span></span>  
  
2.  <span data-ttu-id="fee57-109">Déplacer vers \< *lecteur*\>\ Program Files\\ [!INCLUDE[btsCoName](../../includes/btsconame-md.md)] BizTalk \<version\> Accelerator for RosettaNet\SDK\\.</span><span class="sxs-lookup"><span data-stu-id="fee57-109">Move to \<*drive*\>\ Program Files\\[!INCLUDE[btsCoName](../../includes/btsconame-md.md)] BizTalk \<version\> Accelerator for RosettaNet\SDK\\.</span></span>  
  
3.  <span data-ttu-id="fee57-110">À l’invite de commandes, tapez **CertWizard**, tapez les interrupteurs requis, puis appuyez sur ENTRÉE.</span><span class="sxs-lookup"><span data-stu-id="fee57-110">At the command prompt, type **CertWizard**, type the required and appropriate switches, and then press ENTER.</span></span>  
  
## <a name="syntax-for-certwizard"></a><span data-ttu-id="fee57-111">Syntaxe de CertWizard</span><span class="sxs-lookup"><span data-stu-id="fee57-111">Syntax for CertWizard</span></span>  
 <span data-ttu-id="fee57-112">Voici la syntaxe que vous utilisez pour démarrer cet utilitaire de ligne de commande :</span><span class="sxs-lookup"><span data-stu-id="fee57-112">The following shows the syntax that you use to start this command-line utility:</span></span>  
  
### <a name="syntax-for-importing-a-private-key"></a><span data-ttu-id="fee57-113">Syntaxe pour l'importation d'une clé privée</span><span class="sxs-lookup"><span data-stu-id="fee57-113">Syntax for Importing a Private Key</span></span>  
  
```  
CertWizard /Privatekey <filename>.pfx [/Filepassword <filepassword>] [/Useridentity <useridentity>] [/Password <password>] [/Thumbprint <thumbprint>] [/Usage sign|decrypt|both|none] [/Exportable true|false]  
```  
  
### <a name="syntax-for-importing-a-public-key"></a><span data-ttu-id="fee57-114">Syntaxe pour l'importation d'une clé publique</span><span class="sxs-lookup"><span data-stu-id="fee57-114">Syntax for Importing a Public Key</span></span>  
  
```  
CertWizard /Publickey <filename>.cer [/Thumbprint <thumbprint>]  
```  
  
### <a name="syntax-for-importing-a-root-key"></a><span data-ttu-id="fee57-115">Syntaxe pour l'importation d'une clé racine</span><span class="sxs-lookup"><span data-stu-id="fee57-115">Syntax for Importing a Root Key</span></span>  
  
```  
CertWizard /Rootkey <filename>.cer [/Thumbprint <thumbprint>]  
```  
  
### <a name="syntax-description"></a><span data-ttu-id="fee57-116">Description de la syntaxe</span><span class="sxs-lookup"><span data-stu-id="fee57-116">Syntax Description</span></span>  
 <span data-ttu-id="fee57-117">Le tableau suivant décrit les éléments de la syntaxe utilisée par l'utilitaire CertWizard.</span><span class="sxs-lookup"><span data-stu-id="fee57-117">The following table describes each part of the syntax that the CertWizard utility uses.</span></span>  
  
|<span data-ttu-id="fee57-118">**Syntaxe**</span><span class="sxs-lookup"><span data-stu-id="fee57-118">**Syntax**</span></span>|<span data-ttu-id="fee57-119">**Description**</span><span class="sxs-lookup"><span data-stu-id="fee57-119">**Description**</span></span>|  
|----------------|---------------------|  
|<span data-ttu-id="fee57-120">**PrivateKey**</span><span class="sxs-lookup"><span data-stu-id="fee57-120">**Privatekey**</span></span>|<span data-ttu-id="fee57-121">Utilisée pour importer une clé privée.</span><span class="sxs-lookup"><span data-stu-id="fee57-121">Used to import a private key.</span></span>|  
|<span data-ttu-id="fee57-122">**Clé publique**</span><span class="sxs-lookup"><span data-stu-id="fee57-122">**Publickey**</span></span>|<span data-ttu-id="fee57-123">Utilisée pour importer une clé publique.</span><span class="sxs-lookup"><span data-stu-id="fee57-123">Used to import a public key.</span></span>|  
|<span data-ttu-id="fee57-124">**Cle_principale**</span><span class="sxs-lookup"><span data-stu-id="fee57-124">**Rootkey**</span></span>|<span data-ttu-id="fee57-125">Utilisée pour importer une clé racine (d’une autorité de certification).</span><span class="sxs-lookup"><span data-stu-id="fee57-125">Used to import a root key—from a certification authority.</span></span>|  
|<span data-ttu-id="fee57-126">**nom_fichier.pfx (ou .cer)**</span><span class="sxs-lookup"><span data-stu-id="fee57-126">**filename.pfx (or .cer)**</span></span>|<span data-ttu-id="fee57-127">Chemin d'accès complet du fichier .pfx (clés privées) ou .cer (clés publiques).</span><span class="sxs-lookup"><span data-stu-id="fee57-127">Full path for the .pfx (private keys) or .cer (public keys) file.</span></span>|  
|<span data-ttu-id="fee57-128">**Filepassword**</span><span class="sxs-lookup"><span data-stu-id="fee57-128">**Filepassword**</span></span>|<span data-ttu-id="fee57-129">Mot de passe requis pour déverrouiller le fichier .pfx.</span><span class="sxs-lookup"><span data-stu-id="fee57-129">The password required to unlock the .pfx file.</span></span>|  
|<span data-ttu-id="fee57-130">**Identité de l’utilisateur**</span><span class="sxs-lookup"><span data-stu-id="fee57-130">**Useridentity**</span></span>|<span data-ttu-id="fee57-131">Identité de service utilisée par un ou plusieurs hôtes BizTalk.</span><span class="sxs-lookup"><span data-stu-id="fee57-131">A service identity that one or more BizTalk Hosts uses.</span></span> <span data-ttu-id="fee57-132">Entrez un compte d'utilisateur si vous ne souhaitez pas spécifier l'hôte mais importer un certificat sous un compte d'utilisateur.</span><span class="sxs-lookup"><span data-stu-id="fee57-132">Enter a user account if you do not want to specify the host, but want to import a certificate under a user account.</span></span> <span data-ttu-id="fee57-133">**Remarque :** si vous n’ajoutez pas le **Useridentity** basculer, les importations d’utilitaire et de définir le certificat pour tous les utilisateurs.</span><span class="sxs-lookup"><span data-stu-id="fee57-133">**Note:**  If you do not add the **Useridentity** switch, the utility imports and set the certificate for all users.</span></span> <span data-ttu-id="fee57-134">**Remarque :** si vous ajoutez le **Useridentity** commutateur, mais n’entrez pas de valeur, WMI génère automatiquement l’identité de l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="fee57-134">**Note:**  If you add the **Useridentity** switch, but do not enter a value, WMI automatically generates the user identity.</span></span>|  
|<span data-ttu-id="fee57-135">**Mot de passe**</span><span class="sxs-lookup"><span data-stu-id="fee57-135">**Password**</span></span>|<span data-ttu-id="fee57-136">Mot de passe de l'utilisateur de l'identité du service.</span><span class="sxs-lookup"><span data-stu-id="fee57-136">The password for the service identity user.</span></span>|  
|<span data-ttu-id="fee57-137">**Empreinte numérique**</span><span class="sxs-lookup"><span data-stu-id="fee57-137">**Thumbprint**</span></span>|<span data-ttu-id="fee57-138">Empreinte d'un certificat spécifique, au cas où le fichier contient plusieurs certificats.</span><span class="sxs-lookup"><span data-stu-id="fee57-138">The thumbprint of a specific certificate, in case the file contains more than one certificate.</span></span> <span data-ttu-id="fee57-139">**Remarque :** pour un fichier de certificat public, si le fichier contient plusieurs certificats et que vous ne spécifiez pas l’empreinte numérique, l’utilitaire importe tous les certificats dans le fichier.</span><span class="sxs-lookup"><span data-stu-id="fee57-139">**Note:**  For a public certificate file, if the file contains more than one certificate and you do not specify the thumbprint, the utility imports all certificates in the file.</span></span> <span data-ttu-id="fee57-140">Dans le cas d'un fichier de certificat privé, l'utilitaire vous invite à sélectionner le certificat à importer.</span><span class="sxs-lookup"><span data-stu-id="fee57-140">For a private certificate file, the utility prompts you to select the certificate to import.</span></span>|  
|<span data-ttu-id="fee57-141">**Utilisation**</span><span class="sxs-lookup"><span data-stu-id="fee57-141">**Usage**</span></span>|<span data-ttu-id="fee57-142">Utilisation prévue du certificat privé importé.</span><span class="sxs-lookup"><span data-stu-id="fee57-142">The intended usage of the imported private certificate.</span></span> <span data-ttu-id="fee57-143">Peut être l’authentification (pour un certificat de signature), déchiffrer (pour un certificat de déchiffrement), à la fois (pour un certificat est un certificat de signature et un certificat de déchiffrement) ou none (également pour un certificat est un certificat de signature et un certificat de déchiffrement ).</span><span class="sxs-lookup"><span data-stu-id="fee57-143">Can be sign (for a signing certificate), decrypt (for a decryption certificate), both (for a certificate that is both a signing certificate and a decryption certificate), or none (also for a certificate that is both a signing certificate and a decryption certificate).</span></span> <span data-ttu-id="fee57-144">**Remarque :** si vous définissez la **/Usage** commutateur None, l’Assistant ne définit pas de l’empreinte numérique du certificat sur les hôtes BizTalk ou le groupe BizTalk.</span><span class="sxs-lookup"><span data-stu-id="fee57-144">**Note:**  If you set the **/Usage** switch to none, the wizard will not set the thumbprint for the certificate on the BizTalk Hosts or the BizTalk Group.</span></span>|  
|<span data-ttu-id="fee57-145">**Exportable**</span><span class="sxs-lookup"><span data-stu-id="fee57-145">**Exportable**</span></span>|<span data-ttu-id="fee57-146">Peut être `True` ou `False`.</span><span class="sxs-lookup"><span data-stu-id="fee57-146">Can be `True` or `False`.</span></span> <span data-ttu-id="fee57-147">Si `True`, la clé privée peut être de nouveau exportée.</span><span class="sxs-lookup"><span data-stu-id="fee57-147">If `True`, the private key can be re-exported.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="fee57-148">Notes</span><span class="sxs-lookup"><span data-stu-id="fee57-148">Remarks</span></span>  
 <span data-ttu-id="fee57-149">L'utilitaire CertWizard importe une clé privée d'un fichier .pfx dans le magasin personnel, et importe une clé publique d'un fichier .cer dans un magasin public.</span><span class="sxs-lookup"><span data-stu-id="fee57-149">CertWizard imports a private key from a .pfx file into the personal store, and imports a public key from a .cer file into a public store.</span></span> <span data-ttu-id="fee57-150">Lors de l'importation d'une clé privée, le certificat peut être un certificat de déchiffrement pour les messages entrants, ou un certificat de signature pour les messages sortants.</span><span class="sxs-lookup"><span data-stu-id="fee57-150">When importing a private key, the certificate can be a decryption certificate for incoming messages or a signing certificate for outgoing messages.</span></span>  
  
 <span data-ttu-id="fee57-151">Si vous n'entrez pas l'intégralité de la commande dans l'invite, CertWizard vous invite à fournir les valeurs requises.</span><span class="sxs-lookup"><span data-stu-id="fee57-151">If you do not give the full command at the command prompt, CertWizard will prompt you to provide the required values.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fee57-152">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="fee57-152">See Also</span></span>  
 <span data-ttu-id="fee57-153">[Utilitaires](../../adapters-and-accelerators/accelerator-rosettanet/utilities1.md) </span><span class="sxs-lookup"><span data-stu-id="fee57-153">[Utilities](../../adapters-and-accelerators/accelerator-rosettanet/utilities1.md) </span></span>  
 [<span data-ttu-id="fee57-154">Importation de certificats à l’aide de l’utilitaire CertWizard</span><span class="sxs-lookup"><span data-stu-id="fee57-154">Importing Certificates Using the CertWizard Utility</span></span>](../../adapters-and-accelerators/accelerator-rosettanet/importing-certificates-using-the-certwizard-utility.md)