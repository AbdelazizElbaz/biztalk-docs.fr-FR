---
title: "Développement des schémas EDI | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 7a8fbf3d-ebc7-47f6-87fa-e45722651262
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: b241b5d0477d7aa477511c43b642e4e312f2651a
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="developing-edi-schemas"></a>Développement des schémas EDI
Les rubriques de cette section décrivent la modification des schémas EDI à des fins d'utilisation dans [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].  
  
 Pour utiliser un schéma de document dans votre solution, vous devez déployer celui-ci en l'ajoutant à un projet BizTalk dans [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)], puis en créant et en déployant le projet. [!INCLUDE[btsVStudioNoVersion](../includes/btsvstudionoversion-md.md)] déploie le projet dans l'Application 1 par défaut de BizTalk. Vous pouvez voir les schémas qui sont déployés en ouvrant le **schémas** nœud sous **BizTalk Application 1** nœud le **Applications** nœud dans le [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] Console d’administration. Vous pouvez déployer un assembly dans une autre application à l'aide de l'outil de ligne de commande pour le déploiement `BTSTask`.  
  
 Les schémas de service et de contrôle sont automatiquement déployés par l'Assistant Configuration de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]. Pour les afficher, cliquez sur le **schémas** nœud dans le **Application EDI BizTalk** nœud dans la Console d’Administration. Pour plus d’informations sur ces schémas, consultez [Service EDI et des schémas de contrôle](../core/edi-service-and-control-schemas.md).  
  
## <a name="in-this-section"></a>Dans cette section  
  
-   [Modification des schémas EDI](../core/modifying-edi-schemas.md)  
  
-   [Personnalisation des énumérations dans le schéma d’enveloppe](../core/customizing-enumerations-in-the-envelope-schema.md)  
  
-   [Configuration de la Validation de champ croisé](../core/configuring-cross-field-validation.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Développement et la configuration des Solutions EDI BizTalk Server](../core/developing-and-configuring-biztalk-server-edi-solutions.md)