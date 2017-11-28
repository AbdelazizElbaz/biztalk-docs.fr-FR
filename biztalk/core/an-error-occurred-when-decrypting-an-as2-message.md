---
title: "Une erreur s’est produite lors du déchiffrement d’un message AS2 | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0bfb1d2a-c79d-4541-8a6d-bab0986f456b
caps.latest.revision: "12"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 183933ae48468569cdd89f1d051f4bf961c71e05
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="an-error-occurred-when-decrypting-an-as2-message"></a><span data-ttu-id="499b4-102">Une erreur s'est produite lors du déchiffrage d'un message AS2</span><span class="sxs-lookup"><span data-stu-id="499b4-102">An error occurred when decrypting an AS2 message</span></span>
## <a name="details"></a><span data-ttu-id="499b4-103">Détails</span><span class="sxs-lookup"><span data-stu-id="499b4-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="499b4-104">Nom du produit</span><span class="sxs-lookup"><span data-stu-id="499b4-104">Product Name</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|<span data-ttu-id="499b4-105">Version du produit</span><span class="sxs-lookup"><span data-stu-id="499b4-105">Product Version</span></span>|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|<span data-ttu-id="499b4-106">ID d'événement</span><span class="sxs-lookup"><span data-stu-id="499b4-106">Event ID</span></span>|-|  
|<span data-ttu-id="499b4-107">Source de l'événement</span><span class="sxs-lookup"><span data-stu-id="499b4-107">Event Source</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="499b4-108"> EDI</span><span class="sxs-lookup"><span data-stu-id="499b4-108"> EDI</span></span>|  
|<span data-ttu-id="499b4-109">Composant</span><span class="sxs-lookup"><span data-stu-id="499b4-109">Component</span></span>|<span data-ttu-id="499b4-110">Moteur AS2</span><span class="sxs-lookup"><span data-stu-id="499b4-110">AS2 Engine</span></span>|  
|<span data-ttu-id="499b4-111">Nom symbolique</span><span class="sxs-lookup"><span data-stu-id="499b4-111">Symbolic Name</span></span>|-|  
|<span data-ttu-id="499b4-112">Texte du message</span><span class="sxs-lookup"><span data-stu-id="499b4-112">Message Text</span></span>|<span data-ttu-id="499b4-113">Une erreur s'est produite lors du déchiffrage d'un message AS2.</span><span class="sxs-lookup"><span data-stu-id="499b4-113">An error occurred when decrypting an AS2 message.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="499b4-114">Explication</span><span class="sxs-lookup"><span data-stu-id="499b4-114">Explanation</span></span>  
 <span data-ttu-id="499b4-115">Cet événement d'erreur/d'avertissement/d'informations indique que le composant Décodeur AS2 du pipeline de réception n'a pas pu déchiffrer le message AS2.</span><span class="sxs-lookup"><span data-stu-id="499b4-115">This Error/Warning/Information event indicates that the AS2 Decoder component of the receive pipeline could not decrypt the AS2 message.</span></span> <span data-ttu-id="499b4-116">Cela peut se produire si le certificat utilisé dans le processus de déchiffrement n'est pas valide, n'est pas stocké dans l'emplacement approprié ou ne correspond pas au certificat utilisé dans le processus de chiffrement.</span><span class="sxs-lookup"><span data-stu-id="499b4-116">This can occur if the certificate used in the decryption process is not valid, is not stored in the appropriate location, or does not match the certificate used in the encryption process.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="499b4-117">Action de l'utilisateur</span><span class="sxs-lookup"><span data-stu-id="499b4-117">User Action</span></span>  
 <span data-ttu-id="499b4-118">Pour résoudre cette erreur, procédez de l'une des manières suivantes :</span><span class="sxs-lookup"><span data-stu-id="499b4-118">To resolve this error, do one or more of the following:</span></span>  
  
-   <span data-ttu-id="499b4-119">Vérifiez que le wrapper de chiffrement du message AS2 est valide.</span><span class="sxs-lookup"><span data-stu-id="499b4-119">Verify that the encryption wrapper in the AS2 message is valid.</span></span> <span data-ttu-id="499b4-120">Sinon, déterminez pour quelle raison le message était codé de manière inappropriée par l'encodeur.</span><span class="sxs-lookup"><span data-stu-id="499b4-120">If not, determine why the message was encoded improperly by the encoder.</span></span>  
  
-   <span data-ttu-id="499b4-121">Vérifiez que la clé publique utilisée dans le processus de chiffrement et la clé privée utilisée dans le processus de déchiffrement correspondent.</span><span class="sxs-lookup"><span data-stu-id="499b4-121">Verify that the public key used in the encryption process and the private key used in the decryption process match.</span></span>  
  
-   <span data-ttu-id="499b4-122">Vérifiez que la propriété Utilisation de la clé du certificat utilisé pour le chiffrement et le déchiffrement est définie sur « chiffrement des données ».</span><span class="sxs-lookup"><span data-stu-id="499b4-122">Verify that the Key Usage property of the certificate used for encryption and decryption is set to "data encipherment".</span></span>  
  
-   <span data-ttu-id="499b4-123">Vérifiez l'existence d'une chaîne brisée d'autorités de certification intermédiaires.</span><span class="sxs-lookup"><span data-stu-id="499b4-123">Verify that there is not a broken chain of intermediate certificate authorities.</span></span> <span data-ttu-id="499b4-124">Si c'est le cas, supprimez l'ancien certificat, et créez-en un.</span><span class="sxs-lookup"><span data-stu-id="499b4-124">If there is, delete the old certificate, and create and use a new certificate.</span></span>  
  
-   <span data-ttu-id="499b4-125">Vérifiez que le certificat n'a pas expiré en examinant sa date d'expiration dans le magasin de certificats à l'aide de la console MMC et du composant logiciel enfichable Certificats.</span><span class="sxs-lookup"><span data-stu-id="499b4-125">Verify that the certificate has not timed out by checking its expiration date in the Certificates store (using MMC with a certificates snap-in.).</span></span>  
  
-   <span data-ttu-id="499b4-126">Vérifiez que le certificat n'a pas été révoqué en vérifiant la liste de révocation des certificats.</span><span class="sxs-lookup"><span data-stu-id="499b4-126">Verify that the certificate has not been revoked by checking the Certification Revocation List.</span></span> <span data-ttu-id="499b4-127">(BizTalk Server peut procéder automatiquement à cette vérification si la propriété Vérifier la liste de révocation des certificats dans les propriétés AS2 générales de la console Administration de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] est activée.)</span><span class="sxs-lookup"><span data-stu-id="499b4-127">(You can have BizTalk Server check this automatically by checking the Check Certification Revocation List property in the General AS2 properties in the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration console.)</span></span>  
  
-   <span data-ttu-id="499b4-128">Vérifiez que le certificat utilisé pour le déchiffrement est stocké dans le magasin de certificats Utilisateur actuel\Personne de chaque serveur BizTalk qui héberge un pipeline Décodeur MIME/SMIME en tant que compte de service d'instance d'hôte.</span><span class="sxs-lookup"><span data-stu-id="499b4-128">Verify that the certificate used for decryption is stored in the Current User\Personal store of each BizTalk server that hosts a MIME/SMIME decoder pipeline as each host instance service account.</span></span>