---
title: "Différents Types de schémas BizTalk | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ad8847d3-6f0e-4982-b4a8-92a5f39a4b48
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 051cd8fb9824cece316ea6f56e318490eacf88c0
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="different-types-of-biztalk-schemas"></a>Différents types de schémas BizTalk
[!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] prend en charge les quatre types de schémas suivants :  
  
-   **Schéma XML**. un schéma XML définit la structure d'une classe de messages d'instance XML. Étant donné que ce type de schéma utilise le langage XSD (XML Schema Definition) pour définir la structure d'un message d'instance XML, ce qui est la finalité d'XSD, ces schémas utilisent XSD de manière simplifiée.  
  
-   **Schéma de fichier plat**. un schéma de fichier plat définit la structure d'une classe de messages d'instance qui utilisent un format de fichier plat délimité, positionnel ou combinant ces deux types de formats. Les fonctionnalités sémantiques natives de XSD ne prenant pas en compte toutes les exigences pour définir la structure de messages d'instance de fichier plat, telles que les différents types de délimiteurs qui peuvent être utilisés pour des enregistrements et des champs différents dans un fichier plat, BizTalk Server utilise les capacités d'annotation de XSD pour stocker ces informations supplémentaires dans un schéma XSD. BizTalk Server définit un vaste ensemble de balises d'annotation spécifiques qui peuvent être utilisées pour stocker toutes les informations supplémentaires requises.  
  
-   **Schéma d’enveloppe**. un schéma d'enveloppe est un type spécial de schéma XML. Les schémas d'enveloppe servent à définir la structure d'enveloppes XML, qui sont utilisées pour encapsuler un ou plusieurs documents commerciaux XML dans un seul message d'instance XML. Lorsque vous définissez un schéma XML de sorte qu'il soit un schéma d'enveloppe, deux paramètres de propriété supplémentaires sont requis, par exemple selon qu'il y a ou non plus d'un enregistrement racine défini dans le schéma d'enveloppe.  
  
-   **Schéma de propriété**. Il joue un rôle dans le processus de copie de propriétés promues dans un sens et dans l'autre entre le message d'instance et le contexte de message. La promotion de propriété est le processus de copie de valeurs spécifiques situées profondément dans un message d'instance dans le contexte du message. À partir du contexte de message, ces valeurs sont plus facilement accessibles par divers composants de BizTalk Server. Ces composants se servent des valeurs pour effectuer des opérations telles que le routage des messages. Les valeurs des propriétés promues peuvent également être copiées dans l'autre sens, du contexte de message plus facilement accessible vers les profondeurs du message d'instance, juste avant que le message d'instance ne soit envoyé vers sa destination. Un schéma de propriété est la version simple d'un schéma BizTalk qui joue un rôle dans le processus de copie de propriétés promues dans un sens et dans l'autre entre le message d'instance et le contexte de message.  
  
 Le reste de la section fournit des informations supplémentaires à propos de ces quatre types de schémas dans BizTalk Server.  
  
## <a name="in-this-section"></a>Dans cette section  
  
-   [Schémas XML](../core/xml-schemas.md)  
  
-   [Schémas de fichier plat](../core/flat-file-schemas.md)  
  
-   [Schémas d’enveloppe](../core/envelope-schemas.md)  
  
-   [Schémas de propriété](../core/property-schemas.md)