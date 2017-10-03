---
title: "Blocs de construction pour développer des applications BizTalk à l’adaptateur SQL | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: fac7cbf4-b111-43ad-8726-36d037918c9c
caps.latest.revision: "11"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 58198376a5ce42fc9c77fc18822c2ed739e5db00
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="building-blocks-to-develop-biztalk-applications-with-the-sql-adapter"></a>Blocs de construction pour développer des applications BizTalk à l’adaptateur SQL
Pour effectuer des opérations sur SQL Server à l’aide de la [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] avec [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)], vous devez effectuer un ensemble de tâches au moment du design et au moment à l’aide de [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)] et [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] respectivement de la console Administration. Cette section fournit une vue d’ensemble de ces tâches. Toutes les rubriques de cette section, qui montrent comment effectuer des opérations spécifiques sur l’utilisation de SQL Server [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)], sont modélisées sur ces tâches de niveau supérieur.  
  
## <a name="using-visual-studio"></a>Utilisation de Visual Studio  
  
1.  **Créer un projet BizTalk et générer le schéma**. Vous devez créer un projet BizTalk dans [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)]et générer le schéma pour l’opération que vous effectuerez sur SQL Server. Par exemple, si vous souhaitez insérer des enregistrements dans une table SQL Server, vous devez générer le schéma pour l’opération d’insertion pour cette table. Pour générer le schéma, vous devez utiliser le [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)] ou [!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)]. Pour plus d’informations, consultez [récupérer des métadonnées pour les opérations de SQL Server dans Visual Studio à l’aide de l’adaptateur SQL](../../adapters-and-accelerators/adapter-sql/get-metadata-for-sql-server-operations-in-visual-studio-using-the-sql-adapter.md).  
  
2.  **Configurer une orchestration**. Une fois que vous avez généré le schéma, vous devez configurer une orchestration à l’aide du Concepteur d’Orchestration. Pour une orchestration de base, ajouter l’envoi et réception de formes, ainsi que l’envoi et ports logiques de réception. Dans les étapes ultérieures, vous mappez ces ports logiques aux ports physiques à l’aide de la [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] console d’Administration. L’orchestration utilise ces ports pour sélectionner les messages qu’un client de l’adaptateur envoie. L’orchestration puis transmet les messages à SQL Server. Une fois que SQL Server envoie une réponse, l’orchestration transmet la réponse au client de carte.  
  
3.  **Créer des messages et le lier au schéma**. Dans l’orchestration, vous devez créer des messages qui seront mappées vers le schéma que vous avez créé à la première étape. En général, vous créez un message de demande et un message de réponse. Ces messages sont mappées à la demande correspondante et les schémas de réponse.  
  
4.  **Mapper des formes de message pour les messages et les ports**. Dans l’orchestration, vous devez maintenant mapper chaque forme que vous avez ajouté dans la deuxième étape de messages que vous avez créé dans la troisième étape. Vous devez également mapper une forme de message au port d’envoi de ce message.  
  
     Par exemple, si la première forme dans l’orchestration est une forme réception qui reçoit un message, vous devez mapper cette forme à un message de demande et le port qui envoie le message de demande.  
  
5.  **Générer et déployer le projet BizTalk**. Une fois que vous avez configuré l’orchestration et les messages mappés, les ports et les schémas, vous devez générer la solution BizTalk. Pour générer un projet [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)], vous avez besoin d’un fichier de clé d’assembly. Après avoir généré la solution, vous devez déployer la solution.  
  
> [!NOTE]
>  Description plus détaillée de ces tâches de niveau supérieur, y compris des informations procédurales, est fournie dans les différentes rubriques de cette section.  
  
 Une fois que vous avez créé et déployé le projet BizTalk, vos tâches dans [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)] sont accomplies. Vous devez effectuer maintenant certaines tâches à l’aide de la [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] console d’Administration.  
  
## <a name="using-the-biztalk-server-administration-console"></a>À l’aide de la Console Administration de BizTalk Server  
  
1.  **Configurer l’application**. Le projet BizTalk que vous avez déployé à l’aide de [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)] s’affiche dans le [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] console d’Administration en tant qu’orchestration. Vous devez configurer cette orchestration en mappant les ports logiques que vous avez créé dans [!INCLUDE[btsVStudioNoVersion](../../includes/btsvstudionoversion-md.md)] aux ports physiques que vous devez maintenant créer à l’aide de la [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] console d’Administration.  
  
     Sur les ports physiques, vous devez spécifier une « action » ou un « mappage d’action ». Cette action correspond à l’opération que vous souhaitez effectuer sur SQL Server. Vous devez spécifier l’action si vous n’utilisez pas les actions dynamiques. Pour plus d’informations sur les actions, consultez [configurer l’action SOAP pour l’adaptateur SQL](../../adapters-and-accelerators/adapter-sql/configure-the-soap-action-for-the-sql-adapter.md).  
  
2.  **Démarrez l’application**. Une fois que l’application est configurée, vous devez démarrer l’application et supprimer les messages de demande à un emplacement de fichier défini. L’orchestration consomme les messages de demande, les transmet au serveur SQL Server et reçoit une réponse. Cette réponse est disponible pour le client de carte à un autre emplacement de fichier défini.  
  
 Pour mener à bien ces tâches de niveau supérieur, vous devez également effectuer d’autres tâches. Par exemple, lorsque vous utilisez la [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)] ou [!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)] pour générer le schéma, vous devez spécifier un URI de connexion pour se connecter à SQL Server. Cette section fournit des informations sur ces tâches répétitives que vous devez effectuer lorsque vous développez des applications BizTalk à l’aide de la [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)].  
  
## <a name="in-this-section"></a>Dans cette section  
  
-   [Ajout de l’adaptateur SQL à la Console Administration de BizTalk Server](../../adapters-and-accelerators/adapter-sql/adding-the-sql-adapter-to-biztalk-server-administration-console.md)  
  
-   [Configurer l’URI de connexion de l’adaptateur SQL](../../adapters-and-accelerators/adapter-sql/configure-the-connection-uri-for-the-sql-adapter.md)  
  
-   [Configurer l’authentification dans les informations d’identification de l’adaptateur SQL](../../adapters-and-accelerators/adapter-sql/configure-the-sign-in-credentials-for-the-sql-adapter.md)
  
-   [Configurer les propriétés de liaison de l’adaptateur SQL](../../adapters-and-accelerators/adapter-sql/configure-the-binding-properties-for-the-sql-adapter.md) 
  
-   [Configurer l’action SOAP pour l’adaptateur SQL](../../adapters-and-accelerators/adapter-sql/configure-the-soap-action-for-the-sql-adapter.md)
  
-   [Configurer manuellement une liaison de port physique à l’adaptateur SQL](../../adapters-and-accelerators/adapter-sql/manually-configure-a-physical-port-binding-to-the-sql-adapter.md) 
  
-   [Configurer une liaison de port physique à l’aide d’un fichier de liaison de port à utiliser l’adaptateur SQL](../../adapters-and-accelerators/adapter-sql/configure-a-physical-port-binding-using-a-port-binding-file-to-sql-adapter.md)
  
-   [Configurer des ports dynamiques](../../adapters-and-accelerators/adapter-sql/configure-dynamic-ports-in-the-sql-adapter.md)
  
-   [Réutiliser les liaisons de l’adaptateur](../../adapters-and-accelerators/adapter-sql/reuse-sql-adapter-bindings.md)
  
## <a name="see-also"></a>Voir aussi  
[Développer des applications BizTalk](../../adapters-and-accelerators/adapter-sql/develop-biztalk-applications-using-the-sql-adapter.md)