---
title: "Exceptions et gestion des erreurs avec l’adaptateur Siebel | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- error handling, troubleshooting
- exceptions, troubleshooting
- troubleshooting, exceptions and error handling
ms.assetid: d46e908f-0715-43e2-879b-f5d0beb9bc64
caps.latest.revision: "5"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 743e2a0f03e35282c24a506ff37e9d774f0b7505
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="exceptions-and-error-handling-with-the-siebel-adapter"></a>Exceptions et gestion des erreurs avec l’adaptateur Siebel
## <a name="exception-list"></a>Liste des exceptions
Les exceptions levées par le [!INCLUDE[adaptersiebel](../../includes/adaptersiebel-md.md)]. Il peuvent contenir :  
  
-   Une exception interne qui est une exception levée système par le .NET Framework  
  
-   Une exception levée LOB par la bibliothèque cliente LOB.  
  
 Pour plus d’informations sur l’exception interne, reportez-vous à la documentation de .NET Framework ou Siebel respectif. L’exception contient également un message d’erreur détaillé qui vous aide à résoudre le problème. Notez que la liste des exceptions mentionnées ici n’est pas complet.  
  
|Exception|Erreur de Cause possible/Description|  
|---------------|---------------------------------------|  
|ConnectionException|L’adaptateur lève cette exception s’il est impossible d’établir une connexion ou fermez une connexion existante à un système Siebel.|  
|CredentialsException|L’adaptateur lève cette exception si le client de l’adaptateur ne spécifie pas un nom d’utilisateur ou le mot de passe pour se connecter à un système Siebel.|  
|MetadataException|L’adaptateur lève cette exception en cas d’échec récupérer des métadonnées pour les artefacts de Siebel.|  
|XmlReaderParsingException|L’adaptateur lève cette exception si les informations d’entrée fournies par les clients de la carte pour appeler une opération dans le système Siebel, est incomplète ou incorrecte.|  
|XmlReaderGenerationException|L’adaptateur lève cette exception s’il est impossible de générer la sortie d’une opération exécutée dans un système Siebel.|  
|TargetSystemException|L’adaptateur lève cette exception si l’API COM Siebel, que l’adaptateur utilise pour interagir avec le système Siebel, lève une exception. L’exception interne contient l’exception levée par l’API de COM Siebel.|  
  
## <a name="see-also"></a>Voir aussi  
 [Comprendre l’adaptateur BizTalk pour Siebel eBusiness Applications](../../adapters-and-accelerators/adapter-siebel/understand-biztalk-adapter-for-siebel-ebusiness-applications.md)   
[Dépanner l’adaptateur Siebel](../../adapters-and-accelerators/adapter-siebel/troubleshoot-the-siebel-adapter.md)