---
title: "Validation d’exécution pour le moteur d’Orchestration | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- validating, assemblies
- orchestrations, validating
- validating, orchestration engine
- schemas, validating
- correlations, validating
- validating, schemas
- orchestration engine, runtime validation
- assemblies, validating
- validating, correlations
- validating, orchestrations
- validating
ms.assetid: f6085889-05d6-4eba-a528-9d034c4e4225
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: e53adb5aa42c7dfe23df50707754bde200ea838a
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="runtime-validation-for-the-orchestration-engine"></a><span data-ttu-id="da200-102">Validation d'exécution pour le moteur d'orchestration</span><span class="sxs-lookup"><span data-stu-id="da200-102">Runtime Validation for the Orchestration Engine</span></span>
<span data-ttu-id="da200-103">Vous pouvez configurer le moteur d'orchestration de sorte qu'il effectue plusieurs validations d'exécution qui pourront vous aider à tester votre orchestration et à diagnostiquer les éventuelles erreurs de configuration ou de données.</span><span class="sxs-lookup"><span data-stu-id="da200-103">You can configure the orchestration engine to perform various runtime validations that can help you test your orchestration and diagnose configuration or data errors that might arise.</span></span>  
  
 <span data-ttu-id="da200-104">Vous pouvez définir des indicateurs dans BTSNTSvc.exe.config, un fichier de configuration que vous pouvez créer ou modifier dans le même répertoire que BTSNTSvc.exe (normalement dans le répertoire de déploiement BizTalk).</span><span class="sxs-lookup"><span data-stu-id="da200-104">You can set flags in BTSNTSvc.exe.config, a configuration file that you can create or edit in the same directory as BTSNTSvc.exe (normally in the BizTalk deployment directory).</span></span> <span data-ttu-id="da200-105">Vous pouvez définir les indicateurs suivants dans le fichier BTSNTSvc.exe.config :</span><span class="sxs-lookup"><span data-stu-id="da200-105">You can set the following flags in the BTSNTSvc.exe.config file:</span></span>  
  
-   <span data-ttu-id="da200-106">Si vous définissez la **ValidateAssemblies** indicateur `True`, le moteur ne tente de charger tous les assemblys référencés par des assemblys immédiatement dépendants d’une orchestration et lors de la défaillance lève Erreur Microsoft.XLANGs.Core.AssemblyValidationException.</span><span class="sxs-lookup"><span data-stu-id="da200-106">If you set the **ValidateAssemblies** flag to `True`, the engine tries to load all assemblies referenced by immediate dependent assemblies of an orchestration and upon failure throws Microsoft.XLANGs.Core.AssemblyValidationException.</span></span>  
  
-   <span data-ttu-id="da200-107">Si vous définissez la **ValidateSchemas** indicateur `True`, le moteur utilise System.Xml.XmlValidatingReader pour valider chaque schéma représentant un type de partie de message et en cas d’échec, lève System.Xml.XmlException.</span><span class="sxs-lookup"><span data-stu-id="da200-107">If you set the **ValidateSchemas** flag to `True`, the engine uses System.Xml.XmlValidatingReader to validate every schema representing a message part type and upon failure throws System.Xml.XmlException.</span></span>  
  
-   <span data-ttu-id="da200-108">Si vous définissez la **ValidateCorrelations** indicateur `True`, le moteur vérifie que dans un convoi parallèle tous les messages qui correspondent à un du convoi reçoit ont les mêmes valeurs de propriété de corrélation et en cas d’échec, lève Erreur Microsoft.XLANGs.Core.CorrelationValidationException.</span><span class="sxs-lookup"><span data-stu-id="da200-108">If you set the **ValidateCorrelations** flag to `True`, the engine verifies that in a parallel convoy all messages that match one of the convoy receives have the same correlation property values and upon failure throws Microsoft.XLANGs.Core.CorrelationValidationException.</span></span>  
  
-   <span data-ttu-id="da200-109">Si vous définissez la **ExtendedLogging** indicateur `True`, le moteur affiche les propriétés promues dans les informations pour Microsoft.XLANGs.BaseTypes.PublishMessageException pour le message d’échec de la publication.</span><span class="sxs-lookup"><span data-stu-id="da200-109">If you set the **ExtendedLogging** flag to `True`, the engine displays the promoted properties in the information for Microsoft.XLANGs.BaseTypes.PublishMessageException for the message that failed to publish.</span></span>  
  
 <span data-ttu-id="da200-110">Si vous souhaitez désactiver une validation, supprimez entièrement l'indicateur du fichier de configuration.</span><span class="sxs-lookup"><span data-stu-id="da200-110">If you want to disable a validation, remove the flag entirely from the configuration file.</span></span> <span data-ttu-id="da200-111">Si toutes les validations sont activées, le moteur validera des assemblys, des schémas et une corrélation.</span><span class="sxs-lookup"><span data-stu-id="da200-111">When all validations are on, the engine will validate assemblies, schemas, and correlation.</span></span> <span data-ttu-id="da200-112">Pour plus d’informations et des exemples de BTSNTSvc.exe.config, consultez [Configuration du moteur d’Orchestration](../core/orchestration-engine-configuration.md).</span><span class="sxs-lookup"><span data-stu-id="da200-112">For more information and examples of BTSNTSvc.exe.config, see [Orchestration Engine Configuration](../core/orchestration-engine-configuration.md).</span></span>  
  
## <a name="validate-assemblies"></a><span data-ttu-id="da200-113">Validation d'assemblys</span><span class="sxs-lookup"><span data-stu-id="da200-113">Validate Assemblies</span></span>  
 <span data-ttu-id="da200-114">Le moteur d'orchestration vérifie que tous les assemblys référencés par l'orchestration sont disponibles.</span><span class="sxs-lookup"><span data-stu-id="da200-114">The orchestration engine will verify that any assemblies referenced by the orchestration are available.</span></span> <span data-ttu-id="da200-115">Pour que la validation réussisse, tous les assembly référencés doivent se trouver dans le Global Assembly Cache (GAC) lorsque la première instance de l'orchestration est activée.</span><span class="sxs-lookup"><span data-stu-id="da200-115">For the validation to succeed, all referenced assemblies must be in the Global Assembly Cache (GAC) when the first instance of the orchestration is activated.</span></span> <span data-ttu-id="da200-116">Si la validation échoue, une erreur est consignée dans le journal de l'application et l'orchestration est suspendue.</span><span class="sxs-lookup"><span data-stu-id="da200-116">If the validation fails, an error will be logged to the application log and the orchestration will be suspended.</span></span>  
  
## <a name="validate-schemas"></a><span data-ttu-id="da200-117">Validation de schémas</span><span class="sxs-lookup"><span data-stu-id="da200-117">Validate Schemas</span></span>  
 <span data-ttu-id="da200-118">À chaque fois qu'une partie XSD est attribuée, le moteur d'orchestration valide ses données en fonction de son schéma.</span><span class="sxs-lookup"><span data-stu-id="da200-118">Any time an XSD part is assigned, the orchestration engine will validate the part's data against its schema.</span></span> <span data-ttu-id="da200-119">Si la validation échoue, une erreur est consignée dans le journal de l'application et une exception est levée.</span><span class="sxs-lookup"><span data-stu-id="da200-119">If the validation fails, the error will be logged to the application log and an exception will be thrown.</span></span>  
  
## <a name="validate-correlation"></a><span data-ttu-id="da200-120">Validation d'une corrélation</span><span class="sxs-lookup"><span data-stu-id="da200-120">Validate Correlation</span></span>  
 <span data-ttu-id="da200-121">Le moteur d'orchestration confirmera que les valeurs de propriété spécifiées pour être corrélées avec une instance donnée d'une orchestration sont reflétées dans tous les messages envoyés à partir de cette instance d'orchestration.</span><span class="sxs-lookup"><span data-stu-id="da200-121">The orchestration engine will confirm that the property values that are specified for correlation with a given instance of an orchestration are reflected in any messages that are sent from that orchestration instance.</span></span> <span data-ttu-id="da200-122">Si **validateCorrelation** n’est pas défini, le moteur supposera que le message envoyé contient les valeurs de corrélation correctes et aucune vérification ne sera effectuée.</span><span class="sxs-lookup"><span data-stu-id="da200-122">If **validateCorrelation** is not set, the engine will assume that the sent message contains the correct correlation values, and no check will be performed.</span></span>  
  
 <span data-ttu-id="da200-123">Si une validation de corrélation échoue, le moteur enregistre une erreur dans le journal des applications et lever une exception de type **CorrelationValidationException**.</span><span class="sxs-lookup"><span data-stu-id="da200-123">If any correlation validation fails, the engine will log an error to the application log and throw an exception of type **CorrelationValidationException**.</span></span>  
  
 <span data-ttu-id="da200-124">Par défaut, **validateCorrelation** n’est pas définie.</span><span class="sxs-lookup"><span data-stu-id="da200-124">By default, **validateCorrelation** is not set.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="da200-125">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="da200-125">See Also</span></span>  
 <span data-ttu-id="da200-126">[Débogage des Orchestrations](../core/debugging-orchestrations.md) </span><span class="sxs-lookup"><span data-stu-id="da200-126">[Debugging Orchestrations](../core/debugging-orchestrations.md) </span></span>  
 [<span data-ttu-id="da200-127">Configuration du moteur d’orchestration</span><span class="sxs-lookup"><span data-stu-id="da200-127">Orchestration Engine Configuration</span></span>](../core/orchestration-engine-configuration.md)