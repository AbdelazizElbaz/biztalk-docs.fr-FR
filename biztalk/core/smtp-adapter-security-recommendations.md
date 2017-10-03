---
title: "Recommandations de sécurité de l’adaptateur SMTP | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- configuring [SMTP adapters], security
- SMTP adapters, security
- security, SMTP adapters
ms.assetid: 45f13744-a0eb-4b4e-85cd-6b862b384ad5
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: ca1aeed0ad8c80cc32d333aeef37d1da6feabfc2
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="smtp-adapter-security-recommendations"></a>Recommandations de sécurité de l’adaptateur SMTP
L'adaptateur SMTP permet d'échanger des informations entre un serveur exécutant BizTalk Server et d'autres applications via le protocole SMTP (Simple Mail Transfer Protocol). BizTalk Server peut envoyer des messages à d'autres applications en créant un message électronique qu'il remet à une adresse de messagerie spécifiée. L'adaptateur SMTP sert uniquement à l'envoi des messages. Pour plus d’informations sur l’adaptateur SMTP, consultez [adaptateur SMTP](../core/smtp-adapter.md).  
  
 Lorsque vous configurez le compte de service pour l'instance d'hôte qui exécute l'adaptateur SMTP, vous devez spécifier le type d'authentification que vous souhaitez utiliser avec le serveur SMTP distant. Les options d'authentification suivantes sont disponibles : Authentification de base (texte clair), NTLM (à l'aide des informations d'identifications actuelles) et Aucune (si l'authentification n'est pas requise par le serveur SMTP).  
  
 Lorsque vous envoyez un message à l'aide de l'adaptateur SMTP, BizTalk Server envoie le message en texte clair par défaut. Si vous utilisez un pipeline doté d'un composant de codage S/MIME, vous pouvez chiffrer le message avant de l'envoyer au serveur SMTP. Toutefois, l'en-tête SMTP est toujours en texte clair.  
  
 Si vous souhaitez auditer les messages électroniques envoyés par BizTalk Server, vous devez utiliser l'adaptateur SMTP pour le connecter à votre propre serveur SMTP, sur lequel vous pouvez ensuite auditer les messages.  
  
 L'adaptateur SMTP ne prend pas en charge le protocole SSL (Secure Sockets Layer).  
  
## <a name="see-also"></a>Voir aussi  
 [Ports pour les serveurs de l’envoi et la réception](../core/ports-for-the-receive-and-send-servers.md)   
 [Droits d’utilisateur de sécurité minimales](../core/minimum-security-user-rights.md)