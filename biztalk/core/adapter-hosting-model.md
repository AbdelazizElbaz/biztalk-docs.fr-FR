---
title: "Modèle d’hébergement de carte | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: cf9a8e6b-8c8d-47ec-b2a3-aed58206121d
caps.latest.revision: "14"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 645a1fcd41650c98c442549a898f7083be770842
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="adapter-hosting-model"></a>Modèle d’hébergement de carte
En général, les adaptateurs BizTalk sont hébergés dans le service BizTalk, Btsntsvc.exe. Cela signifie que [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] gère la durée de vie de l’adaptateur. Il existe également des cas de figure (voir ci-dessous) où d'autres processus gèrent les adaptateurs.  
  
## <a name="in-process-adapters"></a>Adaptateurs in-process  
 Les cartes qui sont gérés par [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] sont appelés adaptateurs in-process. [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]effectue l’opération suivante pour ces adaptateurs :  
  
-   Il instancie l'adaptateur dès que [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] a démarré.  
  
-   Il transmet à l'adaptateur son proxy de transport durant l'initialisation.  
  
-   Il répond aux requêtes de l'adaptateur.  
  
-   Il met fin à l'adaptateur à la fermeture du service [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].  
  
 Au moment de l'exécution, [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] fournit à l'adaptateur des informations sur la configuration des gestionnaires et des points de terminaison. D'autres points relatifs à la configuration sont spécifiés, comme ceux concernant les fenêtres de service qui définissent des périodes spécifiques durant lesquelles l'adaptateur est activé de manière à gérer activement les requêtes.  
  
 Il est possible de fermer manuellement le service BizTalk à l'aide de la console Administration de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] ou du gestionnaire de contrôle des services. Si la connectivité avec les bases de données [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] est perdue, le service se recycle automatiquement.  
  
 Dans le modèle d'hébergement typique, les adaptateurs côté réception et les adaptateurs côté envoi sont hébergés dans le même processus que le service BizTalk, avec le moteur de messagerie et le moteur d'orchestration. Le modèle d'hébergement est suffisamment flexible pour permettre la séparation des hôtes de réception, d'envoi et d'orchestration et la combinaison de ces derniers. Dans la figure ci-dessous, l'hôte exécute les trois dans un même processus.  
  
 Du fait du modèle d'hébergement riche, il est important, lorsque vous développez des adaptateurs, que vous vous rappeliez que les adaptateurs d'envoi et de réception peuvent éventuellement ne jamais être configurés dans le même hôte. Il se peut même qu'ils soient configurés pour être exécutés sur plusieurs ordinateurs différents.  
  
 ![](../core/media/regularadapterhostingmodel.gif "RegularAdapterHostingModel")  
Le modèle d'hébergement d'adaptateurs in-process  
  
## <a name="isolated-adapters"></a>Adaptateurs isolés  
 Il existe des cas où héberger des adaptateurs de réception dans le service BizTalk est impossible. Ainsi, le modèle de processus IIS (Internet Information Services) est tel qu'IIS gère la durée de vie des applications ASP.NET et des extensions ISAPI. L'adaptateur SOAP BizTalk doit être exécuté dans le même espace de processus qu'ISS pour que [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] ne puisse pas contrôler la durée de vie des instances de l'adaptateur SOAP.  
  
 Pour ces types d'adaptateurs, il existe un autre modèle d'hébergement appelé «°adaptateurs de réception isolés », ou simplement « adaptateurs isolés ». Par contre, on ne parle pas d'adaptateurs d'envoi isolés.  
  
 [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] ne pouvant pas créer un adaptateur isolé, l'adaptateur doit acquérir son propre proxy de transport et s'inscrire lui-même auprès de ce proxy.  
  
 Le schéma suivant illustre l'architecture d'hébergement de [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)]. Pour des raisons de performances, l'architecture de l'hôte isolé tente d'éliminer toute communication inutile entre processus. L'adaptateur isolé et la pile du moteur de messagerie BizTalk faisant partie d'un même processus, il n'y a pas de communication entre processus lorsque l'adaptateur appelle le moteur de messagerie. Dans ce cas, la seule communication entre processus intervient entre le moteur de messagerie et la base de données, ce qui est inévitable.  
  
 ![](../core/media/isolatedadapters.gif "IsolatedAdapters")  
Le modèle d'hébergement d'adaptateurs isolés  
  
## <a name="see-also"></a>Voir aussi  
 [Quelle est l’infrastructure d’adaptateurs ?](../core/what-is-the-adapter-framework.md)