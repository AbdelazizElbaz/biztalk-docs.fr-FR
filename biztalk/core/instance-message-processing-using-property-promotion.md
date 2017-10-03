---
title: "Le traitement des messages à l’aide de la Promotion des propriétés de l’instance | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 753571b8-4609-4ac4-a974-8bd6dfecb077
caps.latest.revision: "11"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 288657d43443582c5a05df5dd6e67059eca572e9
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="instance-message-processing-using-property-promotion"></a>Traitement des messages d'instance à l'aide de la promotion de propriétés
Promotion des propriétés à l’aide de la **champ de propriété** méthode requiert la création d’un schéma de propriété. Pour plus d’informations sur la création d’un schéma de propriété, consultez [comment créer des schémas de propriété](../core/how-to-create-property-schemas.md). Comme avec toutes les promotions de propriété, vous utilisez la **promouvoir les propriétés** boîte de dialogue, qui est accessible à l’aide de la **promouvoir les propriétés** propriété de la **schéma** nœud schémas de message.  
  
> [!NOTE]
>  Vous devez choisir un pipeline qui promeut les propriétés afin de pouvoir accéder à et utiliser les propriétés promues. Par exemple, si vous utilisez le pipeline PassthruReceive, aucune propriété ne sera promue et le routage basé sur le contenu ainsi que d'autres fonctionnalités ne fonctionneront pas comme prévu.  
  
 Dans le **promouvoir les propriétés** boîte de dialogue zone, assurez-vous que le **champs de propriété** onglet est sélectionné dans la partie droite de la boîte de dialogue. Vérifiez ensuite le schéma de propriété approprié est inclus dans la liste des schémas de propriété en haut de la **champs de propriété** onglet. Si nécessaire, utilisez le bouton de dossier pour sélectionner le schéma de propriété approprié à l’aide de la **sélecteur de Type BizTalk** boîte de dialogue. Ensuite, développez les nœuds dans l’arborescence de schéma sur le côté gauche de la boîte de dialogue pour rechercher et sélectionner le **Fieldelement** nœud ou **attribut de champ** nœud que vous souhaitez promouvoir en tant que champ de propriété, puis cliquez sur  **Ajouter**. Enfin, utilisez la liste déroulante dans le **propriété** colonne de la **dictionnaire des champs de propriété** table pour sélectionner un **élément de champ** nœud dans un schéma de propriété avec lequel associer la propriété promue. Pour obtenir des instructions sur la promotion des propriétés pour les champs de propriété à l’aide de la **promouvoir les propriétés** ox de la boîte de dialogue, consultez [comment copier des données dans le contexte du Message en tant que champs de propriété](../core/how-to-copy-data-to-the-message-context-as-property-fields.md).  
  
> [!NOTE]
>  Vous pouvez également promouvoir un **enregistrement** nœud à un **élément de champ** nœud dans le schéma de propriété, mais uniquement si le **le Type de contenu** propriété de la **enregistrement**nœud a la valeur **SimpleContent**.  
  
> [!NOTE]
>  Une même propriété peut être promue plusieurs fois dans un schéma tant que les promotions sont effectuées sous différents nœuds racine. En effet, le message est validé par rapport à un nœud racine unique et seules les propriétés promues sous ce nœud racine sont évaluées lors de l'exécution.  
  
 Pour supprimer un **élément de champ** nœud ou **attribut de champ** à partir de l’ensemble des propriétés promues en tant que champs de propriété, sélectionnez la propriété promue dans le **dictionnaire des champs de propriété**  table sur le **champs de propriété** onglet, puis cliquez sur **supprimer**.  
  
 Le **chemin d’accès du nœud** colonne dans la **dictionnaire des champs de propriété** table indique le XPath vers le nœud de schéma correspondant à la propriété promue. Vous pouvez modifier cette valeur directement à l’aide du **modifier le XPath d’Instance** boîte de dialogue. Vous pouvez ouvrir cette boîte de dialogue en cliquant sur le bouton de sélection (**...** ) bouton qui apparaît à l’extrémité droite de la cellule correspondante lorsque vous sélectionnez cette cellule. La modification directe de valeurs XPath doit se faire avec discernement, car les XPath qui ne peuvent pas être résolus par l'Éditeur BizTalk empêchent le bon déroulement des opérations de validation.  
  
 L’Éditeur BizTalk fournit également une commande simplifiée pour la promotion de propriétés à l’aide de la **champ de propriété** mécanisme. Cette commande est appelée Promotion rapide, et il est disponible à l’aide du **promouvoir &#124; Promotion rapide** commande dans les menus BizTalk et contextuel. Cette commande promeut sélectionné **champ** nœud (ou **enregistrement** nœud) à un champ de propriété qui est créé automatiquement dans le schéma de propriété spécifié par le **nom du schéma de propriété par défaut**  propriété dans le **Pages de propriétés** boîte de dialogue du schéma contenant. Pour obtenir des instructions sur la promotion des propriétés pour les champs de propriété à l’aide de la commande Promotion rapide, consultez [comment copier des données dans le contexte du Message en tant que champs de propriété](../core/how-to-copy-data-to-the-message-context-as-property-fields.md).  
  
 Lorsque vous assurez la promotion d'une propriété à l'aide du mécanisme des champs de propriété, deux fragments de langage XSD (XML Schema Definition) sont ajoutés à la représentation XSD du schéma de message. Le premier fragment XSD est un fragment d’annotation associé à la **schéma** qui identifie le schéma de propriété correspondant, comme dans l’exemple suivant :  
  
```  
<xs:annotation>  
    <xs:appinfo>  
        <b:imports>  
            <b:namespace prefix="ns0"  
                uri="http://BizTalk_Server_Project1.PropertySchema1"  
                location=".\propertyschema1.xsd" />  
        </b:imports>  
    </xs:appinfo>  
</xs:annotation>  
```  
  
 Le deuxième fragment XSD est un fragment d’annotation associé à la **racine** élément (indépendamment de si elle a été renommé) qui identifie le **élément de champ** nœud ou **champ Attribut** les valeurs de nœud qui ont été promues à l’aide de la propriété de champ mécanisme, comme dans l’exemple suivant :  
  
```  
<xs:annotation>  
    <xs:appinfo>  
        <b:properties>  
            <b:property name="ns0:PromProp1"  
                xpath="/*[local-name()='Root' and namespace-  
                 uri()='http://BizTalk_Server_Project1.Schema2']/  
                 *[local-name()='MyRec1']/@*[local-  
                 name()='Field_x0020_1']" />  
            <b:property name="ns0:PromProp2"  
                xpath="/*[local-name()='Root' and namespace-  
                 uri()='http://BizTalk_Server_Project1.Schema2']/  
                 *[local-name()='MyRec1']/*[local-  
                 name()='ProgramManager']/*[local-name()='Name']" />  
        </b:properties>  
    </xs:appinfo>  
</xs:annotation>  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Façons d’utiliser le contenu de Message pour le traitement des messages de contrôle](../core/ways-to-use-message-content-to-control-message-processing.md)   
 [Comment copier des données dans le contexte du Message en tant que champs de propriété](../core/how-to-copy-data-to-the-message-context-as-property-fields.md)