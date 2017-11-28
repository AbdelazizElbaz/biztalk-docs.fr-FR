---
title: "Une erreur s’est produite lors de la validation d’un message AS2 | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0cf97c63-2bff-4474-9cd8-f68634493dcc
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 73f1c9b7cf4e444e256aadc3ade717fcf30735bd
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="an-error-occurred-when-validating-an-as2-message"></a><span data-ttu-id="58d3a-102">Une erreur s'est produite lors de la validation d'un message AS2</span><span class="sxs-lookup"><span data-stu-id="58d3a-102">An error occurred when validating an AS2 message</span></span>
## <a name="details"></a><span data-ttu-id="58d3a-103">Détails</span><span class="sxs-lookup"><span data-stu-id="58d3a-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="58d3a-104">Nom du produit</span><span class="sxs-lookup"><span data-stu-id="58d3a-104">Product Name</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|<span data-ttu-id="58d3a-105">Version du produit</span><span class="sxs-lookup"><span data-stu-id="58d3a-105">Product Version</span></span>|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|<span data-ttu-id="58d3a-106">ID d'événement</span><span class="sxs-lookup"><span data-stu-id="58d3a-106">Event ID</span></span>|-|  
|<span data-ttu-id="58d3a-107">Source de l'événement</span><span class="sxs-lookup"><span data-stu-id="58d3a-107">Event Source</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="58d3a-108"> EDI</span><span class="sxs-lookup"><span data-stu-id="58d3a-108"> EDI</span></span>|  
|<span data-ttu-id="58d3a-109">Composant</span><span class="sxs-lookup"><span data-stu-id="58d3a-109">Component</span></span>|<span data-ttu-id="58d3a-110">Moteur AS2</span><span class="sxs-lookup"><span data-stu-id="58d3a-110">AS2 Engine</span></span>|  
|<span data-ttu-id="58d3a-111">Nom symbolique</span><span class="sxs-lookup"><span data-stu-id="58d3a-111">Symbolic Name</span></span>|-|  
|<span data-ttu-id="58d3a-112">Texte du message</span><span class="sxs-lookup"><span data-stu-id="58d3a-112">Message Text</span></span>|<span data-ttu-id="58d3a-113">Une erreur s'est produite lors de la validation d'un message AS2.</span><span class="sxs-lookup"><span data-stu-id="58d3a-113">An error occurred when validating an AS2 message.</span></span> <span data-ttu-id="58d3a-114">Assurez-vous que les certificats utilisés n'ont pas dépassé le délai de temporisation ou été révoqués.</span><span class="sxs-lookup"><span data-stu-id="58d3a-114">Make sure the certificates used have not timed out or been revoked.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="58d3a-115">Explication</span><span class="sxs-lookup"><span data-stu-id="58d3a-115">Explanation</span></span>  
 <span data-ttu-id="58d3a-116">Cet événement de type erreur/avertissement/information indique que le pipeline de réception AS2 ou le pipeline d'envoi AS2 n'a pas pu valider le message AS2.</span><span class="sxs-lookup"><span data-stu-id="58d3a-116">This Error/Warning/Information event indicates that the AS2 receive pipeline or the AS2 send pipeline could not validate the AS2 message.</span></span> <span data-ttu-id="58d3a-117">Cela peut se produire si le certificat utilisé dans le processus de vérification des signatures n'est pas valide, n'est pas stocké à l'emplacement approprié ou ne correspond pas au certificat utilisé dans le processus de signature.</span><span class="sxs-lookup"><span data-stu-id="58d3a-117">This can occur if the certificate used in the signature verification process is not valid, is not stored in the appropriate location, or does not match the certificate used in the signing process.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="58d3a-118">Action de l'utilisateur</span><span class="sxs-lookup"><span data-stu-id="58d3a-118">User Action</span></span>  
 <span data-ttu-id="58d3a-119">Pour résoudre cette erreur, procédez de l'une des manières suivantes :</span><span class="sxs-lookup"><span data-stu-id="58d3a-119">To resolve this error, do one or more of the following:</span></span>  
  
-   <span data-ttu-id="58d3a-120">Vérifier que le wrapper de signature dans le message AS2 est valide.</span><span class="sxs-lookup"><span data-stu-id="58d3a-120">Verify that the signature wrapper in the AS2 message is valid.</span></span> <span data-ttu-id="58d3a-121">Si ce n'est pas le cas, déterminer la raison pour laquelle le message a été incorrectement signé par l'encodeur.</span><span class="sxs-lookup"><span data-stu-id="58d3a-121">If not, determine why the message was signed improperly by the encoder.</span></span>  
  
-   <span data-ttu-id="58d3a-122">Vérifier que la clé privée utilisée dans le processus de signature et la clé publique utilisée dans le processus de vérification des signatures concordent.</span><span class="sxs-lookup"><span data-stu-id="58d3a-122">Verify that the private key used in the signing process and the public key used in the signature verification process match.</span></span>  
  
-   <span data-ttu-id="58d3a-123">Vérifier que la propriété KeyUsage du certificat utilisé pour la signature et la vérification des signatures est définie sur « data encipherment ».</span><span class="sxs-lookup"><span data-stu-id="58d3a-123">Verify that the Key Usage property of the certificate used for signing and signature verification is set to "data encipherment".</span></span>  
  
-   <span data-ttu-id="58d3a-124">Vérifiez l'existence d'une chaîne brisée d'autorités de certification intermédiaires.</span><span class="sxs-lookup"><span data-stu-id="58d3a-124">Verify that there is not a broken chain of intermediate certificate authorities.</span></span> <span data-ttu-id="58d3a-125">Si c'est le cas, supprimez l'ancien certificat, et créez-en un.</span><span class="sxs-lookup"><span data-stu-id="58d3a-125">If there is, delete the old certificate, and create and use a new certificate.</span></span>  
  
-   <span data-ttu-id="58d3a-126">Vérifiez que le certificat n'a pas expiré en examinant sa date d'expiration dans le magasin de certificats à l'aide de la console MMC et du composant logiciel enfichable Certificats.</span><span class="sxs-lookup"><span data-stu-id="58d3a-126">Verify that the certificate has not timed out by checking its expiration date in the Certificates store (using MMC with a certificates snap-in.).</span></span>  
  
-   <span data-ttu-id="58d3a-127">Vérifiez que le certificat n'a pas été révoqué en vérifiant la liste de révocation des certificats.</span><span class="sxs-lookup"><span data-stu-id="58d3a-127">Verify that the certificate has not been revoked by checking the Certification Revocation List.</span></span> <span data-ttu-id="58d3a-128">(Vous pouvez automatiser cette opération en activant la propriété Vérifier la liste de révocation des certificats dans les propriétés AS2 générales de la console Administration de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].)</span><span class="sxs-lookup"><span data-stu-id="58d3a-128">(You can have BizTalk Server check this automatically by checking the Check Certification Revocation List property in the General AS2 properties in the [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Administration Console.)</span></span>  
  
-   <span data-ttu-id="58d3a-129">Vérifier que le certificat utilisé pour la vérification des signatures est stocké dans le magasin Ordinateur local \Autres personnes de chaque serveur BizTalk qui héberge un pipeline de décodeur MIME/SMIME en tant que compte de service de chaque instance hôte.</span><span class="sxs-lookup"><span data-stu-id="58d3a-129">Verify that the certificate used for signature verification is stored in the Local computer/Other People store of each BizTalk server that hosts a MIME/SMIME decoder pipeline as each host instance service account.</span></span>