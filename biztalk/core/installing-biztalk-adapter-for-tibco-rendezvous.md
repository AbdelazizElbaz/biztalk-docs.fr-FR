---
title: "Installation, les schémas et les limitations de l’adaptateur TIBCO Rendezvous | Documents Microsoft"
description: "Installation, de génération de schéma et les limitations de l’adaptateur BizTalk pour TIBCO Rendezvous dans BizTalk Server"
ms.custom: 
ms.date: 10/23/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c6404e7e-f671-4c57-a222-0bbe7cbc334f
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 2a158d4f627a553a87f0bc8fa08333a5864bb884
ms.sourcegitcommit: dd7c54feab783ae2f8fe75873363fe9ffc77cd66
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/07/2017
---
# <a name="install-schemas-and-limitations-of-the-tibco-rendezvous-adapter"></a><span data-ttu-id="ce9db-103">Installation, les schémas et les limitations de l’adaptateur TIBCO Rendezvous</span><span class="sxs-lookup"><span data-stu-id="ce9db-103">Install, schemas, and limitations of the TIBCO Rendezvous adapter</span></span>

## <a name="install-and-setup"></a><span data-ttu-id="ce9db-104">Installer et configurer</span><span class="sxs-lookup"><span data-stu-id="ce9db-104">Install and setup</span></span>

<span data-ttu-id="ce9db-105">[Installer et configurer les adaptateurs pour les applications d’entreprise](../adapters-and-accelerators/install-configure-biztalk-adapters-enterprise-applications.md) inclut les étapes pour installer les adaptateurs d’entreprise et inclut également des informations clées à connaître avant d’installer l’adaptateur, et après l’installation de l’adaptateur.</span><span class="sxs-lookup"><span data-stu-id="ce9db-105">[Install and configure the adapters for enterprise applications](../adapters-and-accelerators/install-configure-biztalk-adapters-enterprise-applications.md) includes the steps to install the enterprise adapters, and also includes key information to know before you install the adapter, and after you install the adapter.</span></span> 

## <a name="generate-schemas"></a><span data-ttu-id="ce9db-106">Générer des schémas</span><span class="sxs-lookup"><span data-stu-id="ce9db-106">Generate schemas</span></span>
<span data-ttu-id="ce9db-107">Un système TIBCO Rendezvous ne comporte pas de référentiel des types de messages.</span><span class="sxs-lookup"><span data-stu-id="ce9db-107">A TIBCO Rendezvous system does not include a message types repository.</span></span> <span data-ttu-id="ce9db-108">La construction et l'analyse d'un message sont enfouies au niveau de l'application Rendezvous.</span><span class="sxs-lookup"><span data-stu-id="ce9db-108">All the message construction and parsing is buried at the Rendezvous application level.</span></span> <span data-ttu-id="ce9db-109">En raison de cette limitation, l’adaptateur ne peut pas fournir des fonctionnalités de génération de schéma.</span><span class="sxs-lookup"><span data-stu-id="ce9db-109">Because of this limitation, adapter cannot provide schema-generation capabilities.</span></span>  
  
<span data-ttu-id="ce9db-110">Vous devez écrire un schéma et utiliser **ajouter un élément existant** dans Visual Studio pour l’importer pour une utilisation dans les orchestrations.</span><span class="sxs-lookup"><span data-stu-id="ce9db-110">You must write a schema, and use **Add Existing Item** in Visual Studio to import it for use in orchestrations.</span></span> <span data-ttu-id="ce9db-111">Les schémas sont essentiels aux outils de développement BizTalk Server et à l'intégration dans Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="ce9db-111">Schemas are very important for BizTalk Server development tools and for integration in Visual Studio.</span></span> <span data-ttu-id="ce9db-112">Les développeurs BizTalk Server peuvent choisir de fournir un schéma complet, minimum ou une version intermédiaire.</span><span class="sxs-lookup"><span data-stu-id="ce9db-112">BizTalk Server developers can choose to provide a complete schema, a minimalist schema, or a version somewhere in between.</span></span>  

## <a name="limitations"></a><span data-ttu-id="ce9db-113">Limitations</span><span class="sxs-lookup"><span data-stu-id="ce9db-113">Limitations</span></span>

- <span data-ttu-id="ce9db-114">L’unicité du nom du champ n’est pas garantie.</span><span class="sxs-lookup"><span data-stu-id="ce9db-114">Field name uniqueness is not guaranteed.</span></span> <span data-ttu-id="ce9db-115">Si un message TIBCO Rendezvous contient deux noms de champ identiques, le fichier XML qui en résulte n'est pas valide.</span><span class="sxs-lookup"><span data-stu-id="ce9db-115">If a TIBCO Rendezvous message contains two field names that are the same, the resulting XML is not valid.</span></span>  
  
-   <span data-ttu-id="ce9db-116">Il n'est pas possible de classer/trier les champs.</span><span class="sxs-lookup"><span data-stu-id="ce9db-116">Field ordering/sorting is not provided.</span></span>  
  
-   <span data-ttu-id="ce9db-117">Selon la documentation de TIBCO Rendezvous, les caractères non imprimables ne sont pas utilisés dans les noms d'objet. Il reste toutefois possible que de tels caractères soient utilisés.</span><span class="sxs-lookup"><span data-stu-id="ce9db-117">According to TIBCO Rendezvous documentation, non-printable characters are not used in subject names; however, it is still possible that such characters are used.</span></span> <span data-ttu-id="ce9db-118">L'adaptateur BizTalk pour TIBCO Rendezvous ne prend pas en charge les noms d'objet contenant ces caractères.</span><span class="sxs-lookup"><span data-stu-id="ce9db-118">BizTalk Adapter for TIBCO Rendezvous does not support subject names containing those characters.</span></span>  
  
-   <span data-ttu-id="ce9db-119">La connexion sécurisée aux démons n'est pas prise en charge.</span><span class="sxs-lookup"><span data-stu-id="ce9db-119">Secure connection to daemons is not supported.</span></span>  
  
-   <span data-ttu-id="ce9db-120">Les types de données personnalisés ne sont pas pris en charge.</span><span class="sxs-lookup"><span data-stu-id="ce9db-120">Custom data types are not supported.</span></span>  
  
-   <span data-ttu-id="ce9db-121">La messagerie certifiée n'est pas prise en charge du côté transmetteur.</span><span class="sxs-lookup"><span data-stu-id="ce9db-121">Certified Messaging is not supported on the transmit side.</span></span>  
-   
## <a name="next-step"></a><span data-ttu-id="ce9db-122">Étape suivante</span><span class="sxs-lookup"><span data-stu-id="ce9db-122">Next step</span></span>

[<span data-ttu-id="ce9db-123">Didacticiels : Utilisation de l’adaptateur Microsoft BizTalk pour TIBCO Rendezvous</span><span class="sxs-lookup"><span data-stu-id="ce9db-123">Tutorials: Using the Microsoft BizTalk Adapter for TIBCO Rendezvous</span></span>](../core/tutorials-using-the-microsoft-biztalk-adapter-for-tibco-rendezvous.md)  