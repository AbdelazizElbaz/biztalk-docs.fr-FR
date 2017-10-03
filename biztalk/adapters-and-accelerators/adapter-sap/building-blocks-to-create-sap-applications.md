---
title: "Blocs de construction pour créer des applications SAP | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- design-time tasks
- run-time tasks
- developing, fundamentals of (BizTalk applications)
ms.assetid: 591a5597-5e7d-44b0-8bee-e1c987c5e6c3
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 8d507518b61b3c61b1815ec3ffe94bc1df5603d6
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="building-blocks-to-create-sap-applications"></a>Blocs de construction pour créer des applications SAP
Exécution d’opérations sur un système SAP à l’aide [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] implique les deux ensemble d’activités : les activités au moment du design et moment de l’exécution. Pour effectuer des opérations sur un système SAP à l’aide de la [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] avec [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)], vous devez effectuer un ensemble de tâches au moment du design et au moment à l’aide de [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)] et [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] respectivement de la console Administration. Cette section fournit une vue d’ensemble de ces tâches. Toutes les rubriques de cette section, qui montrent comment effectuer des opérations spécifiques sur un système SAP à l’aide [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)], sont modélisées sur ces tâches de niveau supérieur.  
  
## <a name="design-time-tasks"></a>Tâches au moment du design  
 Le [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)] fournit une fonctionnalité permettant de parcourir, rechercher et extraire les métadonnées SAP pour RFC, BAPI et IDOC sous la forme de langages de définition de schéma XML (XSD) à l’aide de la [!INCLUDE[consumeadapterservlong](../../includes/consumeadapterservlong-md.md)] ou [!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)]. Les XSD sont spécifiques à l’opération à effectuer sur le système SAP, et le [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)] ou [!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)] est disponible uniquement lorsque vous créez un projet BizTalk. Au moment du design, vous devez effectuer les tâches suivantes.  
  
-   **Créer un projet BizTalk et générer le schéma**. Pour commencer, vous devez créer un projet BizTalk dans Microsoft [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)] et générer le schéma pour le document RFC vous appellerez dans le système SAP. Par exemple, si vous souhaitez appeler RFC_CUSTOMER_GET dans le système SAP, vous devez générer les métadonnées pour RFC_CUSTOMER_GET. Dans cette étape, vous utilisez la [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)] ou [!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)] pour générer le schéma. Pour plus d’informations, consultez [obtenir les métadonnées pour les opérations de SAP dans Visual Studio](../../adapters-and-accelerators/adapter-sap/get-metadata-for-sap-operations-in-visual-studio.md).  
  
-   **Configurer une orchestration**. Une fois que vous avez généré le schéma, vous devez configurer une orchestration à l’aide du Concepteur d’Orchestration. Pour une orchestration de base, ajouter l’envoi et réception de formes, ainsi que l’envoi et ports logiques de réception. Dans les étapes ultérieures, vous mappez ces ports logiques aux ports physiques à l’aide de la console Administration de BizTalk Server. L’orchestration utilise ces ports pour sélectionner les messages qu’un client de l’adaptateur envoie. L’orchestration puis transmet les messages au système SAP. Une fois qu’une réponse est reçue à partir du système SAP, l’orchestration transmet la réponse au client de carte.  
  
-   **Créer des messages et le lier au schéma**. Dans l’orchestration, vous devez créer des messages qui seront mappées vers le schéma que vous avez créé à la première étape. En général, vous créez un message de demande et un message de réponse. Ces messages sont mappées à la demande correspondante et les schémas de réponse.  
  
-   **Mapper des formes de message pour les messages et les ports**. Dans l’orchestration, vous devez maintenant mapper chaque forme que vous avez ajoutée à la deuxième étape de messages que vous avez créé dans la troisième étape. Vous devez également mapper une forme de message au port d’envoi de ce message.  
  
     Par exemple, si la première forme dans l’orchestration est une forme réception qui reçoit un message, vous devez mapper cette forme à un message de demande et le port qui envoie le message de demande.  
  
-   **Générer et déployer le projet BizTalk**. Après avoir configuré l’orchestration et mis en correspondance les messages, les ports et les schémas, vous devez générer la solution BizTalk. Pour générer un projet [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)], vous devez un fichier de clé d’assembly. Après avoir généré la solution, vous devez déployer la solution.  
  
    > [!NOTE]
    >  Description plus détaillée de ces tâches de niveau supérieur, y compris des informations procédurales, est fournie dans les différentes rubriques de cette section.  
  
 Une fois que la solution est déployée, vos tâches au moment du design sont accomplies. Vous devez maintenant effectuer les tâches d’exécution.  
  
## <a name="run-time-tasks"></a>Tâches d’exécution  
 Au moment de l’exécution, vous pouvez utiliser la console Administration de BizTalk Server pour déployer et surveiller l’orchestration que vous avez créé au moment du design. En outre, vous devez :  
  
-   **Configurer l’application**. Le projet BizTalk que vous avez déployé au moment du design s’affiche dans la console Administration de BizTalk Server en tant qu’orchestration. Vous devez configurer cette orchestration en mappant les ports logiques que vous avez créé au moment du design pour les ports physiques que vous devez maintenant créer à l’aide de la [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] console d’Administration.  
  
     Sur les ports physiques, vous devez spécifier une « action » ou un « mappage d’action ». Cette action correspond à l’opération à effectuer sur le système SAP. Vous devez définir l’action si vous n’utilisez pas les actions dynamiques. 
  
-   **Démarrez l’application**. Une fois que l’application est configurée, vous devez démarrer l’application et supprimer les messages d’entrée à un emplacement de fichier défini. L’orchestration consomme les messages d’entrée et les transmet au système SAP et reçoit une réponse. Cette réponse sera auquel vous avez accès à un autre emplacement de fichier défini.  
  
 Pour mener à bien ces tâches au moment du design et au moment de haut niveau, vous devez également effectuer d’autres tâches. Par exemple, lorsque vous utilisez la [!INCLUDE[consumeadapterservlong](../../includes/consumeadapterservlong-md.md)] ou [!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)] pour générer le schéma, vous devez spécifier un URI de connexion pour se connecter au système SAP. Cette section fournit des informations sur ces tâches répétitives que vous devez effectuer lorsque vous développez des applications BizTalk à l’aide de la [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)].  
  
## <a name="in-this-section"></a>Dans cette section  
  
-   [Ajouter l’adaptateur SAP à la Console Administration de BizTalk Server](../../adapters-and-accelerators/adapter-sap/add-the-sap-adapter-to-biztalk-server-administration-console.md)  
  
-   [Configurer l’URI de connexion pour l’adaptateur SAP](../../adapters-and-accelerators/adapter-sap/configure-the-connection-uri-for-the-sap-adapter.md)  
  
-   [Configurer l’authentification dans les informations d’identification pour le système SAP](../../adapters-and-accelerators/adapter-sap/configure-the-sign-in-credentials-for-the-sap-system.md) 
  
-   [Configurer les propriétés de liaison de l’adaptateur SAP](../../adapters-and-accelerators/adapter-sap/configure-the-binding-properties-for-the-sap-adapter.md)
  
-   [Configuration de l’action SOAP pour le système SAP](../../adapters-and-accelerators/adapter-sap/configure-the-soap-action-for-the-sap-system.md)
  
-   [Configurer manuellement une liaison de port physique à l’adaptateur SAP](../../adapters-and-accelerators/adapter-sap/manually-configure-a-physical-port-binding-to-the-sap-adapter.md)
  
-   [Configurer une liaison de port physique à l’aide d’un fichier de liaison de port à SAP](../../adapters-and-accelerators/adapter-sap/configure-a-physical-port-binding-using-a-port-binding-file-to-sap.md)
  
-   [Configurer des ports dynamiques dans l’adaptateur SAP](../../adapters-and-accelerators/adapter-sap/configure-dynamic-ports-in-the-sap-adapter.md)
  
-   [Réutiliser les liaisons de l’adaptateur SAP](../../adapters-and-accelerators/adapter-sap/reuse-sap-adapter-bindings.md)
  
## <a name="see-also"></a>Voir aussi  
[Développer des applications BizTalk à l’aide de l’adaptateur SAP](../../adapters-and-accelerators/adapter-sap/develop-biztalk-applications-using-the-sap-adapter.md)