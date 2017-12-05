---
title: "Validation de la Configuration de l’adaptateur | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 8eeb8742-7083-462b-8d3a-e58103112542
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: c03054332e0cd2117c1219afec3dd1aa0a09d6bd
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="validating-the-adapter-configuration"></a><span data-ttu-id="a4ad2-102">Validation de la configuration des adaptateurs</span><span class="sxs-lookup"><span data-stu-id="a4ad2-102">Validating the Adapter Configuration</span></span>
<span data-ttu-id="a4ad2-103">Lors de l’ajout de l’emplacement de réception et le port d’envoi, vous devez configurer les propriétés personnalisées dans le  **\<**  *nom de l’adaptateur*  **\> propriétés du Transport**  boîte de dialogue.</span><span class="sxs-lookup"><span data-stu-id="a4ad2-103">While adding the receive location and send port, you will be asked to configure your custom properties in the **\<***Adapter Name***\> Transport Properties** dialog box.</span></span> <span data-ttu-id="a4ad2-104">Les fichier de schéma XSD du projet AdapterHarness définissent ces propriétés.</span><span class="sxs-lookup"><span data-stu-id="a4ad2-104">The XSD schema files in the AdapterHarness project define these properties.</span></span>  
  
 <span data-ttu-id="a4ad2-105">La validation du schéma de configuration s'effectue en trois phases :</span><span class="sxs-lookup"><span data-stu-id="a4ad2-105">Validation of the configuration schema occurs in three parts:</span></span>  
  
1.  <span data-ttu-id="a4ad2-106">Lors de l'affichage d'une configuration enregistrée, l'infrastructure d'adaptateurs valide le document XML enregistré par rapport au schéma avant de charger le document dans la page de propriétés.</span><span class="sxs-lookup"><span data-stu-id="a4ad2-106">When displaying a saved configuration, the Adapter Framework validates the saved XML document against the schema before loading the document into the property page.</span></span> <span data-ttu-id="a4ad2-107">L'infrastructure suppose qu'un document non valide indique un changement dans la définition du schéma de configuration.</span><span class="sxs-lookup"><span data-stu-id="a4ad2-107">The framework assumes that a document that is not valid indicates a change in the configuration schema definition.</span></span> <span data-ttu-id="a4ad2-108">Seuls les documents valides sont chargés dans la page de propriétés.</span><span class="sxs-lookup"><span data-stu-id="a4ad2-108">Only valid documents get loaded into the property page.</span></span>  
  
2.  <span data-ttu-id="a4ad2-109">Lors de l’enregistrement d’une configuration, si l’adaptateur implémente les **IAdapterConfigValidation** interface, l’infrastructure transmet à l’adaptateur le document XML construit à partir de la sérialisation des données de la page de propriété.</span><span class="sxs-lookup"><span data-stu-id="a4ad2-109">When saving a configuration, if the adapter implements the **IAdapterConfigValidation** interface, the framework passes to the adapter the XML document constructed from serializing the property page data.</span></span> <span data-ttu-id="a4ad2-110">L'adaptateur traite ensuite le document.</span><span class="sxs-lookup"><span data-stu-id="a4ad2-110">The adapter then processes the document.</span></span> <span data-ttu-id="a4ad2-111">Les erreurs doivent générer des exceptions qui sont appelées par l'infrastructure et affichées à l'écran de l'utilisateur.</span><span class="sxs-lookup"><span data-stu-id="a4ad2-111">Any errors should produce exceptions that are caught by the framework and displayed to the user.</span></span> <span data-ttu-id="a4ad2-112">Les valeurs manquantes ou générées doivent être générées lors de la validation.</span><span class="sxs-lookup"><span data-stu-id="a4ad2-112">Any missing or generated values should be generated during validation.</span></span> <span data-ttu-id="a4ad2-113">À l’aide de la \<browsable show = « false »\> décoration supprime l’affichage d’une entrée dans la grille des propriétés, même si la valeur s’affiche dans l’instance XML.</span><span class="sxs-lookup"><span data-stu-id="a4ad2-113">Using the \<browsable show="false"\> decoration suppresses showing an entry in the property grid, even though the value appears in the XML instance.</span></span>  
  
3.  <span data-ttu-id="a4ad2-114">Si vous enregistrez une configuration avant de placer la valeur dans la base de données, l'infrastructure valide à nouveau le document XML par rapport au schéma.</span><span class="sxs-lookup"><span data-stu-id="a4ad2-114">When saving a configuration before placing the value into the database, the framework again validates the XML document against the schema.</span></span> <span data-ttu-id="a4ad2-115">Cela permet de garantir que seules les valeurs valides sont conservées.</span><span class="sxs-lookup"><span data-stu-id="a4ad2-115">This ensures that only valid data is persisted.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a4ad2-116">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a4ad2-116">See Also</span></span>  
 [<span data-ttu-id="a4ad2-117">Problèmes de conception de l’adaptateur</span><span class="sxs-lookup"><span data-stu-id="a4ad2-117">Adapter Design Issues</span></span>](../core/adapter-design-issues.md)