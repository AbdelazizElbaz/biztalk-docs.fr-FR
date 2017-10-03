---
title: Construction de Messages Web | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Web messages, about Web messages
- Web messages, message types
- Web services, Web messages
- Web messages, parts
- Web messages
- messages, Web messages
ms.assetid: ca1792be-5fba-4f5d-a88e-b854f6a8ce33
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 8c344bbb836a6524ec1fd2656a5ba3f8bc8fad7d
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="constructing-web-messages"></a>Création des messages Web
Vous générez un message Web à partir d'un type de message Web. Lorsque vous ajoutez une référence Web, BizTalk crée automatiquement des types de messages Web basés sur les méthodes Web du service Web ajouté. Vous ajoutez un message Web à votre orchestration en définissant le type de message sur l'un des types de messages Web. Vous créez des parties de message individuelles basées sur un type .NET primitif ou de schéma. Vous pouvez générer un message Web qui ne contient aucune partie de message.  
  
 **Types de messages Web**  
  
 Les types de messages Web (définis dans Reference.odx) sont identiques à un type de message normal, sauf que vous ne pouvez pas les modifier, les renommer ou les supprimer. Pour supprimer un type de message Web, vous devez supprimer la référence Web de votre projet BizTalk.  
  
 Le projet BizTalk crée une demande et un type de message Web de réponse pour chaque méthode Web dans le service Web ajouté. Si la méthode Web est une opération unidirectionnelle, BizTalk crée uniquement un type de message Web de demande. Un type de message Web de demande contient une partie de message pour chaque paramètre d'entrée de la méthode Web. Un type de message Web de réponse contient une partie de message pour la valeur renvoyée et une partie de message pour chaque paramètre de sortie de la méthode Web.  
  
 Selon le paramètre de méthode Web (entrée ou sortie), BizTalk crée un type de message Web à partir d'un type .NET primitif ou de schéma. Si le paramètre de méthode Web est un type .NET primitif, la partie de message utilise un type .NET primitif. Si le paramètre de méthode Web est un type de schéma, BizTalk ajoute le type de schéma au projet BizTalk en tant que schéma dans Reference.xsd. Le schéma constitue la base de la partie du message. Le fichier Reference.xsd se trouve dans le dossier des références Web.  
  
 Vous pouvez également créer des types .NET primitifs et de schéma en appelant une classe .NET. Pour plus d’informations sur la création de types de messages à l’aide d’une classe .NET, consultez [construction de Messages dans le Code utilisateur](../core/constructing-messages-in-user-code.md).  
  
 **Messages Web**  
  
 Les messages Web sont des messages utilisés dans le cadre de l'utilisation (appel) d'un service Web. Vous ajoutez un message Web à une orchestration comme vous le faites pour un message normal. Vous devez seulement définir le type de message sur un des types de messages Web créés par BizTalk lorsque vous avez ajouté une référence Web.  
  
 **Parties de message**  
  
 Une fois que vous avez créé le message Web, vous générez les parties de message individuelles. Si votre partie de message utilise un type .NET primitif, vous utilisez un **assignation du Message** forme. Si votre partie de message utilise un type de schéma, vous utilisez un **transformer** forme ou **assignation du Message** forme. Pour plus d’informations, consultez [construction de Messages dans le Code utilisateur](../core/constructing-messages-in-user-code.md).  
  
## <a name="in-this-section"></a>Dans cette section  
  
-   [Comment ajouter des Messages Web](../core/how-to-add-web-messages.md)  
  
-   [Comment déterminer un Type de partie de Message Web](../core/how-to-determine-a-web-message-part-type.md)  
  
-   [Comment construire une partie de Message Web à partir d’un Type .NET primitif](../core/how-to-construct-a-web-message-part-from-a-primitive-net-type.md)  
  
-   [Comment construire une partie de Message Web à partir d’un Type de schéma](../core/how-to-construct-a-web-message-part-from-a-schema-type.md)  
  
-   [Comment construire un Message Web sans partie de Message](../core/how-to-construct-a-web-message-with-no-message-parts.md)