---
title: "Se connecter au système SAP dans Visual Studio | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- SAP system, connecting to
- Add Adapter Service Reference Visual Studio Plug-in
- Consume Adapter Service BizTalk Project Add-in
ms.assetid: 5fc356b1-05e8-4235-bb04-5ef6192c5291
caps.latest.revision: "7"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 20cd25c327f2081fed61e19e1571b91a0e39f556
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="connect-to-the-sap-system-in-visual-studio"></a>Se connecter au système SAP dans Visual Studio
Cette section fournit des informations sur l’utilisation de la [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)], le [!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)]et le [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)].  
  
-   Le  **[!INCLUDE[consumeadapterservlong](../../includes/consumeadapterservlong-md.md)]**  est disponible dans les projets BizTalk Server. Vous utilisez le [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)] pour générer des schémas de message (XSD) pour les opérations que vous souhaitez cibler dans votre solution BizTalk. Pour plus d’informations sur le développement de solutions avec BizTalk Server, consultez [applications SAP de développer à l’aide du modèle de Service WCF](../../adapters-and-accelerators/adapter-sap/develop-sap-applications-using-the-wcf-service-model.md).  
  
-   Le  **[!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)]**  est disponible dans les projets BizTalk Server. Vous utilisez le [!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)] pour générer des schémas de message (XSD) pour les opérations que vous souhaitez cibler dans votre solution BizTalk. Pour plus d’informations sur le développement de solutions avec BizTalk Server, consultez [applications SAP de développer à l’aide du modèle de Service WCF](../../adapters-and-accelerators/adapter-sap/develop-sap-applications-using-the-wcf-service-model.md).  
  
    > [!NOTE]
    >  Étant donné que le [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] est exposé comme une liaison WCF-Custom et comme l’adaptateur BizTalk, vous pouvez utiliser le [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)] ou le [!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)] à partir d’un projet BizTalk pour se connecter à un système SAP.  
  
-   Le  **[!INCLUDE[addadapterservreflong](../../includes/addadapterservreflong-md.md)]**  est disponible dans les projets de programmation non-BizTalk. Vous utilisez le [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)] pour générer une classe de client WCF ou d’une interface de rappel de service WCF lorsque vous développez des solutions à l’aide du modèle de service WCF. Pour plus d’informations sur le développement de solutions avec le modèle de service WCF, consultez [applications SAP de développer à l’aide du modèle de Service WCF](../../adapters-and-accelerators/adapter-sap/develop-sap-applications-using-the-wcf-service-model.md).  
  
 Pour utiliser le [!INCLUDE[consumeadapterservlong](../../includes/consumeadapterservlong-md.md)], le [!INCLUDE[addadapterwiz](../../includes/addadapterwiz-md.md)], ou [!INCLUDE[addadapterservreflong](../../includes/addadapterservreflong-md.md)] vous devez vous connecter au système SAP. Toute l’interface utilisateur trois présente une boîte de dialogue par le biais duquel vous configurez une connexion en définissant les éléments suivants :  
  
-   **Paramètres de connexion**. Voici les paramètres qui sont utilisés pour générer l’URI de connexion telles que l’hôte d’application serveur ou hôte du serveur et l’ID de client.  
  
-   **Informations d’identification de mot de passe de nom utilisateur pour le système SAP**. Ils sont utilisés pour vous authentifier sur le système SAP lorsque la connexion est établie. Vous devez spécifier un nom d’utilisateur et un mot de passe.  
  
-   **Propriétés de liaison**. Propriétés de liaison sont facultatifs, et si vous les spécifiez dépend principalement si vous ciblez les opérations qui nécessitent des propriétés de liaison spécifique. Par exemple, pour une opération de ReceiveIdoc, vous devez définir le **ReceiveIdocFormat** propriété de liaison de chaîne. Pour plus d’informations sur les propriétés de liaison, consultez [en savoir plus sur l’adaptateur BizTalk pour les propriétés de liaison mySAP Business Suite](../../adapters-and-accelerators/adapter-sap/read-about-biztalk-adapter-for-mysap-business-suite-binding-properties.md).  
  
 Au minimum, lorsque vous configurez la connexion au système SAP, vous ne devez spécifier les propriétés de liaison et les paramètres de connexion qui sont nécessaires pour établir la connexion et qui affectent les métadonnées retournées par le [!INCLUDE[adaptersap_short](../../includes/adaptersap-short-md.md)] pour les opérations vous vous souhaitez cibler. Toutefois, vous souhaiterez également spécifier des valeurs pour toutes les propriétés de liaison supplémentaires et des paramètres de connexion qui seront utilisés au moment de l’exécution. Il s’agit, car :  
  
-   Le [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)] crée un fichier de liaison de port de BizTalk à partir des propriétés de liaison et les paramètres de connexion que vous spécifiez lorsque vous configurez la connexion et ajoute ce fichier à votre projet.  
  
-   Le [!INCLUDE[addadapterservrefshort](../../includes/addadapterservrefshort-md.md)] crée un fichier app.config dans les propriétés de liaison et les propriétés de connexion que vous spécifiez lorsque vous configurez la connexion et ajoute ce fichier dans votre répertoire de projet.  
  

  
## <a name="see-also"></a>Voir aussi  
 [Obtenir les métadonnées pour les opérations de SAP dans Visual Studio](../../adapters-and-accelerators/adapter-sap/get-metadata-for-sap-operations-in-visual-studio.md)