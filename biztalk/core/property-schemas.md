---
title: "Schémas de propriété | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 8018bb72-a037-4eeb-bbbe-dd0cc6209aec
caps.latest.revision: "14"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: d2fb50536b2521e77994baf0b6457206614b7eed
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="property-schemas"></a>Schémas de propriété

## <a name="promoted-properties"></a>Propriétés promues
Dans Microsoft [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)], les propriétés promues permettent à divers composants BizTalk Server d'accéder à des éléments clés de données, connues dans ce contexte sous le nom de champs distinctifs et de champs de propriétés et qui arrivent dans un message d'instance sans avoir besoin de savoir comment les rechercher dans le message lui-même. Vous pouvez déterminer les éléments de données qui requièrent la promotion à un niveau plus visible pour des types de messages différents. Selon la manière dont vous choisissez de promouvoir ces champs, vous pourrez avoir besoin de créer et de définir un schéma de propriété associé.  
  
> [!NOTE]
>  Les propriétés promues sont limitées à des éléments/attributs non répétés.  
  
 Les champs distinctifs ne sont accessibles que dans les orchestrations et ne nécessitent pas la création d'un schéma de propriété correspondant. Si vous avez uniquement besoin d'accéder à des données de message promues à partir d'une orchestration, vous pouvez les promouvoir sous la forme d'un ou de plusieurs champs distinctifs.  
  
 Les champs de propriété sont accessibles à partir de divers composants BizTalk Server et notamment à partir de pipelines et d'orchestrations. Les champs de propriétés peuvent également être utilisés pour le routage des messages. Si vous avez besoin d'accéder à des données de message promues à partir de contextes autres que des orchestrations, vous devez créer un ou plusieurs schémas de propriété pour décrire les données dont vous assurez la promotion.  
  
 Un schéma de propriété est un schéma spécial que l'on associe à un schéma de message. On l'utilise pour la promotion de valeurs spécifiques à partir d'un message d'instance vers le contexte de message. La promotion de propriété fournit un mécanisme centralisé pour extraire des éléments d'information clés que vous définissez à partir d'un message d'instance et pour rendre ces éléments plus accessibles aux composants BizTalk Server qui gèrent le message lors de sa transmission via BizTalk Server.  
  
## <a name="create-property-schema-overview"></a>Créer la vue d’ensemble du schéma de propriété
 Vous pouvez automatiquement créer un schéma de propriété par défaut en utilisant la fonctionnalité de promotion rapide de BizTalk Server. C'est la méthode la plus aisée pour créer le schéma de propriété requis par la promotion de champ de propriété. Pour plus d’informations sur la réalisation de promotions rapides, consultez [comment copier des données dans le contexte du Message en tant que champs de propriété](../core/how-to-copy-data-to-the-message-context-as-property-fields.md).  
  
 Vous pouvez également créer le nouveau schéma de propriété. Lorsqu’un projet BizTalk est ouvert, sélectionnez le projet BizTalk, avec le bouton droit et sélectionnez **ajouter**, cliquez sur **un nouvel élément**, puis cliquez sur **schéma**.  
  
> [!NOTE]
>  - Si un schéma de propriété est associé à un schéma de message, ils doivent tous deux faire partie du même projet BizTalk. Séparer un schéma de propriété de son schéma de message associé dans divers projets BizTalk n'est pas pris en charge.  
>
>  - Si vous disposez de deux schémas de propriété ayant le même espace de noms, bien qu'ils soient définis dans des assemblys différents, les schémas ne seront pas résolus correctement lors de l'exécution. Vous obtiendrez une erreur de routage lors de l'exécution.  

## <a name="distinguished-fields-and-property-fields"></a>Les champs distinctifs et les champs de propriété 
 Il existe deux types de promotions de propriétés : champs distinctifs et les champs de propriété. Le deuxième cité utilise des schémas de propriété. Dans l’Éditeur BizTalk, vous gérez ces deux types de promotions de propriétés à l’aide de la **promouvoir les propriétés** boîte de dialogue, vous accédez en utilisant le **promouvoir les propriétés** propriété de la  **Schéma** nœud.  
  
> [!NOTE]
>  - Il existe certaines restrictions concernant les valeurs qu'il est possible de promouvoir. Pour plus d’informations, consultez le tableau dans [promotion des propriétés](../core/promoting-properties.md).  
>
>  - Les champs distinctifs n'apparaissent pas dans les expressions de filtre. C'est uniquement le cas des champs de propriété.  
  
 Les schémas de propriété sont simples comparés aux schémas de message. Dans l’arborescence du schéma, vous êtes uniquement autorisé à insérer **élément de champ** nœuds en tant que nœuds enfants immédiats de le **schéma** nœud, en créant une structure qui comprend deux niveaux. Dans la plupart des cas, vous définissez les propriétés de la **élément de champ** nœuds comme vous le feriez pour **élément de champ** nœuds figurant dans un schéma de message. Vous êtes limité à utilisation des seuls types simples XSD.  
  
> [!IMPORTANT]
>  Ne renommez pas un schéma utilisé par un autre schéma. Cela concerne également les schémas de propriété pour lesquels des promotions ont déjà été établies. Si vous ne respectez pas cette règle, le schéma utilisé ne pourra pas retrouver l'autre schéma, car le nom qu'il contient ne sera plus exact.  
  
 Le **Property Schema Base** propriété est unique **élément de champ** nœuds tels qu’ils apparaissent dans les schémas de propriété. Cette propriété est vide par défaut, mais peut être définie avec la valeur **MessageDataPropertyBase** ou **MessageContextPropertyBase**, ce qui engendre une **propSchFieldBase** attribut ajouté à la **fieldInfo** élément d’annotation avec une ou l’autre de ces valeurs.  
  
 Lorsque le **propSchFieldBase** attribut a la valeur **MessageDataPropertyBase**, cela signifie que la valeur de la propriété promue correspond aux données dans le message, telles que la valeur d’un champ. Lorsque le **propSchFieldBase** attribut a la valeur **MessageContextPropertyBase**, cela signifie que la valeur de la propriété promue peut-être provenir d’un autre endroit, par exemple une enveloppe, ou qu’il peut être définie par un composant de pipeline.  
  
 **Élément de champ** nœuds dans les schémas de propriété possèdent également une propriété appelée **des informations sensibles**, lorsque la valeur **Oui**, empêche la valeur correspondante d’être visible à partir de L’Explorateur BizTalk et le message d’événement et instances de service de suivi, conservant ainsi sa nature confidentielle.  Consultez **des informations sensibles** [!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)] pour plus d’informations.
  
 La représentation de langage XSD (XML Schema Definition) suivante d'un schéma de propriété contient une annotation associée à l'élément de schéma qui identifie ce schéma en tant que schéma de propriété (schema_type="property"). Il contient également trois **Fieldelement** nœuds ci-dessous le **schéma** nœud. La première **élément de champ** nœud, nommé PromProp1, n’a pas une valeur définie pour sa **Property Schema Base** propriété, mais les deux derniers **élément de champ** nœuds ont qui propriété **MessageDataPropertyBase** et **MessageContextPropertyBase**, respectivement.  
  
```  
<?xml version="1.0" encoding="utf-16" ?>   
<xs:schema xmlns="http://BizTalk_Server_Project1.PropertySchema1"  
           xmlns:b="http://schemas.microsoft.com/BizTalk/2003"  
           targetNamespace="http://BizTalk_Server_Project1.PropertySchema1"  
           xmlns:xs="http://www.w3.org/2001/XMLSchema">  
    <xs:annotation>  
       <xs:appinfo>  
  
        </xs:appinfo>  
    </xs:annotation>  
    <xs:element name="" type="xs:string">  
        <xs:annotation>  
            <xs:appinfo>  
  
            </xs:appinfo>  
        </xs:annotation>  
    </xs:element>  
    <xs:element name="" type="xs:string">  
        <xs:annotation>  
            <xs:appinfo>  
  
            </xs:appinfo>  
        </xs:annotation>  
    </xs:element>  
    <xs:element name="" type="xs:string">  
        <xs:annotation>  
            <xs:appinfo>  
  
            </xs:appinfo>  
        </xs:annotation>  
    </xs:element>  
</xs:schema>  
  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Différents Types de schémas BizTalk](../core/different-types-of-biztalk-schemas.md)