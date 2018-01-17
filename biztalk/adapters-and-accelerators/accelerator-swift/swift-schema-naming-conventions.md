---
title: "Conventions d’affectation de noms de schéma SWIFT | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- naming conventions [schemas]
- schemas, naming conventions
ms.assetid: 3c1f2519-2575-4178-89c1-e97333c1e6bd
caps.latest.revision: "5"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 14245a185adcccdfb1f2ea2ed9382820fb84177e
ms.sourcegitcommit: 3fd1c85d9dc2ce7b77da75a5c2087cc48cfcbe50
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/17/2018
---
# <a name="swift-schema-naming-conventions"></a><span data-ttu-id="90a4e-102">Conventions d’affectation de noms de schéma SWIFT</span><span class="sxs-lookup"><span data-stu-id="90a4e-102">SWIFT Schema Naming Conventions</span></span>
[!INCLUDE[btsCoName](../../includes/btsconame-md.md)]<span data-ttu-id="90a4e-103">[!INCLUDE[A4SWIFT_CurrentVersion_FirstRef](../../includes/a4swift-currentversion-firstref-md.md)] inclut des schémas pour la société pour les messages FIN de télécommunication financières Interbank (SWIFT) dans le monde entier ont été créés à l’aide de l’Éditeur BizTalk.</span><span class="sxs-lookup"><span data-stu-id="90a4e-103"> [!INCLUDE[A4SWIFT_CurrentVersion_FirstRef](../../includes/a4swift-currentversion-firstref-md.md)] includes schemas for Society for Worldwide Interbank Financial Telecommunication (SWIFT) FIN messages that were created using BizTalk Editor.</span></span> <span data-ttu-id="90a4e-104">Ces schémas sont conformes aux conventions suivantes dans l’ensemble de :</span><span class="sxs-lookup"><span data-stu-id="90a4e-104">These schemas conform to the following conventions throughout:</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="90a4e-105">Tous les schémas sont gérées.</span><span class="sxs-lookup"><span data-stu-id="90a4e-105">All schemas are versioned.</span></span> <span data-ttu-id="90a4e-106">Pour afficher la version, ouvrez [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)], cliquez sur le schéma dans l’Explorateur de solutions.</span><span class="sxs-lookup"><span data-stu-id="90a4e-106">To see the version, open [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)], and right-click the schema in Solution Explorer.</span></span> <span data-ttu-id="90a4e-107">Avec la \<schéma\> nœud sélectionné dans l’Éditeur BizTalk, dans le volet Propriétés défiler la propriété Version Standard.</span><span class="sxs-lookup"><span data-stu-id="90a4e-107">With the \<Schema\> node selected in BizTalk Editor, in the Properties pane scroll down to the Standard Version property.</span></span>  
  
-   <span data-ttu-id="90a4e-108">Le nom de chaque fichier de schéma d’échange est **MT*xxx*.xsd**, où *xxx* est le type de message FIN.</span><span class="sxs-lookup"><span data-stu-id="90a4e-108">The name of each interchange schema file is **MT*xxx*.xsd**, where *xxx* is the FIN message type.</span></span>  
  
-   <span data-ttu-id="90a4e-109">Le nom du fichier de stratégie principal associé pour chaque message est **MT*xxx*_Master_Policy.xml**, et le nom correspondant dans le moteur de règles d’entreprise (BRE) est **MT*xxx* _Master_Policy**, avec un nom de la liste de **MT*xxx*_PolicyList**.</span><span class="sxs-lookup"><span data-stu-id="90a4e-109">The name of the associated master policy file for each message is **MT*xxx*_Master_Policy.xml**, and the corresponding name in the Business Rule Engine (BRE) is **MT*xxx*_Master_Policy**, with a list name of **MT*xxx*_PolicyList**.</span></span>  
  
-   <span data-ttu-id="90a4e-110">Le nom du fichier de stratégie de validation associés pour chaque message est **MT*xxx*_Validation_Policy.xml**, et le nom correspondant dans le moteur BRE est **MT*xxx*_Validation_Policy**.</span><span class="sxs-lookup"><span data-stu-id="90a4e-110">The name of the associated validation policy file for each message is **MT*xxx*_Validation_Policy.xml**, and the corresponding name in the BRE is **MT*xxx*_Validation_Policy**.</span></span>  
  
-   <span data-ttu-id="90a4e-111">Dans chaque schéma de message, le nom de la racine est **SWIFT_CATEGORY*z*_MT*zxx*_Interchange**, où *z* est la catégorie de message () premier chiffre de type de message) et *zxx* est le type de message.</span><span class="sxs-lookup"><span data-stu-id="90a4e-111">Within each message schema, the name of the root is **SWIFT_CATEGORY*z*_MT*zxx*_Interchange**, where *z* is the message category (first digit of the message type) and *zxx* is the message type.</span></span>  
  
-   <span data-ttu-id="90a4e-112">L’espace de noms cible pour chaque schéma de message est **http://schemas.microsoft.com/BizTalk/Solutions/FinancialServices/SWIFT/Category*z*/MT*zxx ***, où *z* est la catégorie de message (premier chiffre de type de message) et *zxx* est le type de message.</span><span class="sxs-lookup"><span data-stu-id="90a4e-112">The target namespace for each message schema is **http://schemas.microsoft.com/BizTalk/Solutions/FinancialServices/SWIFT/Category*z*/MT*zxx***, where *z* is the message category (first digit of the message type) and *zxx* is the message type.</span></span>  
  
-   <span data-ttu-id="90a4e-113">Le type de document est **MT*zxx ***, où *zxx* est le type de message.</span><span class="sxs-lookup"><span data-stu-id="90a4e-113">The document type is **MT*zxx***, where *zxx* is the message type.</span></span>  
  
-   <span data-ttu-id="90a4e-114">Les noms des champs qui ne sont pas numérotées et sous-champs incluent les noms descriptifs.</span><span class="sxs-lookup"><span data-stu-id="90a4e-114">The names of fields that are not numbered and sub-fields include descriptive business names.</span></span> <span data-ttu-id="90a4e-115">La première lettre de chaque mot en majuscules et les noms n’incluent pas un espace intermédiaire ou ponctuation entre les mots (par exemple, le nom serait **ServiceIdentifier**, et non **identificateur Service**) .</span><span class="sxs-lookup"><span data-stu-id="90a4e-115">The first letter of each word is capitalized, and the names do not include an intervening space or punctuation between words (for example, the name would be **ServiceIdentifier**, not **Service Identifier**).</span></span>  
  
-   <span data-ttu-id="90a4e-116">Les étiquettes de séquences dans les messages sont conformes à la *Guide de référence SWIFT* (par exemple, **SequenceA**).</span><span class="sxs-lookup"><span data-stu-id="90a4e-116">The labels of sequences within messages conform to the *SWIFT Reference Guide* (for example, **SequenceA**).</span></span>  
  
-   <span data-ttu-id="90a4e-117">Les étiquettes de numérotées SWIFT champs inclure un titre descriptif, suivi de la séquence (le cas échéant), suivi par le code numérique et le format de lettre facultative (par exemple, **Reference_A_20C**).</span><span class="sxs-lookup"><span data-stu-id="90a4e-117">The labels of numbered SWIFT fields include a descriptive title followed by the sequence (if present), followed by the number code and optional letter format (for example, **Reference_A_20C**).</span></span>  
  
-   <span data-ttu-id="90a4e-118">S’il existe un choix de plusieurs formats pour un champ, l’étiquette du nœud est  **\< *choix*\>**, puis chaque option est un champ numéroté (par exemple, **Date _A_98A** et **DateTime_A_98C**).</span><span class="sxs-lookup"><span data-stu-id="90a4e-118">Where there is a choice of multiple formats for a field, the label of the node is **\<*Choice*\>**, and then each option is a numbered field (for example, **Date_A_98A** and **DateTime_A_98C**).</span></span>  
  
-   <span data-ttu-id="90a4e-119">Le nom de la définition d’élément de niveau le plus bas d’un champ se compose du nom du champ secondaire suivi **Type** (par exemple, **accountType** compte).</span><span class="sxs-lookup"><span data-stu-id="90a4e-119">The name of the lowest level element definition of a sub-field consists of the name of the sub-field followed by **Type** (for example, **accountType** for Account).</span></span>  
  
 <span data-ttu-id="90a4e-120">Autres espaces de noms dans le schéma de message sont les suivantes :</span><span class="sxs-lookup"><span data-stu-id="90a4e-120">Other namespaces in the message schema include the following:</span></span>  
  
-   <span data-ttu-id="90a4e-121">xmlns:xs="http://www.w3.org/2001/XMLSchema".</span><span class="sxs-lookup"><span data-stu-id="90a4e-121">xmlns:xs="http://www.w3.org/2001/XMLSchema".</span></span> <span data-ttu-id="90a4e-122">Il s’agit de l’espace de noms du schéma XML de W3C par défaut.</span><span class="sxs-lookup"><span data-stu-id="90a4e-122">This is the default W3C XML Schema namespace.</span></span>  
  
-   <span data-ttu-id="90a4e-123">xmlns:b="http://schemas.microsoft.com/BizTalk/2003".</span><span class="sxs-lookup"><span data-stu-id="90a4e-123">xmlns:b="http://schemas.microsoft.com/BizTalk/2003".</span></span> <span data-ttu-id="90a4e-124">Il s’agit de l’espace de noms BizTalk par défaut.</span><span class="sxs-lookup"><span data-stu-id="90a4e-124">This is the default BizTalk namespace.</span></span>  
  
 <span data-ttu-id="90a4e-125">Chaque schéma de message fait référence directement le type de base et des schémas de type de données courants.</span><span class="sxs-lookup"><span data-stu-id="90a4e-125">Each message schema directly references the base type and common data type schemas.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="90a4e-126">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="90a4e-126">See Also</span></span>  
 [<span data-ttu-id="90a4e-127">Utilisation des schémas</span><span class="sxs-lookup"><span data-stu-id="90a4e-127">Working with Schemas</span></span>](../../adapters-and-accelerators/accelerator-swift/working-with-schemas.md)