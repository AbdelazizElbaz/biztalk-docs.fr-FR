---
title: "À propos des Messages d’Instance | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: de7fc3d3-57a7-4df9-b981-127e21941e22
caps.latest.revision: "6"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: bf956fb9f201697ac8c2b7da2135e469e03de55e
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="about-instance-messages"></a>À propos des Messages d’Instance
Microsoft [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] envoie et reçoit des messages d'instance qui représentent généralement chacun un ou plusieurs documents commerciaux tels qu'un bon de commande. Un message d'instance est une instance d'une structure de messages définie par un ou plusieurs schémas. Un schéma ou un jeu de schémas utilisés ensemble définissent ce qui constitue un message d'instance valide. À titre d'exemple, un bon de commande peut être défini de façon à comporter plusieurs enregistrements : un enregistrement ShipTo, un enregistrement BillTo, un enregistrement Items, etc. Chacun de ces enregistrements peut être défini de manière à contenir ses propres sous-enregistrements et champs. Le schéma correspondant définit les contenus potentiels de ces enregistrements et champs et les messages d'instance correspondants contiennent les bons de commande réels qui contiennent les données de bon de commande structurées en fonction du schéma.  
  
 BizTalk Server peut envoyer et recevoir des messages d'instance sous une infinité de formats bien que l'un de ces formats, XML, revêt une importance significative, étant celui dans lequel tous les formats de message sont convertis pour le traitement interne. Un document XML particulier utilise un ensemble bien défini de balises de début et de fin, agencées de façon hiérarchique, pour organiser les données dans le message et déterminer où un élément de données commence et où un autre s'achève. Un ou plusieurs schémas XML correspondants définissent quelles sont les balises autorisées dans les autres balises et dans quel ordre, présidant ainsi à la structure des messages conformes.  
  
 Les « formats de fichier plat » appartiennent à une autre vaste catégorie de formats et sont généralement utilisés par les systèmes existants. Ces formats utilisent une certaine combinaison de délimiteurs (tels que des tabulations) et des champs de longueur fixe pour déterminer où finit un élément de données et où commence un autre.  
  
 Cette section propose une présentation détaillée de la structure de ces deux types de messages, communément gérés par BizTalk Server.  
  
## <a name="in-this-section"></a>Dans cette section  
  
-   [Structure d’un Message XML](../core/structure-of-an-xml-message.md)  
  
-   [Structure d’un Message de fichier plat](../core/structure-of-a-flat-file-message.md)