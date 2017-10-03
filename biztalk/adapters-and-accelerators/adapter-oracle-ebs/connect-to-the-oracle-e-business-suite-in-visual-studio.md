---
title: "Se connecter à Oracle E-Business Suite dans Visual Studio | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e290ea7e-03f3-49d4-9f18-1e539d727d9c
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 7b9221914a9f58c3f739eefd5f07986b0105f77e
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="connect-to-the-oracle-e-business-suite-in-visual-studio"></a>Se connecter à Oracle E-Business Suite dans Visual Studio
Cette section fournit des informations sur l’utilisation de la [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)], le [!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)]et le [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)].  
  
-   Le  **[!INCLUDE[consumeadapterservlong](../../includes/consumeadapterservlong-md.md)]**  est disponible dans [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] projets. Vous utilisez le [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)] pour générer des schémas de message (XSD) pour les opérations que vous souhaitez cibler dans votre solution BizTalk. Pour plus d’informations sur le développement de solutions avec BizTalk Server, consultez [développement d’Applications BizTalk Server](../../core/developing-biztalk-server-applications.md).  
  
-   Le  **[!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)]**  est disponible dans [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] projets. Vous utilisez le [!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)] pour générer des schémas de message (XSD) pour les opérations que vous souhaitez cibler dans votre solution BizTalk. Pour plus d’informations sur le développement de solutions avec BizTalk Server, consultez [développement d’Applications BizTalk Server](../../core/developing-biztalk-server-applications.md).  
  
    > [!NOTE]
    >  Étant donné que le [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)] est exposé comme une liaison WCF-Custom et comme l’adaptateur BizTalk, vous pouvez utiliser le [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)] ou le [!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)] à partir d’un projet BizTalk pour se connecter à Oracle E-Business Suite.  
  
-   Le  **[!INCLUDE[addadapterservreflong](../../includes/addadapterservreflong-md.md)]**  est disponible dans les projets de programmation non-BizTalk. Vous utilisez le [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)] pour générer une classe de client WCF ou d’une interface de rappel de service WCF lorsque vous développez des solutions à l’aide du modèle de service WCF. Pour plus d’informations sur le développement de solutions avec le modèle de service WCF, consultez [applications développer Oracle E-Business Suite à l’aide du modèle de Service WCF](../../adapters-and-accelerators/adapter-oracle-ebs/develop-oracle-e-business-suite-applications-using-the-wcf-service-model.md).  
  
 Pour utiliser le [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)], le [!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)], ou [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)], vous devez tout d’abord vous connecter à Oracle E-Business Suite. Les trois méthodes présentent une boîte de dialogue par le biais duquel vous configurez une connexion en définissant les éléments suivants :  
  
-   **Paramètres de connexion**. Voici les paramètres qui sont utilisés pour générer l’URI de connexion. Vous devez spécifier une source de données (nom de service réseau Oracle).  
  
-   **Informations d’identification du mot de passe utilisateur nom d’Oracle E-Business Suite**. Ils sont utilisés pour vous authentifier sur Oracle E-Business Suite, lorsque la connexion est établie. Vous devez spécifier un nom d’utilisateur et un mot de passe.  
  
    > [!IMPORTANT]
    >  À ce stade, vous pouvez spécifier les informations d’identification pour Oracle E-Business Suite ou de la base de données Oracle. Pour vous connecter et de générer des métadonnées, vous pouvez spécifier les informations d’identification. Toutefois, lors de l’opération pour appeler un artefact d’Oracle E-Business Suite, vous devez spécifier les informations d’identification Oracle E-Business Suite car ils sont requis pour définir le contexte de l’application pour l’application Oracle E-Business Suite, que vous souhaitez appeler. Pour plus d’informations sur le contexte des applications de paramètre, consultez [définir le contexte Application](../../adapters-and-accelerators/adapter-oracle-ebs/set-application-context.md).  
  
-   **Propriétés de liaison**. Propriétés de liaison sont facultatives au moment du design, autrement dit, lors de la génération de métadonnées pour les opérations. Pour plus d’informations sur les propriétés de liaison, consultez [en savoir plus sur l’adaptateur BizTalk pour les propriétés de liaison d’Oracle E-Business Suite](../../adapters-and-accelerators/adapter-oracle-ebs/read-about-the-biztalk-adapter-for-oracle-e-business-suite-binding-properties.md).  
  
 Au minimum, lorsque vous configurez la connexion à la base de données Oracle, vous ne devez spécifier les propriétés de liaison et les paramètres de connexion qui sont nécessaires pour établir la connexion et qui affectent les métadonnées retournées par le [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)] pour les opérations vous souhaitez cibler. Toutefois, vous souhaiterez également spécifier des valeurs pour toutes les propriétés de liaison supplémentaires et des paramètres de connexion qui seront utilisés au moment de l’exécution. Il s’agit, car :  
  
-   Le [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)] crée un fichier de liaison de port de BizTalk à partir des propriétés de liaison et les paramètres de connexion que vous spécifiez lorsque vous configurez la connexion et ajoute ce fichier à votre projet. Une version ultérieure, vous pouvez utiliser ce fichier de liaison pour créer un port dans le [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] console d’Administration. Pour plus d’informations sur le fichier de liaison, consultez [configurer une liaison de port physique à l’aide d’un fichier de liaison de port pour la base de données Oracle](../../adapters-and-accelerators/adapter-oracle-database/configure-a-physical-port-binding-using-a-port-binding-file-to-oracle-database.md).  
  
-   Le [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)] crée un fichier app.config dans les propriétés de liaison et les propriétés de connexion que vous spécifiez lorsque vous configurez la connexion et ajoute ce fichier dans votre répertoire de projet.  
  

-   [Se connecter à Oracle E-Business Suite dans Visual Studio à l’aide du plug-in référence Ajouter adaptateur Service](../../adapters-and-accelerators/adapter-oracle-ebs/connect-to-oracle-ebs-in-visual-studio-using-add-adapter-service-reference.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Obtenir les métadonnées pour les opérations Oracle E-Business Suite dans Visual Studio](../../adapters-and-accelerators/adapter-oracle-ebs/get-metadata-for-oracle-e-business-suite-operations-in-visual-studio.md)