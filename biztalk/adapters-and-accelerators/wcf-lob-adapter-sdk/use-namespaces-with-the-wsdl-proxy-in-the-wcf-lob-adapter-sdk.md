---
title: Utiliser des espaces de noms avec le Proxy WSDL dans WCF LOB Adapter SDK | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 781d20fa-83e3-42fa-866e-5650d5eb71a7
caps.latest.revision: "11"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: dc85d47da81d2d7425c7db4aad90ea32389f7d84
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="use-namespaces-with-the-wsdl-proxy-in-the-wcf-lob-adapter-sdk"></a><span data-ttu-id="31bdd-102">Utiliser des espaces de noms avec le Proxy WSDL dans WCF LOB Adapter SDK</span><span class="sxs-lookup"><span data-stu-id="31bdd-102">Use namespaces with the WSDL-Proxy in the WCF LOB Adapter SDK</span></span>
<span data-ttu-id="31bdd-103">Le [!INCLUDE[afproductnamelong](../../includes/afproductnamelong-md.md)] génère WSDL et des proxys pour un adaptateur à l’aide des valeurs fournies par le développeur à l’aide de la [!INCLUDE[afdevwizardnamelong](../../includes/afdevwizardnamelong-md.md)] ou spécifié dans le code par une modification de la variable privée SERVICENAMESPACE et/ou `Namespace` propriété de l’adaptateur.</span><span class="sxs-lookup"><span data-stu-id="31bdd-103">The [!INCLUDE[afproductnamelong](../../includes/afproductnamelong-md.md)] generates WSDL and proxies for an adapter using values supplied by the developer using the [!INCLUDE[afdevwizardnamelong](../../includes/afdevwizardnamelong-md.md)] or specified in code through modification of the SERVICENAMESPACE private variable and/or the `Namespace` property of the adapter.</span></span>  
  
 <span data-ttu-id="31bdd-104">Les types de schéma et les éléments définis dans le \<WSDL : types >\<schéma > utilisent le {OperationNamespace} par défaut.</span><span class="sxs-lookup"><span data-stu-id="31bdd-104">The schema types and elements defined within the \<wsdl:types>\<schema> use the {OperationNamespace} by default.</span></span> <span data-ttu-id="31bdd-105">Si un type particulier a un TypeNamespace substituée définie dans le **TypeMetadata** de l’objet, cet espace de noms est utilisé pour le type complexe et/ou ou définition de l’élément.</span><span class="sxs-lookup"><span data-stu-id="31bdd-105">If a particular type has an overridden TypeNamespace set in the **TypeMetadata** object, that namespace is used for the complex type and/or or element definition.</span></span>  
  
## <a name="impact-on-wsdl"></a><span data-ttu-id="31bdd-106">Impact sur WSDL</span><span class="sxs-lookup"><span data-stu-id="31bdd-106">Impact on WSDL</span></span>  
 <span data-ttu-id="31bdd-107">Le tableau suivant montre comment les différents espaces de noms dans un adaptateur personnalisé affectent le WSDL correspondant.</span><span class="sxs-lookup"><span data-stu-id="31bdd-107">The following table shows how the different namespaces in a custom adapter affect the corresponding WSDL.</span></span> <span data-ttu-id="31bdd-108">Dans la table, ~ {OperationNamespace} est le mappage d’espace de noms de classe d’un URI ; par exemple, si {OperationNamespace} est « myscheme://a.b/c », ~ {OperationNamespace} sera myscheme.a.b.c.</span><span class="sxs-lookup"><span data-stu-id="31bdd-108">In the table, ~{OperationNamespace} is the class namespace mapping of a URI; for example, if {OperationNamespace} is "myscheme://a.b/c", ~{OperationNamespace} will be myscheme.a.b.c.</span></span>  
  
|<span data-ttu-id="31bdd-109">Construction WSDL</span><span class="sxs-lookup"><span data-stu-id="31bdd-109">WSDL Construct</span></span>|<span data-ttu-id="31bdd-110">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="31bdd-110">Syntax</span></span>|  
|--------------------|------------|  
|<span data-ttu-id="31bdd-111">TargetNamespace WSDL,</span><span class="sxs-lookup"><span data-stu-id="31bdd-111">WSDL targetNamespace,</span></span><br /><br /> <span data-ttu-id="31bdd-112">Xmlns:TS</span><span class="sxs-lookup"><span data-stu-id="31bdd-112">Xmlns:ts</span></span>|<span data-ttu-id="31bdd-113">{Personnalisé} Adapter.Namespace</span><span class="sxs-lookup"><span data-stu-id="31bdd-113">{Custom}Adapter.Namespace</span></span>|  
|<span data-ttu-id="31bdd-114">\<WSDL : portType ></span><span class="sxs-lookup"><span data-stu-id="31bdd-114">\<wsdl:portType></span></span>|<span data-ttu-id="31bdd-115">{schéma de}. ~ {OperationNamespace}</span><span class="sxs-lookup"><span data-stu-id="31bdd-115">{scheme}.~{OperationNamespace}</span></span>|  
|<span data-ttu-id="31bdd-116">Nom du Message d’entrée WSDL</span><span class="sxs-lookup"><span data-stu-id="31bdd-116">WSDL Input Message Name</span></span>|<span data-ttu-id="31bdd-117">{schéma de}. ~ {OperationNamespace} _ {NomOpération} _InputMessage</span><span class="sxs-lookup"><span data-stu-id="31bdd-117">{scheme}.~{OperationNamespace}_{OperationName}_InputMessage</span></span>|  
|<span data-ttu-id="31bdd-118">Nom de Message de sortie WSDL</span><span class="sxs-lookup"><span data-stu-id="31bdd-118">WSDL Output Message Name</span></span>|<span data-ttu-id="31bdd-119">{schéma de}. ~ {OperationNamespace} _ {NomOpération} _OutputMessage</span><span class="sxs-lookup"><span data-stu-id="31bdd-119">{scheme}.~{OperationNamespace}_{OperationName}_OutputMessage</span></span>|  
|<span data-ttu-id="31bdd-120">\<WSDL : types >\<schéma > targetNamespace</span><span class="sxs-lookup"><span data-stu-id="31bdd-120">\<wsdl:types>\<schema> targetNamespace</span></span>|<span data-ttu-id="31bdd-121">{schéma}  :// {OperationNamespace}</span><span class="sxs-lookup"><span data-stu-id="31bdd-121">{scheme}://{OperationNamespace}</span></span>|  
|<span data-ttu-id="31bdd-122">\<élément >\<complexType ></span><span class="sxs-lookup"><span data-stu-id="31bdd-122">\<element>\<complexType></span></span>|<span data-ttu-id="31bdd-123">Utilisez {TypeNamespace} si sa valeur n’est pas null ou vide.</span><span class="sxs-lookup"><span data-stu-id="31bdd-123">Use {TypeNamespace} if its value is not null or empty.</span></span>|  
  
## <a name="impact-on-proxy"></a><span data-ttu-id="31bdd-124">Impact sur le serveur Proxy</span><span class="sxs-lookup"><span data-stu-id="31bdd-124">Impact on Proxy</span></span>  
 <span data-ttu-id="31bdd-125">Trois attributs différents dans le proxy sont affectées par les espaces de noms :</span><span class="sxs-lookup"><span data-stu-id="31bdd-125">Three different attributes in the proxy are affected by namespaces:</span></span>  
  
-   <span data-ttu-id="31bdd-126">[**System.ServiceModel.ServiceContractAttribute**(nom = « {schéma}. ~ {OperationNamespace} », Namespace="{Custom}Adapter.Namespace »]</span><span class="sxs-lookup"><span data-stu-id="31bdd-126">[**System.ServiceModel.ServiceContractAttribute**(Name="{scheme}.~{OperationNamespace}", Namespace="{Custom}Adapter.Namespace”]</span></span>  
  
-   <span data-ttu-id="31bdd-127">[**System.ServiceModel.MessageContractAttribute**(attributs WrapperName = « DivideResponse », WrapperNamespace = « {schéma}  :// {OperationNamespace} », IsWrapped = true)]</span><span class="sxs-lookup"><span data-stu-id="31bdd-127">[**System.ServiceModel.MessageContractAttribute**(WrapperName="DivideResponse", WrapperNamespace="{scheme}://{OperationNamespace}", IsWrapped=true)]</span></span>  
  
-   <span data-ttu-id="31bdd-128">[**System.ServiceModel.MessageBodyMemberAttribute**(Namespace = « {schéma}  :// {TypeNamespace} », ordre = 0)]</span><span class="sxs-lookup"><span data-stu-id="31bdd-128">[**System.ServiceModel.MessageBodyMemberAttribute**(Namespace="{scheme}://{TypeNamespace}", Order=0)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="31bdd-129">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="31bdd-129">See Also</span></span>  
 [<span data-ttu-id="31bdd-130">Recommandées de développement à l’aide de WCF LOB Adapter SDK</span><span class="sxs-lookup"><span data-stu-id="31bdd-130">Development best practices using the WCF LOB Adapter SDK</span></span>](../../adapters-and-accelerators/wcf-lob-adapter-sdk/development-best-practices-using-the-wcf-lob-adapter-sdk.md)