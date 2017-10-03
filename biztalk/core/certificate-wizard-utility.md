---
title: Assistant utilitaire de certificat | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 5ff72810-c7b3-4f67-8f9f-e127eacc153e
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 8e3acbb1198034e76bb1e0f45c0f9755ec6ac95d
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="certificate-wizard-utility"></a><span data-ttu-id="7f94b-102">Utilitaire de l'Assistant Certificat</span><span class="sxs-lookup"><span data-stu-id="7f94b-102">Certificate Wizard Utility</span></span>
<span data-ttu-id="7f94b-103">L'utilitaire CertWizard permet d'importer un certificat d'un fichier .pfx ou .cer dans un magasin privé ou public pour l'utiliser avec Microsoft [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="7f94b-103">You use the CertWizard utility to import a certificate from a .pfx or .cer file into a private or public store for use with Microsoft [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].</span></span>  
  
 <span data-ttu-id="7f94b-104">Vous trouverez le code source pour l’Assistant de certificat dans le **C:\Program Files\Microsoft BizTalk Server \<version > \SDK\Utilities\Certificate Assistant** dossier.</span><span class="sxs-lookup"><span data-stu-id="7f94b-104">The source code for the Certificate Wizard can be found in the **C:\Program Files\Microsoft BizTalk Server \<version>\SDK\Utilities\Certificate Wizard** folder.</span></span> <span data-ttu-id="7f94b-105">Avec un système d’exploitation 64 bits et une version de [!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)], doivent être dans le **(x86) de C:\Program Files \Microsoft BizTalk Server \<version > \SDK\Utilities\Certificate Assistant** dossier.</span><span class="sxs-lookup"><span data-stu-id="7f94b-105">With a 64-bit operating system and version of [!INCLUDE[btsBizTalkServer2006r3](../includes/btsbiztalkserver2006r3-md.md)], it will be in the **C:\Program Files (x86)\Microsoft BizTalk Server \<version>\SDK\Utilities\Certificate Wizard** folder.</span></span> <span data-ttu-id="7f94b-106">Pour utiliser l'Assistant Certificat, vous devez commencer par le créer à l'aide de [!INCLUDE[vs2010](../includes/vs2010-md.md)].</span><span class="sxs-lookup"><span data-stu-id="7f94b-106">To use the Certificate Wizard you will first have to build it using [!INCLUDE[vs2010](../includes/vs2010-md.md)].</span></span>  
  
 <span data-ttu-id="7f94b-107">L'utilitaire CertWizard importe une clé privée d'un fichier .pfx dans le magasin personnel, et importe une clé publique d'un fichier .cer dans un magasin public.</span><span class="sxs-lookup"><span data-stu-id="7f94b-107">CertWizard imports a private key from a .pfx file into the personal store, and imports a public key from a .cer file into a public store.</span></span> <span data-ttu-id="7f94b-108">Lors de l'importation d'une clé privée, le certificat peut être un certificat de déchiffrement pour les messages entrants, ou un certificat de signature pour les messages sortants.</span><span class="sxs-lookup"><span data-stu-id="7f94b-108">When importing a private key, the certificate can be a decryption certificate for incoming messages or a signing certificate for outgoing messages.</span></span>  
  
 <span data-ttu-id="7f94b-109">**Description de la syntaxe**</span><span class="sxs-lookup"><span data-stu-id="7f94b-109">**Syntax Description**</span></span>  
  
 <span data-ttu-id="7f94b-110">Le tableau suivant décrit les éléments de la syntaxe utilisée par l'utilitaire CertWizard.</span><span class="sxs-lookup"><span data-stu-id="7f94b-110">The following table describes each part of the syntax that the CertWizard utility uses.</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="7f94b-111">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="7f94b-111">Syntax</span></span>|<span data-ttu-id="7f94b-112"> Description</span><span class="sxs-lookup"><span data-stu-id="7f94b-112">Description</span></span>|  
|<span data-ttu-id="7f94b-113">Privatekey</span><span class="sxs-lookup"><span data-stu-id="7f94b-113">Privatekey</span></span>|<span data-ttu-id="7f94b-114">Utilisée pour importer une clé privée.</span><span class="sxs-lookup"><span data-stu-id="7f94b-114">Used to import a private key.</span></span>|  
|<span data-ttu-id="7f94b-115">Publickey</span><span class="sxs-lookup"><span data-stu-id="7f94b-115">Publickey</span></span>|<span data-ttu-id="7f94b-116">Utilisée pour importer une clé publique.</span><span class="sxs-lookup"><span data-stu-id="7f94b-116">Used to import a public key.</span></span>|  
|<span data-ttu-id="7f94b-117">Rootkey</span><span class="sxs-lookup"><span data-stu-id="7f94b-117">Rootkey</span></span>|<span data-ttu-id="7f94b-118">Utilisée pour importer une clé racine (d’une autorité de certification).</span><span class="sxs-lookup"><span data-stu-id="7f94b-118">Used to import a root key—from a certification authority.</span></span>|  
|<span data-ttu-id="7f94b-119">nom_fichier.pfx (ou .cer)</span><span class="sxs-lookup"><span data-stu-id="7f94b-119">filename.pfx (or .cer)</span></span>|<span data-ttu-id="7f94b-120">Chemin d'accès complet du fichier .pfx (clés privées) ou .cer (clés publiques).</span><span class="sxs-lookup"><span data-stu-id="7f94b-120">Full path for the .pfx (private keys) or .cer (public keys) file.</span></span>|  
|<span data-ttu-id="7f94b-121">Filepassword</span><span class="sxs-lookup"><span data-stu-id="7f94b-121">Filepassword</span></span>|<span data-ttu-id="7f94b-122">Mot de passe requis pour déverrouiller le fichier .pfx.</span><span class="sxs-lookup"><span data-stu-id="7f94b-122">The password required to unlock the .pfx file.</span></span>|  
|<span data-ttu-id="7f94b-123">Useridentity</span><span class="sxs-lookup"><span data-stu-id="7f94b-123">Useridentity</span></span>|<span data-ttu-id="7f94b-124">Identité de service utilisée par un ou plusieurs hôtes BizTalk.</span><span class="sxs-lookup"><span data-stu-id="7f94b-124">A service identity that one or more BizTalk Hosts uses.</span></span> <span data-ttu-id="7f94b-125">Entrez un compte d'utilisateur si vous ne souhaitez pas spécifier l'hôte mais importer un certificat sous un compte d'utilisateur.</span><span class="sxs-lookup"><span data-stu-id="7f94b-125">Enter a user account if you do not want to specify the host, but want to import a certificate under a user account.</span></span> <span data-ttu-id="7f94b-126">**Remarque :** si vous n’ajoutez pas le commutateur Useridentity, l’utilitaire importe et définir le certificat pour tous les utilisateurs.</span><span class="sxs-lookup"><span data-stu-id="7f94b-126">**Note:**  If you do not add the Useridentity switch, the utility imports and set the certificate for all users.</span></span> <span data-ttu-id="7f94b-127">**Remarque :** si vous ajoutez le commutateur Useridentity, mais que vous n’entrez pas de valeur, WMI génère automatiquement l’identité de l’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="7f94b-127">**Note:**  If you add the Useridentity switch, but do not enter a value, WMI automatically generates the user identity.</span></span>|  
|<span data-ttu-id="7f94b-128">Mot de passe</span><span class="sxs-lookup"><span data-stu-id="7f94b-128">Password</span></span>|<span data-ttu-id="7f94b-129">Mot de passe de l'utilisateur de l'identité du service.</span><span class="sxs-lookup"><span data-stu-id="7f94b-129">The password for the service identity user.</span></span>|  
|<span data-ttu-id="7f94b-130">Thumbprint</span><span class="sxs-lookup"><span data-stu-id="7f94b-130">Thumbprint</span></span>|<span data-ttu-id="7f94b-131">Empreinte d'un certificat spécifique, au cas où le fichier contient plusieurs certificats.</span><span class="sxs-lookup"><span data-stu-id="7f94b-131">The thumbprint of a specific certificate, in case the file contains more than one certificate.</span></span> <span data-ttu-id="7f94b-132">**Remarque :** pour un fichier de certificat public, si le fichier contient plusieurs certificats et que vous ne spécifiez pas l’empreinte numérique, l’utilitaire importe tous les certificats dans le fichier.</span><span class="sxs-lookup"><span data-stu-id="7f94b-132">**Note:**  For a public certificate file, if the file contains more than one certificate and you do not specify the thumbprint, the utility imports all certificates in the file.</span></span> <span data-ttu-id="7f94b-133">Dans le cas d'un fichier de certificat privé, l'utilitaire vous invite à sélectionner le certificat à importer.</span><span class="sxs-lookup"><span data-stu-id="7f94b-133">For a private certificate file, the utility prompts you to select the certificate to import.</span></span>|  
|<span data-ttu-id="7f94b-134">Utilisation</span><span class="sxs-lookup"><span data-stu-id="7f94b-134">Usage</span></span>|<span data-ttu-id="7f94b-135">Utilisation prévue du certificat privé importé.</span><span class="sxs-lookup"><span data-stu-id="7f94b-135">The intended usage of the imported private certificate.</span></span> <span data-ttu-id="7f94b-136">Les valeurs possibles sont les suivantes :</span><span class="sxs-lookup"><span data-stu-id="7f94b-136">Can be one of the following:</span></span><br /><br /> <span data-ttu-id="7f94b-137">**signe** (pour un certificat de signature)</span><span class="sxs-lookup"><span data-stu-id="7f94b-137">**sign** (for a signing certificate)</span></span><br /><br /> <span data-ttu-id="7f94b-138">**déchiffrer** (pour un certificat de déchiffrement)</span><span class="sxs-lookup"><span data-stu-id="7f94b-138">**decrypt** (for a decryption certificate)</span></span><br /><br /> <span data-ttu-id="7f94b-139">**les deux** (pour un certificat est un certificat de signature et un certificat de déchiffrement)</span><span class="sxs-lookup"><span data-stu-id="7f94b-139">**both** (for a certificate that is both a signing certificate and a decryption certificate)</span></span><br /><br /> <span data-ttu-id="7f94b-140">**aucun** (également pour un certificat qui est un certificat de signature et un certificat de déchiffrement).</span><span class="sxs-lookup"><span data-stu-id="7f94b-140">**none** (also for a certificate that is both a signing certificate and a decryption certificate).</span></span> <span data-ttu-id="7f94b-141">**Remarque :** si vous définissez le commutateur /Usage sur None, l’Assistant ne définit pas l’empreinte numérique du certificat sur les hôtes BizTalk ou le groupe BizTalk.</span><span class="sxs-lookup"><span data-stu-id="7f94b-141">**Note:**  If you set the /Usage switch to none, the wizard will not set the thumbprint for the certificate on the BizTalk Hosts or the BizTalk Group.</span></span>|  
|<span data-ttu-id="7f94b-142">Exportable</span><span class="sxs-lookup"><span data-stu-id="7f94b-142">Exportable</span></span>|<span data-ttu-id="7f94b-143">Peut être **True** ou **False**.</span><span class="sxs-lookup"><span data-stu-id="7f94b-143">Can be **True** or **False**.</span></span> <span data-ttu-id="7f94b-144">Si **True**, la clé privée peut être de nouveau exportée.</span><span class="sxs-lookup"><span data-stu-id="7f94b-144">If **True**, the private key can be re-exported.</span></span>|  
  
 <span data-ttu-id="7f94b-145">**Syntaxe pour l’importation d’une clé privée**</span><span class="sxs-lookup"><span data-stu-id="7f94b-145">**Syntax for Importing a Private Key**</span></span>  
  
```  
CertWizard /Privatekey <filename>.pfx [/Filepassword <filepassword>] [/Useridentity <useridentity>] [/Password <password>] [/Thumbprint <thumbprint>] [/Usage sign|decrypt|both|none] [/Exportable true|false]  
```  
  
 <span data-ttu-id="7f94b-146">**Syntaxe pour l’importation d’une clé publique**</span><span class="sxs-lookup"><span data-stu-id="7f94b-146">**Syntax for Importing a Public Key**</span></span>  
  
```  
CertWizard /Publickey <filename>.cer [/Thumbprint <thumbprint>]  
```  
  
 <span data-ttu-id="7f94b-147">**Syntaxe pour l’importation d’une clé racine**</span><span class="sxs-lookup"><span data-stu-id="7f94b-147">**Syntax for Importing a Root Key**</span></span>  
  
```  
CertWizard /Rootkey <filename>.cer [/Thumbprint <thumbprint>]  
```  
  
## <a name="prerequisites"></a><span data-ttu-id="7f94b-148">Conditions préalables</span><span class="sxs-lookup"><span data-stu-id="7f94b-148">Prerequisites</span></span>  
 <span data-ttu-id="7f94b-149">La configuration suivante est requise pour exécuter les procédures décrites dans cette rubrique :</span><span class="sxs-lookup"><span data-stu-id="7f94b-149">The following are prerequisites for performing the procedures in this topic:</span></span>  
  
-   <span data-ttu-id="7f94b-150">Vous devez ouvrir une session en tant que membre du groupe Administrateurs [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="7f94b-150">You must be logged on as a member of the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administrators group.</span></span>  
  
### <a name="to-run-the-certificate-wizard"></a><span data-ttu-id="7f94b-151">Pour exécuter l'Assistant Certificat</span><span class="sxs-lookup"><span data-stu-id="7f94b-151">To run the certificate wizard</span></span>  
  
1.  <span data-ttu-id="7f94b-152">Ouvrez une invite de commandes.</span><span class="sxs-lookup"><span data-stu-id="7f94b-152">Open a command prompt.</span></span>  
  
2.  <span data-ttu-id="7f94b-153">Accédez à [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]SDK\Utilities.</span><span class="sxs-lookup"><span data-stu-id="7f94b-153">Move to [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]SDK\Utilities.</span></span>  
  
3.  <span data-ttu-id="7f94b-154">À l’invite de commandes, tapez **CertWizard**, tapez les interrupteurs requis, puis appuyez sur **entrée**.</span><span class="sxs-lookup"><span data-stu-id="7f94b-154">At the command prompt, type **CertWizard**, type the required and appropriate switches, and then press **Enter**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="7f94b-155">Si vous n'entrez pas l'intégralité de la commande dans l'invite, CertWizard vous invite à fournir les valeurs requises.</span><span class="sxs-lookup"><span data-stu-id="7f94b-155">If you do not give the full command at the command prompt, CertWizard will prompt you to provide the required values.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7f94b-156">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="7f94b-156">See Also</span></span>  
 [<span data-ttu-id="7f94b-157">Utilitaires dans le Kit de développement</span><span class="sxs-lookup"><span data-stu-id="7f94b-157">Utilities in the SDK</span></span>](../core/utilities-in-the-sdk.md)