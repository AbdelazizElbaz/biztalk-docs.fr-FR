---
title: "Résolution des problèmes de Migration BizTalk Server | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e6eddc0a-2403-4bcd-9327-23f51ce7d57b
caps.latest.revision: "4"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 1dcdb53c7123b4ffaa2294db080e1efc4fb4eb65
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="troubleshooting-biztalk-server-migration"></a>Dépannage de la migration BizTalk Server
Cette section centralise les informations sur les problèmes connus rencontrés lors de la migration d'applications BizTalk depuis [!INCLUDE[btsbiztalkserver2006r2](../includes/btsbiztalkserver2006r2-md.md)] ou [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 2009 vers [!INCLUDE[prague](../includes/prague-md.md)].  
  
## <a name="known-issues"></a>Problèmes connus  
  
#### <a name="custom-applications-might-not-work-while-upgrading"></a>Les applications personnalisées ne fonctionnent pas pendant la mise à niveau  
  
##### <a name="problem"></a>Problème  
 Certaines applications personnalisées ne fonctionnent pas pendant la mise à niveau depuis [!INCLUDE[btsbiztalkserver2006r2](../includes/btsbiztalkserver2006r2-md.md)] ou [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] 2009 vers [!INCLUDE[prague](../includes/prague-md.md)].  
  
##### <a name="cause"></a>Cause  
 Tous les composants de code géré de BizTalk s'exécutent sous CLR 4.0. La compilation de ces composants s'effectuant par rapport à [!INCLUDE[netfx40_short](../includes/netfx40-short-md.md)], ils nécessitent un fichier de configuration pour pouvoir s'exécuter sous CLR 4.0.  
  
##### <a name="solution"></a>Solution  
 Pour résoudre ce problème, mettez le fichier de configuration à jour.  
  
```  
<configuration>  
<startup useLegacyV2RuntimeActivationPolicy="true">  
<supportedRuntime version="v4.0" />  
</startup>  
</configuration>  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Dépannage](../core/troubleshooting.md)