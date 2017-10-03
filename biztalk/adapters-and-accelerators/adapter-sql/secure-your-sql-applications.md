---
title: "Sécuriser vos applications SQL | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 4b182593-fcca-4ebc-a2fd-7684b84cfb15
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: d631bc3ad87e9a8ec8ac51850b7dbe1eb244c140
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="secure-your-sql-applications"></a><span data-ttu-id="eb055-102">Sécuriser vos applications SQL</span><span class="sxs-lookup"><span data-stu-id="eb055-102">Secure your SQL applications</span></span>
## <a name="overview"></a><span data-ttu-id="eb055-103">Vue d'ensemble</span><span class="sxs-lookup"><span data-stu-id="eb055-103">Overview</span></span>
<span data-ttu-id="eb055-104">Bases de données SQL Server contiennent souvent des informations sensibles telles que les détails du compte client.</span><span class="sxs-lookup"><span data-stu-id="eb055-104">SQL Server databases often contain sensitive business information such as customer account details.</span></span> <span data-ttu-id="eb055-105">Les applications qui utilisent le [!INCLUDE[adaptersql](../../includes/adaptersql-md.md)] pour accéder et modifier ces informations soit localement ou via un réseau distribué peut par inadvertance l’exposer pour accéder aux acteurs non autorisés, à moins que les efforts sont effectuées pour protéger et sécuriser les données pendant transmission.</span><span class="sxs-lookup"><span data-stu-id="eb055-105">Applications that use the [!INCLUDE[adaptersql](../../includes/adaptersql-md.md)] to access and modify this information either locally or across a distributed network might inadvertently expose it to access by unauthorized actors, unless efforts are made to protect and secure the data during transmission.</span></span> <span data-ttu-id="eb055-106">Sécurité et protection des données sont généralement considérées dans les termes suivants :</span><span class="sxs-lookup"><span data-stu-id="eb055-106">Data protection and security are usually thought of in the following terms:</span></span>  
  
-   <span data-ttu-id="eb055-107">*Autorisation* contrôle l’accès à une ressource basée sur l’identité du demandeur.</span><span class="sxs-lookup"><span data-stu-id="eb055-107">*Authorization* controls access to a resource based on the identity of the requestor.</span></span>  
  
-   <span data-ttu-id="eb055-108">*Authentification* fournit des mécanismes pour vérifier l’identité d’un demandeur.</span><span class="sxs-lookup"><span data-stu-id="eb055-108">*Authentication* provides mechanisms for verifying the identity of a requestor.</span></span>  
  
-   <span data-ttu-id="eb055-109">*La confidentialité des données* fournit des mécanismes de protection de la confidentialité des données via le chiffrement.</span><span class="sxs-lookup"><span data-stu-id="eb055-109">*Data confidentiality* provides mechanisms for protecting the privacy of data through encryption.</span></span>  
  
-   <span data-ttu-id="eb055-110">*L’intégrité des données* fournit des mécanismes pour signer numériquement des données, afin que le récepteur peut vous assurer que les données n’a pas été modifié en transit.</span><span class="sxs-lookup"><span data-stu-id="eb055-110">*Data integrity* provides mechanisms to digitally sign data, so that the receiver can ensure that the data has not been altered in-transit.</span></span>  
  
 <span data-ttu-id="eb055-111">Un autre important problème concerne les informations d’identification de mot de passe de nom d’utilisateur que vous fournissez à la [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)].</span><span class="sxs-lookup"><span data-stu-id="eb055-111">Another important area of concern is the user-name password credentials that you supply to the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)].</span></span> <span data-ttu-id="eb055-112">L’adaptateur utilise ces informations d’identification d’ouverture de connexions dans le système SQL.</span><span class="sxs-lookup"><span data-stu-id="eb055-112">The adapter uses these credentials to open connections to the SQL system.</span></span> <span data-ttu-id="eb055-113">Le [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] n’autorise pas les informations d’identification doivent être fournis dans l’URI de connexion.</span><span class="sxs-lookup"><span data-stu-id="eb055-113">The [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] does not allow credentials to be supplied in the connection URI.</span></span> <span data-ttu-id="eb055-114">Cela empêche les informations d’identification à partir de la mise en route exposées par inadvertance.</span><span class="sxs-lookup"><span data-stu-id="eb055-114">This prevents the credentials from getting exposed inadvertently.</span></span> <span data-ttu-id="eb055-115">Le [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] fournit deux autres méthodes pour fournir ces informations d’identification de manière plus sécurisée :</span><span class="sxs-lookup"><span data-stu-id="eb055-115">The [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] provides two alternative methods to supply these credentials in a more secure manner:</span></span>  
  
 <span data-ttu-id="eb055-116">Sécurité intégrée.</span><span class="sxs-lookup"><span data-stu-id="eb055-116">Integrated Security.</span></span> <span data-ttu-id="eb055-117">Dans ce cas, le [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] utilise Microsoft [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)] informations d’identification.</span><span class="sxs-lookup"><span data-stu-id="eb055-117">In this case, the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] uses the Microsoft [!INCLUDE[adapterpacknoversion](../../includes/adapterpacknoversion-md.md)] credentials.</span></span> <span data-ttu-id="eb055-118">Vous devez configurer le serveur SQL server pour accepter ces informations d’identification pour cette méthode fonctionne.</span><span class="sxs-lookup"><span data-stu-id="eb055-118">You must configure the SQL server to accept these credentials for this method to work.</span></span>  
  
 <span data-ttu-id="eb055-119">Enterprise Single Sign-on (SSO).</span><span class="sxs-lookup"><span data-stu-id="eb055-119">Enterprise Single Sign-on (SSO).</span></span> <span data-ttu-id="eb055-120">Pour plus d’informations sur l’utilisation de l’authentification unique, consultez [sécurité avec l’adaptateur SQL et BizTalk Server](../../adapters-and-accelerators/adapter-sql/security-with-the-sql-adapter-and-biztalk-server.md) .</span><span class="sxs-lookup"><span data-stu-id="eb055-120">For more information about using SSO, see [Security with the SQL adapter and BizTalk Server](../../adapters-and-accelerators/adapter-sql/security-with-the-sql-adapter-and-biztalk-server.md) .</span></span>  
  
 <span data-ttu-id="eb055-121">Les rubriques de cette section fournissent des indications pour vous aider à mieux sécuriser les solutions que vous développez avec le [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)].</span><span class="sxs-lookup"><span data-stu-id="eb055-121">The topics in this section provide guidelines to help you better secure the solutions that you develop with the [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)].</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="eb055-122">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="eb055-122">In This Section</span></span>  
  
-   [<span data-ttu-id="eb055-123">Sécurité entre le serveur SQL Server et de la carte</span><span class="sxs-lookup"><span data-stu-id="eb055-123">Security between the SQL Server and the adapter</span></span>](../../adapters-and-accelerators/adapter-sql/security-between-the-sql-server-and-the-adapter.md)
  
-   [<span data-ttu-id="eb055-124">Sécurité avec l’adaptateur SQL et BizTalk Server</span><span class="sxs-lookup"><span data-stu-id="eb055-124">Security with the SQL adapter and BizTalk Server</span></span>](../../adapters-and-accelerators/adapter-sql/security-with-the-sql-adapter-and-biztalk-server.md) 
  
-   [<span data-ttu-id="eb055-125">Programmation sécurisée avec l’adaptateur SQL</span><span class="sxs-lookup"><span data-stu-id="eb055-125">Secure programming with the SQL adapter</span></span>](../../adapters-and-accelerators/adapter-sql/secure-programming-with-the-sql-adapter.md)
  
-   [<span data-ttu-id="eb055-126">Meilleures pratiques</span><span class="sxs-lookup"><span data-stu-id="eb055-126">Best practices</span></span>](../../adapters-and-accelerators/adapter-sql/best-practices-to-secure-the-sql-adapter.md)