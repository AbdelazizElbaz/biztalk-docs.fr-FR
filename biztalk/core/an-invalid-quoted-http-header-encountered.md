---
title: "Non valide entre guillemets en-tête HTTP détecté | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: bb530ee6-ec6a-4791-ae99-b9db426c0896
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 1e154e3bacf34025edd837516a15dca6f2caa174
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="an-invalid-quoted-http-header-encountered"></a><span data-ttu-id="4830e-102">En-tête HTTP entre guillemets non valide rencontré</span><span class="sxs-lookup"><span data-stu-id="4830e-102">An invalid quoted HTTP header encountered</span></span>
## <a name="details"></a><span data-ttu-id="4830e-103">Détails</span><span class="sxs-lookup"><span data-stu-id="4830e-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="4830e-104">Nom du produit</span><span class="sxs-lookup"><span data-stu-id="4830e-104">Product Name</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]|  
|<span data-ttu-id="4830e-105">Version du produit</span><span class="sxs-lookup"><span data-stu-id="4830e-105">Product Version</span></span>|[!INCLUDE[btsEDIVersion](../includes/btsediversion-md.md)]|  
|<span data-ttu-id="4830e-106">ID d'événement</span><span class="sxs-lookup"><span data-stu-id="4830e-106">Event ID</span></span>|-|  
|<span data-ttu-id="4830e-107">Source de l'événement</span><span class="sxs-lookup"><span data-stu-id="4830e-107">Event Source</span></span>|[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]<span data-ttu-id="4830e-108"> EDI</span><span class="sxs-lookup"><span data-stu-id="4830e-108"> EDI</span></span>|  
|<span data-ttu-id="4830e-109">Composant</span><span class="sxs-lookup"><span data-stu-id="4830e-109">Component</span></span>|<span data-ttu-id="4830e-110">Moteur AS2</span><span class="sxs-lookup"><span data-stu-id="4830e-110">AS2 Engine</span></span>|  
|<span data-ttu-id="4830e-111">Nom symbolique</span><span class="sxs-lookup"><span data-stu-id="4830e-111">Symbolic Name</span></span>|-|  
|<span data-ttu-id="4830e-112">Texte du message</span><span class="sxs-lookup"><span data-stu-id="4830e-112">Message Text</span></span>|<span data-ttu-id="4830e-113">En-tête HTTP entre guillemets non valide rencontré.</span><span class="sxs-lookup"><span data-stu-id="4830e-113">An invalid quoted HTTP header encountered.</span></span>  <span data-ttu-id="4830e-114">Détails sont les suivants : nom d’en-tête : valeur d’en-tête « {0} » : « {{1} »</span><span class="sxs-lookup"><span data-stu-id="4830e-114">Details are as follows:  Header Name: "{0}"  Header Value: "{1}"</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="4830e-115">Explication</span><span class="sxs-lookup"><span data-stu-id="4830e-115">Explanation</span></span>  
 <span data-ttu-id="4830e-116">Cet événement d'erreur/d'avertissement/d'informations indique que le pipeline de réception AS2 ou le pipeline d'envoi AS2 n'a pas pu traiter le message AS2 car le nom de l'en-tête AS2-From ou AS2-To du message est placé entre guillemets de manière incorrecte.</span><span class="sxs-lookup"><span data-stu-id="4830e-116">This Error/Warning/Information event indicates that the AS2 receive pipeline or the AS2 send pipeline could not process the AS2 message because the name of the AS2-From or AS2-To HTTP header in the message was not quoted correctly.</span></span> <span data-ttu-id="4830e-117">Le nom de l'en-tête est placé entre guillemets pour prendre en compte un espace, une barre oblique ou des guillemets doubles dans le nom.</span><span class="sxs-lookup"><span data-stu-id="4830e-117">The header name is quoted in order to accommodate a space, backslash, or double quotes within the name.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="4830e-118">Action de l'utilisateur</span><span class="sxs-lookup"><span data-stu-id="4830e-118">User Action</span></span>  
 <span data-ttu-id="4830e-119">Pour résoudre cette erreur, placez le nom d'en-tête du message AS2 entre guillemets de manière à ce qu'il soit conforme aux spécifications de la section 6.2 (« Identificateurs de système AS2 ») de la norme (« Échange de données d'entreprise MIME pair à pair sécurisé via HTTP, AS2 (Applicability Statement 2) »).</span><span class="sxs-lookup"><span data-stu-id="4830e-119">To resolve this error, quote the header name in the AS2 message in accordance with the rules stated in section 6.2, "AS2 System Identifiers", in RFC 4130, "MIME-Based Secure Peer-to-Peer Business Data Interchange Using HTTP, Applicability Statement 2 (AS2)".</span></span>