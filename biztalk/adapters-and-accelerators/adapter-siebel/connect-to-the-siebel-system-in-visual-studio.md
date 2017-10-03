---
title: "Se connecter au système Siebel dans Visual Studio | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Add Adapter Service Reference Plug-in
- Consume Adapter Service Add-in
- how to, connect to the Siebel System in Visual Studio
ms.assetid: 4a94bce9-fda9-4e00-b26c-08672a80e3be
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: c3f7bacf42f90da21830d24587cc7ae6a6e042bf
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="connect-to-the-siebel-system-in-visual-studio"></a>Se connecter au système Siebel dans Visual Studio
Cette section fournit des instructions sur l’utilisation de la [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)], le [!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)]et le [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)].  
  
-   Le  **[!INCLUDE[consumeadapterservlong](../../includes/consumeadapterservlong-md.md)]**  est disponible dans [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] projets et est installé dans le cadre de la [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)] installation. Vous utilisez le [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)] pour générer des schémas de message (XSD) pour les opérations que vous souhaitez cibler dans votre solution BizTalk. Pour plus d’informations sur le développement de solutions avec [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)], consultez [BizTalk de développer les applications à l’aide de l’adaptateur Siebel](../../adapters-and-accelerators/adapter-siebel/develop-biztalk-applications-using-the-siebel-adapter.md).  
  
-   Le  **[!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)]**  est disponible dans le [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] projets et est installé dans le cadre de la [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] installation. Vous utilisez le [!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)] pour générer des schémas de message (XSD) pour les opérations que vous souhaitez cibler dans votre solution BizTalk. Pour plus d’informations sur le développement de solutions avec [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)], consultez [BizTalk de développer les applications à l’aide de l’adaptateur Siebel](../../adapters-and-accelerators/adapter-siebel/develop-biztalk-applications-using-the-siebel-adapter.md).  
  
    > [!NOTE]
    >  Étant donné que le [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)] est exposé comme une liaison WCF-Custom et comme l’adaptateur BizTalk, vous pouvez utiliser le [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)] ou le [!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)] à partir d’un projet BizTalk pour se connecter à un système Siebel.  
  
-   Le  **[!INCLUDE[addadapterservreflong](../../includes/addadapterservreflong-md.md)]**  est disponible dans les projets de programmation non-BizTalk. Vous utilisez le [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)] pour générer une classe de client WCF ou d’une interface de rappel de service WCF lorsque vous développez des solutions à l’aide du modèle de service WCF. Pour plus d’informations sur le développement de solutions avec le modèle de service WCF, consultez [Siebel de développer les applications à l’aide du modèle de Service WCF](../../adapters-and-accelerators/adapter-siebel/develop-siebel-applications-using-the-wcf-service-model.md).  
  
 Pour utiliser le [!INCLUDE[consumeadapterservlong](../../includes/consumeadapterservlong-md.md)], [!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)], ou [!INCLUDE[addadapterservreflong](../../includes/addadapterservreflong-md.md)], vous devez vous connecter au système Siebel. Les trois méthodes présentent une boîte de dialogue par le biais duquel vous configurez une connexion en définissant les éléments suivants :  
  
-   **Paramètres de connexion**. Voici les paramètres qui sont utilisés pour générer l’URI de connexion telles que le nom du serveur de l’entreprise Siebel.  
  
-   **Informations d’identification de mot de passe de nom utilisateur pour le système Siebel**. Ils sont utilisés pour vous authentifier sur le système Siebel lorsque la connexion est établie. Vous devez spécifier un nom d’utilisateur et un mot de passe.  
  
-   **Propriétés de liaison**. Propriétés de liaison sont facultatifs, et si vous les spécifiez dépend principalement si vous ciblez les opérations qui nécessitent des propriétés de liaison spécifique.  
  
 Au minimum, lorsque vous configurez la connexion au système Siebel, vous ne devez spécifier les propriétés de liaison et les paramètres de connexion qui sont nécessaires pour établir la connexion et qui affectent les métadonnées retournées par le [!INCLUDE[adaptersiebel_short](../../includes/adaptersiebel-short-md.md)] pour les opérations vous vous souhaitez cibler. Toutefois, vous souhaiterez également spécifier des valeurs pour toutes les propriétés de liaison supplémentaires et des paramètres de connexion qui seront utilisés au moment de l’exécution. Il s’agit, car :  
  
-   Le [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)] crée un fichier de liaison de port de BizTalk à partir des propriétés de liaison et les paramètres de connexion que vous spécifiez lorsque vous configurez la connexion et ajoute ce fichier à votre projet.  
  
-   Le [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)] crée un fichier app.config dans les propriétés de liaison et les propriétés de connexion que vous spécifiez lorsque vous configurez la connexion et ajoute ce fichier dans votre répertoire de projet.  
  
 
  
## <a name="see-also"></a>Voir aussi  
 [Obtenir les métadonnées pour les opérations Siebel dans Visual Studio](../../adapters-and-accelerators/adapter-siebel/get-metadata-for-siebel-operations-in-visual-studio.md)