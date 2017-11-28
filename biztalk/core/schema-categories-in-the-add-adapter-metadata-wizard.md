---
title: "Catégories de schémas dans l’Assistant Ajout d’adaptateur métadonnées | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3927c676-f60a-449e-be43-6f75e28aefe1
caps.latest.revision: "27"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 4fda24ee5ef4993c90eb82e0f406da2e06618776
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="schema-categories-in-the-add-adapter-metadata-wizard"></a><span data-ttu-id="1fd4d-102">Catégories de schémas dans l'Assistant Ajouter les métadonnées de l'adaptateur</span><span class="sxs-lookup"><span data-stu-id="1fd4d-102">Schema Categories in the Add Adapter Metadata Wizard</span></span>

## <a name="overview"></a><span data-ttu-id="1fd4d-103">Vue d'ensemble</span><span class="sxs-lookup"><span data-stu-id="1fd4d-103">Overview</span></span>
> [!NOTE]
>  <span data-ttu-id="1fd4d-104">Cette rubrique concerne uniquement les adaptateurs statiques implémentant le **IStaticAdapterConfig** interface.</span><span class="sxs-lookup"><span data-stu-id="1fd4d-104">This topic is only for static adapters that implement the **IStaticAdapterConfig** interface.</span></span>  
  
 <span data-ttu-id="1fd4d-105">Un adaptateur peut utiliser n'importe lequel des milliers de schémas disponibles pour transformer les données avant leur transmission à [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].</span><span class="sxs-lookup"><span data-stu-id="1fd4d-105">An adapter may use any one of thousands of schemas to transform data before passing it to [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].</span></span> <span data-ttu-id="1fd4d-106">Lorsque vous ajoutez des métadonnées à un projet BizTalk, utilisez l'Assistant Ajouter les métadonnées de l'adaptateur pour sélectionner un schéma dans la liste avec lequel l'adaptateur va interagir.</span><span class="sxs-lookup"><span data-stu-id="1fd4d-106">When adding metadata to a BizTalk project, use the Add Adapter Metadata Wizard to select a schema from a list of all the schemas with which the adapter interacts.</span></span>  
  
 <span data-ttu-id="1fd4d-107">Dans l'adaptateur File donné en exemple, le fichier CategorySchema.xml est une instance de schéma utilisée conjointement avec le fichier BiztalkAdapterFramework.xsd de l'infrastructure d'adaptateurs pour renseigner l'arborescence des schémas de service.</span><span class="sxs-lookup"><span data-stu-id="1fd4d-107">In the sample file adapter, the CategorySchema.xml file is a schema instance that is used in conjunction with the Adapter Framework's BiztalkAdapterFramework.xsd file to populate a tree-view organization of service schemas.</span></span>  <span data-ttu-id="1fd4d-108">Le fichier BizTalkAdapterFramework.xsd se trouve dans le dossier [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]\Developer Tools.</span><span class="sxs-lookup"><span data-stu-id="1fd4d-108">The BizTalkAdapterFramework.xsd file is located in the [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]Developer Tools folder.</span></span>  
  
 <span data-ttu-id="1fd4d-109">Vous devez créer ce fichier de sorte qu'il organise les schémas d'une façon intuitive pour votre solution.</span><span class="sxs-lookup"><span data-stu-id="1fd4d-109">You should create this file so that it organizes the schemas in a manner that is intuitive to your solution.</span></span> <span data-ttu-id="1fd4d-110">Les catégories qui se trouvent déjà dans le fichier CategorySchema.xml ne sont que des exemples de ce que vous pouvez faire dans votre propre arborescence.</span><span class="sxs-lookup"><span data-stu-id="1fd4d-110">The existing categories in CategorySchema.xml are just an example of what you can do in your own tree.</span></span> <span data-ttu-id="1fd4d-111">Les catégories ne présentent pas de pertinence particulière par rapport aux données transmises par l'exemple d'adaptateur.</span><span class="sxs-lookup"><span data-stu-id="1fd4d-111">The categories do not have any particular relevance to the data that is passed by the sample adapter.</span></span> <span data-ttu-id="1fd4d-112">L'organisation des schémas se révèle particulièrement importante avec les adaptateurs spécifiques des applications, car des milliers de schémas différents peuvent être disponibles.</span><span class="sxs-lookup"><span data-stu-id="1fd4d-112">The organization of the schemas is particularly important with application-specific adapters, where thousands of different schemas may be available.</span></span> <span data-ttu-id="1fd4d-113">Dans le cas des adaptateurs propres au transport, cette organisation en arborescence est inutile.</span><span class="sxs-lookup"><span data-stu-id="1fd4d-113">For transport-specific adapters, this tree-view organization is unnecessary.</span></span>  
  
 <span data-ttu-id="1fd4d-114">L’illustration suivante montre le **sélectionner les Services à importer** page de l’Assistant Ajout de métadonnées d’adaptateur.</span><span class="sxs-lookup"><span data-stu-id="1fd4d-114">The following figure shows the **Select Services to Import** page in the Add Adapter Metadata Wizard.</span></span>  
  
 ![](../core/media/ebiz-prog-custad-tree.gif "ebiz_prog_custad_tree")  
<span data-ttu-id="1fd4d-115">Arborescence des catégories de schémas dans l'Assistant Ajouter les métadonnées de l'adaptateur</span><span class="sxs-lookup"><span data-stu-id="1fd4d-115">Tree view of the schema categories in the Add Adapter Metadata Wizard</span></span>  


## <a name="sample-xml"></a><span data-ttu-id="1fd4d-116">Exemple de code XML</span><span class="sxs-lookup"><span data-stu-id="1fd4d-116">Sample XML</span></span>
  
 <span data-ttu-id="1fd4d-117">Le code suivant montre le fichier CategorySchema.xml :</span><span class="sxs-lookup"><span data-stu-id="1fd4d-117">The following code shows the CategorySchema.xml file:</span></span>  
  
```  
<?xml version="1.0" encoding="utf-8" ?>  
<CategoryTree>  
     <DisplayName>Services Organization</DisplayName>  
     <DisplayDescription>An organization of application services</DisplayDescription>  
     <CategoryTreeNode>  
          <DisplayName>Health Care</DisplayName>  
          <Description>Services under Health Care</Description>  
          <CategoryTreeNode>  
               <DisplayName>Administrative</DisplayName>  
               <Description>Administrative Health Care Services</Description>  
               <ServiceTreeNode>  
                    <DisplayName>Eligibility</DisplayName>  
                    <Description>Eligibility Verification Transactions</Description>  
                    <WSDLReference>ANSI X 12 270</WSDLReference>  
               </ServiceTreeNode>  
          </CategoryTreeNode>  
     </CategoryTreeNode>  
     <CategoryTreeNode>  
          <DisplayName>Manufacturing</DisplayName>  
          <Description>Manufacturing Services</Description>  
          <CategoryTreeNode>  
               <DisplayName>Inventory</DisplayName>  
               <Description>Inventory Services</Description>  
               <ServiceTreeNode>  
                    <DisplayName>Requisition</DisplayName>  
                    <Description>Requisition</Description>  
                    <WSDLReference>RequisitionService</WSDLReference>  
               </ServiceTreeNode>  
          </CategoryTreeNode>  
     </CategoryTreeNode>  
</CategoryTree>  
```  
  
 <span data-ttu-id="1fd4d-118">Les types de nœuds suivants s'affichent dans cette instance de schéma :</span><span class="sxs-lookup"><span data-stu-id="1fd4d-118">The following node types appear in this schema instance:</span></span>  
  
-   <span data-ttu-id="1fd4d-119">**Structure CategoryTree.**</span><span class="sxs-lookup"><span data-stu-id="1fd4d-119">**CategoryTree.**</span></span> <span data-ttu-id="1fd4d-120">structure de premier niveau d'un modèle d'informations système.</span><span class="sxs-lookup"><span data-stu-id="1fd4d-120">Top-level structure of a model of system information.</span></span> <span data-ttu-id="1fd4d-121">Contient aucun ou plusieurs nœuds CategoryTreeNode, ExpandableCategoryTreeNode et ServiceTreeNode.</span><span class="sxs-lookup"><span data-stu-id="1fd4d-121">Contains zero or more of the CategoryTreeNode, ExpandableCategoryTreeNode, and ServiceTreeNode nodes.</span></span>  
  
-   <span data-ttu-id="1fd4d-122">**Nœud CategoryTreeNode.**</span><span class="sxs-lookup"><span data-stu-id="1fd4d-122">**CategoryTreeNode.**</span></span> <span data-ttu-id="1fd4d-123">contient aucun ou plusieurs nœuds CategoryTreeNode et ServiceTreeNode.</span><span class="sxs-lookup"><span data-stu-id="1fd4d-123">Contains zero or more CategoryTreeNode and ServiceTreeNode nodes.</span></span> <span data-ttu-id="1fd4d-124">Servez-vous du nœud CategoryTreeNode qui s'affiche sous forme de dossier dans l'interface utilisateur pour grouper un ensemble de services associés.</span><span class="sxs-lookup"><span data-stu-id="1fd4d-124">Use the CategoryTreeNode that appears as a folder in the user interface (UI) to group a set of related services.</span></span> <span data-ttu-id="1fd4d-125">Il contient généralement le nom et la description des services à afficher.</span><span class="sxs-lookup"><span data-stu-id="1fd4d-125">Typically this contains a display name and description of the services to be displayed.</span></span> <span data-ttu-id="1fd4d-126">Un adaptateur peut utiliser un nœud CategoryTreeNode si le nombre de nœuds enfants est restreint.</span><span class="sxs-lookup"><span data-stu-id="1fd4d-126">An adapter might use a CategoryTreeNode if the number of child nodes is small.</span></span>  
  
-   <span data-ttu-id="1fd4d-127">**Nœud ExpandableCategoryTreeNode.**</span><span class="sxs-lookup"><span data-stu-id="1fd4d-127">**ExpandableCategoryTreeNode.**</span></span> <span data-ttu-id="1fd4d-128">un nœud inférieur qui est dynamiquement renseigné lorsqu'il est développé.</span><span class="sxs-lookup"><span data-stu-id="1fd4d-128">A leaf node that is dynamically populated when expanded.</span></span> <span data-ttu-id="1fd4d-129">Le nœud ExpandableCategoryTreeNode sert d'espace réservé et s'affiche sous forme de dossier dans l'interface utilisateur.</span><span class="sxs-lookup"><span data-stu-id="1fd4d-129">The ExpandableCategoryTreeNode is used as a placeholder and appears as a folder in the UI.</span></span> <span data-ttu-id="1fd4d-130">Il permet de reporter la saisie automatique des sous-éléments d'un nœud de catégorie au moment où un utilisateur clique sur le nœud pour le développer.</span><span class="sxs-lookup"><span data-stu-id="1fd4d-130">This can be used to defer populating a category node with subelements until the user clicks to expand the node.</span></span> <span data-ttu-id="1fd4d-131">Un adaptateur peut utiliser un nœud ExpandableCategoryTreeNode si une catégorie contient un nombre de nœuds enfants conséquent.</span><span class="sxs-lookup"><span data-stu-id="1fd4d-131">An adapter might use an ExpandableCategoryTreeNode if a category contains a large number of child nodes.</span></span>  
  
-   <span data-ttu-id="1fd4d-132">**ServiceTreeNode.**</span><span class="sxs-lookup"><span data-stu-id="1fd4d-132">**ServiceTreeNode.**</span></span> <span data-ttu-id="1fd4d-133">ce nœud s'affiche sous forme de document, ou nœud inférieur, dans l'interface utilisateur et représente un fichier WSDL (Web Services Description Language).</span><span class="sxs-lookup"><span data-stu-id="1fd4d-133">A ServiceTreeNode appears as a document, or leaf node, in the UI and represents a Web Services Description Language (WSDL) file.</span></span>  
  
 <span data-ttu-id="1fd4d-134">Lorsqu’un utilisateur clique sur le dossier pour développer un nœud, l’infrastructure d’adaptateurs appelle la **IStaticAdapterConfig.GetServiceOrganization** méthode sur la carte en passant le nom du nœud en tant que la valeur de la **NodeIdentifier** attribut.</span><span class="sxs-lookup"><span data-stu-id="1fd4d-134">When a user clicks the folder to expand a node, the Adapter Framework calls the **IStaticAdapterConfig.GetServiceOrganization** method on the adapter passing the name of the node as the value of the **NodeIdentifier** attribute.</span></span> <span data-ttu-id="1fd4d-135">L'adaptateur doit retourner une structure CategoryTree contenant les sous-nœuds à ajouter au nœud ExpandableCategoryTreeNode.</span><span class="sxs-lookup"><span data-stu-id="1fd4d-135">The adapter should return a CategoryTree containing the subnodes to add under the ExpandableCategoryTreeNode.</span></span> <span data-ttu-id="1fd4d-136">L'infrastructure d'adaptateurs remplace le nœud ExpandableCategoryTreeNode par un nœud CategoryTreeNode et lui ajoute les enfants de la structure CategoryTree retournée.</span><span class="sxs-lookup"><span data-stu-id="1fd4d-136">The Adapter Framework replaces the ExpandableCategoryTreeNode with a CategoryTreeNode and adds to it the children of the returned CategoryTree.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="1fd4d-137">Dans l’appel initial à **IStaticAdapterConfig.GetServiceOrganization** l’infrastructure d’adaptateurs transmet la valeur null pour l’identificateur du nœud.</span><span class="sxs-lookup"><span data-stu-id="1fd4d-137">In the initial call to **IStaticAdapterConfig.GetServiceOrganization** the Adapter Framework passes null for the node identifier.</span></span> <span data-ttu-id="1fd4d-138">L'adaptateur retourne alors la structure CategoryTree racine.</span><span class="sxs-lookup"><span data-stu-id="1fd4d-138">This tells the adapter to return the root-level CategoryTree.</span></span>  
  
 <span data-ttu-id="1fd4d-139">Le schéma ci-après est le schéma d'arborescence de catégories extrait du fichier BiztalkAdapterFramework.xsd.</span><span class="sxs-lookup"><span data-stu-id="1fd4d-139">Below is the category tree schema extracted from the BiztalkAdapterFramework.xsd file.</span></span> <span data-ttu-id="1fd4d-140">L'Assistant Ajouter les métadonnées de l'adaptateur s'en sert comme arborescence squelette pour la saisie automatique des entités dépendantes d'une application à partir d'un fichier XML.</span><span class="sxs-lookup"><span data-stu-id="1fd4d-140">This is used by the Add Adapter Metadata Wizard as the skeleton tree with which to populate with specific application-dependent entities from an XML file.</span></span> <span data-ttu-id="1fd4d-141">Dans l'exemple ci-dessous, il s'agit du fichier CategorySchema.xml.</span><span class="sxs-lookup"><span data-stu-id="1fd4d-141">In our example that file is the CategorySchema.xml file.</span></span>  
  
```  
<!-- Service Organization Tree schema used by Add Adapter Wizard -->  
    <xs:element name="CategoryTree" type="CategoryTree" />  
    <xs:complexType name="CategoryTree">  
        <xs:sequence>  
            <xs:element name="DisplayName" type="xs:string" />  
            <xs:element name="DisplayDescription" type="xs:string" />  
            <xs:choice minOccurs="0" maxOccurs="unbounded">  
                <xs:element name="ExpandableCategoryTreeNode" type="ExpandableCategoryTreeNode" minOccurs="0" maxOccurs="unbounded" />  
                <xs:element name="CategoryTreeNode" type="CategoryTreeNode" minOccurs="0" maxOccurs="unbounded" />  
                <xs:element name="ServiceTreeNode" type="ServiceTreeNode" minOccurs="0" maxOccurs="unbounded" />  
            </xs:choice>  
        </xs:sequence>  
    </xs:complexType>  
    <xs:complexType name="ExpandableCategoryTreeNode">  
        <xs:sequence>  
            <xs:element name="DisplayName" type="xs:string" />  
            <xs:element name="Description" type="xs:string" />  
        </xs:sequence>  
        <xs:attribute name="NodeIdentifier" type="xs:string" use="required"></xs:attribute>  
    </xs:complexType>  
    <xs:complexType name="CategoryTreeNode">  
        <xs:sequence>  
            <xs:element name="DisplayName" type="xs:string" />  
            <xs:element name="Description" type="xs:string" />  
            <xs:choice minOccurs="0" maxOccurs="unbounded">  
                <xs:element name="ExpandableCategoryTreeNode" type="ExpandableCategoryTreeNode" minOccurs="0" maxOccurs="unbounded" />  
                <xs:element name="CategoryTreeNode" type="CategoryTreeNode" minOccurs="0" maxOccurs="unbounded" />  
                <xs:element name="ServiceTreeNode" type="ServiceTreeNode" minOccurs="0" maxOccurs="unbounded" />  
            </xs:choice>  
        </xs:sequence>  
    </xs:complexType>  
    <xs:complexType name="ServiceTreeNode">  
        <xs:sequence>  
            <xs:element name="DisplayName" type="xs:string" />  
            <xs:element name="Description" type="xs:string" />  
            <xs:element name="WSDLReference" type="xs:string" />  
        </xs:sequence>  
    </xs:complexType>  
</xs:schema>  
```  
  
 <span data-ttu-id="1fd4d-142">Après modification du fichier CategorySchema.xml, recréez le projet AdapterManagement, puis exécutez l'Assistant Ajouter les métadonnées de l'adaptateur afin de vérifier que l'arborescence représentée dans le fichier CategorySchema.xml s'affiche correctement.</span><span class="sxs-lookup"><span data-stu-id="1fd4d-142">After modifying your CategorySchema.xml file, rebuild the AdapterManagement project, and then run the Add Adapter Metadata Wizard to ensure that the tree represented in CategorySchema.xml appears correctly.</span></span>  
  
 <span data-ttu-id="1fd4d-143">Pour plus d’informations sur l’exécution de l’Assistant Ajout de métadonnées d’adaptateur, consultez le **boîte de dialogue d’Assistant Ajouter adaptateur métadonnées** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)].</span><span class="sxs-lookup"><span data-stu-id="1fd4d-143">For information about running the Add Adapter Metadata Wizard, see the **Add Adapter Metadata Wizard Dialog Box** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)].</span></span>