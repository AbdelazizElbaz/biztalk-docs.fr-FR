---
title: "Générer un schéma XSD pour un message JSON | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 5453b76c-b282-442f-9eb1-6c2628b38ad5
caps.latest.revision: "4"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 88caf75d312179cd45bb1b3b421d6c2c7f25c2a8
ms.sourcegitcommit: 3fc338e52d5dbca2c3ea1685a2faafc7582fe23a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/01/2017
---
# <a name="generate-an-xsd-schema-for-json-message"></a>Générer un schéma XSD pour un message JSON
> [!NOTE]
>  Ce didacticiel s’applique uniquement à BizTalk Server.  
  
 Dans cette solution, une application [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] reçoit un message JSON. Pour que l'application puisse traiter le message, celui-ci doit être converti en un schéma XSD. Pour cela, [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] fournit un Assistant Schéma JSON qui créé un schéma XSD à partir d'un message JSON.  
  
1.  Dans Visual Studio, créez un nouveau projet [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].  
  
2.  Dans l’Explorateur de solutions, cliquez sur le nom du projet > **ajouter** > **un nouvel élément** > **Assistant schéma JSON**. Fournissez un nom pour le schéma (`PO.xsd`), puis cliquez sur **ajouter**.  
  
3.  Dans l’Assistant schéma JSON, sur la page d’accueil, cliquez sur **suivant**.  
  
4.  Dans la page des informations sur le schéma JSON, indiquez l'emplacement du fichier du bon de commande JSON qui est envoyé à l'application [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]. Entrez un nom de nœud racine, un espace de noms cible, puis cliquez sur **Terminer**.  
  
     ![Schéma XSD généré pour JSON](../core/media/btsjson-wizard.png "BTSJSON_Wizard")  
  
5.  Un schéma avec le nom spécifié est ajouté au projet [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]. Le fichier de schéma généré (**PO.xsd**) est également fourni avec l’exemple.  
  
## <a name="see-also"></a>Voir aussi  
 [Traitement des messages JSON à l’aide de BizTalk Server](../core/processing-json-messages-using-biztalk-server.md)