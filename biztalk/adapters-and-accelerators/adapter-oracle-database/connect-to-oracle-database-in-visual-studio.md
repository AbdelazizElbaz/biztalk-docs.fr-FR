---
title: "Se connecter à la base de données Oracle dans Visual Studio | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 766264c8-bb3f-49e9-b851-1022d1fa5076
caps.latest.revision: "5"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: b1c0bd45e311a2d6b56fdda9560a1c0300bb711b
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="connect-to-oracle-database-in-visual-studio"></a>Se connecter à la base de données Oracle dans Visual Studio
Comment utiliser le [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)], le [!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)]et le [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)].  

## <a name="connection-options-in-visual-studio"></a>Options de connexion dans Visual Studio

Lorsque vous utilisez [!INCLUDE[btsVStudioNoVersion_md](../../includes/btsvstudionoversion-md.md)], plusieurs options sont disponibles pour vous connecter à la base de données Oracle. Ces options sont les suivantes : 

-   Le  **[!INCLUDE[consumeadapterservlong](../../includes/consumeadapterservlong-md.md)]**  est disponible dans [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] projets. Vous utilisez le [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)] pour générer des schémas de message (XSD) pour les opérations que vous souhaitez cibler dans votre solution BizTalk. Pour plus d’informations sur le développement de solutions avec BizTalk Server, consultez [BizTalk de développer les applications à l’aide de l’adaptateur de base de données Oracle](../../adapters-and-accelerators/adapter-oracle-database/develop-biztalk-applications-using-the-oracle-database-adapter.md).  
  
-   Le  **[!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)]**  est disponible dans [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] projets. Vous utilisez le [!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)] pour générer des schémas de message (XSD) pour les opérations que vous souhaitez cibler dans votre solution BizTalk. Pour plus d’informations sur le développement de solutions avec BizTalk Server, consultez [BizTalk de développer les applications à l’aide de l’adaptateur de base de données Oracle](../../adapters-and-accelerators/adapter-oracle-database/develop-biztalk-applications-using-the-oracle-database-adapter.md).  
  
    > [!NOTE]
    >  Étant donné que le [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] est exposé comme une liaison WCF-Custom et comme l’adaptateur BizTalk, vous pouvez utiliser le [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)] ou le [!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)] à partir d’un projet BizTalk pour se connecter à SQL Server.  
  
-   Le  **[!INCLUDE[addadapterservreflong](../../includes/addadapterservreflong-md.md)]**  est disponible dans les projets de programmation non-BizTalk. Vous utilisez le [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)] pour générer une classe de client WCF ou d’une interface de rappel de service WCF lorsque vous développez des solutions à l’aide du modèle de service WCF. Pour plus d’informations sur le développement de solutions avec le modèle de service WCF, consultez [applications développer la base de données Oracle à l’aide du modèle de Service WCF](../../adapters-and-accelerators/adapter-oracle-database/develop-oracle-database-applications-using-the-wcf-service-model.md).  
  
 Pour utiliser le [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)], le [!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)], ou [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)], vous devez tout d’abord vous connecter à la base de données Oracle. Les trois méthodes présentent une boîte de dialogue par le biais duquel vous configurez une connexion en définissant les éléments suivants :  
  
-   **Paramètres de connexion**. Voici les paramètres qui sont utilisés pour générer l’URI de connexion. Vous devez spécifier une source de données (nom de service réseau Oracle).  
  
-   **Informations d’identification de mot de passe de nom utilisateur pour la base de données Oracle**. Ils sont utilisés pour vous authentifier sur la base de données Oracle lorsque la connexion est établie. Vous devez spécifier un nom d’utilisateur et un mot de passe.  
  
-   **Propriétés de liaison**. Propriétés de liaison sont facultatives au moment du design, autrement dit, lors de la génération de métadonnées pour les opérations. Pour plus d’informations sur les propriétés de liaison, consultez [en savoir plus sur les propriétés de liaison de carte de base de données Oracle](../../adapters-and-accelerators/adapter-oracle-database/read-about-the-oracle-database-adapter-binding-properties.md).  
  
 Au minimum, lorsque vous configurez la connexion à la base de données Oracle, vous ne devez spécifier les propriétés de liaison et les paramètres de connexion qui sont nécessaires pour établir la connexion et qui affectent les métadonnées retournées par le [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] pour les opérations vous souhaitez cibler. Toutefois, vous souhaiterez également spécifier des valeurs pour toutes les propriétés de liaison supplémentaires et des paramètres de connexion qui seront utilisés au moment de l’exécution. Il s’agit, car :  
  
-   Le [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)] crée un fichier de liaison de port de BizTalk à partir des propriétés de liaison et les paramètres de connexion que vous spécifiez lorsque vous configurez la connexion et ajoute ce fichier à votre projet. Une version ultérieure, vous pouvez utiliser ce fichier de liaison pour créer un port dans le [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] console d’Administration. Pour plus d’informations sur le fichier de liaison, consultez [configurer une liaison de port physique à l’aide d’un fichier de liaison de port pour la base de données Oracle](../../adapters-and-accelerators/adapter-oracle-database/configure-a-physical-port-binding-using-a-port-binding-file-to-oracle-database.md).  
  
-   Le [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)] crée un fichier app.config dans les propriétés de liaison et les propriétés de connexion que vous spécifiez lorsque vous configurez la connexion et ajoute ce fichier dans votre répertoire de projet.  
  

  
## <a name="see-also"></a>Voir aussi  
[Obtenir les métadonnées pour les opérations de base de données Oracle dans Visual Studio](../../adapters-and-accelerators/adapter-oracle-database/get-metadata-for-oracle-database-operations-in-visual-studio.md)