---
title: "Blocs de construction pour créer des applications BizTalk avec l’adaptateur Siebel | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- developing BizTalk applicatons, run-time tasks
- developing BizTalk applications, design-time tasks
ms.assetid: 76204181-18ad-43b5-b589-539aafd66835
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: dea8fc354c3187ef7613ac35850b9408a05a9c0e
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="building-blocks-to-create-biztalk-applications-with-the-siebel-adapter"></a>Blocs de construction pour créer des applications BizTalk avec l’adaptateur Siebel
Exécution d’opérations sur un système Siebel à l’aide [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)] implique les deux ensemble d’activités : les activités au moment du design et moment de l’exécution. Pour effectuer des opérations sur un système Siebel à l’aide de la [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)] avec [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)], vous devez effectuer un ensemble de tâches au moment du design et au moment à l’aide de [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)] et [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] respectivement de la console Administration. Cette section fournit une vue d’ensemble de ces tâches. Toutes les rubriques de cette section, qui montrent comment effectuer des opérations spécifiques sur un système Siebel à l’aide [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)], sont modélisées sur ces tâches de niveau supérieur.  
  
## <a name="design-time-tasks"></a>Tâches au moment du design  
 Le [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)] fournit une fonctionnalité permettant de parcourir, rechercher et récupérer les métadonnées Siebel pour les composants d’entreprise et les services d’entreprise sous la forme de langages de définition de schéma XML (XSD) à l’aide de la [!INCLUDE[consumeadapterservlong](../../includes/consumeadapterservlong-md.md)] ou [!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)]. Les XSD sont spécifiques à l’opération que vous souhaitez exécuter sur le système Siebel et le [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)] ou [!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)] est disponible uniquement lorsque vous créez un projet BizTalk. Au moment du design, vous devrez peut-être effectuer les tâches suivantes.  
  
-   **Créer un projet BizTalk et générer le schéma**. Pour commencer, vous devez créer un projet BizTalk dans Microsoft [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)] et générer le schéma pour les composants d’entreprise ou les services d’entreprise vous appellerez dans le système Siebel. Par exemple, si vous souhaitez insérer un enregistrement dans le composant de gestion de compte, vous devez générer les métadonnées pour l’opération d’insertion pour le composant de gestion de compte. Dans cette étape, vous utilisez la [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)] ou [!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)] pour générer le schéma. Pour plus d’informations, consultez [obtenir les métadonnées pour les opérations Siebel dans Visual Studio](../../adapters-and-accelerators/adapter-siebel/get-metadata-for-siebel-operations-in-visual-studio.md).  
  
-   **Configurer une orchestration**. Une fois que vous avez généré le schéma, vous devez configurer une orchestration à l’aide du Concepteur d’Orchestration. Pour une orchestration de base, ajouter l’envoi et réception de formes, ainsi que l’envoi et ports logiques de réception. Dans les étapes ultérieures, vous allez mapper ces ports logiques aux ports physiques à l’aide de la console Administration de BizTalk Server. L’orchestration utilise ces ports pour récupérer les messages envoyés par un client de carte. L’orchestration puis transmet les messages au système Siebel. Une fois qu’une réponse est reçue à partir du système Siebel, l’orchestration transmet la réponse au client de carte.  
  
-   **Créer des messages et le lier au schéma**. Dans l’orchestration, vous devez créer des messages qui seront mappées vers le schéma que vous avez créé à la première étape. En règle générale, vous devez créer une demande et un message de réponse. Ces messages sont mappées à la demande correspondante et les schémas de réponse.  
  
-   **Mapper des formes de message pour les messages et les ports**. Dans l’orchestration, vous devez maintenant mapper chaque forme que vous avez ajoutée à la deuxième étape de messages que vous avez créé dans la troisième étape. Vous devez également mapper une forme de message au port d’envoi de ce message.  
  
     Par exemple, si la première forme dans l’orchestration est une forme réception qui reçoit un message, vous allez mapper cette forme à un message de « requête » et le port qui envoie le message de demande.  
  
-   **Générer et déployer le projet BizTalk**. Après avoir configuré l’orchestration et mis en correspondance les messages, les ports et les schémas, vous devez générer la solution BizTalk. Pour générer un projet [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)], vous devez un fichier de clé d’assembly. Après avoir généré la solution, vous devez déployer la solution.  
  
    > [!NOTE]
    >  Plus la description de ces tâches de niveau élevé, y compris des informations procédurales est fourni sous les rubriques qui suivent.  
  
 Une fois que la solution est déployée, vos tâches de conception d’heure sont accomplies. Vous devez maintenant effectuer les tâches d’exécution.  
  
## <a name="run-time-tasks"></a>Tâches d’exécution  
  
-   **Configurer l’application**. Le projet BizTalk que vous avez déployé au moment du design s’afficheront dans la console Administration de BizTalk Server en tant qu’orchestration. Vous devez configurer cette orchestration en mappant les ports logiques que vous avez créé au moment du design pour les ports physiques que vous devez maintenant créer à l’aide de la console Administration de BizTalk Server.  
  
     Sur les ports physiques, vous devez spécifier une « action » ou un « mappage d’action ». Cette action correspond à l’opération à effectuer sur le système Siebel. Vous devez définir l’action si vous n’utilisez pas les actions dynamiques. 
  
-   **Démarrez l’application**. Une fois que l’application est configurée, vous devez démarrer l’application et supprimer les messages d’entrée à un emplacement de fichier défini. L’orchestration consomme les messages d’entrée et les transmet au système Siebel et reçoit une réponse. Cette réponse sera auquel vous avez accès à un autre emplacement de fichier défini.  
  
 Pour mener à bien ces tâches au moment du design et au moment de haut niveau, vous devez également effectuer d’autres tâches. Par exemple, lorsque vous utilisez la [!INCLUDE[consumeadapterservlong](../../includes/consumeadapterservlong-md.md)] ou [!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)] pour générer le schéma, vous devez spécifier un URI de connexion pour se connecter au système Siebel. Cette section fournit des informations sur ces tâches répétitives que vous devez effectuer lorsque vous développez des applications BizTalk à l’aide de la [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)].  
  
