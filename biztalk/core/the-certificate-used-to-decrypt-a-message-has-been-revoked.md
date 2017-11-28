---
title: "Le certificat utilisé pour déchiffrer un message a été révoqué. | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 01767cb2-b16e-4b4b-ac4d-cd79b6c8860a
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 7cd9404f13f737b4cb82317193344e006979d333
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="the-certificate-used-to-decrypt-a-message-has-been-revoked"></a><span data-ttu-id="5bb32-102">Le certificat utilisé pour déchiffrer un message a été révoqué.</span><span class="sxs-lookup"><span data-stu-id="5bb32-102">The certificate used to decrypt a message has been revoked</span></span>
## <a name="details"></a><span data-ttu-id="5bb32-103">Détails</span><span class="sxs-lookup"><span data-stu-id="5bb32-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="5bb32-104">Nom du produit</span><span class="sxs-lookup"><span data-stu-id="5bb32-104">Product Name</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|<span data-ttu-id="5bb32-105">Version du produit</span><span class="sxs-lookup"><span data-stu-id="5bb32-105">Product Version</span></span>|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|<span data-ttu-id="5bb32-106">ID d'événement</span><span class="sxs-lookup"><span data-stu-id="5bb32-106">Event ID</span></span>|-|  
|<span data-ttu-id="5bb32-107">Source de l'événement</span><span class="sxs-lookup"><span data-stu-id="5bb32-107">Event Source</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="5bb32-108"> EDI</span><span class="sxs-lookup"><span data-stu-id="5bb32-108"> EDI</span></span>|  
|<span data-ttu-id="5bb32-109">Composant</span><span class="sxs-lookup"><span data-stu-id="5bb32-109">Component</span></span>|<span data-ttu-id="5bb32-110">Moteur AS2</span><span class="sxs-lookup"><span data-stu-id="5bb32-110">AS2 Engine</span></span>|  
|<span data-ttu-id="5bb32-111">Nom symbolique</span><span class="sxs-lookup"><span data-stu-id="5bb32-111">Symbolic Name</span></span>|<span data-ttu-id="5bb32-112">DecryptionCertificateHasBeenRevokedError</span><span class="sxs-lookup"><span data-stu-id="5bb32-112">DecryptionCertificateHasBeenRevokedError</span></span>|  
|<span data-ttu-id="5bb32-113">Texte du message</span><span class="sxs-lookup"><span data-stu-id="5bb32-113">Message Text</span></span>|<span data-ttu-id="5bb32-114">Le certificat utilisé pour déchiffrer un message a été révoqué.</span><span class="sxs-lookup"><span data-stu-id="5bb32-114">The certificate used to decrypt a message has been revoked.</span></span> <span data-ttu-id="5bb32-115">Empreinte numérique du certificat : {0}</span><span class="sxs-lookup"><span data-stu-id="5bb32-115">Certificate thumbprint: {0}</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="5bb32-116">Explication</span><span class="sxs-lookup"><span data-stu-id="5bb32-116">Explanation</span></span>  
 <span data-ttu-id="5bb32-117">Cet événement de type erreur/avertissement/information indique que le pipeline de réception n'a pas pu traiter le message entrant, car le certificat à utiliser pour le déchiffrer a été révoqué.</span><span class="sxs-lookup"><span data-stu-id="5bb32-117">This Error/Warning/Information event indicates that the receive pipeline could not process the incoming message because the certificate to be used to decrypt the message has been revoked.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="5bb32-118">Action de l'utilisateur</span><span class="sxs-lookup"><span data-stu-id="5bb32-118">User Action</span></span>  
 <span data-ttu-id="5bb32-119">Pour résoudre cette erreur, effectuez l’une des opérations suivantes :</span><span class="sxs-lookup"><span data-stu-id="5bb32-119">To resolve this error, do one of the following:</span></span>  
  
-   <span data-ttu-id="5bb32-120">Créer un certificat pour remplacer le certificat révoqué.</span><span class="sxs-lookup"><span data-stu-id="5bb32-120">Create a new certificate to replace the revoked certificate.</span></span> <span data-ttu-id="5bb32-121">Ajouter le certificat au magasin de certificats Utilisateur actuel/Personnel et envoyer la clé publique du certificat à l'émetteur du message AS2.</span><span class="sxs-lookup"><span data-stu-id="5bb32-121">Add the certificate to the Current User/Personal certificate store, and then send the public key of the certificate to the sending of the AS2 message.</span></span>  
  
-   <span data-ttu-id="5bb32-122">Désactivez la vérification de la liste de révocation. Pour ce faire, ouvrez la console Administration de BizTalk Server, ouvrez la boîte de dialogue Propriétés AS2 pour le tiers correspondant au message sortant, cliquez sur le nœud Général, puis désactivez la propriété Vérifier la liste de révocation des certificats.</span><span class="sxs-lookup"><span data-stu-id="5bb32-122">Disable the revocation list check by opening the BizTalk Server Administration Console, opening the AS2 Properties dialog box for the party resolved for the outgoing message, clicking the General node, and then clearing the Check Certification Revocation List property.</span></span>