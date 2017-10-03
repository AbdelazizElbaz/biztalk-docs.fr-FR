---
title: "Développement d’adaptateurs personnalisés | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 44765fbb-b24d-43b6-a40c-d28e319b90a5
caps.latest.revision: "29"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 3c13aba7e378d67523ec755837ac65b26989730a
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="developing-custom-adapters"></a>Développement d'adaptateurs personnalisés
Pour échanger des messages avec des systèmes, des applications et des entités externes, [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] fait appel aux adaptateurs. Les adaptateurs sont COM ou [!INCLUDE[btsDotNetFramework](../includes/btsdotnetframework-md.md)] composants qui transfèrent les messages vers et depuis la fin de l’entreprise. points (tels que les systèmes de fichiers, les bases de données et les applications d’entreprise personnalisées) à l’aide de divers protocoles de communication. [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]Fournit des adaptateurs natifs qui prennent en charge divers protocoles. notamment :  
  
-   un adaptateur File qui gère l'envoi et la réception des messages depuis un emplacement File ;  
  
-   des adaptateurs pour les protocoles EDI, FTP, HTTP, MSMQ, SMTP, POP3 et SOAP ;  
  
-   un adaptateur pour [!INCLUDE[btsWinSharePointSvcsNoVersion](../includes/btswinsharepointsvcsnoversion-md.md)].  
  
 Il peut arriver que [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] doive acheminer des messages vers une application personnalisée ou utiliser un protocole pour lequel aucun adaptateur natif n'est prévu. Des entreprises tierces ont élaboré des adaptateurs qui prennent en charge des protocoles supplémentaires, et vous souhaitez peut-être savoir s'il existe un adaptateur adapté à votre protocole avant d'écrire le vôtre. Pour obtenir la liste des adaptateurs et fournisseurs associés, consultez [http://go.microsoft.com/fwlink/?LinkId=47140](http://go.microsoft.com/fwlink/?LinkId=47140). Si vous ne parvenez pas à trouver un adaptateur qui prenne en charge vos conditions de communication, il vous reste la possibilité de développer votre propre adaptateur.  
  
 L'écriture d'un adaptateur personnalisé peut se révéler difficile. Pour vous faciliter la tâche, Microsoft a développé une structure de base appelée Infrastructure d'adaptateurs. Vous pouvez vous baser sur cette infrastructure, de même que vous pouvez utiliser l'exemple de code source fourni dans le kit SDK de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].  
  
 Les rubriques de cette section contiennent les conseils et les recommandations qui vous permettront de développer votre propre adaptateur.  
  
## <a name="in-this-section"></a>Dans cette section  
  
-   [Quelle est l’infrastructure d’adaptateurs ?](../core/what-is-the-adapter-framework.md)  
  
-   [Comment BizTalk Server instancie un adaptateur](../core/how-biztalk-server-instantiates-an-adapter.md)  
  
-   [Lots de messages](../core/message-batches.md)  
  
-   [Lots de messages transactionnels](../core/transactional-message-batches.md)  
  
-   [Développement d’un adaptateur de réception](../core/developing-a-receive-adapter.md)  
  
-   [Développement d’un adaptateur d’envoi](../core/developing-a-send-adapter.md)  
  
-   [Instanciation d’adaptateurs isolés](../core/instantiating-isolated-adapters.md)  
  
-   [Problèmes de conception de l’adaptateur](../core/adapter-design-issues.md)  
  
-   [Comment les adaptateurs de traiter les Messages volumineux](../core/how-adapters-handle-large-messages.md)  
  
-   [Comment gérer les défaillances d’adaptateur](../core/how-to-handle-adapter-failures.md)  
  
-   [Comment arrêter un adaptateur](../core/how-to-terminate-an-adapter.md)  
  
-   [Comment concevoir un adaptateur Performant](../core/how-to-design-a-performant-adapter.md)  
  
-   [Comment déployer un adaptateur personnalisé](../core/how-to-deploy-a-custom-adapter.md)  
  
-   [Comment tester et déboguer un adaptateur](../core/how-to-test-and-debug-an-adapter.md)  
  
-   [Comment ajouter des métadonnées de l’adaptateur à un projet BizTalk](../core/how-to-add-adapter-metadata-to-a-biztalk-project.md)  
  
-   [Problèmes de localisation de l’adaptateur](../core/adapter-localization-issues.md)  
  
-   [Conseils pour la conception de votre adaptateur.](../core/tips-for-designing-your-adapter.md)  
  
-   [Configuration de l’adaptateur au moment du Design](../core/adapter-design-time-configuration.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Développement de composants personnalisés](../core/developing-custom-components.md)