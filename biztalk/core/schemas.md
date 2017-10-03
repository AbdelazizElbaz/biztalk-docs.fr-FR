---
title: "Schémas | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- schemas, schema types
- deploying, schemas
- schemas
- schemas, about schemas
- property schemas
- envelope schemas
- schemas, deploying
- XML schemas
- flat file schemas
ms.assetid: aea772bd-e7ab-448e-ba82-e7c8f38087db
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 696c79a30bb58cd91536c19c97db54d6159762b6
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="schemas"></a>Schémas
Microsoft [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] utilise le langage de XML Schema definition (XSD) pour définir la structure de tous les messages qu’il traite et fait référence à ces définitions de structure de message en tant que *schémas*. À de rares exceptions près, les messages structurés constituent le noyau de toute application. Ces messages structurés peuvent prendre n’importe quelle forme, petite ou grande, et ciblent un grand éventail de systèmes principaux et de banques de données. Les systèmes qui créent et utilisent fréquemment les messages structurés font appel à des formats différents, XML et les fichiers plats étant les deux formats les plus courants.  
  
 BizTalk Server prend en charge les quatre types de schémas suivants :  
  
-   Schéma XML : un schéma XML définit la structure d'une classe de messages d'instance XML. Étant donné que ce type de schéma utilise le langage XSD (XML Schema Definition) pour définir la structure d'un message d'instance XML, ce qui est la finalité d'XSD, ces schémas utilisent XSD de manière simplifiée. Pour plus d’informations sur les schémas XML, consultez [schémas XML](../core/xml-schemas.md).  
  
-   Schéma de fichier plat : un schéma de fichier plat définit la structure d'une classe de messages d'instance qui utilisent un format de fichier plat délimité, positionnel ou combinant ces deux types de formats. Les fonctionnalités sémantiques natives de XSD ne prenant pas en compte toutes les exigences pour définir la structure de messages d'instance de fichier plat, telles que les différents types de délimiteurs qui peuvent être utilisés pour des enregistrements et des champs différents dans un fichier plat, BizTalk Server utilise les capacités d'annotation de XSD pour stocker ces informations supplémentaires dans un schéma XSD. BizTalk Server définit un vaste ensemble de balises d'annotation spécifiques qui peuvent être utilisées pour stocker toutes les informations supplémentaires requises. Pour plus d’informations sur les schémas de fichier plat, voir [schémas de fichier plat](../core/flat-file-schemas.md).  
  
-   Schéma d'enveloppe : un schéma d'enveloppe est un type de schéma XML. Les schémas d'enveloppe servent à définir la structure d'enveloppes XML, qui sont utilisées pour encapsuler un ou plusieurs documents commerciaux XML dans un seul message d'instance XML. Lorsque vous définissez un schéma XML de sorte qu'il soit un schéma d'enveloppe, des paramètres de propriété supplémentaires sont requis, par exemple selon qu'il y a ou non plus d'un enregistrement racine défini dans le schéma d'enveloppe. Pour plus d’informations sur les schémas d’enveloppe, consultez [schémas d’enveloppe](../core/envelope-schemas.md).  
  
-   Schéma de propriété. un schéma de propriété est utilisé avec l'un des deux mécanismes qui existent dans BizTalk Server pour la promotion de propriété. *Promotion de propriété* est le processus de copie des valeurs spécifiques situées profondément dans un message d’instance dans le contexte du message. À partir du contexte de message, ces valeurs sont plus facilement accessibles par divers composants de BizTalk Server. Ces composants se servent des valeurs pour effectuer des opérations telles que le routage des messages. Les valeurs des propriétés promues peuvent également être copiées dans l'autre sens, du contexte de message plus facilement accessible vers les profondeurs du message d'instance, juste avant que le message d'instance ne soit envoyé vers sa destination. Un schéma de propriété, qui est la version simple d'un schéma BizTalk, joue un rôle dans le processus de copie de propriétés promues dans un sens et dans l'autre entre le message d'instance et le contexte de message. Pour plus d’informations sur les schémas de propriété, consultez [les schémas de propriété](../core/property-schemas.md).  
  
## <a name="schema-deployment"></a>Déploiement des schémas  
 Vous déployez différents types de schémas, tels que les schémas de message, de propriété et d'enveloppe. Chaque schéma présentant des caractéristiques propres, la façon dont ils sont gérés après le déploiement est légèrement différente. Cette section traite des points communs à tous les schémas et décrit les différences liées au type des schémas.  
  
 Lorsque vous déployez un schéma, la base de données de gestion stocke le contenu du schéma. Vous pouvez déployer plusieurs schémas avec le même espace de noms cible. BizTalk Server pointe explicitement vers le schéma dans le Concepteur de pipeline utilisé lors de l'exécution. Si vous utilisez les pipelines par défaut, ou si vous ne spécifiez pas de schéma dans le Concepteur de pipeline et que plusieurs versions du même schéma ont été déployées, BizTalk Server détermine le schéma à utiliser. Dans ce cas, le schéma sera associé à la version la plus récente (dotée du numéro de version le plus élevé) de l'assembly déployé à l'aide de ce schéma.  
  
 Lorsque vous supprimez la version la plus récente de l'assembly utilisé pour déployer un schéma, le schéma provenant de la précédente version du même assembly devient le schéma actif.  
  
 Si vous déployez des schémas avec des espaces de noms cibles identiques, vous devez faire référence à un schéma issu d'un pipeline utilisateur personnalisé. Cela fournit au moteur de messagerie des informations supplémentaires lui permettant de charger le schéma approprié.  
  
 Par exemple, vous utilisez des espaces de noms cibles identiques lorsque vous créez plusieurs versions d'un schéma de service Web.  
  
## <a name="see-also"></a>Voir aussi  
 [Création de schémas à l’aide de l’Éditeur BizTalk](../core/creating-schemas-using-biztalk-editor.md)   
 [Représentation BizTalk de schémas](../core/biztalk-representation-of-schemas.md)   
 [Artefacts](../core/artifacts.md)