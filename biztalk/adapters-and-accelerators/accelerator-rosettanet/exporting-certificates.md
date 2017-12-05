---
title: Exportation de certificats | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- exporting certificates
- certificates, exporting
ms.assetid: edeeb300-19d6-44a8-b730-dcd15891cdf9
caps.latest.revision: "4"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 32dc7b0f73955c080f875eada2705300800df452
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="exporting-certificates"></a><span data-ttu-id="853ad-102">Exportation de certificats</span><span class="sxs-lookup"><span data-stu-id="853ad-102">Exporting Certificates</span></span>
<span data-ttu-id="853ad-103">Cette rubrique explique comment exporter un certificat à l'aide de l'Assistant Exportation du certificat.</span><span class="sxs-lookup"><span data-stu-id="853ad-103">This topic describes how to export a certificate by using the Certificate Export Wizard.</span></span> <span data-ttu-id="853ad-104">Utilisez cet Assistant pour exporter un certificat public ou un certificat privé.</span><span class="sxs-lookup"><span data-stu-id="853ad-104">Use this wizard to export either a public certificate or a private certificate.</span></span>  
  
### <a name="to-export-a-partner-certificate"></a><span data-ttu-id="853ad-105">Pour exporter un certificat de partenaire</span><span class="sxs-lookup"><span data-stu-id="853ad-105">To export a partner certificate</span></span>  
  
1.  <span data-ttu-id="853ad-106">Cliquez sur **Démarrer**, pointez sur **tous les programmes**, pointez sur **Microsoft** [!INCLUDE[btaBTARNNoVersionui](../../includes/btabtarnnoversionui-md.md)] puis cliquez sur [!INCLUDE[btaBTARNNoVersionui](../../includes/btabtarnnoversionui-md.md)] **Console de gestion**.</span><span class="sxs-lookup"><span data-stu-id="853ad-106">Click **Start**, point to **All Programs**, point to **Microsoft**[!INCLUDE[btaBTARNNoVersionui](../../includes/btabtarnnoversionui-md.md)] and then click [!INCLUDE[btaBTARNNoVersionui](../../includes/btabtarnnoversionui-md.md)] **Management Console**.</span></span>  
  
2.  <span data-ttu-id="853ad-107">Développez **Certificats (Ordinateur local)**, développez **Autres personnes**, puis cliquez sur **Certificats**.</span><span class="sxs-lookup"><span data-stu-id="853ad-107">Expand **Certificates (Local Computer)**, expand **Other People**, and then click **Certificates**.</span></span>  
  
3.  <span data-ttu-id="853ad-108">Dans le volet droit, cliquez avec le bouton droit sur le nom du certificat, pointez sur **Toutes les tâches**, puis cliquez sur **Exporter**.</span><span class="sxs-lookup"><span data-stu-id="853ad-108">In the right pane, right-click the name of the certificate, point to **All Tasks**, and then click **Export**.</span></span>  
  
4.  <span data-ttu-id="853ad-109">Dans la page **Bienvenue dans l'Assistant Exportation du certificat** , cliquez sur **Suivant**.</span><span class="sxs-lookup"><span data-stu-id="853ad-109">On the **Welcome to the Certificate Export Wizard** page, click **Next**.</span></span>  
  
5.  <span data-ttu-id="853ad-110">Dans la page **Format du fichier d'exportation** , sélectionnez le format à utiliser pour le fichier.</span><span class="sxs-lookup"><span data-stu-id="853ad-110">On the **Export File Format** page, select the format that you want to use for the file.</span></span> <span data-ttu-id="853ad-111">Il s'agit généralement du format x.509 binaire encodé DER pour exporter un fichier binaire, ou du format x.509 encodé Base 64 pour exporter un fichier Base 64.</span><span class="sxs-lookup"><span data-stu-id="853ad-111">This format is generally either DER encoded binary x.509 to export a binary-encoded file, or Base-64 encoded x.509 to export a Base-64 encoded file.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="853ad-112">L'encodage d'un certificat au format Base 64 vous permet d'utiliser le certificat sur un serveur UNIX.</span><span class="sxs-lookup"><span data-stu-id="853ad-112">Encoding a certificate in Base-64 lets you use the certificate on a UNIX server.</span></span>  
  
6.  <span data-ttu-id="853ad-113">Dans la page **Fichier à exporter** , cliquez sur **Parcourir**, recherchez l'emplacement de stockage du fichier, tapez le nom de ce dernier, cliquez sur **Suivant**, puis sur **Terminer**.</span><span class="sxs-lookup"><span data-stu-id="853ad-113">On the **File to Export** page, click **Browse**, locate where you want to store the file, type the name of the file, click **Next**, and then click **Finish**.</span></span>  
  
### <a name="to-export-the-home-organization-certificate"></a><span data-ttu-id="853ad-114">Pour exporter le certificat de l'organisation d'origine</span><span class="sxs-lookup"><span data-stu-id="853ad-114">To export the home organization certificate</span></span>  
  
1.  <span data-ttu-id="853ad-115">Cliquez sur **Démarrer**, cliquez sur **exécuter**, type **runas/user :\<héberger le service\> mmc**, où \< *hostservice*  \> est le nom du service que vous avez associé le service hôte lorsque vous avez installé [!INCLUDE[btsCoName](../../includes/btsconame-md.md)] [!INCLUDE[BTARN_CurrentVersion_FirstRef](../../includes/btarn-currentversion-firstref-md.md)], puis cliquez sur **OK** pour exécuter le [!INCLUDE[btsCoName](../../includes/btsconame-md.md)] gestion Console (MMC) dans le contexte du service hôte.</span><span class="sxs-lookup"><span data-stu-id="853ad-115">Click **Start**, click **Run**, type **runas /user:\<host service\> mmc**, where \<*hostservice*\> is the name of the service that you associated with the host service when you installed [!INCLUDE[btsCoName](../../includes/btsconame-md.md)][!INCLUDE[BTARN_CurrentVersion_FirstRef](../../includes/btarn-currentversion-firstref-md.md)], and then click **OK** to run the [!INCLUDE[btsCoName](../../includes/btsconame-md.md)] Management Console (MMC) in the context of the host service.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="853ad-116">Vous exécutez la commande **runas** pour emprunter l'identité du service hôte, ce qui est indispensable pour accéder au certificat de l'organisation d'origine.</span><span class="sxs-lookup"><span data-stu-id="853ad-116">You run the **runas** command to assume the identity of the host service, which is required to access the home-organization certificate.</span></span>  
  
2.  <span data-ttu-id="853ad-117">Développez **Certificats - Utilisateur actuel**, développez **Personnel**, puis cliquez sur **Certificats**.</span><span class="sxs-lookup"><span data-stu-id="853ad-117">Expand **Certificates - Current User**, expand **Personal**, and then click **Certificates**.</span></span>  
  
3.  <span data-ttu-id="853ad-118">Dans le volet droit, cliquez avec le bouton droit sur le nom du certificat, pointez sur **Toutes les tâches**, puis cliquez sur **Exporter**.</span><span class="sxs-lookup"><span data-stu-id="853ad-118">In the right pane, right-click the name of the certificate, point to **All Tasks**, and then click **Export**.</span></span>  
  
4.  <span data-ttu-id="853ad-119">Dans la page **Bienvenue dans l'Assistant Exportation du certificat** , cliquez sur **Suivant**.</span><span class="sxs-lookup"><span data-stu-id="853ad-119">On the **Welcome to the Certificate Export Wizard** page, click **Next**.</span></span>  
  
5.  <span data-ttu-id="853ad-120">Pour exporter la clé publique associée à la clé privée d'un certificat, laissez l'option **Non, ne pas exporter la clé privée** sélectionnée.</span><span class="sxs-lookup"><span data-stu-id="853ad-120">To export the public key associated with the private key of a certificate, leave **No, do not export the private key** selected.</span></span> <span data-ttu-id="853ad-121">Pour exporter la clé privée, sélectionnez **Oui, exporter la clé privée**.</span><span class="sxs-lookup"><span data-stu-id="853ad-121">To export the private key, select **Yes, export the private key**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="853ad-122">Si vous sélectionnez **Oui, exporter la clé privée**, il est fortement recommandé de ne pas envoyer le fichier résultant à un partenaire.</span><span class="sxs-lookup"><span data-stu-id="853ad-122">If you select **Yes, export the private key**, it is highly recommended that you do not send the resulting file to a partner.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="853ad-123">L'option **Oui, exporter la clé privée** n'est pas disponible si vous n'avez pas rendu la clé privée exportable quand vous l'avez importée au préalable.</span><span class="sxs-lookup"><span data-stu-id="853ad-123">The **Yes, export the private key** option will not be available if you did not make the private key exportable when you first imported it.</span></span>  
  
6.  <span data-ttu-id="853ad-124">Dans la page **Format du fichier d'exportation** , sélectionnez le format à utiliser pour le fichier.</span><span class="sxs-lookup"><span data-stu-id="853ad-124">On the **Export File Format** page, select the format that you want to use for the file.</span></span> <span data-ttu-id="853ad-125">Il s'agit généralement du format x.509 binaire encodé DER pour exporter un fichier binaire, ou du format x.509 encodé Base 64 pour exporter un fichier Base 64.</span><span class="sxs-lookup"><span data-stu-id="853ad-125">This format is generally either DER encoded binary x.509 to export a binary-encoded file, or Base-64 encoded x.509 to export a Base-64 encoded file.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="853ad-126">L'encodage d'un certificat au format Base 64 vous permet d'utiliser le certificat sur un serveur UNIX.</span><span class="sxs-lookup"><span data-stu-id="853ad-126">Encoding a certificate in Base-64 lets you use the certificate on a UNIX server.</span></span>  
  
7.  <span data-ttu-id="853ad-127">Dans la page **Fichier à exporter** , cliquez sur **Parcourir**, recherchez l'emplacement de stockage du fichier, tapez le nom de ce dernier, cliquez sur **Suivant**, puis sur **Terminer**.</span><span class="sxs-lookup"><span data-stu-id="853ad-127">On the **File to Export** page, click **Browse**, locate where you want to store the file, type the name of the file, click **Next**, and then click **Finish**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="853ad-128">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="853ad-128">See Also</span></span>  
 [<span data-ttu-id="853ad-129">Gestion des certificats</span><span class="sxs-lookup"><span data-stu-id="853ad-129">Managing Certificates</span></span>](../../adapters-and-accelerators/accelerator-rosettanet/managing-certificates1.md)