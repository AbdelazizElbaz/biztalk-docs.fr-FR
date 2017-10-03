---
title: "Les membres de l’Exception API ESB | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 8a095549-7e5d-4a7c-96d2-8fc6ca3efd63
caps.latest.revision: "5"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 5e267f8533948fc46c4604ebfffb6d22367a321e
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="the-esb-exception-api-members"></a>Les membres de l’Exception API ESB
Le **ESB. ExceptionHandling** assembly expose des méthodes publiques pour créer des messages d’erreur et pour gérer et de les récupérer pour le traitement, comme décrit dans le tableau suivant.  
  
|Cas de membre et d’utilisation| Description|  
|-------------------------|-----------------|  
|**CreateFaultMessage** [étendue du Gestionnaire d’exceptions]|**public XLANGMessage CreateFaultMessage() statique** ne prend aucun paramètre. Retourne une instance du message d’erreur ESB en tant qu’un **XLANGMessage** instance remplie avec le nom de l’orchestration en cours, ID d’instance d’orchestration (GUID), **System.Exception** instance et les autres propriétés ambiantes. **Remarque :** cette Interface de programmation d’applications (API) doit être appelée uniquement à partir d’un bloc d’exception dans XLANG.|  
|**AddMessage** [étendue du Gestionnaire d’exceptions]|**AddMessage static public void (faultMessage, existingMessage)** prend comme paramètres deux **XLANGMessage** instances ; le premier est un message d’erreur ESB nouvellement créé, et la seconde n’importe quelle instance de message existant dans la orchestration. La méthode rend persistant de l’instance de message existant et ses propriétés de contexte de message dans le message d’erreur et la rend disponible pour récupération à l’aide de la **GetMessage** (méthode). Aucune valeur de retour.|  
|**SetException** [étendue du Gestionnaire d’exceptions]|**SetException statique publique void (faultMessage, exception)** prend comme paramètres d’un message d’erreur ESB en tant qu’un **XLANGMessage** instance et **Exception** comme un **objet**  instance. La méthode rend persistante de l’exception dans le message d’erreur et rend disponibles pour récupération à l’aide du **GetException** (méthode). Aucune valeur de retour.|  
|**GetMessage** [abonné/processeur]|**public XLANGMessage GetMessage(faultMessage, messageName) statique** prend comme paramètres une architecture ESB erreur message reçu à partir d’un abonnement comme un **XLANGMessage** instance et le (**chaîne**) nom du message précédemment ajouté au message d’erreur (dans le Gestionnaire d’exceptions de la forme d’orchestration d’origine). Retourne un **XLANGMessage** instance qui correspond au nom de message et qui contient toutes les les propriétés d’origine contexte, y compris les propriétés promues personnalisées.|  
|**GetMessages** [abonné/processeur]|**public MessageCollection GetMessages(faultMessage) statique** prend comme paramètre unique, un message d’erreur ESB reçu à partir d’un abonnement comme un **XLANGMessage** instance. Retourne un **MessageCollection** instance remplie avec tous les **XLANGMessage** instances précédemment ajoutés au message d’erreur (dans le Gestionnaire d’exceptions de la forme d’orchestration d’origine). Chaque **XLANGMessage** instance contient toutes les les propriétés d’origine contexte, y compris les propriétés promues personnalisées.|  
|**GetException** [abonné/processeur]|**GetException(faultMessage) de System.Exception statique publique** prend comme paramètre unique, un message d’erreur reçu à partir d’un abonnement comme un **XLANGMessage** instance. Retourne le **System.Exception** objet précédemment ajouté au message d’erreur (dans le Gestionnaire d’exceptions de la forme d’orchestration d’origine).|  
|**FaultSeverity** [étendue du Gestionnaire d’Exception et abonné/processeur]|Propriété en lecture/écriture publique du message d’erreur ESB **XLANGMessage** classe qui expose la gravité d’un message d’erreur. Une valeur à partir de la **FaultCodes** énumération : **informations** (0), **avertissement** (1), **erreur** (2), **sévères**(3), ou **critique** (4).|  
|**MessageCollection** [abonné/processeur]|Une collection des messages retournés par la **GetMessages** (méthode). Cette classe dérive **ArrayList** et implémente un énumérateur pour permettre à l’aide de l’itération la **MoveNext** (méthode).|