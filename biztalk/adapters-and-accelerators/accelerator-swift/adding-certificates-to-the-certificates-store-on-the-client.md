---
title: Ajout de certificats dans le magasin de certificats sur le Client | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- certificates, adding to certificates store
- certificates store
ms.assetid: 9e2722ee-dd6f-4b14-9796-2f2157e8cad2
caps.latest.revision: "4"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 48a2e01fa60eccc8a6a0f06f4cf1f9fafb3f982b
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="adding-certificates-to-the-certificates-store-on-the-client"></a><span data-ttu-id="2e0d0-102">Ajout de certificats dans le magasin de certificats sur le Client</span><span class="sxs-lookup"><span data-stu-id="2e0d0-102">Adding Certificates to the Certificates Store on the Client</span></span>
<span data-ttu-id="2e0d0-103">Utilisez les étapes suivantes pour ajouter des certificats dans le dossier personnel dans le magasin de certificats sur chaque ordinateur client.</span><span class="sxs-lookup"><span data-stu-id="2e0d0-103">Use the following steps to add certificates to the Personal folder in the certificates store on each client computer.</span></span> <span data-ttu-id="2e0d0-104">Les certificats doivent être ajoutés dans le dossier personnel dans les certificats - magasin de l’utilisateur actuel.</span><span class="sxs-lookup"><span data-stu-id="2e0d0-104">The certificates must be added to the Personal folder in the Certificates - Current User store.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="2e0d0-105">Si vos certificats ne sont pas distribués via une entreprise approuvé l’autorité de Certification, vous devez importer le certificat racine de l’autorité de Certification sur l’ordinateur client.</span><span class="sxs-lookup"><span data-stu-id="2e0d0-105">If your certificates are not distributed via an enterprise trusted Certification Authority, you must import the Certification Authority's root certificate onto the client computer(s).</span></span> <span data-ttu-id="2e0d0-106">Dans le cas contraire, vos certificats personnels ne fonctionnera pas.</span><span class="sxs-lookup"><span data-stu-id="2e0d0-106">Otherwise, your personal certificates will not work.</span></span> <span data-ttu-id="2e0d0-107">Importez le certificat de l’autorité de Certification dans le dossier autorités de Certification racines de confiance dans le nœud certificats (ordinateur Local).</span><span class="sxs-lookup"><span data-stu-id="2e0d0-107">Import the Certification Authority's certificate into the Trusted Root Certification Authorities folder in the Certificates (Local Computer) node.</span></span>  
  
### <a name="to-add-certificates-to-the-certificate-store"></a><span data-ttu-id="2e0d0-108">Pour ajouter des certificats au magasin de certificats</span><span class="sxs-lookup"><span data-stu-id="2e0d0-108">To add certificates to the certificate store</span></span>  
  
1.  <span data-ttu-id="2e0d0-109">Cliquez sur **Démarrer**, puis sur **Exécuter**.</span><span class="sxs-lookup"><span data-stu-id="2e0d0-109">Click **Start**, and then click **Run**.</span></span> <span data-ttu-id="2e0d0-110">Entrez **mmc**, puis cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="2e0d0-110">Enter **mmc**, and then click **OK**.</span></span>  
  
2.  <span data-ttu-id="2e0d0-111">Dans la boîte de dialogue Console1, cliquez sur **fichier**, puis cliquez sur **ajouter/supprimer un composant logiciel enfichable**.</span><span class="sxs-lookup"><span data-stu-id="2e0d0-111">In the Console1 dialog box, click **File**, and then click **Add/Remove Snap-in**.</span></span>  
  
3.  <span data-ttu-id="2e0d0-112">Dans la boîte de dialogue Ajouter/supprimer un composant logiciel enfichable, cliquez sur **ajouter**.</span><span class="sxs-lookup"><span data-stu-id="2e0d0-112">In the Add/Remove Snap-in dialog box, click **Add**.</span></span>  
  
4.  <span data-ttu-id="2e0d0-113">Dans la boîte de dialogue Ajouter Standalone Snap-in, cliquez sur **certificats**, puis cliquez sur **ajouter**.</span><span class="sxs-lookup"><span data-stu-id="2e0d0-113">In the Add Standalone Snap-in dialog box, click **Certificates**, and then click **Add**.</span></span>  
  
5.  <span data-ttu-id="2e0d0-114">Dans la boîte de dialogue composant logiciel enfichable Certificats, cliquez sur **mon compte d’utilisateur**, puis cliquez sur **Terminer**.</span><span class="sxs-lookup"><span data-stu-id="2e0d0-114">In the Certificates snap-in dialog box, click **My user account**, and then click **Finish**.</span></span>  
  
6.  <span data-ttu-id="2e0d0-115">Dans la boîte de dialogue Ajouter Standalone Snap-in, cliquez sur **certificats**, puis cliquez sur **ajouter**.</span><span class="sxs-lookup"><span data-stu-id="2e0d0-115">In the Add Standalone Snap-in dialog box, click **Certificates**, and then click **Add**.</span></span>  
  
7.  <span data-ttu-id="2e0d0-116">Dans la boîte de dialogue composant logiciel enfichable Certificats, cliquez sur **compte d’ordinateur**, puis cliquez sur **suivant**.</span><span class="sxs-lookup"><span data-stu-id="2e0d0-116">In the Certificates snap-in dialog box, click **Computer account**, and then click **Next**.</span></span>  
  
8.  <span data-ttu-id="2e0d0-117">Dans la boîte de dialogue Sélectionner un ordinateur, assurez-vous que **ordinateur Local** est sélectionné, puis cliquez sur **Terminer**.</span><span class="sxs-lookup"><span data-stu-id="2e0d0-117">In the Select Computer dialog box, make sure **Local computer** is selected, and then click **Finish**.</span></span>  
  
9. <span data-ttu-id="2e0d0-118">Dans la boîte de dialogue Ajouter Standalone Snap-in, cliquez sur **fermer**.</span><span class="sxs-lookup"><span data-stu-id="2e0d0-118">In the Add Standalone Snap-in dialog box, click **Close**.</span></span>  
  
10. <span data-ttu-id="2e0d0-119">Dans la boîte de dialogue Ajouter/supprimer un composant logiciel enfichable, cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="2e0d0-119">In the Add/Remove Snap-in dialog box, click **OK**.</span></span>  
  
11. <span data-ttu-id="2e0d0-120">Dans le **racine de la Console** volet de la boîte de dialogue Console1, développez le **certificats - utilisateur actuel** dossiers.</span><span class="sxs-lookup"><span data-stu-id="2e0d0-120">In the **Console Root** pane of the Console1 dialog box, expand the **Certificates - Current User** folders.</span></span>  
  
12. <span data-ttu-id="2e0d0-121">Sous **certificats - utilisateur actuel**, développez **personnel**.</span><span class="sxs-lookup"><span data-stu-id="2e0d0-121">Under **Certificates - Current User**, expand **Personal**.</span></span>  
  
13. <span data-ttu-id="2e0d0-122">Avec le bouton droit **certificats**, pointez sur **toutes les tâches**, puis cliquez sur **importation**.</span><span class="sxs-lookup"><span data-stu-id="2e0d0-122">Right-click **Certificates**, point to **All Tasks**, and then click **Import**.</span></span>  
  
14. <span data-ttu-id="2e0d0-123">Dans la page d’accueil de l’Assistant Importation de certificat, cliquez sur **suivant**.</span><span class="sxs-lookup"><span data-stu-id="2e0d0-123">On the Welcome to the Certificate Import Wizard page, click **Next**.</span></span>  
  
15. <span data-ttu-id="2e0d0-124">Dans la page fichier à importer, cliquez sur **Parcourir**.</span><span class="sxs-lookup"><span data-stu-id="2e0d0-124">On the File to Import page, click **Browse**.</span></span>  
  
16. <span data-ttu-id="2e0d0-125">Dans la boîte de dialogue Ouvrir, déplacer vers l’emplacement du fichier où vous avez enregistré votre certificat, sélectionnez **tous les fichiers** pour **types de fichiers**, sélectionnez le certificat que vous souhaitez importer, puis cliquez sur  **Ouvrez**.</span><span class="sxs-lookup"><span data-stu-id="2e0d0-125">In the Open dialog box, move to the file location where you have saved your certificate, select **All Files** for **Files of Type**, select the certificate that you want to import, and then click **Open**.</span></span>  
  
17. <span data-ttu-id="2e0d0-126">Dans la page fichier à importer, cliquez sur **suivant**.</span><span class="sxs-lookup"><span data-stu-id="2e0d0-126">On the File to Import page, click **Next**.</span></span>  
  
18. <span data-ttu-id="2e0d0-127">Dans la page magasin de certificats, vérifiez que **placer tous les certificats dans le magasin suivant** est sélectionnée, vérifiez que **personnel** s’affiche dans le **magasin de certificats** zone, puis cliquez sur **suivant**.</span><span class="sxs-lookup"><span data-stu-id="2e0d0-127">On the Certificate Store page, verify that **Place all certificates in the following store** is selected, verify that **Personal** is displayed in the **Certificate Store** box, and then click **Next**.</span></span>  
  
19. <span data-ttu-id="2e0d0-128">Sur la fin de la page de l’Assistant Importation de certificat, cliquez sur **Terminer**.</span><span class="sxs-lookup"><span data-stu-id="2e0d0-128">On the Completing the Certificate Import Wizard page, click **Finish**.</span></span>  
  
20. <span data-ttu-id="2e0d0-129">Dans la boîte de dialogue Assistant Importation de certificat indiquant une importation réussie, cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="2e0d0-129">In the Certificate Import Wizard dialog box indicating a successful import, click **OK**.</span></span>  
  
21. <span data-ttu-id="2e0d0-130">Répétez les étapes 13 à 20 pour tous les autres certificats que vous allez utiliser dans le message repair et new submission.</span><span class="sxs-lookup"><span data-stu-id="2e0d0-130">Repeat steps 13 through 20 for all other certificates that you will use in message repair and new submission.</span></span>