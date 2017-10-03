---
title: Adaptateur SMTP | Documents Microsoft
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- SMTP adapters, about SMTP adapters
- SMTP adapters, authenticating
- send adapters, SMTP adapters
- authenticating, SMTP adapters
- SMTP adapters
- SMTP adapters, send adapters
ms.assetid: b712f76d-3ce4-4780-9627-951e5951bd8a
caps.latest.revision: "11"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: c0d0d16bf266d0b636aa9955b5c25b37d9ab54d4
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="smtp-adapter"></a>Adaptateur SMTP
L'adaptateur SMTP permet d'échanger des informations entre un serveur exécutant Microsoft BizTalk Server et d'autres applications via le protocole SMTP (Simple Mail Transfer Protocol). BizTalk Server peut envoyer des messages à d'autres applications en créant un message électronique qu'il remet à une adresse de messagerie spécifiée. L'adaptateur d'envoi SMTP crée en interne un message électronique SMTP et l'envoie à une adresse de messagerie cible. L'adresse de messagerie cible est une propriété de l'adaptateur SMTP. L'Explorateur BizTalk expose cette propriété lors de la configuration du port d'envoi SMTP.  
  
 L’adaptateur SMTP prend en charge les caractères génériques dans le **à**, **FROM**, **CC** et **sujet** propriétés et les résout à leur réelle valeurs. Si les caractères génériques dans le **à**, **FROM**, et **CC** ne peuvent pas être résolu, le transport SMTP consigne une erreur et place le message dans la file d’attente suspendue ou redirige le message vers le transport secondaire. Si les caractères génériques ne peuvent pas être résolues dans le **sujet** propriété, le message est envoyé avec la **objet** propriété spécifiée exactement comme dans la propriété (par exemple, « Message MessageID % »).  
  
 Par défaut, le texte des messages SMTP est au format Texte brut. Pour utiliser le format HTML dans le corps des messages, vous pouvez configurer l'adaptateur pour qu'il utilise le contenu d'un fichier HTML pour le texte du message.  
  
 Pour plus d’informations sur les problèmes de sécurité SMTP, consultez [recommandations de sécurité de l’adaptateur SMTP](../core/smtp-adapter-security-recommendations.md).  
  
 L'adaptateur SMTP est constitué d'un seul adaptateur d'envoi. L'adaptateur d'envoi contrôle les ports d'envoi qui utilisent l'adaptateur SMTP.  
  
 Cette rubrique décrit le flux d'un message via l'adaptateur d'envoi SMTP.  
  
 **Adaptateur d’envoi SMTP**  
  
 L'adaptateur d'envoi SMTP récupère les messages auprès du serveur avant de les publier sur un serveur SMTP qui les envoie aux destinataires des messages électroniques. L'adaptateur d'envoi SMTP récupère le contenu du message à partir du corps de l'objet message BizTalk, d'un fichier spécifié ou d'un texte entré dans une boîte de dialogue affichée lors de la configuration de l'adaptateur.  
  
 Une fois que l'adaptateur d'envoi SMTP a publié un message sur le serveur SMTP, il supprime le message de la base de données MessageBox.  
  
 Pour chaque message qu'il envoie, l'adaptateur d'envoi SMTP peut demander un accusé de réception et une confirmation de lecture. L’adaptateur SMTP remet l’accusé de réception de notification et les informations à l’adresse spécifiée sur le protocole SMTP **de** en-tête.  
  
 **Authentification avec le serveur SMTP**  
  
 Si l'authentification du serveur SMTP est requise, l'adaptateur SMTP utilise l'un des types d'authentifications suivants :  
  
-   **De base.** Le serveur SMTP utilise les informations d'identification fournies par l'utilisateur à des fins d'authentification.  
  
-   **Compte du processus (NTLM).** Le serveur SMTP utilise les informations d'identification du processus actuel à des fins d'authentification.  
  
## <a name="in-this-section"></a>Dans cette section  
  
-   [Configuration de l’adaptateur SMTP](../core/configuring-the-smtp-adapter.md)  
  
-   [Restrictions relatives à la configuration de l’adaptateur SMTP](../core/restrictions-when-configuring-the-smtp-adapter.md)  
  
-   [Recommandations de sécurité de l’adaptateur SMTP](../core/smtp-adapter-security-recommendations.md)