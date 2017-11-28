---
title: "Sécuriser vos applications Siebel | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- security and protection
- data protection
ms.assetid: 8977cbd3-0025-48d4-8203-8e9e72ea7d26
caps.latest.revision: "5"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: a3b597120de91b6a09fdc26b90a2cb357cdc7dd1
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="secure-your-siebel-applications"></a><span data-ttu-id="dbbd3-102">Sécuriser vos applications Siebel</span><span class="sxs-lookup"><span data-stu-id="dbbd3-102">Secure your Siebel applications</span></span>
<span data-ttu-id="dbbd3-103">Le système Siebel contient souvent des informations sensibles telles que les détails du compte client.</span><span class="sxs-lookup"><span data-stu-id="dbbd3-103">The Siebel system often contains sensitive business information such as customer account details.</span></span> <span data-ttu-id="dbbd3-104">Les applications qui utilisent le [!INCLUDE[adaptersiebel](../../includes/adaptersiebel-md.md)] pour accéder et modifier ces informations soit localement ou via un réseau distribué peut par inadvertance l’exposer pour accéder aux acteurs non autorisés, à moins que les efforts sont effectuées pour protéger et sécuriser les données pendant transmission.</span><span class="sxs-lookup"><span data-stu-id="dbbd3-104">Applications that use the [!INCLUDE[adaptersiebel](../../includes/adaptersiebel-md.md)] to access and modify this information either locally or across a distributed network might inadvertently expose it to access by unauthorized actors, unless efforts are made to protect and secure the data during transmission.</span></span> <span data-ttu-id="dbbd3-105">Sécurité et protection des données sont généralement considérées dans les termes suivants :</span><span class="sxs-lookup"><span data-stu-id="dbbd3-105">Data protection and security are usually thought of in the following terms:</span></span>  
  
-   <span data-ttu-id="dbbd3-106">*Autorisation* contrôle l’accès à une ressource basée sur l’identité du demandeur.</span><span class="sxs-lookup"><span data-stu-id="dbbd3-106">*Authorization* controls access to a resource based on the identity of the requester.</span></span>  
  
-   <span data-ttu-id="dbbd3-107">*Authentification* fournit des mécanismes pour vérifier l’identité d’un demandeur.</span><span class="sxs-lookup"><span data-stu-id="dbbd3-107">*Authentication* provides mechanisms for verifying the identity of a requester.</span></span>  
  
-   <span data-ttu-id="dbbd3-108">*La confidentialité des données* fournit des mécanismes de protection de la confidentialité des données via le chiffrement.</span><span class="sxs-lookup"><span data-stu-id="dbbd3-108">*Data confidentiality* provides mechanisms for protecting the privacy of data through encryption.</span></span>  
  
-   <span data-ttu-id="dbbd3-109">*L’intégrité des données* fournit des mécanismes pour signer numériquement des données, afin que le récepteur peut vous assurer que les données n’a pas été modifié en transit.</span><span class="sxs-lookup"><span data-stu-id="dbbd3-109">*Data integrity* provides mechanisms to digitally sign data, so that the receiver can ensure that the data has not been altered in-transit.</span></span>  
  
 <span data-ttu-id="dbbd3-110">Un autre important problème concerne les informations d’identification de mot de passe de nom d’utilisateur que vous fournissez à la [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)].</span><span class="sxs-lookup"><span data-stu-id="dbbd3-110">Another important area of concern is the user-name password credentials that you supply to the [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)].</span></span> <span data-ttu-id="dbbd3-111">L’adaptateur utilise ces informations d’identification d’ouverture de connexions au système Siebel.</span><span class="sxs-lookup"><span data-stu-id="dbbd3-111">The adapter uses these credentials to open connections to the Siebel system.</span></span> <span data-ttu-id="dbbd3-112">Ces informations d’identification peuvent être fournies dans la connexion URI ; Toutefois, étant donné que le nom d’utilisateur et un mot de passe sont texte clair, le [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)] fournit d’autres méthodes que vous pouvez utiliser pour fournir ces informations d’identification de manière plus sécurisée.</span><span class="sxs-lookup"><span data-stu-id="dbbd3-112">These credentials can be supplied in the connection URI; however, because the user name and password are clear text, the [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)] provides alternative methods that you can use to supply these credentials in a more secure manner.</span></span>  
  
 <span data-ttu-id="dbbd3-113">Les rubriques de cette section fournissent des indications pour vous aider à mieux sécuriser les solutions que vous développez avec le [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)].</span><span class="sxs-lookup"><span data-stu-id="dbbd3-113">The topics in this section provide guidelines to help you better secure the solutions that you develop with the [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)].</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="dbbd3-114">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="dbbd3-114">In This Section</span></span>  
  
-   [<span data-ttu-id="dbbd3-115">Sécurité entre le système Siebel et de la carte</span><span class="sxs-lookup"><span data-stu-id="dbbd3-115">Security between the Siebel system and the adapter</span></span>](../../adapters-and-accelerators/adapter-siebel/security-between-the-siebel-system-and-the-adapter.md)
  
-   [<span data-ttu-id="dbbd3-116">Sécurité avec l’adaptateur Siebel et BizTalk Server</span><span class="sxs-lookup"><span data-stu-id="dbbd3-116">Security with Siebel adapter and BizTalk Server</span></span>](../../adapters-and-accelerators/adapter-siebel/security-with-siebel-adapter-and-biztalk-server.md)
  
-   [<span data-ttu-id="dbbd3-117">Programmation sécurisée avec l’adaptateur Siebel</span><span class="sxs-lookup"><span data-stu-id="dbbd3-117">Secure programming with the Siebel adapter</span></span>](../../adapters-and-accelerators/adapter-siebel/secure-programming-with-the-siebel-adapter.md)
  
-   [<span data-ttu-id="dbbd3-118">Meilleures pratiques pour sécuriser l’adaptateur Siebel</span><span class="sxs-lookup"><span data-stu-id="dbbd3-118">Best practices to secure the Siebel adapter</span></span>](../../adapters-and-accelerators/adapter-siebel/best-practices-to-secure-the-siebel-adapter.md)