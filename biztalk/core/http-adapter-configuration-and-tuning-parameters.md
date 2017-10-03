---
title: "Paramètres de réglage et de Configuration de l’adaptateur HTTP | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- HTTP adapters, parameters
- configuring [HTTP adapters], parameters
- HTTP adapters, tuning
- RequestQueueSize key [HTTP adapters]
- HttpReceiveThreadsPerCpu key [HTTP adapters]
- HttpOutTimeoutInterval key [HTTP adapters]
- HttpOutInflightSize key [HTTP adapters]
- configuring [HTTP adapters], tuning
- DisableChunkEncoding key [HTTP adapters]
- HttpOutCompleteSize key [HTTP adapters]
ms.assetid: c8989a88-722a-40b5-94cf-4b6840add02e
caps.latest.revision: "20"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 5db4f4dc4403ddfbf677ac2729c00e2b1976db61
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="http-adapter-configuration-and-tuning-parameters"></a>Paramètres de réglage et de Configuration de l’adaptateur HTTP
Plusieurs paramètres de configuration et de personnalisation sont accessibles pour l'adaptateur HTTP à travers les entrées de clé de Registre et les modifications apportées au fichier BTSNTSvc.exe.config situé dans le répertoire d'installation BizTalk Server racine.  
  
 **Paramètres du Registre qui affectent les performances de l’adaptateur HTTP**  
  
 Le tableau suivant décrit les paramètres du Registre qui affectent les performances de l'adaptateur HTTP. Remarquez que, par défaut, aucune clé de l'adaptateur HTTP n'existe dans le Registre. L'adaptateur HTTP utilise donc les paramètres par défaut. Si vous devez modifier les paramètres par défaut dans le Registre, vous devez créer les clés de Registre suivantes dans les emplacements suivants :  
  
-   **DisableChunkEncoding**, **RequestQueueSize**, et **HttpReceiveThreadsPerCpu** doit être défini dans **HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\ BTSSvc.3.0\HttpReceive**.  
  
-   **HttpOutTimeoutInterval**, **HttpOutInflightSize**, et **HttpOutCompleteSize** doit être défini dans **HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\ BTSSvc {GUID}** où **GUID** est l’ID de l’hôte pour le Gestionnaire d’envoi HTTP.  
  
|Nom de clé|Type|Valeur par défaut|Explication|  
|--------------|----------|-------------|-----------------|  
|**DisableChunkEncoding**|DWORD|0|Détermine si l'adaptateur de réception HTTP utilise le codage segmenté lors du renvoi de réponses au client.<br /><br /> Définissez une valeur différente de zéro pour désactiver le codage segmenté pour les réponses de l'adaptateur de réception HTTP.<br /><br /> **Valeur minimale :** 0<br /><br /> **Valeur maximale :** toute valeur différente de zéro|  
|**RequestQueueSize**|DWORD|256|Définit le nombre de requêtes simultanées que l'adaptateur de réception HTTP traite à la fois.<br /><br /> **Valeur minimale :** 10<br /><br /> **Valeur maximale :** 2048|  
|**HttpReceiveThreadsPerCpu**|DWORD|2|Définit le nombre de threads par UC qui est alloué à l'adaptateur de réception HTTP.<br /><br /> **Valeur minimale :** 1<br /><br /> **Valeur maximale :** 10|  
|**HttpOutTimeoutInterval**|DWORD|2000|Définit l'intervalle en secondes durant lequel l'adaptateur d'envoi HTTP attend avant expiration.<br /><br /> **Valeur minimale :** 500<br /><br /> **Valeur maximale :** 10000000|  
|**HttpOutInflightSize**|DWORD|100|Il s'agit du nombre maximal de requêtes HTTP simultanées que l'instance de l'adaptateur d'envoi HTTP BizTalk Server traitera.<br /><br /> La valeur recommandée pour la latence est entre 3 à 5 fois celle de la **maxconnection** entrée de fichier de configuration décrite ci-dessous.<br /><br /> **Valeur minimale :** 1<br /><br /> **Valeur maximale :** 1024|  
|**HttpOutCompleteSize**|DWORD|5|Contrôle la taille du lot de messages renvoyé par l'adaptateur d'envoi HTTP. Si la mémoire tampon n’est pas plein et que des réponses en attente l’adaptateur attend 1 seconde avant de valider le lot.  Pour les scénarios de faible latence cela doit être définie à 1 afin de permettre l’adaptateur envoyer des messages de réponse immédiatement dans la boîte de message pour traitement.<br /><br /> **Valeur minimale :** 1<br /><br /> **Valeur maximale :** 1024|  
  
 **Entrée de fichier de configuration pour indiquer le nombre de connexions simultanées effectuées par l’adaptateur d’envoi HTTP à un serveur de Destination particulier**  
  
 Vous pouvez configurer le nombre de connexions simultanées ouvertes par l'adaptateur HTTP pour un serveur de destination particulier en créant une entrée dans le fichier BTSNTSvc.exe.config situé dans le répertoire d'installation BizTalk Server racine.  
  
> [!NOTE]
>  Cette propriété est appliquée aux adaptateurs HTTP et SOAP s'ils envoient des messages au même serveur HTTP de destination. La valeur par défaut de la propriété « maxconnexion » est 2. La valeur maximale qui peut être définie pour la propriété « maxconnexion » pour tous les URI est 20.  
  
 Voici un exemple de configuration de la propriété du nombre maximal de connexions :  
  
```  
<configuration>  
  <system.net>  
    <connectionManagement>  
      <add address = "http://www.contoso.com" maxconnection = "20" />  
      <add address = "http://www.northwind.com" maxconnection = "2" />  
    </connectionManagement>  
  </system.net>  
</configuration>  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Configuration de l’adaptateur HTTP](../core/configuring-the-http-adapter.md)