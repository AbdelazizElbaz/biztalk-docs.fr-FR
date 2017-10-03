---
title: "Propriétés et schéma de propriété de l’adaptateur file | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- configuring [File adapters], properties
- schemas, File adapters
- File adapters, schemas
- Password property [File adapters]
- ReceivedFileName property [File adapters]
- configuring [File adapters], schemas
- CopyMode property [File adapters]
- AllowCacheOnWrite property [File adapters]
- FileCreationTime property [File adapters]
- UserName property, File adapters
- File adapters, properties
- UserName property
ms.assetid: c5ae5339-67bf-4fde-a721-5b1aa3b9caca
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 37e1c6860b002b41555337a0bf7e8cb931f2c2bf
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="file-adapter-property-schema-and-properties"></a>Propriétés et schéma de propriété de l’adaptateur de fichier
Le tableau suivant répertorie les propriétés du schéma de propriété de l'adaptateur FILE.  
  
 **Namespace :** http://schemas.microsoft.com/BizTalk/2003/file-properties  
  
|Nom|Type| Description|  
|----------|----------|-----------------|  
|**CopyMode**|xs:unsignedInt|Définit le mode de copie à utiliser lors de l'écriture d'un message dans un fichier. Les valeurs valides sont :<br /><br /> **Ajouter (0).** le gestionnaire d'envoi FILE ouvre un fichier s'il existe et ajoute un message à la fin du fichier. Si le fichier n'existe pas, il le crée.<br /><br /> **Créer (1).** si aucun fichier n'existe, le gestionnaire d'envoi FILE en crée un et y enregistre des éléments. si le fichier existe déjà, il signale une erreur et applique la procédure logique commune pour les nouvelles tentatives sur l'adaptateur pour les ports d'envoi. Il s'agit d'un mode de copie par défaut pour le gestionnaire d'envoi FILE.<br /><br /> **Remplacer (2).** le gestionnaire d'envoi FILE ouvre un fichier s'il existe et remplace son contenu. Si le fichier n'existe pas, il le crée.|  
|**AllowCacheOnWrite**|xs:Boolean|Précise si l'adaptateur FILE utilise la mise en cache du système de fichiers lors de l'écriture de messages dans un fichier.|  
|**ReceivedFileName**|xs:string|Définit le nom complet du fichier à partir duquel l'adaptateur FILE lit le message.|  
|**FileCreationTime**|xs:datetime|Définit l'heure à laquelle le fichier a été écrit dans le dossier surveillé par l'adaptateur de réception FILE.|  
|**Nom d’utilisateur**|xs:string|Définit le nom d'utilisateur du compte utilisé lors de la spécification d'autres informations d'identification pour accéder à un partage réseau.|  
|**Mot de passe**|xs:string|Définit le mot de passe du compte utilisé lors de la spécification d'autres informations d'identification pour accéder à un partage réseau.|  
  
## <a name="see-also"></a>Voir aussi  
 [Configuration de l’adaptateur de fichier](../core/configure-the-file-adapter.md)