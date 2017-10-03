---
title: "Création de schémas à l’aide de l’Éditeur BizTalk | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 03fac91b-5b67-4baf-968c-294c525d3018
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: fb9e4c6496f43a9602ad56bc0e095d98f2da90d9
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="create-schemas-using-biztalk-editor"></a>Créer des schémas à l’aide de l’Éditeur BizTalk

## <a name="overview"></a>Vue d'ensemble
L’Éditeur BizTalk est un outil s’exécutant dans l’environnement Microsoft [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)]. Vous pouvez l’utiliser pour créer, modifier et gérer des schémas à utiliser avec votre application. L’Éditeur BizTalk utilise son propre système graphique d’enregistrements et champs hiérarchiques pour représenter la structure des messages d'instance et utilise le langage XSD (XML Schema definition) pour stocker les schémas qu’il définit. Cela est vrai quel que soit le format dans lequel les messages d’instance sont échangés. Par exemple, supposons que vous échangiez des fichiers plats avec un partenaire commercial. Pendant que BizTalk Server traite ces fichiers plats, il les convertit vers ou à partir d'un format XML conforme au schéma XSD que vous avez défini dans l’Éditeur BizTalk.  
  
 Les schémas que vous créez à l’aide de l’Éditeur BizTalk peuvent être utilisés au sein d’un processus d'entreprise orchestré, comme indiqué dans l’illustration suivante.  
  
 ![](../core/media/ebiz-dev-busprcsh.gif "ebiz_dev_busprcsh")  
  
 Les schémas sont également utilisés par des assembleurs et des désassembleurs pour convertir des messages d'instance depuis un format vers un autre, par exemple d'un format de fichier plat à un format XML. Ils jouent par ailleurs un rôle important dans la transformation d'un message d'instance : les données d'un message d'instance sont utilisées pour élaborer un message d'instance avec une structure différente. Le nouveau message d'instance peut être sémantiquement équivalent, telles que des représentations différentes d'un bon d'achat, ou il peut être d'un type différent mais connexe exigeant tout ou partie des données contenues dans le message d'instance d'origine.  
  
 La conversion de tous les messages d’instance en un format XML conforme à un schéma XSD est importante, car elle permet de simplifier le processus de transformation d’un message d’une structure en une autre structure. Les structures de message sont généralement sémantiquement équivalentes, malgré leurs différences syntaxiques. Par exemple, vous risquez de structurer vos bons de commande différemment de votre partenaire commercial, toutefois, les informations de base qu'ils contiennent sont les mêmes, ce qui permet de les convertir d'un format vers l'autre et inversement. En commençant par convertir tous les messages d'instance en un format XML géré par un schéma XSD correspondant, vous pouvez convertir les messages d’instance d'un format XML en format non XML et vice versa, et les transformer d'une structure XML à une autre. Pour plus d’informations sur la distinction entre la conversion et la transformation des messages d’instance, consultez [Transformation des données](../core/data-transformation.md).  
  
 L'outil d'accompagnement de l'Éditeur BizTalk au sein de l'environnement Microsoft Visual Studio est le Mappeur BizTalk. Une fois que vous avez utilisé l’Éditeur BizTalk pour créer les schémas définissant la structure et le format d’une paire de messages d’instance connexes, vous utilisez le Mappeur BizTalk pour définir graphiquement la façon dont un message d'instance conforme à un schéma (le schéma et le message d'instance source) est transformé en un message conforme à un autre schéma (le schéma et le message d'instance de destination). La spécification de telles transformations est mise en œuvre à l'aide de feuilles de style XSLT (Extensible Stylesheet Language Transformations) et conservée en tant que fichiers appelés mappages. Pour plus d’informations conceptuelles et procédurales sur le Mappeur BizTalk, voir [création de mappages à l’aide du mappeur de BizTalk](../core/creating-maps-using-biztalk-mapper.md). Pour plus d’informations de référence sur les fonctoids et les propriétés du Mappeur BizTalk, consultez le **référence de mappage de propriété** et **référence du fonctoid**[!INCLUDE[ui-guidance-developers-reference](../includes/ui-guidance-developers-reference.md)].  
  
 Dans l’Éditeur BizTalk, vous pouvez ouvrir un schéma vide ne contenant aucune structure, vous pouvez ouvrir un schéma XSD existant ou vous pouvez générer un schéma à partir d’une source non XSD. Lorsque vous générez un schéma à partir d’une source non XSD, l’Éditeur BizTalk interprète la structure de la source et produit un schéma correspondant à une représentation XSD de ce dernier. Vous pouvez modifier tous les enregistrements et champs apparaissant dans l’arborescence du schéma de l’Éditeur BizTalk, puis enregistrer la structure en tant que schéma BizTalk.  
  
 Pour plus d’informations sur l’utilisation des raccourcis clavier pour l’Éditeur BizTalk, consultez [raccourcis clavier de l’Éditeur BizTalk](../core/biztalk-editor-keyboard-shortcuts.md).  
  
## <a name="next-steps"></a>Étapes suivantes
  
-   [Planification de la création de schémas](../core/planning-for-schema-creation.md)  
  
-   [À propos des Messages d’Instance](../core/about-instance-messages.md)  
  
-   [À propos des schémas](../core/about-schemas.md)  
  
-   [À l’aide de l’Éditeur BizTalk](../core/using-biztalk-editor.md)  
  
-   [Création de schémas](../core/creating-schemas.md)  
  
-   [Création de schémas à l’aide d’Assistant schéma de fichier plat BizTalk](../core/creating-schemas-using-biztalk-flat-file-schema-wizard.md)  
  
-   [Test de schémas](../core/testing-schemas.md)  
  
-   [Extension de l’Éditeur BizTalk](../core/extending-biztalk-editor.md)  
  
-   [Considérations relatives à la création de schémas](../core/considerations-when-creating-schemas.md)  
  
-   [Problèmes connus avec la Validation et génération de schéma](../core/known-issues-with-schema-generation-and-validation.md)