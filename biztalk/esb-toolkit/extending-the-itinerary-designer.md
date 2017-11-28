---
title: "Étendre le Concepteur d’itinéraire | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f26b825b-ebab-4dac-b7ed-0608c79e146a
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: fb44c851258cc623cf991a0b2be5c18d58e59770
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="extending-the-itinerary-designer"></a><span data-ttu-id="2eb96-102">Étendre le Concepteur d’itinéraire</span><span class="sxs-lookup"><span data-stu-id="2eb96-102">Extending the Itinerary Designer</span></span>
<span data-ttu-id="2eb96-103">Le Concepteur d’itinéraire est un langage spécifique à un domaine visuel (DSL) pour Microsoft Visual Studio qui permet la modélisation graphique des itinéraires pour une utilisation avec le [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)].</span><span class="sxs-lookup"><span data-stu-id="2eb96-103">The Itinerary Designer is a visual domain-specific language (DSL) for Microsoft Visual Studio that enables the graphical modeling of itineraries for use with the [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)].</span></span> <span data-ttu-id="2eb96-104">Le concepteur expose plusieurs points d’extension pour laquelle les développeurs peuvent écrire des extensions personnalisées pour activer les nouvelles fonctionnalités et/ou de nouvelles options de configuration.</span><span class="sxs-lookup"><span data-stu-id="2eb96-104">The designer exposes various extension points for which developers can write custom extensions to enable new functionality and/or new configuration options.</span></span>  
  

  
 <span data-ttu-id="2eb96-105">**Création d’un exportateur d’itinéraire personnalisé**</span><span class="sxs-lookup"><span data-stu-id="2eb96-105">**Creating a Custom Itinerary Exporter**</span></span>  
  
 <span data-ttu-id="2eb96-106">Permet à l’architecture du Concepteur d’itinéraire pour la création des exportateurs de modèle personnalisé qui sérialisent et conserver les données dans un modèle d’itinéraire.</span><span class="sxs-lookup"><span data-stu-id="2eb96-106">The architecture of the Itinerary Designer allows for the creation of custom model exporters that serialize and persist the data in an Itinerary model.</span></span>  
  
 <span data-ttu-id="2eb96-107">**Création d’une extension personnalisée pour un Service de messagerie**</span><span class="sxs-lookup"><span data-stu-id="2eb96-107">**Creating a Custom Extender for a Messaging Service**</span></span>  
  
 <span data-ttu-id="2eb96-108">L’architecture du Concepteur d’itinéraire vous permet de créer des extensions personnalisées pour les éléments de modèle de Service de l’itinéraire qui peuvent être utilisés pour ajouter des propriétés pour le jeu de propriétés pour une utilisation par les Services de messagerie.</span><span class="sxs-lookup"><span data-stu-id="2eb96-108">The architecture of the Itinerary Designer allows you to create custom extenders for Itinerary Service model elements that can be used to add properties to the property bag for use by Messaging Services.</span></span>  
  
 <span data-ttu-id="2eb96-109">Pour obtenir un exemple montrant comment créer un extendeur de ce type, consultez [l’installation et l’exécution de l’exemple d’extensibilité de concepteur](../esb-toolkit/installing-and-running-the-designer-extensibility-sample.md).</span><span class="sxs-lookup"><span data-stu-id="2eb96-109">For a sample of how to create such an extender, see [Installing and Running the Designer Extensibility Sample](../esb-toolkit/installing-and-running-the-designer-extensibility-sample.md).</span></span>  
  
 <span data-ttu-id="2eb96-110">**Création d’une extension personnalisée pour un Service d’Orchestration d’itinéraire**</span><span class="sxs-lookup"><span data-stu-id="2eb96-110">**Creating a Custom Extender for an Orchestration-Based Itinerary Service**</span></span>  
  
 <span data-ttu-id="2eb96-111">L’architecture du Concepteur d’itinéraire vous permet de créer des extensions personnalisées pour les éléments de modèle de Service de l’itinéraire qui peuvent être utilisés pour ajouter des propriétés pour le jeu de propriétés pour une utilisation par des services d’orchestration d’itinéraire.</span><span class="sxs-lookup"><span data-stu-id="2eb96-111">The architecture of the Itinerary Designer allows you to create custom extenders for Itinerary Service model elements that can be used to add properties to the property bag for use by orchestration-based itinerary services.</span></span>  
  
 <span data-ttu-id="2eb96-112">Pour obtenir un exemple montrant comment créer un extendeur de ce type, consultez [l’installation et l’exécution de l’exemple d’extensibilité de concepteur](../esb-toolkit/installing-and-running-the-designer-extensibility-sample.md).</span><span class="sxs-lookup"><span data-stu-id="2eb96-112">For a sample of how to create such an extender, see [Installing and Running the Designer Extensibility Sample](../esb-toolkit/installing-and-running-the-designer-extensibility-sample.md).</span></span>  
  
 <span data-ttu-id="2eb96-113">**Création d’un extendeur de programme de résolution personnalisé**</span><span class="sxs-lookup"><span data-stu-id="2eb96-113">**Creating a Custom Resolver Extender**</span></span>  
  
 <span data-ttu-id="2eb96-114">L’architecture du Concepteur d’itinéraire vous permet de vous permet de créer des extensions personnalisées pour la configuration des programmes de résolution personnalisés.</span><span class="sxs-lookup"><span data-stu-id="2eb96-114">The architecture of the Itinerary Designer allows you to create custom extenders for the configuration of custom resolvers.</span></span> <span data-ttu-id="2eb96-115">Ces extensions fournissent une interface graphique pour configurer les paires nom-valeur dans la chaîne de connexion de programme de résolution, qui correspondent aux propriétés de la classe d’extendeur de programme de résolution spécifique.</span><span class="sxs-lookup"><span data-stu-id="2eb96-115">These extenders provide a graphical interface for configuring the name-value pairs in the resolver connection string, which map to properties in the specific resolver extender class.</span></span>  
  
 <span data-ttu-id="2eb96-116">Pour obtenir un exemple montrant comment créer un extendeur de ce type, consultez [l’installation et l’exécution de l’exemple d’extensibilité de concepteur](../esb-toolkit/installing-and-running-the-designer-extensibility-sample.md).</span><span class="sxs-lookup"><span data-stu-id="2eb96-116">For a sample of how to create such an extender, see [Installing and Running the Designer Extensibility Sample](../esb-toolkit/installing-and-running-the-designer-extensibility-sample.md).</span></span>  
  
 <span data-ttu-id="2eb96-117">**Création d’un fichier Manifest pour les propriétés de l’adaptateur personnalisé**</span><span class="sxs-lookup"><span data-stu-id="2eb96-117">**Creating a Manifest File for Custom Adapter Properties**</span></span>  
  
 <span data-ttu-id="2eb96-118">Lorsque vous créez un fournisseur de l’adaptateur personnalisé, vous devez également fournir la prise en charge de concepteur pour le fournisseur de l’adaptateur pour les extendeurs de programme de résolution qui affichent une propriété de configuration de point de terminaison.</span><span class="sxs-lookup"><span data-stu-id="2eb96-118">When creating a custom adapter provider, you must also provide designer support for the adapter provider to those resolver extenders that display an endpoint configuration property.</span></span> <span data-ttu-id="2eb96-119">Pour activer la prise en charge de concepteur, il est nécessaire créer un fichier de manifeste de fournisseur de carte.</span><span class="sxs-lookup"><span data-stu-id="2eb96-119">To enable designer support, it is necessary to create an adapter provider manifest file.</span></span>  
  
 <span data-ttu-id="2eb96-120">Le fichier de manifeste du fournisseur adaptateur définit les propriétés associées à un fournisseur de l’adaptateur spécifique, leurs types, descriptions et l’assembly dans lequel ils se trouvent.</span><span class="sxs-lookup"><span data-stu-id="2eb96-120">The adapter provider manifest file defines the properties associated with a specific adapter provider, their types, descriptions, and the assembly in which they can be found.</span></span> <span data-ttu-id="2eb96-121">Ces fichiers manifestes doivent être placés dans le même dossier que les fichiers binaires du Concepteur d’itinéraire (par exemple, Microsoft.Practices.Itineary.DslPackage.dll) avec un nom unique (par exemple, FTPPropertyManifest.xml).</span><span class="sxs-lookup"><span data-stu-id="2eb96-121">These manifest files should be placed in the same folder as the Itinerary Designer binaries (for example, Microsoft.Practices.Itineary.DslPackage.dll) with a unique name (for example, FTPPropertyManifest.xml).</span></span>  
  
 <span data-ttu-id="2eb96-122">Voici une instance de la référence d’un fichier manifeste de fournisseur d’adaptateur ; les fichiers manifeste personnalisés doivent être structurées de la même manière.</span><span class="sxs-lookup"><span data-stu-id="2eb96-122">The following is a reference instance of an adapter provider manifest file; custom manifest files should be structured likewise.</span></span>  
  
```xml  
\<?xml version="1.0" encoding="utf-8" ?>  
<adapterPropertyManifest adapterName="FTP">  
     <aliases>  
          <alias name="globalPropertySchemas" value="Microsoft.BizTalk.GlobalPropertySchemas, Version=3.0.1.0, Culture=neutral, PublicKeyToken=31bf3856ad364e35" />  
     </aliases>  
     <properties>  
          <property name="UserName" type="FTP.UserName" description="The user name for the connection." encrypted="true" assembly="globalPropertySchemas" />  
          <property name="Password" type="FTP.Password" description="The password for the conection." encrypted="true" assembly="globalPropertySchemas" />  
          <property name="MaxConnections" type="FTP.MaxConnections" description="The maximun number of connections." assembly="globalPropertySchemas" />  
          <property name="EventArgs" type="System.EventArgs" assembly="mscorlib, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" />  
     </properties>  
</adapterPropertyManifest>  
```  
  
 <span data-ttu-id="2eb96-123">**Création d’un extendeur de filtre personnalisé**</span><span class="sxs-lookup"><span data-stu-id="2eb96-123">**Creating a Custom Filter Extender**</span></span>  
  
 <span data-ttu-id="2eb96-124">L’architecture du Concepteur d’itinéraire vous permet de créer des extensions personnalisées pour la configuration des filtres personnalisés.</span><span class="sxs-lookup"><span data-stu-id="2eb96-124">The architecture of the Itinerary Designer allows you to create custom extenders for the configuration of custom filters.</span></span> <span data-ttu-id="2eb96-125">Ces extensions fournissent une interface graphique pour configurer les paires nom-valeur dans la chaîne de connexion de filtre, qui correspondent aux propriétés de la classe d’extendeur filtre spécifique.</span><span class="sxs-lookup"><span data-stu-id="2eb96-125">These extenders provide a graphical interface for configuring the name-value pairs in the filter connection string, which map to properties in the specific filter extender class.</span></span>  
  
-   <span data-ttu-id="2eb96-126">/ Samples/concepteur extensibilité Samples/Extenders.Itinerary.OrchestrationSample/Extenders.Itinerary.OrchestrationSample/Extenders.Itinerary.OrchestrationSample</span><span class="sxs-lookup"><span data-stu-id="2eb96-126">/Samples/Designer Extensibility Samples/Extenders.Itinerary.OrchestrationSample/Extenders.Itinerary.OrchestrationSample/Extenders.Itinerary.OrchestrationSample</span></span>  
  
-   <span data-ttu-id="2eb96-127">/ Samples/concepteur extensibilité Samples/Extenders.Resolvers.ResolverSample/Extenders.Resolvers.ResolverSample</span><span class="sxs-lookup"><span data-stu-id="2eb96-127">/Samples/Designer Extensibility Samples/Extenders.Resolvers.ResolverSample/Extenders.Resolvers.ResolverSample</span></span>  
  
 <span data-ttu-id="2eb96-128">**Création de règles de Validation personnalisées**</span><span class="sxs-lookup"><span data-stu-id="2eb96-128">**Creating Custom Validation Rules**</span></span>  
  
 <span data-ttu-id="2eb96-129">La dernière extension importantes introduite par le Concepteur d’itinéraire est un mécanisme de validation qui vous permet en externe, par rapport à un langage spécifique à un domaine (DSL), spécifier et implémenter des règles de validation du modèle.</span><span class="sxs-lookup"><span data-stu-id="2eb96-129">The last significant extension introduced by the Itinerary Designer is a validation mechanism that allows you to externally, with respect to a domain-specific language (DSL), specify and implement the model validation rules.</span></span> <span data-ttu-id="2eb96-130">Le mécanisme « raccorde » l’infrastructure de validation DSL et est activé lorsque l’utilisateur clique sur **Validate** ou **valider tous les** dans le menu contextuel d’un modèle.</span><span class="sxs-lookup"><span data-stu-id="2eb96-130">The mechanism "hooks into" the DSL validation framework and is activated when the user clicks **Validate** or **Validate all** on the shortcut menu of a model.</span></span> <span data-ttu-id="2eb96-131">Il appelle l’infrastructure DSL **DslCommandSet** objet qui, à son tour, appelle le moteur de validation dans le Concepteur d’itinéraire.</span><span class="sxs-lookup"><span data-stu-id="2eb96-131">This invokes the DSL framework's **DslCommandSet** object that, in turn, calls the validation engine in the Itinerary Designer.</span></span>  
  
 <span data-ttu-id="2eb96-132">Le **ValidationEngine** classe effectue la validation d’élément de modèle à l’aide du bloc d’Application Enterprise Library Validation et consigne les erreurs de validation dans la fenêtre liste d’erreurs dans l’IDE de Microsoft Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="2eb96-132">The **ValidationEngine** class performs the model element validation using the Enterprise Library Validation Application Block and logs the validation errors to the Error List window in Microsoft Visual Studio IDE.</span></span> <span data-ttu-id="2eb96-133">La validation doit être effectuée pour chaque type d’élément dans un modèle est définie dans le fichier de configuration Enterprise Library.</span><span class="sxs-lookup"><span data-stu-id="2eb96-133">The validation that should be performed for each type of element in a model is defined in the Enterprise Library configuration file.</span></span> <span data-ttu-id="2eb96-134">Le fichier est nommé Ruleset.config et se trouve dans le dossier binaire dans lequel se trouvent tous les binaires de concepteur d’itinéraire.</span><span class="sxs-lookup"><span data-stu-id="2eb96-134">The file is named Ruleset.config and is located in the binary folder where all the Itinerary Designer binaries are located.</span></span> <span data-ttu-id="2eb96-135">L’exemple suivant est un fragment du fichier de configuration et inclut les deux règles de validation (nommés validateurs) pour le **UddiResolver** extendeur, un pour le **ServerUrl** propriété et une pour le  **ServiceKey** propriété.</span><span class="sxs-lookup"><span data-stu-id="2eb96-135">The following example is a fragment of the configuration file and includes two validation rules (named validators) for the **UddiResolver** extender, one for the **ServerUrl** property and one for the **ServiceKey** property.</span></span>  
  
```  
\<!--   
UddiResolver  
-->  
<type assemblyName="Microsoft.Practices.Services.Extenders.Resolvers.UDDI"  
 name="Microsoft.Practices.Services.Extenders.Resolvers.UDDI.UddiResolver">  
<ruleset name="Menu">  
<properties>  
<property name="ServerUrl">  
<validator type="Microsoft.Practices.Modeling.Validation.NotEmptyStringValidator, Microsoft.Practices.Modeling.Validation"  
          messageTemplate="The '{1}' property value should not be empty or null."  
          name="UddiResolver.ServerUrl not null validator"/>  
</property>  
<property name="ServiceKey">  
<validator type="Microsoft.Practices.Modeling.Validation.NotEmptyStringValidator, Microsoft.Practices.Modeling.Validation"  
          messageTemplate="The '{1}' property value should not be empty or null."  
          name="UddiResolver.ServiceKey not null validator"/>  
</property>  
</properties>  
</ruleset>  
</type>  
```  
  
 <span data-ttu-id="2eb96-136">Chaque règle identifie le programme de validation qui implémente la règle.</span><span class="sxs-lookup"><span data-stu-id="2eb96-136">Each rule identifies the validator that implements the rule.</span></span> <span data-ttu-id="2eb96-137">Le Concepteur d’itinéraire est fourni avec un grand ensemble de classes de validateur.</span><span class="sxs-lookup"><span data-stu-id="2eb96-137">The Itinerary Designer comes with a large set of validator classes.</span></span> <span data-ttu-id="2eb96-138">Ils sont regroupés dans le projet Microsoft.Practices.Modeling.Validation dans le dossier binaire du concepteur.</span><span class="sxs-lookup"><span data-stu-id="2eb96-138">They are all in the Microsoft.Practices.Modeling.Validation project in the Designer binary folder.</span></span>  
  
 <span data-ttu-id="2eb96-139">Le résultat final de l’utilisation de ce mécanisme de validation est que les utilisateurs peuvent modifier la façon dont les modèles sont validés en modifiant les règles fournies et les validateurs ou en ajoutant leurs propres règles et les validateurs de concepteurs itinéraire.</span><span class="sxs-lookup"><span data-stu-id="2eb96-139">The final result of using this validation mechanism is that Itinerary Designer users can modify how the models are validated by changing the provided rules and validators or by adding their own rules and validators.</span></span> <span data-ttu-id="2eb96-140">Cela peut être effectuée sans ouverture, la modification, la reconstruction et redéployer le DSL en effectuant le des deux étapes suivantes :</span><span class="sxs-lookup"><span data-stu-id="2eb96-140">This can be done without opening, modifying, rebuilding, and re-deploying the DSLs by performing the following two steps:</span></span>  
  
1.  <span data-ttu-id="2eb96-141">Créez une classe du programme de validation et le placer dans une bibliothèque dans le dossier binaire dans lequel le **Microsoft.Practices.Modeling.Validation.dll** se trouve la bibliothèque.</span><span class="sxs-lookup"><span data-stu-id="2eb96-141">Create a validator class and put it in a library inside the binary folder where the **Microsoft.Practices.Modeling.Validation.dll** library is located.</span></span>  
  
2.  <span data-ttu-id="2eb96-142">Ajouter des entrées dans le fichier Rules.config pour définir la propriété de quelle classe d’élément de modèle le validateur doit être appliqué.</span><span class="sxs-lookup"><span data-stu-id="2eb96-142">Add entries to the Rules.config file to define what property of what model element class the validator should be applied.</span></span>