---
title: "Sécuriser vos applications Oracle eBusiness Suite | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 76147120-57a8-4959-a0ff-77d04dee06a6
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: a9a7427d36ead6ba91e0d68b1080c9ab4f5155fa
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="secure-your-oracle-ebs-applications"></a><span data-ttu-id="b4296-102">Sécuriser vos applications Oracle eBusiness Suite</span><span class="sxs-lookup"><span data-stu-id="b4296-102">Secure your Oracle EBS applications</span></span>
<span data-ttu-id="b4296-103">Les applications d’Oracle E-Business traitent des informations métier sensibles telles que les détails du compte client.</span><span class="sxs-lookup"><span data-stu-id="b4296-103">Oracle E-Business applications deal with sensitive business information such as customer account details.</span></span> <span data-ttu-id="b4296-104">Les applications qui utilisent le [!INCLUDE[adapteroracleebusinesslong](../../includes/adapteroracleebusinesslong-md.md)] pour accéder et modifier ces informations soit localement ou via un réseau distribué peut par inadvertance l’exposer pour accéder aux acteurs non autorisés, à moins que les efforts sont effectuées pour protéger et sécuriser les données pendant transmission.</span><span class="sxs-lookup"><span data-stu-id="b4296-104">Applications that use the [!INCLUDE[adapteroracleebusinesslong](../../includes/adapteroracleebusinesslong-md.md)] to access and modify this information either locally or across a distributed network might inadvertently expose it to access by unauthorized actors, unless efforts are made to protect and secure the data during transmission.</span></span> <span data-ttu-id="b4296-105">Sécurité et protection des données sont généralement considérées dans les termes suivants :</span><span class="sxs-lookup"><span data-stu-id="b4296-105">Data protection and security are usually thought of in the following terms:</span></span>  
  
-   <span data-ttu-id="b4296-106">*Autorisation* contrôle l’accès à une ressource basée sur l’identité du demandeur.</span><span class="sxs-lookup"><span data-stu-id="b4296-106">*Authorization* controls access to a resource based on the identity of the requester.</span></span>  
  
-   <span data-ttu-id="b4296-107">*Authentification* fournit des mécanismes pour vérifier l’identité d’un demandeur.</span><span class="sxs-lookup"><span data-stu-id="b4296-107">*Authentication* provides mechanisms for verifying the identity of a requester.</span></span>  
  
-   <span data-ttu-id="b4296-108">*La confidentialité des données* fournit des mécanismes de protection de la confidentialité des données via le chiffrement.</span><span class="sxs-lookup"><span data-stu-id="b4296-108">*Data confidentiality* provides mechanisms for protecting the privacy of data through encryption.</span></span>  
  
-   <span data-ttu-id="b4296-109">*L’intégrité des données* fournit des mécanismes pour signer numériquement des données, afin que le récepteur peut vous assurer que les données n’a pas été modifié en transit.</span><span class="sxs-lookup"><span data-stu-id="b4296-109">*Data integrity* provides mechanisms to digitally sign data, so that the receiver can ensure that the data has not been altered in-transit.</span></span>  
  
 <span data-ttu-id="b4296-110">Un autre important problème concerne les informations d’identification de mot de passe de nom d’utilisateur que vous fournissez à la [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)].</span><span class="sxs-lookup"><span data-stu-id="b4296-110">Another important area of concern is the user-name password credentials that you supply to the [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)].</span></span> <span data-ttu-id="b4296-111">L’adaptateur utilise ces informations d’identification d’ouverture de connexions à la base de données Oracle.</span><span class="sxs-lookup"><span data-stu-id="b4296-111">The adapter uses these credentials to open connections to the Oracle database.</span></span> <span data-ttu-id="b4296-112">Ces informations d’identification peuvent être fournies dans la connexion URI ; Toutefois, étant donné que le nom d’utilisateur et un mot de passe sont texte clair, le [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] fournit d’autres méthodes que vous pouvez utiliser pour fournir ces informations d’identification de manière plus sécurisée.</span><span class="sxs-lookup"><span data-stu-id="b4296-112">These credentials can be supplied in the connection URI; however, because the user name and password are clear text, the [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] provides alternative methods that you can use to supply these credentials in a more secure manner.</span></span>  
  
 <span data-ttu-id="b4296-113">Les rubriques de cette section fournissent des indications pour vous aider à mieux sécuriser les solutions que vous développez avec le [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)].</span><span class="sxs-lookup"><span data-stu-id="b4296-113">The topics in this section provide guidelines to help you better secure the solutions that you develop with the [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)].</span></span>  
  
