---
title: "Blocs de construction pour développer des Applications BizTalk avec la base de données Oracle | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- developing, BizTalk applications
- run-time tasks
- design-time tasks
ms.assetid: ad9ca856-5569-41ab-8617-ae6db5e3b4d7
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 0747569ef58e1f2223baefba6c51b77b205eb0d3
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="building-blocks-to-develop-biztalk-applications-with-oracle-database"></a>Blocs de construction pour développer des Applications BizTalk avec la base de données Oracle
Exécution d’opérations sur une base de données Oracle à l’aide de la [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] implique deux ensembles de tâches : au moment du design et d’exécution.  
  
## <a name="design-time-tasks"></a>Tâches au moment du design  
 Le [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)] fournit une fonctionnalité permettant de parcourir, rechercher et récupérer les métadonnées d’Oracle des tables, des procédures stockées et autres éléments de ce type sous la forme de langages de définition de schéma XML (XSD) à l’aide de la [!INCLUDE[consumeadapterservlong](../../includes/consumeadapterservlong-md.md)]. Les XSD sont spécifiques à l’opération à effectuer sur la base de données Oracle. Le [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)] est disponible uniquement lorsque vous créez un projet BizTalk. Au moment du design, vous devez effectuer les tâches suivantes :  
  
-   **Créer un projet BizTalk et générer le schéma**. Vous devez créer un projet BizTalk dans Microsoft [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)] et générer le schéma pour l’opération sera effectuée sur la base de données Oracle. Par exemple, si vous souhaitez insérer un enregistrement dans la table EMPLOYEE, vous devez générer les métadonnées pour l’opération d’insertion pour la table EMPLOYEE. Dans cette étape, vous utilisez le [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)] pour générer le schéma. Pour plus d’informations, consultez [obtenir les métadonnées pour les opérations de base de données Oracle dans Visual Studio](../../adapters-and-accelerators/adapter-oracle-database/get-metadata-for-oracle-database-operations-in-visual-studio.md).
  
-   **Configurer une orchestration**. Une fois que vous avez généré le schéma, vous devez configurer une orchestration à l’aide du Concepteur d’Orchestration. Pour une orchestration de base, ajouter l’envoi et réception de formes, ainsi que l’envoi et ports logiques de réception. Dans les étapes ultérieures, vous mappez ces ports logiques aux ports physiques à l’aide de la console Administration de BizTalk Server. L’orchestration utilise ces ports pour sélectionner les messages qu’un client de l’adaptateur envoie. L’orchestration puis transmet les messages à la base de données Oracle. Une fois qu’une réponse est reçue à partir de la base de données Oracle, l’orchestration transmet la réponse au client de carte.  
  
-   **Créer des messages et le lier au schéma**. Dans l’orchestration, vous devez créer des messages qui seront mappées vers le schéma que vous avez créé à la première étape. En général, vous créez un message de demande et un message de réponse. Ces messages sont mappées à la demande correspondante et les schémas de réponse.  
  
-   **Mapper des formes de message pour les messages et les ports**. Dans l’orchestration, vous devez maintenant mapper chaque forme que vous avez ajouté dans la deuxième étape de messages que vous avez créé dans la troisième étape. Vous devez également mapper une forme de message au port d’envoi de ce message.  
  
     Par exemple, si la première forme dans l’orchestration est une forme réception qui reçoit un message, vous devez mapper cette forme à un message de demande et le port qui envoie le message de demande.  
  
-   **Générer et déployer le projet BizTalk**. Une fois que vous avez configuré l’orchestration et les messages mappés, les ports et les schémas, vous devez générer la solution BizTalk. Pour générer un projet [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)], vous avez besoin d’un fichier de clé d’assembly. Après avoir généré la solution, vous devez déployer la solution.  
  
    > [!NOTE]
    >  Description plus détaillée de ces tâches de niveau supérieur, y compris des informations procédurales, est fournie dans les différentes rubriques de cette section.  
  
 Une fois que la solution est déployée, vos tâches au moment du design sont accomplies. Vous devez maintenant effectuer les tâches d’exécution.  
  
## <a name="run-time-tasks"></a>Tâches d’exécution  
 Au moment de l’exécution, vous pouvez utiliser la console Administration de BizTalk Server pour déployer et surveiller l’orchestration que vous avez créé au moment du design. En outre, vous devez :  
  
-   **Configurer l’application**. Le projet BizTalk que vous avez déployé au moment du design s’affiche dans la console Administration de BizTalk Server en tant qu’orchestration. Vous devez configurer cette orchestration en mappant les ports logiques que vous avez créé au moment du design pour les ports physiques que vous devez maintenant créer à l’aide de la console Administration de BizTalk Server.  
  
     Sur les ports physiques, vous devez spécifier une « action » ou un « mappage d’action ». Cette action correspond à l’opération à effectuer sur la base de données Oracle. Vous devez définir l’action si vous n’utilisez pas les actions dynamiques.  
  
-   **Démarrez l’application**. Une fois que l’application est configurée, vous devez démarrer l’application et supprimer les messages d’entrée à un emplacement de fichier défini. L’orchestration consomme les messages d’entrée et les transmet à la base de données Oracle et reçoit une réponse. Cette réponse sera auquel vous avez accès à un autre emplacement de fichier défini.  
  
 Pour mener à bien ces tâches au moment du design et au moment de haut niveau, vous devez également effectuer d’autres tâches. Par exemple, lorsque vous utilisez le [!INCLUDE[consumeadapterservlong](../../includes/consumeadapterservlong-md.md)] pour générer le schéma, vous devez spécifier un URI de connexion pour se connecter à la base de données Oracle. Cette section fournit des informations sur ces tâches répétitives que vous devez effectuer lorsque vous développez des applications BizTalk à l’aide de la [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)].  
  

  
## <a name="see-also"></a>Voir aussi  
[Développer des applications BizTalk à l’aide de l’adaptateur de base de données Oracle](../../adapters-and-accelerators/adapter-oracle-database/develop-biztalk-applications-using-the-oracle-database-adapter.md)