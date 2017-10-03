---
title: "Se connecter à SQL Server dans Visual Studio à l’aide de l’adaptateur SQL | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 62fc2c01-6e4d-4b3b-8581-1d57436ef4e9
caps.latest.revision: "11"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: bb5e2d149c9a9533e4bec3c2c1c435bffb3adf26
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="connect-to-sql-server-in-visual-studio-using-the-sql-adapter"></a>Se connecter à SQL Server dans Visual Studio à l’aide de l’adaptateur SQL
Cette section fournit des instructions sur l’utilisation de la [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)], le [!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)]et le [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)].  
  
-   Le  **[!INCLUDE[consumeadapterservlong](../../includes/consumeadapterservlong-md.md)]**  est disponible dans [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] projets et est installé dans le cadre de la [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)] installation. Vous utilisez le [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)] pour générer des schémas de message (XSD) pour les opérations que vous souhaitez cibler dans votre solution BizTalk. Pour plus d’informations sur le développement de solutions avec BizTalk Server, consultez [BizTalk de développer les applications à l’aide de l’adaptateur SQL](../../adapters-and-accelerators/adapter-sql/develop-biztalk-applications-using-the-sql-adapter.md).  
  
-   Le  **[!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)]**  est disponible dans le [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] projets et est installé dans le cadre de la [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] installation. Vous utilisez le [!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)] pour générer des schémas de message (XSD) pour les opérations que vous souhaitez cibler dans votre solution BizTalk. Pour plus d’informations sur le développement de solutions avec [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)], consultez [BizTalk de développer les applications à l’aide de l’adaptateur SQL](../../adapters-and-accelerators/adapter-sql/develop-biztalk-applications-using-the-sql-adapter.md).  
  
    > [!NOTE]
    >  Étant donné que le [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] est exposé comme une liaison WCF-Custom et comme l’adaptateur BizTalk, vous pouvez utiliser le [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)] ou le [!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)] à partir d’un projet BizTalk pour se connecter à SQL Server.  
  
-   Le  **[!INCLUDE[addadapterservreflong](../../includes/addadapterservreflong-md.md)]**  est disponible dans les projets de programmation non-BizTalk. Vous utilisez le [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)] pour générer une classe de client WCF ou d’une interface de rappel de service WCF lorsque vous développez des solutions à l’aide du modèle de service WCF. Pour plus d’informations sur le développement de solutions avec le modèle de service WCF, consultez [applications SAP de développer à l’aide du modèle de Service WCF](../../adapters-and-accelerators/adapter-sap/develop-sap-applications-using-the-wcf-service-model.md).  
  
 Pour utiliser le [!INCLUDE[consumeadapterservlong](../../includes/consumeadapterservlong-md.md)], [!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)], ou [!INCLUDE[addadapterservreflong](../../includes/addadapterservreflong-md.md)], vous devez tout d’abord vous connecter à SQL Server. Les trois méthodes présentent une boîte de dialogue par le biais duquel vous configurez une connexion en définissant les éléments suivants :  
  
-   **Paramètres de connexion**. Voici les paramètres qui sont utilisés pour générer l’URI de connexion telles que le nom SQL Server, le nom de l’instance de base de données et le nom de la base de données.  
  
-   **Informations d’identification de mot de passe de nom utilisateur pour SQL Server**. Ils sont utilisés pour vous authentifier sur SQL Server lorsque la connexion est établie. Vous devez spécifier un nom d’utilisateur et un mot de passe.  
  
-   **Propriétés de liaison**. Propriétés de liaison sont facultatifs, et si vous les spécifiez dépend principalement si vous ciblez les opérations qui nécessitent des propriétés de liaison spécifique. Pour plus d’informations sur les propriétés de liaison, consultez [en savoir plus sur l’adaptateur BizTalk pour les propriétés de liaison de l’adaptateur SQL Server](../../adapters-and-accelerators/adapter-sql/read-about-the-biztalk-adapter-for-sql-server-adapter-binding-properties.md).  
  
 Au minimum, lorsque vous configurez la connexion à SQL Server, vous ne devez spécifier les propriétés de liaison et les paramètres de connexion qui sont nécessaires pour établir la connexion et qui affectent les métadonnées retournées par le [!INCLUDE[adaptersqlshort](../../includes/adaptersqlshort-md.md)] pour les opérations que vous souhaitez cible. Toutefois, vous souhaiterez également spécifier des valeurs pour toutes les propriétés de liaison supplémentaires et des paramètres de connexion qui seront utilisés au moment de l’exécution. Il s’agit, car :  
  
-   Le [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)] crée un fichier de liaison de port de BizTalk à partir des propriétés de liaison et les paramètres de connexion que vous spécifiez lorsque vous configurez la connexion et ajoute ce fichier à votre projet.  
  
-   Le [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)] crée un fichier app.config dans les propriétés de liaison et les propriétés de connexion que vous spécifiez lorsque vous configurez la connexion et ajoute ce fichier dans votre répertoire de projet.  
  
