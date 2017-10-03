---
title: "Accès aux en-têtes SOAP dans les Orchestrations | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- SOAP headers, orchestrations
- SOAP headers, properties
- orchestrations, SOAP headers
ms.assetid: 91fe053a-3f16-497c-b4bb-5fb54bec62e5
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 516b2bcc57bef507a028f30c61fd329a5fd7a598
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="accessing-soap-headers-in-orchestrations"></a>Accès aux en-têtes SOAP dans les Orchestrations
Vous pouvez accéder aux propriétés de contexte des en-têtes SOAP définis et inconnus dans les orchestrations. Pour plus d’informations sur les schémas de propriété et les propriétés de contexte, consultez [les schémas de propriété](../core/property-schemas.md).  
  
## <a name="defined-soap-header-context-properties"></a>Propriétés de contexte des en-têtes SOAP définis  
 Les propriétés de contexte d’en-tête SOAP défini dans les orchestrations nécessitent un schéma de propriété. Le schéma de propriété doit avoir l’espace de noms cible **http://schemas.microsoft.com/BizTalk/2003/SOAPHeader**et le **Property Schema Base** propriété  **MessageContextPropertyBase**. Chaque nom d’élément racine dans le schéma de propriété doit correspondre au nom d’élément de la racine de l’en-tête SOAP défini. Vous pouvez ensuite accédez aux valeurs des propriétés de contexte à l'aide de l'espace de noms du schéma de propriété et à l'aide du nom de la propriété. L'espace de noms du schéma de propriété diffère de l'espace de noms cible mentionné précédemment. Bien que l’espace de noms du schéma de propriété peut être n’importe quelle chaîne, généralement la valeur par défaut le nom du projet.  
  
 L’exemple suivant illustre l’accès à la propriété de contexte d’en-tête SOAP pour un espace de noms du schéma de propriété, **SOAPHeader**et le nom de propriété **OrigDest**:  
  
```  
stringVar = requestMessageInstance(SOAPHeader.OrigDest);  
```  
  
> [!NOTE]
>  Les en-têtes SOAP définis sont traités en tant qu'en-têtes d'« entrée » ou de « sortie ». Si l'Assistant définit le même en-tête SOAP pour le message de requête et pour le message de réponse, il ne renvoie pas automatiquement la valeur d'entrée dans la réponse. Vous devez explicitement copier la propriété de contexte de l'en-tête SOAP du message de requête dans celle du message de réponse.  
  
## <a name="copying-soap-header-context-property-of-incoming-message"></a>Copie de la propriété de contexte de l'en-tête SOAP d'un message entrant  
 Vous pouvez copier la propriété de contexte de l'en-tête SOAP d'un message entrant dans celle d'un message de réponse.  
  
 L'exemple suivant illustre la copie de la propriété de contexte d'un en-tête SOAP :  
  
```  
ResponseMessageInstance(SOAPHeader.OrigDest) = RequestMessageInstance(SOAPHeader.OrigDest);  
```  
  
 Lors de la création d'en-têtes SOAP pour une réponse SOAP, vous devez en premier lieu vous assurer d'avoir correctement créé les en-têtes SOAP. L'adaptateur SOAP ne vérifie pas le contenu des propriétés de contexte d'un en-tête SOAP. Si le message de réponse contient des valeurs d'en-têtes SOAP erronées, l'adaptateur SOAP ne peut pas l'envoyer à l'utilisateur de votre service Web.  
  
## <a name="unknown-soap-header-context-property"></a>Propriétés de contexte des en-têtes SOAP inconnus  
 La propriété de contexte d'un en-tête SOAP inconnu n'a pas besoin d'un schéma de propriété. Vous pouvez accéder à cette propriété de contexte global **SOAP. UnknownHeaders**.  
  
 L’exemple suivant illustre l’accès à la propriété de contexte d’en-tête SOAP inconnu **SOAP. UnknownHeaders**:  
  
```  
stringVar = RequestMessageInstance(SOAP.UnknownHeaders);  
```  
  
 Les valeurs contenues dans les propriétés de contexte correspondent à des chaînes comportant des données XML. Pour accéder à ces données le plus simple consiste à utiliser l’éditeur d’Expression BizTalk dans un **assignation du Message** ou **Expression** mettre en forme et de charger la chaîne dans un **XmlDocument** et utiliser Requêtes XPATH pour accéder aux champs spécifiques. Pour plus d’informations, création de documents XML dans l’éditeur d’Expression BizTalk, consultez [langage XLANG-s](../core/xlang-s-language.md).  
  
 Les propriétés de contexte sont associées à un message spécifique. Le moteur de messagerie ne mappe pas automatiquement les valeurs des en-têtes SOAP connus depuis un message de requête vers un message de réponse. Lors de la création d'un message de réponse pour un service Web, vous devez définir de manière spécifique les valeurs de l'en-tête SOAP. La commande suivante est la méthode la plus simple de configurer une propriété de contexte d’en-tête SOAP :  
  
```  
ResponseMessageInstance(SOAPHeader.OrigDest) = "<?xml version="1.0" encoding="utf-16"?><OrigDest xmlns=\"http://SOAPHeaderSchemas.OrigDestSOAPHeader\"><Origination xmlns=\"\">Home</Origination><Destination xmlns=\"\">Work</Destination> </OrigDest>"  
```  
  
 Vous pouvez également y parvenir en créant un **XmlDocument** et l’écriture de la valeur de chaîne de la **XmlDocument** à la propriété de contexte.  
  
> [!NOTE]
>  Si le **SOAP. UnknownHeaders** propriété est null, BizTalk renvoie automatiquement les en-têtes inconnus reçus dans la demande SOAP à la réponse SOAP. Si le **SOAP. UnknownHeaders** propriété de contexte du message de réponse n’est pas null, puis BizTalk renvoie cette valeur à la réponse SOAP.  
  
## <a name="see-also"></a>Voir aussi  
 [En-têtes SOAP avec les Services Web publiés](../core/soap-headers-with-published-web-services.md)