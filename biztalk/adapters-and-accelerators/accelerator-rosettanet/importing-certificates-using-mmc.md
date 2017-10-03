---
title: "L’importation de certificats à l’aide de MMC | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- certificates, public keys
- certificates, private keys
- importing certificates
- public keys
- private keys
- certificates, importing
ms.assetid: 58fb1711-e295-4aa6-902e-e28e4a2cd921
caps.latest.revision: "4"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 6030b711e0fd48d2632ff84428e1cb9ffc6e0402
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="importing-certificates-using-mmc"></a><span data-ttu-id="dd039-102">L’importation de certificats à l’aide de MMC</span><span class="sxs-lookup"><span data-stu-id="dd039-102">Importing Certificates Using MMC</span></span>
<span data-ttu-id="dd039-103">Cette rubrique décrit comment importer un numérique de certificat qui [!INCLUDE[btsCoName](../../includes/btsconame-md.md)] [!INCLUDE[BTARN_CurrentVersion_FirstRef](../../includes/btarn-currentversion-firstref-md.md)] utilise pour authentifier un partenaire commercial, déchiffrer un message entrant, ou chiffrer ou signer un message sortant.</span><span class="sxs-lookup"><span data-stu-id="dd039-103">This topic describes how to import a digital certificate that [!INCLUDE[btsCoName](../../includes/btsconame-md.md)][!INCLUDE[BTARN_CurrentVersion_FirstRef](../../includes/btarn-currentversion-firstref-md.md)] uses to authenticate a trading partner, decrypt an incoming message, or encrypt or sign an outgoing message.</span></span>  
  
 <span data-ttu-id="dd039-104">Cette procédure utilise le composant logiciel enfichable Certificats pour le [!INCLUDE[btsCoName](../../includes/btsconame-md.md)] Management Console (MMC).</span><span class="sxs-lookup"><span data-stu-id="dd039-104">This procedure uses the Certificates snap-in for the [!INCLUDE[btsCoName](../../includes/btsconame-md.md)] Management Console (MMC).</span></span> <span data-ttu-id="dd039-105">Ce processus manuel importe un certificat dans le magasin de certificats que vous ayez besoin de configurer séparément les utilisation de certificats.</span><span class="sxs-lookup"><span data-stu-id="dd039-105">This manual process imports a certificate into the certificate store, requiring you to configure certificate use separately.</span></span> <span data-ttu-id="dd039-106">Vous pouvez également importer un certificat à l’aide de l’utilitaire CertWizard qui configure automatiquement le certificat utilisé pour vous.</span><span class="sxs-lookup"><span data-stu-id="dd039-106">You can also import a certificate by using the CertWizard utility that automatically configures certificate use for you.</span></span>  
  
 <span data-ttu-id="dd039-107">Pour importer les certificats privés, vous devez utiliser les comptes d’utilisateur sous lequel exécuter les hôtes BizTalk.</span><span class="sxs-lookup"><span data-stu-id="dd039-107">To import private certificates, you must use the user accounts under which the BizTalk Hosts run.</span></span>  
  
### <a name="to-import-a-public-key-certificate"></a><span data-ttu-id="dd039-108">Pour importer un certificat de clé publique</span><span class="sxs-lookup"><span data-stu-id="dd039-108">To import a public-key certificate</span></span>  
  
1.  <span data-ttu-id="dd039-109">Copie le certificat de clé publique (.cer) du fichier vers un emplacement sur le disque dur du serveur sur lequel vous copiez des certificats.</span><span class="sxs-lookup"><span data-stu-id="dd039-109">Copy the public-key (.cer) certificate file to a location on the hard disk of the server to which you are copying certificates.</span></span>  
  
2.  <span data-ttu-id="dd039-110">Cliquez sur **Démarrer**, pointez sur **tous les programmes**, pointez sur **Microsoft** [!INCLUDE[btaBTARNNoVersionui](../../includes/btabtarnnoversionui-md.md)], puis cliquez sur [!INCLUDE[btaBTARNNoVersionui](../../includes/btabtarnnoversionui-md.md)] **Console de gestion**.</span><span class="sxs-lookup"><span data-stu-id="dd039-110">Click **Start**, point to **All Programs**, point to **Microsoft** [!INCLUDE[btaBTARNNoVersionui](../../includes/btabtarnnoversionui-md.md)], and then click [!INCLUDE[btaBTARNNoVersionui](../../includes/btabtarnnoversionui-md.md)] **Management Console**.</span></span>  
  
3.  <span data-ttu-id="dd039-111">Dans le [!INCLUDE[btaBTARNNoVersion](../../includes/btabtarnnoversion-md.md)] Management Console, développez **certificats (ordinateur Local)**.</span><span class="sxs-lookup"><span data-stu-id="dd039-111">In the [!INCLUDE[btaBTARNNoVersion](../../includes/btabtarnnoversion-md.md)] Management Console, expand **Certificates (Local Computer)**.</span></span> <span data-ttu-id="dd039-112">L’utilisateur connecté doit disposer d’autorisations administratives sur l’ordinateur.</span><span class="sxs-lookup"><span data-stu-id="dd039-112">The logged-in user must have administrative permissions to the computer.</span></span>  
  
4.  <span data-ttu-id="dd039-113">Avec le bouton droit **autres personnes**, pointez sur **toutes les tâches**, puis cliquez sur **importation**.</span><span class="sxs-lookup"><span data-stu-id="dd039-113">Right-click **Other People**, point to **All Tasks**, and then click **Import**.</span></span>  
  
5.  <span data-ttu-id="dd039-114">Sur le **certificat Assistant Importation de** , cliquez sur **suivant**.</span><span class="sxs-lookup"><span data-stu-id="dd039-114">On the **Certificate Import Wizard Welcome** page, click **Next**.</span></span>  
  
6.  <span data-ttu-id="dd039-115">Sur le **fichier à importer** , cliquez sur **Parcourir** et recherchez le dossier qui contienne les fichiers de certificat.</span><span class="sxs-lookup"><span data-stu-id="dd039-115">On the **File to Import** page, click **Browse** and locate the folder that contains the certificate files.</span></span> <span data-ttu-id="dd039-116">Sélectionnez le fichier à partir de laquelle vous souhaitez importer le certificat, puis cliquez sur **ouvrir**.</span><span class="sxs-lookup"><span data-stu-id="dd039-116">Select the file from which you want to import the certificate, and then click **Open**.</span></span>  
  
7.  <span data-ttu-id="dd039-117">Sur le **magasin de certificats** page, sélectionnez **sélectionner automatiquement le certificat basé sur le type de certificat** ou **placer tous les certificats dans le magasin suivant**.</span><span class="sxs-lookup"><span data-stu-id="dd039-117">On the **Certificate store** page, select either **Automatically select the certificate based on the type of certificate** or **Place all certificates in the following store**.</span></span> <span data-ttu-id="dd039-118">Si vous sélectionnez **placer tous les certificats dans le magasin suivant**, cliquez sur **Parcourir**, sélectionnez le magasin de certificats, cliquez sur **OK**, puis cliquez sur **suivant**.</span><span class="sxs-lookup"><span data-stu-id="dd039-118">If you select **Place all certificates in the following store**, click **Browse**, select the certificate store, click **OK**, and then click **Next**.</span></span>  
  
8.  <span data-ttu-id="dd039-119">Cliquez sur **Terminer**.</span><span class="sxs-lookup"><span data-stu-id="dd039-119">Click **Finish**.</span></span>  
  
### <a name="to-import-a-private-key-certificate"></a><span data-ttu-id="dd039-120">Pour importer un certificat de clé privée</span><span class="sxs-lookup"><span data-stu-id="dd039-120">To import a private-key certificate</span></span>  
  
1.  <span data-ttu-id="dd039-121">Certificat de clé privée (.pfx) copie les fichiers vers un emplacement sur le disque dur du serveur sur lequel vous copiez des certificats.</span><span class="sxs-lookup"><span data-stu-id="dd039-121">Copy private-key (.pfx) certificate files to a location on the hard disk of the server to which you are copying certificates.</span></span>  
  
2.  <span data-ttu-id="dd039-122">Cliquez sur **Démarrer**, cliquez sur **exécuter**, type **d’identification/User :\<hôte de service > mmc**, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="dd039-122">Click **Start**, click **Run**, type **run as /user:\<host service> mmc**, and then click **OK**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="dd039-123">Pour \< *héberger le service*>, tapez le nom du service qui a été automatiquement sélectionné pour le service hôte lors de l’installation [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)].</span><span class="sxs-lookup"><span data-stu-id="dd039-123">For \<*host service*>, type the name of the service that was automatically selected for the host service when you installed [!INCLUDE[btaBTARN3.3abbrevnonumber](../../includes/btabtarn3-3abbrevnonumber-md.md)].</span></span>  
  
3.  <span data-ttu-id="dd039-124">Tapez le mot de passe \< *héberger le service*>, puis appuyez sur **entrée**.</span><span class="sxs-lookup"><span data-stu-id="dd039-124">Type the password for \<*host service*>, and then press **Enter**.</span></span>  
  
4.  <span data-ttu-id="dd039-125">Dans [!INCLUDE[btsCoName](../../includes/btsconame-md.md)] gestion de la Console, sous le **fichier** menu, cliquez sur **ajouter/supprimer un composant logiciel enfichable**.</span><span class="sxs-lookup"><span data-stu-id="dd039-125">In [!INCLUDE[btsCoName](../../includes/btsconame-md.md)] Management Console, on the **File** menu, click **Add/Remove Snap-in**.</span></span>  
  
5.  <span data-ttu-id="dd039-126">Dans la boîte de dialogue Ajouter/supprimer un composant logiciel enfichable, cliquez sur **ajouter**.</span><span class="sxs-lookup"><span data-stu-id="dd039-126">In the Add/Remove Snap-in dialog box, click **Add**.</span></span>  
  
6.  <span data-ttu-id="dd039-127">Dans la boîte de dialogue Ajouter Standalone Snap-in, sélectionnez **certificats**, cliquez sur **ajouter**, cliquez sur **fermer**, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="dd039-127">In the Add Standalone Snap-in dialog box, select **Certificates**, click **Add**, click **Close**, and then click **OK**.</span></span>  
  
7.  <span data-ttu-id="dd039-128">Dans [!INCLUDE[btsCoName](../../includes/btsconame-md.md)] Management Console, développez **certificats - utilisateur actuel**, avec le bouton droit **personnel**, pointez sur **toutes les tâches**, puis cliquez sur  **Importation**.</span><span class="sxs-lookup"><span data-stu-id="dd039-128">In [!INCLUDE[btsCoName](../../includes/btsconame-md.md)] Management Console, expand **Certificates - Current User**, right-click **Personal**, point to **All Tasks**, and then click **Import**.</span></span>  
  
8.  <span data-ttu-id="dd039-129">Sur le **certificat Assistant Importation de** , cliquez sur **suivant**.</span><span class="sxs-lookup"><span data-stu-id="dd039-129">On the **Certificate Import Wizard Welcome** page, click **Next**.</span></span>  
  
9. <span data-ttu-id="dd039-130">Sur le **fichier à importer** , cliquez sur **Parcourir** et recherchez le dossier qui contient le fichier de certificat .pfx qui contient le certificat que vous souhaitez importer.</span><span class="sxs-lookup"><span data-stu-id="dd039-130">On the **File to Import** page, click **Browse** and locate the folder that contains the .pfx certificate file that contains the certificate that you want to import.</span></span> <span data-ttu-id="dd039-131">Sélectionnez le fichier approprié, puis cliquez sur **ouvrir**.</span><span class="sxs-lookup"><span data-stu-id="dd039-131">Select the appropriate file, and then click **Open**.</span></span>  
  
10. <span data-ttu-id="dd039-132">Sur le **mot de passe** page, dans le **mot de passe** , tapez le mot de passe pour le fichier de clé privée.</span><span class="sxs-lookup"><span data-stu-id="dd039-132">On the **Password** page, in the **Password** box, type the password for the private-key file.</span></span>  
  
11. <span data-ttu-id="dd039-133">Sélectionnez **activer la protection renforcée par clé privée** ou **marquer cette clé comme exportable**, puis cliquez sur **suivant**.</span><span class="sxs-lookup"><span data-stu-id="dd039-133">Select **Enable strong private key protection** or **Mark this key as exportable**, and then click **Next**.</span></span>  
  
12. <span data-ttu-id="dd039-134">Sur le **magasin de certificats** page, sélectionnez **sélectionner automatiquement le certificat basé sur le type de certificat** ou **placer tous les certificats dans le magasin suivant**.</span><span class="sxs-lookup"><span data-stu-id="dd039-134">On the **Certificate store** page, select either **Automatically select the certificate based on the type of certificate** or **Place all certificates in the following store**.</span></span> <span data-ttu-id="dd039-135">Si vous sélectionnez **placer tous les certificats dans le magasin suivant**, cliquez sur **Parcourir**, sélectionnez le magasin, cliquez sur **OK**, puis cliquez sur **suivant**.</span><span class="sxs-lookup"><span data-stu-id="dd039-135">If you select **Place all certificates in the following store**, click **Browse**, select the store, click **OK**, and then click **Next**.</span></span>  
  
13. <span data-ttu-id="dd039-136">Sur le **fin de l’Assistant Importation de certificat** , cliquez sur **Terminer**.</span><span class="sxs-lookup"><span data-stu-id="dd039-136">On the **Completing the Certificate Import Wizard** page, click **Finish**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dd039-137">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="dd039-137">See Also</span></span>  
 <span data-ttu-id="dd039-138">[Configuration des certificats importés à l’aide de MMC](../../adapters-and-accelerators/accelerator-rosettanet/configuring-certificates-imported-using-mmc.md) </span><span class="sxs-lookup"><span data-stu-id="dd039-138">[Configuring Certificates Imported Using MMC](../../adapters-and-accelerators/accelerator-rosettanet/configuring-certificates-imported-using-mmc.md) </span></span>  
 [<span data-ttu-id="dd039-139">CertWizard</span><span class="sxs-lookup"><span data-stu-id="dd039-139">CertWizard</span></span>](../../adapters-and-accelerators/accelerator-rosettanet/certwizard.md)