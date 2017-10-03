---
title: "Étape 3 : Importation publics et privés certificats | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- public certificates
- importing certificates
- private certificates
- double action tutorial, importing certificates
- certificates, importing
ms.assetid: 955bdd69-9fbc-4100-ab8a-8f5dd4a17cbb
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: c910a72f3e5ef39bb2e07e410f484e8c5cbececa
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="step-3-importing-public-and-private-certificates"></a><span data-ttu-id="378f6-102">Étape 3 : Importation publiques et privées des certificats</span><span class="sxs-lookup"><span data-stu-id="378f6-102">Step 3: Importing Public and Private Certificates</span></span>
<span data-ttu-id="378f6-103">Dans cette étape, vous importez les certificats que vous avez créé dans [étape 2 : création d’un Public et privé certificats &#91; RN3 &#93; ](../../adapters-and-accelerators/accelerator-rosettanet/step-2-creating-public-and-private-certificates.md) sur les ordinateurs de Contoso et Fabrikam.</span><span class="sxs-lookup"><span data-stu-id="378f6-103">In this step, you import the certificates you created in [Step 2: Creating Public and Private Certificates &#91;RN3&#93;](../../adapters-and-accelerators/accelerator-rosettanet/step-2-creating-public-and-private-certificates.md) to the Contoso and Fabrikam computers.</span></span> <span data-ttu-id="378f6-104">Chaque ordinateur importe ses propres certificats privés et importe les certificats publics de l’autre organisation.</span><span class="sxs-lookup"><span data-stu-id="378f6-104">Each computer imports its own private certificates and imports the public certificates of the other organization.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="378f6-105">Vous devez transférer les certificats privés de Fabrikam et les certificats publics de Contoso à l’ordinateur Fabrikam pour les importer.</span><span class="sxs-lookup"><span data-stu-id="378f6-105">You have to transfer the Fabrikam private certificates and Contoso public certificates to the Fabrikam computer to import them.</span></span> <span data-ttu-id="378f6-106">Cette étape suppose que vous placez ces certificats dans le dossier C:\Certs sur l’ordinateur Fabrikam.</span><span class="sxs-lookup"><span data-stu-id="378f6-106">This step assumes that you put these certificates in the C:\Certs folder on the Fabrikam computer.</span></span>  
  
### <a name="to-import-the-contoso-private-certificates-on-the-contoso-computer"></a><span data-ttu-id="378f6-107">Pour importer les certificats privés Contoso sur l’ordinateur Contoso</span><span class="sxs-lookup"><span data-stu-id="378f6-107">To import the Contoso private certificates on the Contoso computer</span></span>  
  
1.  <span data-ttu-id="378f6-108">Sur l’ordinateur Contoso, cliquez sur **Démarrer**, cliquez sur **exécuter**, type **cmd**, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="378f6-108">On the Contoso computer, click **Start**, click **Run**, type **cmd**, and then click **OK**.</span></span>  
  
2.  <span data-ttu-id="378f6-109">À l’invite de commandes, accédez au  **\<**  *lecteur***> : \Program Files\Microsoft BizTalk \<version > Accelerator for RosettaNet\SDK** puis appuyez sur **entrée**.</span><span class="sxs-lookup"><span data-stu-id="378f6-109">At the command prompt, move to **\<***drive***>:\Program Files\Microsoft BizTalk \<version> Accelerator for RosettaNet\SDK** and then press **Enter**.</span></span>  
  
3.  <span data-ttu-id="378f6-110">À l’invite de commandes, tapez **CertWizard /Privatekey »\<***lecteur***> : \Certs\Contoso privé Encryption.pfx «**, puis appuyez sur  **Entrez**.</span><span class="sxs-lookup"><span data-stu-id="378f6-110">At the command prompt, type **CertWizard /Privatekey "\<***drive***>:\Certs\Contoso Private Encryption.pfx"**, and then press **Enter**.</span></span>  
  
4.  <span data-ttu-id="378f6-111">À la **Veuillez entrer le mot de passe pour le fichier de certificat** tapez **mysecret**, puis appuyez sur **entrée**.</span><span class="sxs-lookup"><span data-stu-id="378f6-111">At the **Please enter the password for the certificate file** prompt, type **mysecret**, and then press **Enter**.</span></span>  
  
5.  <span data-ttu-id="378f6-112">À la **Entrez le mot de passe pour l’identité < contoso_machine > \HostSvc** invite, tapez le mot de passe du compte HostSvc, puis appuyez sur **entrée**.</span><span class="sxs-lookup"><span data-stu-id="378f6-112">At the **Enter password for identity <contoso_machine>\HostSvc** prompt, type the HostSvc account password, and then press **Enter**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="378f6-113">Si votre BizTalkServerApplication s’exécute sous un nom de compte différent de HostSvc, l’invite doit être différent.</span><span class="sxs-lookup"><span data-stu-id="378f6-113">If your BizTalkServerApplication runs under an account name other than HostSvc, the prompt must be different.</span></span>  
  
6.  <span data-ttu-id="378f6-114">À la **ce certificat accueil sera utilisé pour** tapez **D**, puis appuyez sur **entrée**.</span><span class="sxs-lookup"><span data-stu-id="378f6-114">At the **This home certificate will be used for** prompt, type **D**, and then press **Enter**.</span></span>  
  
     <span data-ttu-id="378f6-115">Le CertWizard importe le certificat dans le magasin de \Personal\Certificates pour hôtes BizTalkServerApplication et BizTalkServerIsolatedHost s’exécutent sous les comptes d’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="378f6-115">The CertWizard imports the certificate into the \Personal\Certificates store for the user accounts that BizTalkServerApplication and BizTalkServerIsolatedHost hosts run under.</span></span>  
  
7.  <span data-ttu-id="378f6-116">Répétez les étapes 3 à 6 pour le certificat privé de Contoso Signature.pfx spécifiant qu’il est un certificat de signature en tapant **S** à la **ce certificat accueil sera utilisé pour** invite indiqué à l’étape 6.</span><span class="sxs-lookup"><span data-stu-id="378f6-116">Repeat steps 3-6 for the Contoso Private Signature.pfx certificate specifying that it is a signature certificate by typing **S** at the **This home certificate will be used for** prompt noted in step 6.</span></span>  
  
### <a name="to-import-the-fabrikam-public-certificates-on-the-contoso-computer"></a><span data-ttu-id="378f6-117">Pour importer les certificats publics Fabrikam sur l’ordinateur Contoso</span><span class="sxs-lookup"><span data-stu-id="378f6-117">To import the Fabrikam public certificates on the Contoso computer</span></span>  
  
1.  <span data-ttu-id="378f6-118">Sur l’ordinateur Contoso, cliquez sur **Démarrer**, cliquez sur **exécuter,** type **cmd**, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="378f6-118">On the Contoso computer, click **Start**, click **Run,** type **cmd**, and then click **OK**.</span></span>  
  
2.  <span data-ttu-id="378f6-119">À l’invite de commandes, accédez au  *\<lecteur >***: \Program Files\Microsoft BizTalk \<version > Accelerator for RosettaNet\SDK** , puis appuyez sur **entrée** .</span><span class="sxs-lookup"><span data-stu-id="378f6-119">At the command prompt, move to *\<drive>***:\Program Files\Microsoft BizTalk \<version> Accelerator for RosettaNet\SDK** and then press **Enter**.</span></span>  
  
3.  <span data-ttu-id="378f6-120">À l’invite de commandes, tapez **/PublicKey de CertWizard «***\<lecteur >***: \Certs\Fabrikam Encryption.cer publique «**, puis appuyez sur  **Entrez**.</span><span class="sxs-lookup"><span data-stu-id="378f6-120">At the command prompt, type **CertWizard /Publickey "***\<drive>***:\Certs\Fabrikam Public Encryption.cer"**, and then press **Enter**.</span></span>  
  
4.  <span data-ttu-id="378f6-121">Répétez l’étape 3 pour le certificat Signature.cer Public de Fabrikam.</span><span class="sxs-lookup"><span data-stu-id="378f6-121">Repeat step 3 for the Fabrikam Public Signature.cer certificate.</span></span>  
  
### <a name="to-import-the-fabrikam-private-certificates-on-the-fabrikam-computer"></a><span data-ttu-id="378f6-122">Pour importer les certificats privés Fabrikam sur l’ordinateur Fabrikam</span><span class="sxs-lookup"><span data-stu-id="378f6-122">To import the Fabrikam private certificates on the Fabrikam computer</span></span>  
  
1.  <span data-ttu-id="378f6-123">Copiez les fichiers suivants à partir de l’ordinateur Contoso à la \<lecteur > : dossier \Certs sur l’ordinateur Fabrikam : Encryption.cer publics de Contoso, Signature.cer publics de Contoso, Encryption.pfx privé de Fabrikam et Fabrikam privé Signature.pfx.</span><span class="sxs-lookup"><span data-stu-id="378f6-123">Copy the following files from the Contoso computer to the \<drive>:\Certs folder on the Fabrikam computer: Contoso Public Encryption.cer, Contoso Public Signature.cer, Fabrikam Private Encryption.pfx, and Fabrikam Private Signature.pfx.</span></span>  
  
2.  <span data-ttu-id="378f6-124">Sur l’ordinateur Fabrikum, cliquez sur **Démarrer**, cliquez sur **exécuter**, type **cmd**, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="378f6-124">On the Fabrikum computer, click **Start**, click **Run**, type **cmd**, and then click **OK**.</span></span>  
  
3.  <span data-ttu-id="378f6-125">À l’invite de commandes, accédez au  *\<lecteur >***: \Program Files\Microsoft BizTalk \<version > Accelerator for RosettaNet\SDK** , puis appuyez sur **entrée** .</span><span class="sxs-lookup"><span data-stu-id="378f6-125">At the command prompt, move to *\<drive>***:\Program Files\Microsoft BizTalk \<version> Accelerator for RosettaNet\SDK** and then press **Enter**.</span></span>  
  
4.  <span data-ttu-id="378f6-126">À l’invite de commandes, tapez **CertWizard /Privatekey »***\<lecteur >***: \Certs\Fabrikam privé Encryption.pfx «**, puis appuyez sur **Entrez**.</span><span class="sxs-lookup"><span data-stu-id="378f6-126">At the command prompt, type **CertWizard /Privatekey "***\<drive>***:\Certs\Fabrikam Private Encryption.pfx"**, and then press **Enter**.</span></span>  
  
5.  <span data-ttu-id="378f6-127">À la **Veuillez entrer le mot de passe pour le fichier de certificat** tapez **mysecret**, puis appuyez sur **entrée**.</span><span class="sxs-lookup"><span data-stu-id="378f6-127">At the **Please enter the password for the certificate file** prompt, type **mysecret**, and then press **Enter**.</span></span>  
  
6.  <span data-ttu-id="378f6-128">À la **Entrez le mot de passe pour l’identité < fabrikam_machine > \HostSvc** invite, tapez le mot de passe du compte HostSvc, puis appuyez sur **entrée**.</span><span class="sxs-lookup"><span data-stu-id="378f6-128">At the **Enter password for identity <fabrikam_machine>\HostSvc** prompt, type the HostSvc account password, and then press **Enter**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="378f6-129">Si votre BizTalkServerApplication s’exécute sous un nom de compte différent de HostSvc, l’invite doit être différent.</span><span class="sxs-lookup"><span data-stu-id="378f6-129">If your BizTalkServerApplication runs under an account name other than HostSvc, the prompt must be different.</span></span>  
  
7.  <span data-ttu-id="378f6-130">À la **ce certificat accueil sera utilisé pour** tapez **D**, puis appuyez sur **entrée**.</span><span class="sxs-lookup"><span data-stu-id="378f6-130">At the **This home certificate will be used for** prompt, type **D**, and then press **Enter**.</span></span>  
  
     <span data-ttu-id="378f6-131">Le CertWizard importe le certificat dans le magasin de \Personal\Certificates pour hôtes BizTalkServerApplication et BizTalkServerIsolatedHost s’exécutent sous les comptes d’utilisateur.</span><span class="sxs-lookup"><span data-stu-id="378f6-131">The CertWizard imports the certificate into the \Personal\Certificates store for the user accounts that BizTalkServerApplication and BizTalkServerIsolatedHost hosts run under.</span></span>  
  
8.  <span data-ttu-id="378f6-132">Répétez les étapes 4 à 7 pour le certificat privé de Fabrikam Signature.pfx spécifiant qu’il est un certificat de signature en tapant **S** à la **ce certificat accueil sera utilisé pour** invite de commandes à l’étape 6.</span><span class="sxs-lookup"><span data-stu-id="378f6-132">Repeat steps 4-7 for the Fabrikam Private Signature.pfx certificate specifying that it is a signature certificate by typing **S** at the **This home certificate will be used for** prompt in step 6.</span></span>  
  
### <a name="to-import-the-contoso-public-certificates-on-the-fabrikam-computer"></a><span data-ttu-id="378f6-133">Pour importer les certificats publics Contoso sur l’ordinateur Fabrikam</span><span class="sxs-lookup"><span data-stu-id="378f6-133">To import the Contoso public certificates on the Fabrikam computer</span></span>  
  
1.  <span data-ttu-id="378f6-134">Sur l’ordinateur Fabrikum, cliquez sur **Démarrer**, cliquez sur **exécuter**, type **cmd**, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="378f6-134">On the Fabrikum computer, click **Start**, click **Run**, type **cmd**, and then click **OK**.</span></span>  
  
2.  <span data-ttu-id="378f6-135">À l’invite de commandes, accédez au  *\<lecteur >***: \Program Files\Microsoft BizTalk \<version > Accelerator for RosettaNet\SDK** , puis appuyez sur **entrée** .</span><span class="sxs-lookup"><span data-stu-id="378f6-135">At the command prompt, move to *\<drive>***:\Program Files\Microsoft BizTalk \<version> Accelerator for RosettaNet\SDK** and then press **Enter**.</span></span>  
  
3.  <span data-ttu-id="378f6-136">À l’invite de commandes, tapez **/PublicKey de CertWizard «***\<lecteur >***: \Certs\Contoso Encryption.cer publique «**, puis appuyez sur  **Entrez**.</span><span class="sxs-lookup"><span data-stu-id="378f6-136">At the command prompt, type **CertWizard /Publickey "***\<drive>***:\Certs\Contoso Public Encryption.cer"**, and then press **Enter**.</span></span>  
  
4.  <span data-ttu-id="378f6-137">Répétez l’étape 3 pour le certificat Signature.cer publics de Contoso.</span><span class="sxs-lookup"><span data-stu-id="378f6-137">Repeat step 3 for the Contoso Public Signature.cer certificate.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="378f6-138">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="378f6-138">See Also</span></span>  
 [<span data-ttu-id="378f6-139">Étape 4 : Sécurisé Sockets Layer dans IIS</span><span class="sxs-lookup"><span data-stu-id="378f6-139">Step 4: Enabling Secure Sockets Layer in IIS</span></span>](../../adapters-and-accelerators/accelerator-rosettanet/step-4-enabling-secure-sockets-layer-in-iis.md)