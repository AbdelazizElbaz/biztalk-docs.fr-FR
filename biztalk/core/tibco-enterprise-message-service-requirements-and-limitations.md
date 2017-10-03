---
title: TIBCO Enterprise Message Service et les Limitations | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- encryption
- messages, compression
- EMS limitations
- message compression
- API, adding to GAC
- global assembly cache, adding API
- GAC, adding TIBCO EMS API
- system requirements
- TIBCO.EMS.dll
- EMS requirements
- messages, encryption
ms.assetid: 6e4c022c-e6a8-4ac5-b998-b0465002a31e
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 81e49f4a74cce4414fd9d0b069a382d9facb03d0
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="tibco-enterprise-message-service-requirements-and-limitations"></a>Impératifs et restrictions de TIBCO Enterprise Message Service
## <a name="system-requirements"></a>Configuration système requise  
 L'adaptateur Microsoft BizTalk pour TIBCO Enterprise Message Service prend en charge TIBCO Enterprise Message Service (EMS) version 4.2. Un client SDK est inclus avec TIBCO EMS version 4.2 (via l'API TIBCO EMS C# ). L'adaptateur BizTalk pour TIBCO EMS utilise cette API pour communiquer avec TIBCO EMS.  
  
## <a name="adding-the-api-to-the-gac"></a>Ajout de l'API au GAC  
 L'adaptateur BizTalk pour TIBCO EMS requiert l'ajout de l'API TIBCO EMS C#, TIBCO.EMS.dll, au GAC (Global Assembly Cache). Si cet assembly n'est pas installé, l'adaptateur déclenche une exception et consigne un message approprié.  
  
#### <a name="to-add-the-tibco-ems-c-api-to-the-gac"></a>Pour ajouter l'API TIBCO EMS C# au GAC  
  
1.  Copiez l'API TIBCO EMS C# sur votre ordinateur exécutant [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)].  
  
2.  Accédez au répertoire contenant le fichier de l'API C#, TIBCO.EMS.DLL.  
  
     Dans le cas d'une installation par défaut, le chemin d'accès à cette DLL est c:\tibco\ems\clients\cs\TIBCO.EMS.DLL.  
  
3.  Ouvrez une invite de commandes, puis tapez :  
  
     `C:\bin> gacutil /i TIBCO.EMS.dll`  
  
     Le fichier TIBCO.EMS.dll affiche maintenant le GAC.  
  
     Pour afficher la liste du GAC, dans le panneau de configuration, ouvrez **outils d’administration**, ouvrez **Microsoft .NET Framework x.x configuration**, puis cliquez sur **Assembly Cache**.  
  
## <a name="limitations"></a>Limitations  
 L'adaptateur BizTalk pour TIBCO Enterprise Message Service utilise le fichier TIBCO.EMS.dll pour communiquer avec TIBCO Enterprise Message Service. Lorsque vous utilisez l'API TIBCO EMS C#, vous devez prendre en compte les limitations suivantes :  
  
-   La compression des messages, qui permet au client TIBCO EMS d'envoyer des messages à EMS sous une forme compressée, n'est pas disponible avec l'API C#.  
  
-   Le chiffrement des messages entre l'adaptateur et le serveur n'est pas disponible avec l'API C#. Cette API n'autorise pas le chiffrement SSL à l'aide des bibliothèques OpenSSL.  
  
-   L'API C# ne prend pas en charge l'API d'administration pour EMS.  
  
-   L'adaptateur BizTalk pour TIBCO EMS ne peut ni envoyer ni recevoir les messages dont la taille dépasse 50 Mo. Au-delà de cette taille, l'environnement rencontre des exceptions System.OutOfMemoryException.  
  
## <a name="see-also"></a>Voir aussi  
 [Planification et Architecture](../core/planning-and-architecture16.md)