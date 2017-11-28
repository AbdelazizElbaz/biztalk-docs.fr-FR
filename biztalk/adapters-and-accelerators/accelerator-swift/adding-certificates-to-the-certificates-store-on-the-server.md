---
title: Ajout de certificats dans le magasin de certificats sur le serveur | Documents Microsoft
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
ms.assetid: 075cfae8-dce7-46f7-9539-796f03229ea2
caps.latest.revision: "4"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 94661568108e5a1cc05140a97c933fb8d00e3c67
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="adding-certificates-to-the-certificates-store-on-the-server"></a><span data-ttu-id="830a4-102">Ajout de certificats dans le magasin de certificats sur le serveur</span><span class="sxs-lookup"><span data-stu-id="830a4-102">Adding Certificates to the Certificates Store on the Server</span></span>
<span data-ttu-id="830a4-103">Utilisez les étapes suivantes pour ajouter des certificats dans le dossier d’autres personnes dans le magasin de certificats (ordinateur Local) sur l’ordinateur du serveur.</span><span class="sxs-lookup"><span data-stu-id="830a4-103">Use the following steps to add certificates to the Other People folder in the Certificates (Local Computer) store on the server computer.</span></span>  
  
### <a name="to-add-certificates-to-the-certificate-store"></a><span data-ttu-id="830a4-104">Pour ajouter des certificats au magasin de certificats</span><span class="sxs-lookup"><span data-stu-id="830a4-104">To add certificates to the certificate store</span></span>  
  
1.  <span data-ttu-id="830a4-105">Cliquez sur **Démarrer**, pointez sur **tous les programmes**, pointez sur **Microsoft BizTalk Accelerator pour SWIFT**, puis cliquez sur **BizTalk Accelerator pour SWIFT gestion Console**.</span><span class="sxs-lookup"><span data-stu-id="830a4-105">Click **Start**, point to **All Programs**, point to **Microsoft BizTalk Accelerator for SWIFT**, and then click **BizTalk Accelerator for SWIFT Management Console**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="830a4-106">Si la fenêtre MMC est toujours ouvert à partir de la procédure précédente (ajout de certificats dans le magasin de certificats sur le Client), vous pouvez l’utiliser pour cette procédure.</span><span class="sxs-lookup"><span data-stu-id="830a4-106">If you still have the MMC window open from the previous procedure (Adding Certificates to the Certificates Store on the Client), you can use it for this procedure.</span></span>  
  
2.  <span data-ttu-id="830a4-107">Dans la fenêtre de la Console d’Administration, développez le **certificats (ordinateur Local)** dossier, puis développez **autres personnes**.</span><span class="sxs-lookup"><span data-stu-id="830a4-107">In the Administration Console window, expand the **Certificates (Local Computer)** folder, and then expand **Other People**.</span></span>  
  
3.  <span data-ttu-id="830a4-108">Avec le bouton droit **certificats**, pointez sur **toutes les tâches**, puis cliquez sur **importation**.</span><span class="sxs-lookup"><span data-stu-id="830a4-108">Right-click **Certificates**, point to **All Tasks**, and then click **Import**.</span></span>  
  
4.  <span data-ttu-id="830a4-109">Dans la page d’accueil de l’Assistant Importation de certificat, cliquez sur **suivant**.</span><span class="sxs-lookup"><span data-stu-id="830a4-109">On the Welcome to the Certificate Import Wizard page, click **Next**.</span></span>  
  
5.  <span data-ttu-id="830a4-110">Dans la page fichier à importer, cliquez sur **Parcourir**.</span><span class="sxs-lookup"><span data-stu-id="830a4-110">On the File to Import page, click **Browse**.</span></span>  
  
6.  <span data-ttu-id="830a4-111">Dans la boîte de dialogue Ouvrir, déplacer vers l’emplacement du fichier où vous avez enregistré votre certificat, sélectionnez **tous les fichiers** pour **types de fichiers**, sélectionnez le certificat que vous souhaitez importer, puis cliquez sur  **Ouvrez**.</span><span class="sxs-lookup"><span data-stu-id="830a4-111">In the Open dialog box, move to the file location where you have saved your certificate, select **All Files** for **Files of Type**, select the certificate that you want to import, and then click **Open**.</span></span>  
  
7.  <span data-ttu-id="830a4-112">Dans la page fichier à importer, cliquez sur **suivant**.</span><span class="sxs-lookup"><span data-stu-id="830a4-112">On the File to Import page, click **Next**.</span></span>  
  
8.  <span data-ttu-id="830a4-113">Dans la page magasin de certificats, vérifiez que **placer tous les certificats dans le magasin suivant** est sélectionnée, vérifiez que **autres personnes** s’affiche dans le **le magasin de certificats**zone, puis cliquez sur **suivant**.</span><span class="sxs-lookup"><span data-stu-id="830a4-113">On the Certificate Store page, verify that **Place all certificates in the following store** is selected, verify that **Other People** is displayed in the **Certificate Store** box, and then click **Next**.</span></span>  
  
9. <span data-ttu-id="830a4-114">Sur la fin de la page de l’Assistant Importation de certificat, cliquez sur **Terminer**.</span><span class="sxs-lookup"><span data-stu-id="830a4-114">On the Completing the Certificate Import Wizard page, click **Finish**.</span></span>  
  
10. <span data-ttu-id="830a4-115">Dans la boîte de dialogue Assistant Importation de certificat indiquant une importation réussie, cliquez sur **OK**.</span><span class="sxs-lookup"><span data-stu-id="830a4-115">In the Certificate Import Wizard dialog box indicating a successful import, click **OK**.</span></span>  
  
11. <span data-ttu-id="830a4-116">Répétez les étapes 3 à 10 pour tous les autres certificats que vous allez utiliser dans le message repair et new submission.</span><span class="sxs-lookup"><span data-stu-id="830a4-116">Repeat steps 3 through 10 for all other certificates that you will use in message repair and new submission.</span></span>