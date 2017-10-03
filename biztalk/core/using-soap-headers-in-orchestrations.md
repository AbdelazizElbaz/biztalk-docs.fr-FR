---
title: "Utilisation des en-têtes SOAP dans les Orchestrations | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- SOAP headers, orchestrations
- SOAP headers, code samples
- SOAP headers, creating
- SOAP headers, properties
- Web services, SOAP headers
- orchestrations, SOAP headers
- creating, SOAP headers
ms.assetid: 4754dd23-386b-4093-8ea4-4da6b4d9279c
caps.latest.revision: "11"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: faae7013c824926adea67feab296e1993f93e326
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="using-soap-headers-in-orchestrations"></a>Utilisation des en-têtes SOAP dans les Orchestrations
Les schémas de propriété permettent aux orchestrations de définir des propriétés de contexte d'en-tête SOAP. L'Éditeur BizTalk vous permet de définir ces propriétés.  
  
## <a name="defining-soap-header-context-properties-with-property-schemas"></a>Définition de propriétés de contexte d'en-tête SOAP à l'aide de schémas de propriété  
 Un schéma de propriété est requis pour utiliser dans les orchestrations des propriétés de contexte d'en-tête SOAP définies. Le schéma de propriété doit avoir l’espace de noms cible **http://schemas.microsoft.com/BizTalk/2003/SOAPHeader**et le **Property Schema Base** propriété  **MessageContextPropertyBase**. Chaque nom d'élément racine du schéma de propriété doit correspondre au nom de l'élément racine de l'en-tête SOAP défini. Vous pouvez ensuite définir des valeurs pour les propriétés de contexte en reprenant l'espace de noms du schéma de propriété et le nom de la propriété.  
  
> [!NOTE]
>  L’espace de noms du schéma de propriété est différente de l’espace de noms du schéma cible (**http://schemas.microsoft.com/BizTalk/2003/SOAPHeader**). Votre espace de noms peut prendre la forme de n'importe quelle chaîne ; toutefois, il utilise généralement la valeur par défaut qu'est le nom du projet.  
  
 Le code suivant illustre l’assignation d’une propriété de contexte d’en-tête SOAP dans lequel l’espace de noms de schéma de propriété est **SOAPHeader** avec le nom de la propriété **OrigDest**:  
  
```  
requestMessageInstance(SOAPHeader.OrigDest) = stringVar;  
```  
  
 Pour plus d’informations sur les schémas de propriété et les propriétés de contexte, consultez [les schémas de propriété](../core/property-schemas.md).  
  
## <a name="using-biztalk-editor-to-set-soap-header-context-properties"></a>Utilisation de l'Éditeur BizTalk pour définir des propriétés de contexte d'en-tête SOAP  
 Pour les orchestrations, les propriétés de contexte d'en-tête SOAP sont définies sur les chaînes qui contiennent des données XML. Vous pouvez définir celles-ci à l’aide de l’éditeur d’Expression BizTalk dans un **assignation du Message** ou **Expression** forme.  
  
 L'exemple suivant illustre la chaîne définissant la propriété de contexte :  
  
```  
RequestMessageInstance(SOAPHeader.OrigDest) = "<?xml version=\"1.0\"?>  
<OrigDest xmlns=\"http://SOAPHeaderSchemas.OrigDestSOAPHeader\">  
<Origination>Home</Origination>  
<Destination>Work</Destination>  
</OrigDest>"  
```  
  
## <a name="using-biztalk-editor-to-create-an-instance-of-a-soap-header-root-element"></a>Utilisation de l'Éditeur BizTalk pour créer une instance d'un élément racine d'en-tête SOAP  
 Il peut être difficile de configurer l'en-tête SOAP sur la chaîne appropriée. Lors de l'ajout d'une référence Web à un projet BizTalk, toutes les parties d'un message Web complexe sont ajoutées en tant qu'éléments racines au fichier Reference.xsd. Ce fichier contient également les éléments racines de chaque en-tête SOAP défini. Pour garantir que vous ayez défini l'en-tête SOAP sur la bonne chaîne, il est recommandé d'utiliser l'Éditeur BizTalk pour créer une instance de l'élément racine de l'en-tête SOAP correspondant à Reference.xsd. Les données de l'instance générées ou les données de l'instance peuvent être utilisées directement ou servir à contenir les données réelles.  
  
 Pour plus d’informations sur l’utilisation de l’Éditeur BizTalk pour générer des données d’instance, consultez [comment générer des Messages d’Instance](../core/how-to-generate-instance-messages.md).  
  
## <a name="creating-an-xmldocument-to-set-context-properties"></a>Création d'un élément XmlDocument pour définir des propriétés de contexte  
 Vous pouvez définir des propriétés de contexte en créant un **XmlDocument** et l’écriture de la valeur de chaîne de la **XmlDocument** à la propriété de contexte. Vous déclarez une variable de type **XMLDocument** et affecter les données XML.  
  
 L’exemple suivant illustre la définition d’une déclaration d’une variable de type **XMLDocument** et affecter les données XML :  
  
```  
xmlDoc.LoadXml("<?xml version=\"1.0\"?><OrigDest xmlns=\"http://SOAPHeaderSchemas.OrigDestSOAPHeader\"><Origination>Home</Origination><Destination>Work</Destination></OrigDest>");  
```  
  
 L'exemple suivant illustre la configuration de la propriété de contexte :  
  
```  
RequestMessageInstance(SOAPHeader.OrigDest) = xmlDoc.OuterXml;  
```  
  
 Pour plus d’informations sur l’utilisation de l’éditeur d’Expression BizTalk, consultez [spécifications et Limitations pour les Expressions](../core/requirements-and-limitations-for-expressions.md). Pour plus d’informations sur l’appel des classes .NET, consultez [construction de Messages dans le Code utilisateur](../core/constructing-messages-in-user-code.md).  
  
## <a name="creating-soap-headers-for-a-soap-request"></a>Création d'en-têtes SOAP pour une requête SOAP  
 Lors de la création d'en-têtes SOAP pour une requête SOAP, vous devez en premier lieu vous assurer d'avoir correctement créé les en-têtes SOAP. L'adaptateur SOAP ne vérifie pas le contenu des propriétés de contexte d'un en-tête SOAP.  
  
> [!NOTE]
>  Si l'en-tête est incorrect, BizTalk ne sera pas en mesure d'envoyer la requête SOAP au service Web.  
  
 La réponse SOAP que BizTalk renvoie au service Web est également susceptible de contenir des en-têtes SOAP. Vous pouvez uniquement accéder à ces en-têtes s'il s'agit d'en-têtes SOAP définis.  
  
> [!NOTE]
>  Les services Web utilisés prennent uniquement en charge les en-têtes SOAP définis.  
  
 Pour plus d’informations sur les en-têtes SOAP définis, consultez [à l’aide des en-têtes SOAP](../core/using-soap-headers.md). Les en-têtes SOAP de réponse sont définis en tant que propriétés de contexte grâce à la même syntaxe que celle des en-têtes SOAP de requête.  
  
 Le code suivant illustre l'accès aux en-têtes SOAP de réponse :  
  
```  
stringVar = ResponseMessageInstance(SOAPHeader.OrigDest);  
```  
  
 Les valeurs contenues dans les propriétés de contexte correspondent à des chaînes comportant des données XML. Vous pouvez définir celles-ci à l’aide d’éditeur d’Expression BizTalk dans un **assignation du Message** ou **Expression** forme. Chargement de la chaîne dans un **XmlDocument** et utiliser des requêtes XPath pour accéder aux champs spécifiques.  
  
 Pour plus d’informations sur la création de documents XML dans Éditeur d’Expression BizTalk, consultez [langage XLANG-s](../core/xlang-s-language.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Langage XLANG-s](../core/xlang-s-language.md)   
 [En-têtes SOAP avec les Services Web utilisés](../core/soap-headers-with-consumed-web-services.md)