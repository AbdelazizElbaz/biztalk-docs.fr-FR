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
# <a name="schema-categories-in-the-add-adapter-metadata-wizard"></a>Catégories de schémas dans l'Assistant Ajouter les métadonnées de l'adaptateur

## <a name="overview"></a>Vue d'ensemble
> [!NOTE]
>  Cette rubrique concerne uniquement les adaptateurs statiques implémentant le **IStaticAdapterConfig** interface.  
  
 Un adaptateur peut utiliser n'importe lequel des milliers de schémas disponibles pour transformer les données avant leur transmission à [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]. Lorsque vous ajoutez des métadonnées à un projet BizTalk, utilisez l'Assistant Ajouter les métadonnées de l'adaptateur pour sélectionner un schéma dans la liste avec lequel l'adaptateur va interagir.  
  
 Dans l'adaptateur File donné en exemple, le fichier CategorySchema.xml est une instance de schéma utilisée conjointement avec le fichier BiztalkAdapterFramework.xsd de l'infrastructure d'adaptateurs pour renseigner l'arborescence des schémas de service.  Le fichier BizTalkAdapterFramework.xsd se trouve dans le dossier [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]\Developer Tools.  
  
 Vous devez créer ce fichier de sorte qu'il organise les schémas d'une façon intuitive pour votre solution. Les catégories qui se trouvent déjà dans le fichier CategorySchema.xml ne sont que des exemples de ce que vous pouvez faire dans votre propre arborescence. Les catégories ne présentent pas de pertinence particulière par rapport aux données transmises par l'exemple d'adaptateur. L'organisation des schémas se révèle particulièrement importante avec les adaptateurs spécifiques des applications, car des milliers de schémas différents peuvent être disponibles. Dans le cas des adaptateurs propres au transport, cette organisation en arborescence est inutile.  
  
 L’illustration suivante montre le **sélectionner les Services à importer** page de l’Assistant Ajout de métadonnées d’adaptateur.  
  
 ![](../core/media/ebiz-prog-custad-tree.gif "ebiz_prog_custad_tree")  
Arborescence des catégories de schémas dans l'Assistant Ajouter les métadonnées de l'adaptateur  


## <a name="sample-xml"></a>Exemple de code XML
  
 Le code suivant montre le fichier CategorySchema.xml :  
  
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
  
 Les types de nœuds suivants s'affichent dans cette instance de schéma :  
  
-   **Structure CategoryTree.** structure de premier niveau d'un modèle d'informations système. Contient aucun ou plusieurs nœuds CategoryTreeNode, ExpandableCategoryTreeNode et ServiceTreeNode.  
  
-   **Nœud CategoryTreeNode.** contient aucun ou plusieurs nœuds CategoryTreeNode et ServiceTreeNode. Servez-vous du nœud CategoryTreeNode qui s'affiche sous forme de dossier dans l'interface utilisateur pour grouper un ensemble de services associés. Il contient généralement le nom et la description des services à afficher. Un adaptateur peut utiliser un nœud CategoryTreeNode si le nombre de nœuds enfants est restreint.  
  
-   **Nœud ExpandableCategoryTreeNode.** un nœud inférieur qui est dynamiquement renseigné lorsqu'il est développé. Le nœud ExpandableCategoryTreeNode sert d'espace réservé et s'affiche sous forme de dossier dans l'interface utilisateur. Il permet de reporter la saisie automatique des sous-éléments d'un nœud de catégorie au moment où un utilisateur clique sur le nœud pour le développer. Un adaptateur peut utiliser un nœud ExpandableCategoryTreeNode si une catégorie contient un nombre de nœuds enfants conséquent.  
  
-   **ServiceTreeNode.** ce nœud s'affiche sous forme de document, ou nœud inférieur, dans l'interface utilisateur et représente un fichier WSDL (Web Services Description Language).  
  
 Lorsqu’un utilisateur clique sur le dossier pour développer un nœud, l’infrastructure d’adaptateurs appelle la **IStaticAdapterConfig.GetServiceOrganization** méthode sur la carte en passant le nom du nœud en tant que la valeur de la **NodeIdentifier** attribut. L'adaptateur doit retourner une structure CategoryTree contenant les sous-nœuds à ajouter au nœud ExpandableCategoryTreeNode. L'infrastructure d'adaptateurs remplace le nœud ExpandableCategoryTreeNode par un nœud CategoryTreeNode et lui ajoute les enfants de la structure CategoryTree retournée.  
  
> [!NOTE]
>  Dans l’appel initial à **IStaticAdapterConfig.GetServiceOrganization** l’infrastructure d’adaptateurs transmet la valeur null pour l’identificateur du nœud. L'adaptateur retourne alors la structure CategoryTree racine.  
  
 Le schéma ci-après est le schéma d'arborescence de catégories extrait du fichier BiztalkAdapterFramework.xsd. L'Assistant Ajouter les métadonnées de l'adaptateur s'en sert comme arborescence squelette pour la saisie automatique des entités dépendantes d'une application à partir d'un fichier XML. Dans l'exemple ci-dessous, il s'agit du fichier CategorySchema.xml.  
  
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
  
 Après modification du fichier CategorySchema.xml, recréez le projet AdapterManagement, puis exécutez l'Assistant Ajouter les métadonnées de l'adaptateur afin de vérifier que l'arborescence représentée dans le fichier CategorySchema.xml s'affiche correctement.  
  
 Pour plus d’informations sur l’exécution de l’Assistant Ajout de métadonnées d’adaptateur, consultez le **boîte de dialogue d’Assistant Ajouter adaptateur métadonnées** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)].