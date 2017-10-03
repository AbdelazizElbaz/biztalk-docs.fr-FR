---
title: "L’authentification unique pour les adaptateurs natifs | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- adapters, SSO
- SSO, adapters
ms.assetid: d8527f0f-910c-42ce-9bd3-83ab6d4349c0
caps.latest.revision: "12"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 45aaf357d943853cc9504762437f554f1d28efb7
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="sso-for-native-adapters"></a>SSO pour adaptateurs natifs
L'authentification unique de l'entreprise (SSO) vous permet de ne vous authentifier qu'une seule fois auprès de différents systèmes informatiques ou sites web. Ce composant de Microsoft [!INCLUDE[btsBizTalkServerNoVersion](../includes/btsbiztalkservernoversion-md.md)] permet aux adaptateurs BizTalk de fournir le bon identifiant d'utilisateur et les bonnes informations d'identification à de multiples applications utilisant, au sein de votre réseau, un mécanisme d'authentification commun basé sur vos informations d'identification Microsoft Windows. Une fois que Windows a authentifié vos informations d'identification, vous n'avez plus besoin de fournir d'autres informations d'identification pour vous connecter aux applications.  
  
 La SSO est disponible pour les adaptateurs HTTP et SOAP, bien qu'elle soit désactivée par défaut. Pour l'adaptateur HTTP, vous pouvez configurer le port d'envoi et l'emplacement de réception pour utiliser la SSO ; pour l'adaptateur SOAP, vous ne pouvez configurer que l'emplacement de réception pour utiliser la SSO. Pour les deux adaptateurs, vous utilisez la console d'administration de Biz Talk Server pour configurer la SSO.  
  
 L'authentification pour la SSO repose en premier lieu sur l'authentification Windows et sur les groupes Windows créés dans Active Directory. Toutes les opérations effectuées par un utilisateur ou un administrateur avec la SSO nécessitent l'authentification préalable de l'utilisateur ou de l'administrateur par Windows.  
  
 Pour plus d'informations sur le fonctionnement de la SSO avec les adaptateurs HTTP et SOAP, consultez les rubriques adéquates dans Voir aussi.  
  
## <a name="see-also"></a>Voir aussi  
 [À l’aide de l’authentification unique](../core/using-sso.md)   
 [Adaptateur HTTP](../core/http-adapter.md)   
 [Adaptateur SOAP](../core/soap-adapter.md)