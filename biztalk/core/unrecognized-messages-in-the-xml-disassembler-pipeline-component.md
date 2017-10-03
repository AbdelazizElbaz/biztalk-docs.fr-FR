---
title: "Composant de Pipeline de Messages non reconnus dans le désassembleur XML | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Allow Unrecognized Messages property
- XMLNorm.AllowUnrecognizedMessage property
- pipeline components, XML Disassembler
- XML Disassembler [pipeline component], unrecognized messages
ms.assetid: 5a6be3a8-0bac-426a-bf0b-5091191091de
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: d82396002ff9d35484af5f0000dc3468c8ad37fb
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="unrecognized-messages-in-the-xml-disassembler-pipeline-component"></a>Messages non reconnus dans le composant de Pipeline désassembleur XML
Le composant Désassembleur XML est susceptible de traiter un message comme « non reconnu » dans les cas suivants :  
  
-   Lorsque le corps du message XML reçu est absent, vide ou qu'il comporte des données vides.  
  
-   Lorsqu'un message XML a été reçu mais qu'aucun schéma n'est déployé à son intention.  
  
 Un message non reconnu est géré selon le **autoriser un message non reconnu** propriété (ou, dans le **XMLNorm.AllowUnrecognizedMessage** propriété du contexte de message).  
  
 Si **autoriser un message non reconnu** a la valeur **True**, les éléments suivants se produisent :  
  
-   Les messages sans corps, avec un corps vide/nul ou avec un corps comportant des données vides/nulles sont transmis sans modification via le Désassembleur XML.  
  
-   Les documents XML sans schéma déployé associé sont transmis sans modification via le Désassembleur XML.  
  
-   Les documents XML associés à un schéma déployé sont traités par le Désassembleur XML que le schéma soit explicitement référencé dans une propriété de composant ou trouvé durant le processus de résolution de schéma.  
  
 Si **autoriser un message non reconnu** a la valeur **False**, les éléments suivants se produisent :  
  
-   Les messages sans corps ou avec un corps vide/nul ou avec un corps comportant des données vides/nulles ne sont pas transmis via le Désassembleur XML.  
  
-   Les documents XML sans schéma déployé associé ne sont pas transmis via le désassembleur. Une erreur est renvoyée et le message est interrompu, le cas échéant.  
  
-   Les documents XML associés à un schéma déployé sont traités par le Désassembleur XML que le schéma soit explicitement référencé dans une propriété de composant ou trouvé durant le processus de résolution de schéma.  
  
 Par défaut, le Désassembleur XML n'autorise pas les messages non reconnus.  
  
> [!NOTE]
>  Les messages non XML ne sont pas traités par le désassembleur XML, quel que soit le **autoriser un message non reconnu** paramètre de propriété.  
  
## <a name="see-also"></a>Voir aussi  
 [Composant de Pipeline désassembleur XML](../core/xml-disassembler-pipeline-component.md)   
 [Comment configurer le composant de Pipeline désassembleur XML](../core/how-to-configure-the-xml-disassembler-pipeline-component.md)