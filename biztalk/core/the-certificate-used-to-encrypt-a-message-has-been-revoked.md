---
title: "Le certificat utilisé pour chiffrer un message a été révoqué. | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 76c90690-002a-43bc-85f2-8aa5e7511ffa
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 4fbe34dcd2906d79a8d80ebdd00c3d9f293e6559
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="the-certificate-used-to-encrypt-a-message-has-been-revoked"></a><span data-ttu-id="6bed2-102">Le certificat utilisé pour chiffrer un message a été révoqué</span><span class="sxs-lookup"><span data-stu-id="6bed2-102">The certificate used to encrypt a message has been revoked</span></span>
## <a name="details"></a><span data-ttu-id="6bed2-103">Détails</span><span class="sxs-lookup"><span data-stu-id="6bed2-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="6bed2-104">Nom du produit</span><span class="sxs-lookup"><span data-stu-id="6bed2-104">Product Name</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|<span data-ttu-id="6bed2-105">Version du produit</span><span class="sxs-lookup"><span data-stu-id="6bed2-105">Product Version</span></span>|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|<span data-ttu-id="6bed2-106">ID d'événement</span><span class="sxs-lookup"><span data-stu-id="6bed2-106">Event ID</span></span>|-|  
|<span data-ttu-id="6bed2-107">Source de l'événement</span><span class="sxs-lookup"><span data-stu-id="6bed2-107">Event Source</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="6bed2-108"> EDI</span><span class="sxs-lookup"><span data-stu-id="6bed2-108"> EDI</span></span>|  
|<span data-ttu-id="6bed2-109">Composant</span><span class="sxs-lookup"><span data-stu-id="6bed2-109">Component</span></span>|<span data-ttu-id="6bed2-110">Moteur AS2</span><span class="sxs-lookup"><span data-stu-id="6bed2-110">AS2 Engine</span></span>|  
|<span data-ttu-id="6bed2-111">Nom symbolique</span><span class="sxs-lookup"><span data-stu-id="6bed2-111">Symbolic Name</span></span>|<span data-ttu-id="6bed2-112">EncryptionCertificateHasBeenRevokedError</span><span class="sxs-lookup"><span data-stu-id="6bed2-112">EncryptionCertificateHasBeenRevokedError</span></span>|  
|<span data-ttu-id="6bed2-113">Texte du message</span><span class="sxs-lookup"><span data-stu-id="6bed2-113">Message Text</span></span>|<span data-ttu-id="6bed2-114">Le certificat utilisé pour chiffrer un message a été révoqué.</span><span class="sxs-lookup"><span data-stu-id="6bed2-114">The certificate used to encrypt a message has been revoked.</span></span> <span data-ttu-id="6bed2-115">Empreinte numérique du certificat : {0}</span><span class="sxs-lookup"><span data-stu-id="6bed2-115">Certificate thumbprint: {0}</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="6bed2-116">Explication</span><span class="sxs-lookup"><span data-stu-id="6bed2-116">Explanation</span></span>  
 <span data-ttu-id="6bed2-117">Cet événement d'erreur/d'avertissement/d'informations indique que le pipeline d'envoi n'a pas pu traiter le message sortant, car le certificat identifié comme étant le certificat de chiffrement a été révoqué.</span><span class="sxs-lookup"><span data-stu-id="6bed2-117">This Error/Warning/Information event indicates that the send pipeline could not process the outgoing message because the certificate identified as the encryption certificate has been revoked.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="6bed2-118">Action de l'utilisateur</span><span class="sxs-lookup"><span data-stu-id="6bed2-118">User Action</span></span>  
 <span data-ttu-id="6bed2-119">Pour résoudre cette erreur, effectuez l’une des opérations suivantes :</span><span class="sxs-lookup"><span data-stu-id="6bed2-119">To resolve this error, do one of the following:</span></span>  
  
-   <span data-ttu-id="6bed2-120">Demandez au récepteur du message de créer un certificat et de vous envoyer la clé publique.</span><span class="sxs-lookup"><span data-stu-id="6bed2-120">Have the receiver of the message create a new certificate and send the public key to you.</span></span> <span data-ttu-id="6bed2-121">Ajoutez le certificat dans le magasin de certificats Ordinateur local\Autres personnes, puis, dans la boîte de dialogue Propriétés de port d'envoi, dans la page Certificat, identifiez-le comme étant le certificat de chiffrement.</span><span class="sxs-lookup"><span data-stu-id="6bed2-121">Add the certificate to the Local computer\Other People certificate store, and then identify the certificate as the encryption certificate in the Certificate page of the Send Port Properties dialog box.</span></span>  
  
-   <span data-ttu-id="6bed2-122">Désactivez la vérification de la liste de révocation. Pour ce faire, ouvrez la console Administration de BizTalk Server, ouvrez la boîte de dialogue Propriétés AS2 pour le tiers correspondant au message sortant, cliquez sur le nœud Général, puis désactivez la propriété Vérifier la liste de révocation des certificats.</span><span class="sxs-lookup"><span data-stu-id="6bed2-122">Disable the revocation list check by opening the BizTalk Server Administration Console, opening the AS2 Properties dialog box for the party resolved for the outgoing message, clicking the General node, and then clearing the Check Certification Revocation List property.</span></span>