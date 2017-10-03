---
title: "Sécurité du Service Web A4SWIFT | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- IIS security
- Web service [A4SWIFT]
- security, transport-level security
- security, message-level security
- ASP.NET security
- A4SWIFT, Web service
- A4SWIFT, security
- security, IIS
- security, ASP.NET
- security, Web service
- messages, security
ms.assetid: e6c7d275-569f-47f6-81fb-10bcd86ff417
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 8510172517d58475d855d258b72b16271835dbc1
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="a4swift-web-service-security"></a>Sécurité du Service Web A4SWIFT
Le [!INCLUDE[A4SWIFT_CurrentVersion_abbrev_md](../../includes/a4swift-currentversion-abbrev-md.md)]service Web par défaut est installé dans un modèle de sécurité hybride hautement sécurisée. Dans le modèle d’IIS/ASP.NET une limite d’approbation existe entre le service Web, le [!INCLUDE[btsWinSharePointSvcsNoVersion](../../includes/btswinsharepointsvcsnoversion-md.md)] site et le [!INCLUDE[A4SWIFT_CurrentVersion_abbrev_md](../../includes/a4swift-currentversion-abbrev-md.md)]base de données.  
  
## <a name="iis-and-aspnet-security-settings"></a>IIS et les paramètres de sécurité ASP.NET  
 Lorsqu’un appel est effectué à la [!INCLUDE[A4SWIFT_CurrentVersion_abbrev_md](../../includes/a4swift-currentversion-abbrev-md.md)] serveur Web, IIS authentifie l’utilisateur la première fois à l’aide de [!INCLUDE[btsWinNoVersion](../../includes/btswinnoversion-md.md)] l’authentification. Le fichier web.config du service Web est définie par défaut à utiliser [!INCLUDE[btsWinNoVersion](../../includes/btswinnoversion-md.md)] l’authentification sans emprunt d’identité et vérifie que l’appelant est un membre de le [!INCLUDE[A4SWIFT_CurrentVersion_abbrev_md](../../includes/a4swift-currentversion-abbrev-md.md)] groupe d’utilisateurs. Si l’appelant est un membre de le [!INCLUDE[A4SWIFT_CurrentVersion_abbrev_md](../../includes/a4swift-currentversion-abbrev-md.md)] groupe d’utilisateurs, les méthodes de service Web sont exécutés sous l’identité du processus du pool d’applications. Pour [!INCLUDE[A4SWIFT_CurrentVersion_abbrev_md](../../includes/a4swift-currentversion-abbrev-md.md)], il s’agit du pool d’applications par défaut pour [!INCLUDE[btsWinSharePointSvcsNoVersion](../../includes/btswinsharepointsvcsnoversion-md.md)].  
  
 Pour le [!INCLUDE[A4SWIFT_CurrentVersion_abbrev_md](../../includes/a4swift-currentversion-abbrev-md.md)] pour supprimer le message de la boîte de réception de l’appelant de la méthode Web, service Web du [!INCLUDE[A4SWIFT_CurrentVersion_abbrev_md](../../includes/a4swift-currentversion-abbrev-md.md)] service Web doit emprunter l’identité de l’appelant pour le **supprimer** et **GetCheckedOutUser** méthodes. Ce sont les seules méthodes s’exécutés sous le contexte de l’appelant d’origine. Étant donné que la [!INCLUDE[A4SWIFT_CurrentVersion_abbrev_md](../../includes/a4swift-currentversion-abbrev-md.md)] service Web emprunte l’identité de l’appelant de ces méthodes Web, l’appelant doit disposer des autorisations explicites définies sur les bibliothèques de documents SharePoint sur laquelle agit l’appelant.  
  
## <a name="a4swift-secure-communication-settings"></a>Paramètres de Communication sécurisé A4SWIFT  
[!INCLUDE[A4SWIFT_CurrentVersion_abbrev_md](../../includes/a4swift-currentversion-abbrev-md.md)]s’inquiète du fait de garantir l’intégrité et la confidentialité des messages de service Web lorsqu’ils passent de [!INCLUDE[btsInpathNoVersion](../../includes/btsinpathnoversion-md.md)] à [!INCLUDE[btsWinSharePointSvcsNoVersion](../../includes/btswinsharepointsvcsnoversion-md.md)] pour les applications BizTalk sur le réseau. Pour fournir le niveau le plus élevé de sécurité [!INCLUDE[A4SWIFT_CurrentVersion_abbrev_md](../../includes/a4swift-currentversion-abbrev-md.md)] prend en charge deux niveaux de sécuriser les communications entre les applications : au niveau du transport et au niveau du message.  
  
## <a name="transport-level-security"></a>Sécurité au niveau du transport  
[!INCLUDE[A4SWIFT_CurrentVersion_abbrev_md](../../includes/a4swift-currentversion-abbrev-md.md)]prend en charge les communications SSL entre [!INCLUDE[btsInpathNoVersion](../../includes/btsinpathnoversion-md.md)], le [!INCLUDE[A4SWIFT_CurrentVersion_abbrev_md](../../includes/a4swift-currentversion-abbrev-md.md)] service Web, [!INCLUDE[btsWinSharePointSvcsNoVersion](../../includes/btswinsharepointsvcsnoversion-md.md)], et [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)]. [!INCLUDE[A4SWIFT_CurrentVersion_abbrev_md](../../includes/a4swift-currentversion-abbrev-md.md)]s’adapte automatiquement aux paramètres de sécurité du site MRSR lors de la transmission des messages.  
  
 Sécurité du protocole Internet (IPSec) peut également être implémentée pour sécuriser la communication entre [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] et [!INCLUDE[btsSQLServerNoVersion](../../includes/btssqlservernoversion-md.md)].  
  
 Pour plus d’informations sur la mise en œuvre d’IPSec pour sécuriser la communication entre [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] et [!INCLUDE[btsSQLServerNoVersion](../../includes/btssqlservernoversion-md.md)], consultez « Sécurisation de votre déploiement de BizTalk Server » dans [!INCLUDE[btsBizTalkServer2006r3](../../includes/btsbiztalkserver2006r3-md.md)] aide.  
  
  
## <a name="message-level-security"></a>Sécurité de niveau message  
[!INCLUDE[A4SWIFT_CurrentVersion_abbrev_md](../../includes/a4swift-currentversion-abbrev-md.md)]sécurité au niveau du message résultant de signer numériquement les messages pour fournir l’intégrité. La signature de message [!INCLUDE[A4SWIFT_CurrentVersion_abbrev_md](../../includes/a4swift-currentversion-abbrev-md.md)] est couvert en détail dans [sécurité InfoPath](../../adapters-and-accelerators/accelerator-swift/infopath-security.md).