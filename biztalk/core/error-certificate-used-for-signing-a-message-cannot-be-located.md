---
title: "Impossible de trouver le certificat utilisé pour signer un message dans le magasin de certificats local | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 2ff3c7a2-954c-4c62-a7b2-06f7a38d61b3
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: d94049a0ecca4e7aec89c5163231c0b9bf4c9e3e
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="the-certificate-used-for-signing-a-message-cannot-be-located-in-the-local-certificate-store"></a><span data-ttu-id="21c60-102">Le certificat utilisé pour la signature d'un message ne peut pas être localisé dans le magasin de certificats local.</span><span class="sxs-lookup"><span data-stu-id="21c60-102">The certificate used for signing a message cannot be located in the local certificate store</span></span>
## <a name="details"></a><span data-ttu-id="21c60-103">Détails</span><span class="sxs-lookup"><span data-stu-id="21c60-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="21c60-104">Nom du produit</span><span class="sxs-lookup"><span data-stu-id="21c60-104">Product Name</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|<span data-ttu-id="21c60-105">Version du produit</span><span class="sxs-lookup"><span data-stu-id="21c60-105">Product Version</span></span>|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|<span data-ttu-id="21c60-106">ID d'événement</span><span class="sxs-lookup"><span data-stu-id="21c60-106">Event ID</span></span>|-|  
|<span data-ttu-id="21c60-107">Source de l'événement</span><span class="sxs-lookup"><span data-stu-id="21c60-107">Event Source</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="21c60-108"> EDI</span><span class="sxs-lookup"><span data-stu-id="21c60-108"> EDI</span></span>|  
|<span data-ttu-id="21c60-109">Composant</span><span class="sxs-lookup"><span data-stu-id="21c60-109">Component</span></span>|<span data-ttu-id="21c60-110">Moteur AS2</span><span class="sxs-lookup"><span data-stu-id="21c60-110">AS2 Engine</span></span>|  
|<span data-ttu-id="21c60-111">Nom symbolique</span><span class="sxs-lookup"><span data-stu-id="21c60-111">Symbolic Name</span></span>|<span data-ttu-id="21c60-112">CertificateMissingError</span><span class="sxs-lookup"><span data-stu-id="21c60-112">CertificateMissingError</span></span>|  
|<span data-ttu-id="21c60-113">Texte du message</span><span class="sxs-lookup"><span data-stu-id="21c60-113">Message Text</span></span>|<span data-ttu-id="21c60-114">Impossible de trouver le certificat utilisé pour signer un message dans le magasin de certificats local.</span><span class="sxs-lookup"><span data-stu-id="21c60-114">The certificate used for signing a message cannot be located in the local certificate store.</span></span> <span data-ttu-id="21c60-115">Empreinte numérique du certificat : {0}</span><span class="sxs-lookup"><span data-stu-id="21c60-115">Certificate thumbprint: {0}</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="21c60-116">Explication</span><span class="sxs-lookup"><span data-stu-id="21c60-116">Explanation</span></span>  
 <span data-ttu-id="21c60-117">Cet événement de type erreur/avertissement/information indique que le pipeline d'envoi n'a pas pu traiter le message sortant, car le certificat identifié comme le certificat de signature ne se trouvait pas dans le magasin de certificats requis.</span><span class="sxs-lookup"><span data-stu-id="21c60-117">This Error/Warning/Information event indicates that the send pipeline could not process the outgoing message because the certificate identified as the signing certificate was not in the required certificate store.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="21c60-118">Action de l'utilisateur</span><span class="sxs-lookup"><span data-stu-id="21c60-118">User Action</span></span>  
 <span data-ttu-id="21c60-119">Pour résoudre cette erreur, procédez comme suit :</span><span class="sxs-lookup"><span data-stu-id="21c60-119">To resolve this error, do the following:</span></span>  
  
1.  <span data-ttu-id="21c60-120">Identifiez le certificat de signature en ouvrant la console Administration BizTalk Server, en cliquant avec le bouton droit de la souris sur Groupe BizTalk, puis en cliquant sur le nœud Certificat.</span><span class="sxs-lookup"><span data-stu-id="21c60-120">Identify the signing certificate by opening the BizTalk Server Administration Console, right-clicking the BizTalk Group, and then clicking the Certificate node.</span></span>  
  
2.  <span data-ttu-id="21c60-121">Ouvrez MMC, ajoutez le composant logiciel enfichable pour Mon compte d'utilisateur, puis ouvrez les nœuds Certificats et Personnel.</span><span class="sxs-lookup"><span data-stu-id="21c60-121">Open MMC, add the snap-in for the My user account, and then open the Certificates, Personal, and Certificates node.</span></span>  
  
3.  <span data-ttu-id="21c60-122">Assurez-vous que le magasin de certificats Utilisateur actuel contient la clé privée correspondant à ce certificat de signature en recherchant l'empreinte identifiée dans le texte du message d'erreur.</span><span class="sxs-lookup"><span data-stu-id="21c60-122">Make sure that the Current User certificate store contains the private key for that signing certificate by looking for the thumbprint identified in the error message text.</span></span>