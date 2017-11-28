---
title: "Sélectionnez un schéma d’URI et le format d’adressage lors de l’utilisation de WCF LOB Adapter SDK | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3bb4feee-3d39-43ca-82ac-aba38c13bc69
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 6df8145fac74761fee4aabd34ff01d708b646c12
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="select-a-uri-scheme-and-addressing-format-when-using-the-wcf-lob-adapter-sdk"></a><span data-ttu-id="427e9-102">Sélectionnez un schéma d’URI et le format d’adressage lors de l’utilisation de WCF LOB Adapter SDK</span><span class="sxs-lookup"><span data-stu-id="427e9-102">Select a URI scheme and addressing format when using the WCF LOB Adapter SDK</span></span>
<span data-ttu-id="427e9-103">Un identificateur de ressource uniforme (URI) identifie de façon unique les ressources comme un service Web ou, dans le cas d’un adaptateur développées avec le [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)], le système pour vous connecter à, ainsi que l’action à effectuer.</span><span class="sxs-lookup"><span data-stu-id="427e9-103">A Uniform Resource Identifier (URI) uniquely identifies resources like a Web service or, in the case of an adapter developed with the [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)], the system to connect to as well as the action to perform.</span></span> <span data-ttu-id="427e9-104">Cette section fournit une recommandation sur la façon de construire un URI pour décrivent de façon unique l’adresse de point de terminaison et l’action de votre adaptateur.</span><span class="sxs-lookup"><span data-stu-id="427e9-104">This section provides a recommendation on how to construct a URI to uniquely describe the endpoint address and the action for your adapter.</span></span>  
  
## <a name="anatomy-of-a-uri"></a><span data-ttu-id="427e9-105">Anatomie d’un URI</span><span class="sxs-lookup"><span data-stu-id="427e9-105">Anatomy of a URI</span></span>  
 <span data-ttu-id="427e9-106">Un URI se compose de trois composants suivants :</span><span class="sxs-lookup"><span data-stu-id="427e9-106">A URI consists of the following three components:</span></span>  
  
-   <span data-ttu-id="427e9-107">**Nom du schéma** est la partie de tête de la chaîne d’URI et est le premier niveau de la structure d’affectation de noms ; exemples incluent http, urn et contoso.</span><span class="sxs-lookup"><span data-stu-id="427e9-107">**Scheme name** is the lead part of the URI string and is the first level of the naming structure; examples include http, urn, and contoso.</span></span>  
  
-   <span data-ttu-id="427e9-108">**Partie hiérarchique** se compose d’informations qui sont généralement hiérarchique et peuvent contenir l’autorité facultatif, nom d’hôte et les informations de port.</span><span class="sxs-lookup"><span data-stu-id="427e9-108">**Hierarchical part** consists of information that is usually hierarchical and can contain optional authority, hostname, and port information.</span></span> <span data-ttu-id="427e9-109">Par exemple www.microsoft.com et le nom d’utilisateur =User@microsoft.com:4099.</span><span class="sxs-lookup"><span data-stu-id="427e9-109">Examples include www.microsoft.com and UserName=User@microsoft.com:4099.</span></span>  
  
-   <span data-ttu-id="427e9-110">**Requête** contient des informations facultatives marqués avec un point d’interrogation ( ?) et généralement regroupés en tant que paires clé/valeur séparées par une esperluette (&).</span><span class="sxs-lookup"><span data-stu-id="427e9-110">**Query** contains optional information marked with a question mark (?) and typically grouped as key/value pairs separated by an ampersand (&).</span></span> <span data-ttu-id="427e9-111">Par exemple, contoso://microsoft.com/functions?name=Find.</span><span class="sxs-lookup"><span data-stu-id="427e9-111">For example, contoso://microsoft.com/functions?name=Find.</span></span>  
  
-   <span data-ttu-id="427e9-112">**Fragment** est utilisé pour stocker les informations d’identification supplémentaires qui peuvent être requises par l’adaptateur.</span><span class="sxs-lookup"><span data-stu-id="427e9-112">**Fragment** is used to store extra identifying information that may be needed by the adapter.</span></span> <span data-ttu-id="427e9-113">Le fragment est séparé par un dièse (#) ; par exemple, contoso://microsoft.com/functions?name=Find#public.</span><span class="sxs-lookup"><span data-stu-id="427e9-113">The fragment is separated by a hash (#); for example, contoso://microsoft.com/functions?name=Find#public.</span></span>  
  
 <span data-ttu-id="427e9-114">Vous ne pouvez pas utiliser toutes les fonctionnalités fournies par la syntaxe d’URI.</span><span class="sxs-lookup"><span data-stu-id="427e9-114">You might not use all of the features provided by the URI syntax.</span></span>  
  
## <a name="designing-the-uri"></a><span data-ttu-id="427e9-115">Conception de l’URI</span><span class="sxs-lookup"><span data-stu-id="427e9-115">Designing the URI</span></span>  
 <span data-ttu-id="427e9-116">En tant que développeur d’adaptateur, vous devrez imaginer un URI correspondant à votre système de line-of-business cible.</span><span class="sxs-lookup"><span data-stu-id="427e9-116">As an adapter developer, you will have to devise an appropriate URI for your target line-of-business system.</span></span> <span data-ttu-id="427e9-117">Lorsque vous concevez votre URI, il est important pour le rendre unique et significatif.</span><span class="sxs-lookup"><span data-stu-id="427e9-117">When designing your URI, it is important to make it unique and meaningful.</span></span>  
  
 <span data-ttu-id="427e9-118">Un URI unique est celle qui n’est pas en conflit avec l’URI existant dans une organisation et entre les autres entreprises et Internet.</span><span class="sxs-lookup"><span data-stu-id="427e9-118">A unique URI is one that does not conflict with existing URIs within an organization and across other businesses and the Internet.</span></span> <span data-ttu-id="427e9-119">Par exemple, en choisissant un nom de schéma comme « http » ou « afs » qui peut être reconnu actuellement ou déjà largement utilisé peut entraîner des problèmes opérationnels ou connexion, car les demandes peuvent être routées vers un autre système et non à votre carte.</span><span class="sxs-lookup"><span data-stu-id="427e9-119">For example, choosing a scheme name like "http" or "afs" that may be currently recognized or already in wide use could cause connection or operational problems because requests might be routed to a different system and not to your adapter.</span></span>  
  
 <span data-ttu-id="427e9-120">Un autre aspect important de la conception de l’URI est qu’il soit explicite à l’audience de développeur qui utilise votre adaptateur.</span><span class="sxs-lookup"><span data-stu-id="427e9-120">Another important aspect of URI design is making it meaningful to the developer audience who will be consuming your adapter.</span></span> <span data-ttu-id="427e9-121">Par exemple, si vous écrivez un adaptateur pour un médical de système de traitement des revendications, vous pouvez créer un modèle URI qui inclut le nom de votre société, les revendications de la cible du traitement de nom du système et la version du système : northwind.contoso.cps.v1.0://.</span><span class="sxs-lookup"><span data-stu-id="427e9-121">For example, if you are writing an adapter for a medical claims processing system, you could design a URI scheme that includes your company name, the target claims processing system name, and system version: northwind.contoso.cps.v1.0://.</span></span>  
  
## <a name="connecting-to-the-target-system"></a><span data-ttu-id="427e9-122">Connexion au système cible</span><span class="sxs-lookup"><span data-stu-id="427e9-122">Connecting to the Target System</span></span>  
 <span data-ttu-id="427e9-123">Chaînes de connexion ont la syntaxe suivante :</span><span class="sxs-lookup"><span data-stu-id="427e9-123">Connection strings have the following syntax:</span></span>  
  
 <span data-ttu-id="427e9-124">**\<schéma > : //[userinfo « @ »]\<LOB de chaîne de connexion >**</span><span class="sxs-lookup"><span data-stu-id="427e9-124">**\<scheme>://[userinfo "@"]\<LOB Connection String>**</span></span>  
  
 <span data-ttu-id="427e9-125">Par exemple, vous pouvez se connecter au catalogue contoso (une ligne de l’exemple d’application d’entreprise) de système de commande à l’aide de ce qui suit :</span><span class="sxs-lookup"><span data-stu-id="427e9-125">For example, you could connect to the contoso catalog ordering system (a sample line of business application) using the following:</span></span>  
  
 <span data-ttu-id="427e9-126">**Northwind.contoso.v1.0://\<nom_serveur > ? Catalogue = Contoso & Integrated Security = True**</span><span class="sxs-lookup"><span data-stu-id="427e9-126">**northwind.contoso.v1.0://\<servername>?Catalog=Contoso&Integrated Security=True**</span></span>  
  
 <span data-ttu-id="427e9-127">Vous pouvez également fournir des informations de l’autorité facultatif dans l’URI, y compris le nom d’utilisateur et mot de passe et autres informations d’identification importantes.</span><span class="sxs-lookup"><span data-stu-id="427e9-127">You can also provide optional authority information in the URI including user name and password and other important credentials.</span></span> <span data-ttu-id="427e9-128">Toutefois, cela peut présenter un risque de sécurité.</span><span class="sxs-lookup"><span data-stu-id="427e9-128">However, this can present a security risk.</span></span>  
  
> [!CAUTION]
>  <span data-ttu-id="427e9-129">Ne passez pas d’informations d’identification utilisateur et d’autres informations sensibles dans l’URI.</span><span class="sxs-lookup"><span data-stu-id="427e9-129">Do not pass user credentials and other sensitive information in the URI.</span></span> <span data-ttu-id="427e9-130">Cette information peut être interceptée ni affichée par des utilisateurs non autorisés.</span><span class="sxs-lookup"><span data-stu-id="427e9-130">This information could be intercepted and viewed by unauthorized users.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="427e9-131">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="427e9-131">See Also</span></span>  
 [<span data-ttu-id="427e9-132">Planifier et concevoir un adaptateur à l’aide de WCF LOB Adapter SDK</span><span class="sxs-lookup"><span data-stu-id="427e9-132">Plan and design an adapter using the WCF LOB Adapter SDK</span></span>](../../adapters-and-accelerators/wcf-lob-adapter-sdk/plan-and-design-an-adapter-using-the-wcf-lob-adapter-sdk.md)