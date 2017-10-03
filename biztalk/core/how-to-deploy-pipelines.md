---
title: "Comment déployer des Pipelines | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- IReceiveLocation interface
- IReceivePort interface
- deploying, pipelines
- pipelines, deploying
- pipelines, compiling
- SendPipelineData method
- pipelines, configuring
- pipelines, code sample
- ReceivePipelineData property
- Validate method
- ISendPort interface
ms.assetid: 7a56c753-a0d4-48ed-a61d-e454bc9cd507
caps.latest.revision: "14"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: db6047752c45a2f72b615102e14a4e66839e3e81
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="how-to-deploy-pipelines"></a><span data-ttu-id="bc15e-102">Déploiement des pipelines</span><span class="sxs-lookup"><span data-stu-id="bc15e-102">How to Deploy Pipelines</span></span>
<span data-ttu-id="bc15e-103">Les pipelines sont compilés et déployés dans le cadre du processus de création et de déploiement de solutions.</span><span class="sxs-lookup"><span data-stu-id="bc15e-103">Pipelines are compiled and deployed as part of the solution build and deploy process.</span></span> <span data-ttu-id="bc15e-104">Le compilateur appelle le **Validate** méthode sur chaque composant, en autorisant les composants retourner des erreurs de compilation dans les informations configurées.</span><span class="sxs-lookup"><span data-stu-id="bc15e-104">The compiler calls the **Validate** method on each component, allowing the components to return compile errors on the configured information.</span></span> <span data-ttu-id="bc15e-105">Après sa création, le pipeline est déployé dans le même assembly que le reste de la solution dès que celle-ci est déployée.</span><span class="sxs-lookup"><span data-stu-id="bc15e-105">After building, the pipeline is deployed in the same assembly with the rest of the solution when the solution is deployed.</span></span>  
  
## <a name="per-instance-pipeline-configuration"></a><span data-ttu-id="bc15e-106">Configuration de pipeline par instance</span><span class="sxs-lookup"><span data-stu-id="bc15e-106">Per-instance pipeline configuration</span></span>  
 <span data-ttu-id="bc15e-107">La configuration de pipeline par instance est utilisée pour modifier les propriétés de composants de pipeline dans un pipeline déployé au niveau du port d'envoi ou de l'emplacement de réception.</span><span class="sxs-lookup"><span data-stu-id="bc15e-107">Per-instance pipeline configuration is used to modify properties of pipeline components within a deployed pipeline at the send port or receive location level.</span></span> <span data-ttu-id="bc15e-108">Elle est utile lorsque seules quelques propriétés de composant de pipeline doivent être modifiées par instance.</span><span class="sxs-lookup"><span data-stu-id="bc15e-108">Per-instance pipeline configuration is useful when only a few pipeline component properties need to be modified per instance.</span></span> <span data-ttu-id="bc15e-109">Par exemple, si vous devez prendre en charge différents types de message dans plusieurs emplacements de réception et possédez un pipeline de réception XML personnalisé, la configuration de pipeline par instance vous permet de déployer le pipeline et de remplacer la configuration par défaut (notamment la spécification de différents noms d'enveloppe et de document).</span><span class="sxs-lookup"><span data-stu-id="bc15e-109">For example, if you need to support different message types in multiple receive locations and have a single custom XML receive pipeline, per-instance pipeline configuration enables you to deploy the pipeline and override the default configuration (including specifying different envelope and document spec names).</span></span> <span data-ttu-id="bc15e-110">Ce mécanisme est pris en charge dans BizTalk Management Console et au niveau logiciel par l'intermédiaire du modèle objet de l'Explorateur.</span><span class="sxs-lookup"><span data-stu-id="bc15e-110">This mechanism is supported in the BizTalk Management console and programmatically through the Explorer object model.</span></span>  
  
### <a name="per-instance-pipeline-configuration-using-biztalk-administration-console"></a><span data-ttu-id="bc15e-111">Configuration de pipeline par instance à l'aide de la console Administration de BizTalk</span><span class="sxs-lookup"><span data-stu-id="bc15e-111">Per-Instance Pipeline Configuration Using BizTalk Administration console</span></span>  
 <span data-ttu-id="bc15e-112">Vous pouvez effectuer la configuration de pipeline par instance à l'aide de BizTalk Management Console.</span><span class="sxs-lookup"><span data-stu-id="bc15e-112">You can perform per-instance pipeline configuration using the BizTalk Management console.</span></span> <span data-ttu-id="bc15e-113">Une fois votre pipeline personnalisé déployé, créez le nombre nécessaire d'emplacements de réception et de ports d'envoi.</span><span class="sxs-lookup"><span data-stu-id="bc15e-113">Once you have deployed your custom pipeline, create as many receive locations or send ports as required.</span></span> <span data-ttu-id="bc15e-114">Ensuite, pour chaque emplacement de réception ou port d'envoi, remplacez les valeurs de propriété par défaut par l'intermédiaire de la boîte de dialogue Configurer le pipeline.</span><span class="sxs-lookup"><span data-stu-id="bc15e-114">Then for each receive location or send port, override default property values through the Configure Pipeline dialog box.</span></span> <span data-ttu-id="bc15e-115">Par exemple, pour spécifier un schéma de document différent, entrez un nom de schéma pour le **EnvelopeDocSpecNames** propriété.</span><span class="sxs-lookup"><span data-stu-id="bc15e-115">For example, to specify a different document schema, enter a schema name for the **EnvelopeDocSpecNames** property.</span></span>  
  
> [!WARNING]
>  <span data-ttu-id="bc15e-116">Aucune validation des valeurs de configuration spécifiées dans l'emplacement de réception ou le port d'envoi sera effectuée.</span><span class="sxs-lookup"><span data-stu-id="bc15e-116">No validation of the configuration values specified in the receive location or send port will be performed.</span></span> <span data-ttu-id="bc15e-117">Si la configuration est incorrecte, les messages échoueront au moment de l'exécution lors de la transmission via le pipeline.</span><span class="sxs-lookup"><span data-stu-id="bc15e-117">If the configuration is incorrect, messages will fail at runtime when passing through the pipeline.</span></span>  
  
### <a name="per-instance-pipeline-configuration-using-the-explorer-object-model"></a><span data-ttu-id="bc15e-118">Configuration du pipeline par instance à l'aide du modèle objet de l'Explorateur</span><span class="sxs-lookup"><span data-stu-id="bc15e-118">Per-Instance Pipeline Configuration Using the Explorer Object Model</span></span>  
 <span data-ttu-id="bc15e-119">Lorsque le fichier XML décrivant la configuration par instance des composants de pipeline est lu, il remplace les propriétés définies dans le fichier de pipeline.</span><span class="sxs-lookup"><span data-stu-id="bc15e-119">When the XML file describing the per-instance configuration of the pipeline components is read, it overrides the properties set in the pipeline file.</span></span>  
  
 <span data-ttu-id="bc15e-120">La configuration de pipeline par instance est définie à l'aide du modèle objet de l'Explorateur BizTalk.</span><span class="sxs-lookup"><span data-stu-id="bc15e-120">Per-instance pipeline configuration is set by using the BizTalk Explorer object model.</span></span> <span data-ttu-id="bc15e-121">Le modèle d’objet de l’Explorateur BizTalk fournit la **ReceivePipelineData** propriété sur le **IReceiveLocation** et **ISendPort** des interfaces pour la définition de la configuration de composants de pipeline de réception.</span><span class="sxs-lookup"><span data-stu-id="bc15e-121">The BizTalk Explorer object model provides the **ReceivePipelineData** property on the **IReceiveLocation** and **ISendPort** interfaces for setting the configuration of receive pipeline components.</span></span> <span data-ttu-id="bc15e-122">Le modèle d’objet de l’Explorateur BizTalk fournit également la **SendPipelineData** méthode sur le **IReceivePort** et **ISendPort** des interfaces pour la définition de la configuration d’envoi composants de pipeline.</span><span class="sxs-lookup"><span data-stu-id="bc15e-122">The BizTalk Explorer object model also provides the **SendPipelineData** method on the **IReceivePort** and **ISendPort** interfaces for setting configuration of send pipeline components.</span></span>  
  
 <span data-ttu-id="bc15e-123">La configuration de pipeline par instance ne prend pas en charge ce qui suit :</span><span class="sxs-lookup"><span data-stu-id="bc15e-123">Per-instance pipeline configuration does not support the following:</span></span>  
  
-   <span data-ttu-id="bc15e-124">Réorganisation des phases dans le pipeline</span><span class="sxs-lookup"><span data-stu-id="bc15e-124">Rearranging stages within the pipeline</span></span>  
  
-   <span data-ttu-id="bc15e-125">Ajout ou suppression de phases</span><span class="sxs-lookup"><span data-stu-id="bc15e-125">Adding or removing stages</span></span>  
  
-   <span data-ttu-id="bc15e-126">Réorganisation des composants dans les phases</span><span class="sxs-lookup"><span data-stu-id="bc15e-126">Rearranging components within stages</span></span>  
  
-   <span data-ttu-id="bc15e-127">Ajout ou suppression de composants</span><span class="sxs-lookup"><span data-stu-id="bc15e-127">Adding or removing components</span></span>  
  
 <span data-ttu-id="bc15e-128">Les seules modifications prises en charge font partie de la configuration des composants de pipeline.</span><span class="sxs-lookup"><span data-stu-id="bc15e-128">The only supported changes are in the configuration of pipeline components.</span></span> <span data-ttu-id="bc15e-129">La configuration par instance d'un composant de pipeline remplace la configuration de composant de pipeline courante.</span><span class="sxs-lookup"><span data-stu-id="bc15e-129">Per-instance configuration of a pipeline component overrides the common pipeline component configuration.</span></span> <span data-ttu-id="bc15e-130">Si le paramètre d'un composant n'est pas spécifié dans la configuration de pipeline par instance, la configuration courante de ce paramètre (telle qu'elle est configurée dans le Concepteur de pipeline) est utilisée.</span><span class="sxs-lookup"><span data-stu-id="bc15e-130">If a parameter of a component is not specified in per-instance pipeline configuration, the common configuration for that parameter (as configured in Pipeline Designer) is used.</span></span>  
  
 <span data-ttu-id="bc15e-131">Ce qui suit est un exemple de données de configuration par instance.</span><span class="sxs-lookup"><span data-stu-id="bc15e-131">The following is an example of per-instance configuration data.</span></span>  
  
```  
<?xml version="1.0" encoding="utf-16"?>  
<Root xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance">  
    <Stages>  
        <Stage CategoryId="9d0e4103-4cce-4536-83fa-4a5040674ad6">  
            <Components>  
                <Component Name=Microsoft Microsoft.BizTalk.Component.MIME_SMIME_Decoder>  
                    <Properties>  
                        <AllowNonMIMEMessage vt=11>true</AllowNonMIMEMessage>  
                    </Properties>  
                </Component>  
            </Components>  
        </Stage>  
        <Stage CategoryId="9d0e4105-4cce-4536-83fa-4a5040674ad6">  
            <Components>  
                <Component Name=Microsoft.BizTalk.Component.XmlDasmComp>  
                    <Properties>  
                        <EnvelopeSpecNames vt=8>MySchemas.EnvelopeSpecNames</EnvelopeSpecNames>  
                        <AllowUnrecognizedMessage vt=11>false</AllowUnrecognizedMessage>  
                    </Properties>  
                </Component>  
            </Components>  
        </Stage>  
        <Stage CategoryId="9d0e410d-4cce-4536-83fa-4a5040674ad6" ExecutionSequence="2">  
            <Components>  
                 <Component Name=Microsoft.BizTalk.Component.XmlValidator >  
                    <Properties>  
                        <DocumentSpecName vt=8>MySchemas.DocspecName</DocumentSpecName>  
                    </Properties>  
                </Component>  
            </Components>  
        </Stage>  
    </Stages>  
</Root>  
```  
  
## <a name="see-also"></a><span data-ttu-id="bc15e-132">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="bc15e-132">See Also</span></span>  
 [<span data-ttu-id="bc15e-133">Développement de composants de Pipeline personnalisé</span><span class="sxs-lookup"><span data-stu-id="bc15e-133">Developing Custom Pipeline Components</span></span>](../core/developing-custom-pipeline-components.md)