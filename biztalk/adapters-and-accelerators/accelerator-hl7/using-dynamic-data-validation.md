---
title: "Utilisation de la Validation de données dynamiques | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- dynamic data validation
- validating, dynamic data
ms.assetid: 8dac7f74-92a7-447c-97bf-b1f3ce39b614
caps.latest.revision: "5"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 3387117648329828c9276545eafddca6872c4aa2
ms.sourcegitcommit: 3fc338e52d5dbca2c3ea1685a2faafc7582fe23a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/01/2017
---
# <a name="using-dynamic-data-validation"></a><span data-ttu-id="f104d-102">Utilisation de la Validation de données dynamiques</span><span class="sxs-lookup"><span data-stu-id="f104d-102">Using Dynamic Data Validation</span></span>
<span data-ttu-id="f104d-103">La validation de contenu du message par rapport à des données dynamiques, qui inclut la validation du format de message et le contenu du message est une partie importante de la validation dynamique des données.</span><span class="sxs-lookup"><span data-stu-id="f104d-103">An important part of dynamic data validation is validating message content against dynamic data, which includes validating the message format and the message content.</span></span> <span data-ttu-id="f104d-104">Un schéma de document, qui [!INCLUDE[btsCoName](../../includes/btsconame-md.md)]BizTalk Server implémente dans un fichier XSD, qui définit et valide les formats de message.</span><span class="sxs-lookup"><span data-stu-id="f104d-104">A document schema, which [!INCLUDE[btsCoName](../../includes/btsconame-md.md)]BizTalk Server implements in an XSD file, defines and validates message formats.</span></span> <span data-ttu-id="f104d-105">Contenu du message, définissent des règles d’entreprise qui [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] valide via des stratégies du moteur de règles d’entreprise.</span><span class="sxs-lookup"><span data-stu-id="f104d-105">Business rules define message content, which [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] validates through Business Rule Engine policies.</span></span> <span data-ttu-id="f104d-106">Validation du contenu peut inclure que les données dans l’instance de message correspond aux données qui peuvent changer avec une fréquence relative de confirmation.</span><span class="sxs-lookup"><span data-stu-id="f104d-106">Content validation can include confirmation that data in the message instance matches data that may change with relative frequency.</span></span> [!INCLUDE[btsCoName](../../includes/btsconame-md.md)]<span data-ttu-id="f104d-107">[!INCLUDE[HL7_CurrentVersion_FirstRef](../../includes/hl7-currentversion-firstref-md.md)]implémente ce type de validation de manière dynamique, afin que vous pouvez mettre à jour ces données dans un environnement de production sans avoir à recompiler le code ou l’arrêt des services.</span><span class="sxs-lookup"><span data-stu-id="f104d-107">[!INCLUDE[HL7_CurrentVersion_FirstRef](../../includes/hl7-currentversion-firstref-md.md)] implements this type of validation in a dynamic manner, so that you can update this data in a production environment, without having to recompile code or shut down services.</span></span>  
  
## <a name="validate-and-expose-data"></a><span data-ttu-id="f104d-108">Valider et exposer des données</span><span class="sxs-lookup"><span data-stu-id="f104d-108">Validate and Expose Data</span></span>  
 <span data-ttu-id="f104d-109">Il existe deux étapes pour effectuer la Validation dynamique des données (DDV) :</span><span class="sxs-lookup"><span data-stu-id="f104d-109">There are two steps in performing Dynamic Data Validation (DDV):</span></span>  
  
-   <span data-ttu-id="f104d-110">Exposer les données.</span><span class="sxs-lookup"><span data-stu-id="f104d-110">Expose the data.</span></span>  
  
-   <span data-ttu-id="f104d-111">Appliquer des règles de validation à l’aide de ces données.</span><span class="sxs-lookup"><span data-stu-id="f104d-111">Apply validation rules using that data.</span></span>  
  
 <span data-ttu-id="f104d-112">DDV fournit la prise en charge suivant pour le stockage, l’exposition et la mise en cache des données dynamiques :</span><span class="sxs-lookup"><span data-stu-id="f104d-112">DDV provides the following support for storing, exposing, and caching dynamic data:</span></span>  
  
-   <span data-ttu-id="f104d-113">Le moteur de règles métier ou de la classe de Message effectue la validation.</span><span class="sxs-lookup"><span data-stu-id="f104d-113">The Business Rule Engine or Message Class performs validation.</span></span>  
  
-   <span data-ttu-id="f104d-114">Le moteur de règles d’entreprise expose des données via le vocabulaire de colonne de table de base de données.</span><span class="sxs-lookup"><span data-stu-id="f104d-114">The Business Rule Engine exposes data through the Database table column vocabulary.</span></span> <span data-ttu-id="f104d-115">Le moteur de règles d’entreprise valide cette dynamique des données contre les messages en implémentant un ensemble de règles qui s’exécute à partir d’un pipeline ou une orchestration.</span><span class="sxs-lookup"><span data-stu-id="f104d-115">The Business Rule Engine validates this dynamic data against messages by implementing a rule set that runs from a pipeline or orchestration.</span></span>  
  
-   <span data-ttu-id="f104d-116">Interfaces SQL existantes, telles que SQL Enterprise Manager et l’Analyseur de requêtes, exposez les données dynamiques est passives au moment du design.</span><span class="sxs-lookup"><span data-stu-id="f104d-116">Existing SQL interfaces, such as SQL Enterprise Manager and Query Analyzer, expose dynamic data that is passive at design time.</span></span>  
  
-   <span data-ttu-id="f104d-117">La définition de vocabulaire de colonne de table moteur des règles d’entreprise de base de données expose des données dynamiques au moment de l’exécution.</span><span class="sxs-lookup"><span data-stu-id="f104d-117">The Business Rule Engine database table column vocabulary definition exposes dynamic data at run time.</span></span>  
  
-   <span data-ttu-id="f104d-118">Le moteur de règles d’entreprise expose les données d’instance de message en cours d’exécution.</span><span class="sxs-lookup"><span data-stu-id="f104d-118">The Business Rule Engine exposes message instance data at run time.</span></span>  
  
-   <span data-ttu-id="f104d-119">Une définition de vocabulaire de document XML de moteur de règles métier expose les données d’instance de message au moment du design.</span><span class="sxs-lookup"><span data-stu-id="f104d-119">A Business Rules Engine XML document vocabulary definition exposes message instance data at design time.</span></span>  
  
-   <span data-ttu-id="f104d-120">Vous pouvez composer des règles au moment du design dans l’interface utilisateur de l’éditeur des règles d’entreprise ou directement dans les règles BRL (Business Language) XML dans un éditeur de texte.</span><span class="sxs-lookup"><span data-stu-id="f104d-120">You can compose rules at design time in the Business Rule Composer user interface or directly in Business Rules Language (BRL) XML in a text editor.</span></span>  
  
 <span data-ttu-id="f104d-121">Pour plus d’informations sur les règles d’entreprise et le moteur de règles d’entreprise, consultez « Développement avec des règles d’entreprise » dans l’aide de BizTalk Server.</span><span class="sxs-lookup"><span data-stu-id="f104d-121">For more information about business rules and the Business Rule Engine, see "Developing with Business Rules" in BizTalk Server Help.</span></span>  
  
## <a name="extending-ddv"></a><span data-ttu-id="f104d-122">Extension DDV</span><span class="sxs-lookup"><span data-stu-id="f104d-122">Extending DDV</span></span>  
 <span data-ttu-id="f104d-123">Si vous modifiez la validation de champ croisé basée sur HL7 ou validation de type de données, vous devez noter deux choses :</span><span class="sxs-lookup"><span data-stu-id="f104d-123">If you change HL7-based cross-field validation or data type validation, you must note two things:</span></span>  
  
-   <span data-ttu-id="f104d-124">Si vous modifiez une règle existante, vous n’avez pas besoin de redéployer.</span><span class="sxs-lookup"><span data-stu-id="f104d-124">If you modify an existing rule, you do not need to redeploy.</span></span>  
  
-   <span data-ttu-id="f104d-125">Si vous créez ou supprimez une règle qui a une incidence sur un composant de pipeline, vous devez recompiler.</span><span class="sxs-lookup"><span data-stu-id="f104d-125">If you create or delete a new rule that a pipeline component affects, then you must recompile.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f104d-126">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="f104d-126">See Also</span></span>  
 <span data-ttu-id="f104d-127">[Guide de programmation](../../adapters-and-accelerators/accelerator-hl7/programming-guide1.md) </span><span class="sxs-lookup"><span data-stu-id="f104d-127">[Programming Guide](../../adapters-and-accelerators/accelerator-hl7/programming-guide1.md) </span></span>  
 [<span data-ttu-id="f104d-128">Didacticiel sur l’enrichissement des messages</span><span class="sxs-lookup"><span data-stu-id="f104d-128">Message Enrichment Tutorial</span></span>](../../adapters-and-accelerators/accelerator-hl7/message-enrichment-tutorial.md)