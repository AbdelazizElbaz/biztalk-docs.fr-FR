---
title: "Génération d’un Message AS2 sortant | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 288c8101-9a96-4f98-ae18-df43c7cdb3a0
caps.latest.revision: "17"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 90a0b1e37e96086de7d8901b61afa8dea859a388
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="generating-an-outgoing-as2-message"></a>Génération d'un message AS2 sortant
Les pipelines d'envoi AS2EDISend et AS2Send génèrent un message sortant comme suit. Chaque pipeline utilise les propriétés dans l’onglet d’accord unidirectionnel de la **propriétés de l’accord** boîte de dialogue pour générer le message AS2 sortant.  
  
## <a name="agreement-destination-and-messageid-determination"></a>Accord, Destination et Détermination de l'ID du message  
 Les pipelines d'envoi AS2 déterminent l'accord et la destination à utiliser lors de l'envoi d'un message AS2 comme suit :  
  
-   Pour déterminer l'accord à utiliser lors du traitement d'un message sortant, l'encodeur AS2 tente de faire correspondre les propriétés AS2-To dans le message et l'AS2Identity d'un profil d'entreprise tiers ou le port d'envoi s'abonnant au message et un port d'envoi associé à l'accord. Pour plus d’informations sur ce processus, consultez [résolution de l’accord pour les Messages AS2 sortants](../core/agreement-resolution-for-outgoing-as2-messages.md).  
  
-   Pour déterminer la destination du message, le pipeline d'envoi d'un port d'envoi dynamique utilise la propriété OutboundTransportLocation, qui doit être écrite ou promue dans le contexte par une application principale pour que le port d'envoi dynamique fonctionne. Le pipeline d'envoi dans un pipeline d'envoi statique détermine la destination à partir de la propriété AS2-From des propriétés de l'accord AS2 et des identités des propriétés du profil d'entreprise.  
  
-   L'encodeur AS2 doit définir l'en-tête MessageId d'un message AS2 sortant. Le pipeline d'envoi détermine le MessageId à partir de la propriété de contexte `EdiIntAS.MessageId` ou `HTTP.UserHttpHeaders`. Si ces deux propriétés de contexte sont définies, l'encodeur utilise la valeur à partir de la propriété de contexte `HTTP.UserHttpHeaders`. Si aucune n'est définie, le pipeline d'envoi génère automatiquement une valeur pour MessageID.  
  
## <a name="outgoing-message-processing"></a>Traitement des messages sortants  
 Les pipelines d'envoi AS2 effectuent le traitement suivant pour le message AS2 sortant :  
  
-   Effectue une copie du message au format natif et la stocke dans la base de données de non-répudiation, si la non-répudiation des messages AS2 est activée dans les propriétés de l'accord.  
  
-   L'encodeur AS2 crée les en-têtes HTTP (et AS2) dans la propriété de contexte `HTTP.UserHttpHeaders`. Pour plus d’informations sur ce processus, consultez [de traitement côté envoi d’un Message EDI sortant sur AS2](../core/send-side-processing-of-an-outgoing-edi-message-over-as2.md).  
  
-   Écrit `HTTP.UserHttpHeaders` dans le contexte.  
  
-   Compresse le message sortant, si activé.  
  
-   Effectue le traitement MIME, notamment le chiffrement du message (si activé dans le **Message doit être chiffré** propriété d’accord) et d’appliquer une signature numérique (si activé dans le **Message doit être signé**propriétés de l’accord). Le pipeline AS2Send utilise SHA1 ou MD5 pour appliquer la signature, en fonction des paramètres de l'accord.  
  
-   Crée un en-tête MIME à disposition de contenu contenant la valeur spécifiée, si la transmission du nom de fichier est active dans les propriétés de l'accord.  
  
-   Effectue une copie du message chiffré (au format câble) et la stocke dans la base de données de non-répudiation, si activé dans le **NRR activé pour les messages AS2 encodés sortants** dans les propriétés de l’accord.  
  
-   Si un MDN est nécessaire, calcule la valeur MIC et la stocke dans la banque de données.  
  
-   Remet le message à l'adaptateur HTTP, lequel écrit les en-têtes à partir de la propriété de contexte UserHTTPHeaders dans le message AS2 sortant.  
  
-   Si la fiabilité de la messagerie est nécessaire, renvoie le message jusqu'à réception d'un MDN.  
  
## <a name="see-also"></a>Voir aussi  
 [Envoi des Messages AS2 par BizTalk Server](../core/how-biztalk-server-sends-as2-messages.md)   
 [AS2 Composants d’envoi](../core/as2-send-components.md)