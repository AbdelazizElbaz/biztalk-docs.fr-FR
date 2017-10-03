---
title: "Le certificat utilisé pour signer un message a été révoqué. | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f822235a-8ad8-4b63-94de-9b7f9361a071
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 8527f89d03d3250a7685380fcabf484254fbbf86
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="the-certificate-used-for-signing-a-message-has-been-revoked"></a><span data-ttu-id="5d634-102">Le certificat utilisé pour signer un message a été révoqué</span><span class="sxs-lookup"><span data-stu-id="5d634-102">The certificate used for signing a message has been revoked</span></span>
## <a name="details"></a><span data-ttu-id="5d634-103">Détails</span><span class="sxs-lookup"><span data-stu-id="5d634-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="5d634-104">Nom du produit</span><span class="sxs-lookup"><span data-stu-id="5d634-104">Product Name</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|<span data-ttu-id="5d634-105">Version du produit</span><span class="sxs-lookup"><span data-stu-id="5d634-105">Product Version</span></span>|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|<span data-ttu-id="5d634-106">ID d'événement</span><span class="sxs-lookup"><span data-stu-id="5d634-106">Event ID</span></span>|-|  
|<span data-ttu-id="5d634-107">Source de l'événement</span><span class="sxs-lookup"><span data-stu-id="5d634-107">Event Source</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="5d634-108"> EDI</span><span class="sxs-lookup"><span data-stu-id="5d634-108"> EDI</span></span>|  
|<span data-ttu-id="5d634-109">Composant</span><span class="sxs-lookup"><span data-stu-id="5d634-109">Component</span></span>|<span data-ttu-id="5d634-110">Moteur AS2</span><span class="sxs-lookup"><span data-stu-id="5d634-110">AS2 Engine</span></span>|  
|<span data-ttu-id="5d634-111">Nom symbolique</span><span class="sxs-lookup"><span data-stu-id="5d634-111">Symbolic Name</span></span>|<span data-ttu-id="5d634-112">SigningCertificateHasBeenRevokedError</span><span class="sxs-lookup"><span data-stu-id="5d634-112">SigningCertificateHasBeenRevokedError</span></span>|  
|<span data-ttu-id="5d634-113">Texte du message</span><span class="sxs-lookup"><span data-stu-id="5d634-113">Message Text</span></span>|<span data-ttu-id="5d634-114">Le certificat utilisé pour signer un message a été révoqué.</span><span class="sxs-lookup"><span data-stu-id="5d634-114">The certificate used for signing a message has been revoked.</span></span> <span data-ttu-id="5d634-115">Empreinte numérique du certificat : {0}</span><span class="sxs-lookup"><span data-stu-id="5d634-115">Certificate thumbprint: {0}</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="5d634-116">Explication</span><span class="sxs-lookup"><span data-stu-id="5d634-116">Explanation</span></span>  
 <span data-ttu-id="5d634-117">Cet événement d'erreur/d'avertissement/d'informations indique que le pipeline d'envoi n'a pas pu traiter le message sortant, car le certificat identifié comme étant le certificat de signature a été révoqué.</span><span class="sxs-lookup"><span data-stu-id="5d634-117">This Error/Warning/Information event indicates that the send pipeline could not process the outgoing message because the certificate identified as the signing certificate has been revoked.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="5d634-118">Action de l'utilisateur</span><span class="sxs-lookup"><span data-stu-id="5d634-118">User Action</span></span>  
 <span data-ttu-id="5d634-119">Pour résoudre cette erreur, effectuez l’une des opérations suivantes :</span><span class="sxs-lookup"><span data-stu-id="5d634-119">To resolve this error, do one of the following:</span></span>  
  
-   <span data-ttu-id="5d634-120">Créez un certificat pour remplacer le certificat révoqué.</span><span class="sxs-lookup"><span data-stu-id="5d634-120">Create a new certificate to replaced the revoked certificate.</span></span> <span data-ttu-id="5d634-121">Ajoutez-le au magasin de certificats Utilisateur actuel, identifiez-le en tant que certificat de signature dans la page Certificat de la boîte de dialogue Propriétés du groupe, puis envoyez la clé publique du certificat au destinataire du message AS2.</span><span class="sxs-lookup"><span data-stu-id="5d634-121">Add the certificate to the Current User certificate store, identify it as the signing certificate in the Certificate page of the Group Properties dialog box, and then send the public key of the certificate to the recipient of the AS2 message.</span></span>  
  
-   <span data-ttu-id="5d634-122">Désactivez la vérification de la liste de révocation. Pour ce faire, ouvrez la console Administration de BizTalk Server, ouvrez la boîte de dialogue Propriétés AS2 pour le tiers correspondant au message sortant, cliquez sur le nœud Général, puis désactivez la propriété Vérifier la liste de révocation des certificats.</span><span class="sxs-lookup"><span data-stu-id="5d634-122">Disable the revocation list check by opening the BizTalk Server Administration Console, opening the AS2 Properties dialog box for the party resolved for the outgoing message, clicking the General node, and then clearing the Check Certification Revocation List property.</span></span>