---
title: "Échec de création de X509CertificateIdentity à partir du certificat codé en base 64 | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a13112bd-e0e8-4b49-ad2f-ea82b2e8162f
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 31cf07660b939beb3ea1a79fd0f34390f873d5cb
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="failed-to-create-x509certificateidentity-from-base-64-encoded-certificate"></a><span data-ttu-id="05194-102">Échec de création de X509CertificateIdentity à partir du certificat codé en base-64</span><span class="sxs-lookup"><span data-stu-id="05194-102">Failed to create X509CertificateIdentity from base-64 encoded certificate</span></span>
## <a name="details"></a><span data-ttu-id="05194-103">Détails</span><span class="sxs-lookup"><span data-stu-id="05194-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="05194-104">Nom du produit</span><span class="sxs-lookup"><span data-stu-id="05194-104">Product Name</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|<span data-ttu-id="05194-105">Version du produit</span><span class="sxs-lookup"><span data-stu-id="05194-105">Product Version</span></span>|[!INCLUDE[btsWCFVersion](../includes/btswcfversion-md.md)]|  
|<span data-ttu-id="05194-106">ID d'événement</span><span class="sxs-lookup"><span data-stu-id="05194-106">Event ID</span></span>|<span data-ttu-id="05194-107">0</span><span class="sxs-lookup"><span data-stu-id="05194-107">0</span></span>|  
|<span data-ttu-id="05194-108">Source de l'événement</span><span class="sxs-lookup"><span data-stu-id="05194-108">Event Source</span></span>|<span data-ttu-id="05194-109">0</span><span class="sxs-lookup"><span data-stu-id="05194-109">0</span></span>|  
|<span data-ttu-id="05194-110">Composant</span><span class="sxs-lookup"><span data-stu-id="05194-110">Component</span></span>|<span data-ttu-id="05194-111">0</span><span class="sxs-lookup"><span data-stu-id="05194-111">0</span></span>|  
|<span data-ttu-id="05194-112">Nom symbolique</span><span class="sxs-lookup"><span data-stu-id="05194-112">Symbolic Name</span></span>|<span data-ttu-id="05194-113">0</span><span class="sxs-lookup"><span data-stu-id="05194-113">0</span></span>|  
|<span data-ttu-id="05194-114">Texte du message</span><span class="sxs-lookup"><span data-stu-id="05194-114">Message Text</span></span>|<span data-ttu-id="05194-115">Échec de création de X509CertificateIdentity à partir du certificat codé en base-64</span><span class="sxs-lookup"><span data-stu-id="05194-115">Failed to create X509CertificateIdentity from base-64 encoded certificate</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="05194-116">Explication</span><span class="sxs-lookup"><span data-stu-id="05194-116">Explanation</span></span>  
 <span data-ttu-id="05194-117">Cette erreur indique que l'adaptateur n'a pas pu créer l'identité du point de terminaison X509Certificate en raison d'un paramètre de certificat non valide.</span><span class="sxs-lookup"><span data-stu-id="05194-117">This error indicates the adapter failed to create the X509Certificate endpoint identity because of an invalid certificate setting.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="05194-118">Action de l'utilisateur</span><span class="sxs-lookup"><span data-stu-id="05194-118">User Action</span></span>  
 <span data-ttu-id="05194-119">La procédure suivante permet de configurer des certificats.</span><span class="sxs-lookup"><span data-stu-id="05194-119">Use the following procedure to configure certificates.</span></span>  
  
#### <a name="to-configure-certificates"></a><span data-ttu-id="05194-120">Pour configurer des certificats</span><span class="sxs-lookup"><span data-stu-id="05194-120">To configure certificates</span></span>  
  
1.  <span data-ttu-id="05194-121">Cliquez sur **Démarrer**, cliquez sur **tous les programmes**, cliquez sur [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], puis cliquez sur **Administration de BizTalk Server**.</span><span class="sxs-lookup"><span data-stu-id="05194-121">Click **Start**, click **All Programs**, click [!INCLUDE[btsBizTalkServerStartMenuItemui](../includes/btsbiztalkserverstartmenuitemui-md.md)], and click **BizTalk Server Administration**.</span></span>  
  
2.  <span data-ttu-id="05194-122">Dans la racine de la Console, développez [!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)], développez **groupe BizTalk**, développez **Applications**.</span><span class="sxs-lookup"><span data-stu-id="05194-122">In the Console Root, expand [!INCLUDE[btsBizTalkServerAdminConsoleui](../includes/btsbiztalkserveradminconsoleui-md.md)], expand **BizTalk Group**, and expand  **Applications**.</span></span>  
  
3.  <span data-ttu-id="05194-123">Recherchez votre application, puis recherchez votre transport.</span><span class="sxs-lookup"><span data-stu-id="05194-123">Locate your application and then locate your transport.</span></span>  
  
4.  <span data-ttu-id="05194-124">Cliquez avec le bouton droit sur le nom du transport.</span><span class="sxs-lookup"><span data-stu-id="05194-124">Right-click the transport name.</span></span>  
  
5.  <span data-ttu-id="05194-125">Cliquez sur **Propriétés**.</span><span class="sxs-lookup"><span data-stu-id="05194-125">Click **Properties**.</span></span>  
  
6.  <span data-ttu-id="05194-126">Dans le port **Type** , sélectionnez le port approprié.</span><span class="sxs-lookup"><span data-stu-id="05194-126">In the port **Type** list, select the correct port.</span></span>  
  
7.  <span data-ttu-id="05194-127">Cliquez sur **configurer**.</span><span class="sxs-lookup"><span data-stu-id="05194-127">Click **Configure**.</span></span>  
  
8.  <span data-ttu-id="05194-128">Dans le **WCF [***type de transport***] propriétés du Transport** boîte de dialogue, cliquez sur le **sécurité** onglet.</span><span class="sxs-lookup"><span data-stu-id="05194-128">In the **WCF [***transport type***] Transport Properties** dialog box, click the **Security** tab.</span></span>  
  
9. <span data-ttu-id="05194-129">Vérifiez que les paramètres sont corrects pour le **empreinte de certificat Client** et **l’empreinte numérique du certificat de Service**.</span><span class="sxs-lookup"><span data-stu-id="05194-129">Ensure that the settings are correct for the **Client Certificate Thumbprint** and the **Service Certificate Thumbprint**.</span></span>