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
ms.openlocfilehash: b450c74f7d2eda6d3b688c40d0f8e8cde5c66d3b
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="generate-an-xsd-schema-for-json-message"></a>Générer un schéma XSD pour un message JSON
> [!NOTE]
>  Ce didacticiel s'applique uniquement à [!INCLUDE[prague](../includes/prague-md.md)].  
  
 Dans cette solution, une application [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] reçoit un message JSON. Pour que l'application puisse traiter le message, celui-ci doit être converti en un schéma XSD. Pour cela, [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] fournit un Assistant Schéma JSON qui créé un schéma XSD à partir d'un message JSON.  
  
1.  Dans Visual Studio, créez un nouveau projet [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].  
  
2.  Dans l’Explorateur de solutions, cliquez sur le nom du projet > **ajouter** > **un nouvel élément** > **Assistant schéma JSON**. Fournissez un nom pour le schéma (`PO.xsd`), puis cliquez sur **ajouter**.  
  
3.  Dans l’Assistant schéma JSON, sur la page d’accueil, cliquez sur **suivant**.  
  
4.  Dans la page des informations sur le schéma JSON, indiquez l'emplacement du fichier du bon de commande JSON qui est envoyé à l'application [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]. Entrez un nom de nœud racine, un espace de noms cible, puis cliquez sur **Terminer**.  
  
     ![Schéma XSD généré pour JSON](../core/media/btsjson-wizard.png "BTSJSON_Wizard")  
  
5.  Un schéma avec le nom spécifié est ajouté au projet [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]. Le fichier de schéma généré (**PO.xsd**) est également fourni avec l’exemple.  
  
## <a name="see-also"></a>Voir aussi  
 [Traitement des messages JSON à l’aide de BizTalk Server](../core/processing-json-messages-using-biztalk-server.md)