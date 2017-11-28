---
title: "Sécuriser vos applications de base de données Oracle | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- adapter, security
- authorization
- data protection
- adapter, data protection
- authentication
- security
ms.assetid: c5f18b0a-1c8e-44c6-ba7e-470fa186f636
caps.latest.revision: "5"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: e8601463c02e32221c369023f05ed2fd3731bb4b
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="secure-your-oracle-database-applications"></a><span data-ttu-id="bd138-102">Sécuriser vos applications de base de données Oracle</span><span class="sxs-lookup"><span data-stu-id="bd138-102">Secure your Oracle Database applications</span></span>
## <a name="data-protection-and-security-overview"></a><span data-ttu-id="bd138-103">Présentation de sécurité et protection des données</span><span class="sxs-lookup"><span data-stu-id="bd138-103">Data protection and security overview</span></span>
<span data-ttu-id="bd138-104">Une base de données contient souvent des informations sensibles telles que les détails du compte client.</span><span class="sxs-lookup"><span data-stu-id="bd138-104">A database often contains sensitive business information such as customer account details.</span></span> <span data-ttu-id="bd138-105">Les applications qui utilisent le [!INCLUDE[adapteroracle](../../includes/adapteroracle-md.md)] pour accéder et modifier ces informations soit localement ou via un réseau distribué peut par inadvertance l’exposer pour accéder aux acteurs non autorisés, à moins que les efforts sont effectuées pour protéger et sécuriser les données pendant transmission.</span><span class="sxs-lookup"><span data-stu-id="bd138-105">Applications that use the [!INCLUDE[adapteroracle](../../includes/adapteroracle-md.md)] to access and modify this information either locally or across a distributed network might inadvertently expose it to access by unauthorized actors, unless efforts are made to protect and secure the data during transmission.</span></span> <span data-ttu-id="bd138-106">Sécurité et protection des données sont généralement considérées dans les termes suivants :</span><span class="sxs-lookup"><span data-stu-id="bd138-106">Data protection and security are usually thought of in the following terms:</span></span>  
  
-   <span data-ttu-id="bd138-107">*Autorisation* contrôle l’accès à une ressource basée sur l’identité du demandeur.</span><span class="sxs-lookup"><span data-stu-id="bd138-107">*Authorization* controls access to a resource based on the identity of the requester.</span></span>  
  
-   <span data-ttu-id="bd138-108">*Authentification* fournit des mécanismes pour vérifier l’identité d’un demandeur.</span><span class="sxs-lookup"><span data-stu-id="bd138-108">*Authentication* provides mechanisms for verifying the identity of a requester.</span></span>  
  
-   <span data-ttu-id="bd138-109">*La confidentialité des données* fournit des mécanismes de protection de la confidentialité des données via le chiffrement.</span><span class="sxs-lookup"><span data-stu-id="bd138-109">*Data confidentiality* provides mechanisms for protecting the privacy of data through encryption.</span></span>  
  
-   <span data-ttu-id="bd138-110">*L’intégrité des données* fournit des mécanismes pour signer numériquement des données, afin que le récepteur peut vous assurer que les données n’a pas été modifié en transit.</span><span class="sxs-lookup"><span data-stu-id="bd138-110">*Data integrity* provides mechanisms to digitally sign data, so that the receiver can ensure that the data has not been altered in-transit.</span></span>  
  
 <span data-ttu-id="bd138-111">Un autre important problème concerne les informations d’identification de mot de passe de nom d’utilisateur que vous fournissez à la [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)].</span><span class="sxs-lookup"><span data-stu-id="bd138-111">Another important area of concern is the user-name password credentials that you supply to the [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)].</span></span> <span data-ttu-id="bd138-112">L’adaptateur utilise ces informations d’identification d’ouverture de connexions à la base de données Oracle.</span><span class="sxs-lookup"><span data-stu-id="bd138-112">The adapter uses these credentials to open connections to the Oracle database.</span></span> <span data-ttu-id="bd138-113">Ces informations d’identification peuvent être fournies dans la connexion URI ; Toutefois, étant donné que le nom d’utilisateur et un mot de passe sont texte clair, le [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] fournit d’autres méthodes que vous pouvez utiliser pour fournir ces informations d’identification de manière plus sécurisée.</span><span class="sxs-lookup"><span data-stu-id="bd138-113">These credentials can be supplied in the connection URI; however, because the user name and password are clear text, the [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] provides alternative methods that you can use to supply these credentials in a more secure manner.</span></span>  
  
 <span data-ttu-id="bd138-114">Les rubriques de cette section fournissent des indications pour vous aider à mieux sécuriser les solutions que vous développez avec le [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)].</span><span class="sxs-lookup"><span data-stu-id="bd138-114">The topics in this section provide guidelines to help you better secure the solutions that you develop with the [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)].</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="bd138-115">Contenu de cette section</span><span class="sxs-lookup"><span data-stu-id="bd138-115">In this section</span></span>  
  
-   [<span data-ttu-id="bd138-116">Sécurité entre la base de données Oracle et de la carte</span><span class="sxs-lookup"><span data-stu-id="bd138-116">Security between the Oracle Database and the adapter</span></span>](../../adapters-and-accelerators/adapter-oracle-database/security-between-the-oracle-database-and-the-adapter.md)
  
-   [<span data-ttu-id="bd138-117">Sécurité avec l’adaptateur de base de données Oracle et BizTalk Server</span><span class="sxs-lookup"><span data-stu-id="bd138-117">Security with the Oracle Database adapter and BizTalk Server</span></span>](../../adapters-and-accelerators/adapter-oracle-database/security-with-the-oracle-database-adapter-and-biztalk-server.md)  
  
-   [<span data-ttu-id="bd138-118">Programmation sécurisée avec l’adaptateur de base de données Oracle</span><span class="sxs-lookup"><span data-stu-id="bd138-118">Secure programming with the Oracle Database adapter</span></span>](../../adapters-and-accelerators/adapter-oracle-database/secure-programming-with-the-oracle-database-adapter.md) 
  
-   [<span data-ttu-id="bd138-119">Meilleures pratiques</span><span class="sxs-lookup"><span data-stu-id="bd138-119">Best practices</span></span>](../../adapters-and-accelerators/adapter-oracle-database/best-practices-to-secure-the-oracle-database-adapter.md)