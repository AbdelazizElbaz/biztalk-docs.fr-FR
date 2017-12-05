---
title: "Propriétés de Configuration de l’adaptateur de fichier | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- File adapters, code sample
- receive locations, adapters
- File adapters, send ports
- File adapters, receive locations
- File adapters, properties
- send ports, adapters
ms.assetid: 53f4fd17-95b9-4861-b433-772b619e90c7
caps.latest.revision: "13"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: fe578337d7137f3c9973ec4d57f195ead94ad908
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="file-adapter-configuration-properties"></a>Propriétés de configuration de l'adaptateur FILE
Le tableau suivant répertorie les propriétés de configuration que vous pouvez définir pour l'emplacement de réception de l'adaptateur FILE :  
  
|Nom de la propriété|Type| Description|Restrictions|Commentaires|  
|-------------------|----------|-----------------|------------------|--------------|  
|RemoveReceivedFileRetryCount|VT_UI4|Indiquer le nombre de tentatives de suppression par l'adaptateur FILE d'un fichier qu'il a lu et envoyé à BizTalk Server.|Les valeurs valides sont comprises entre 0 et 100.|La valeur par défaut est 5.|  
|RemoveReceivedFileMaxInterval|VT_UI4|Indiquer l'intervalle initial en millisecondes pendant lequel l'adaptateur FILE va attendre avant de tenter de supprimer un fichier qu'il a lu et envoyé à BizTalk Server.|Les valeurs valides vont de 1 à 1000.|La valeur par défaut est 10.|  
|FileMask|VT_BSTR|Indiquer le masque des fichiers.|Aucune|La valeur par défaut est *.xml.|  
|BatchSizeInBytes|VT_UI4|Spécifier le nombre total d'octets autorisés pour un lot de fichiers envoyé à la base de données MessageBox de BizTalk.|Les valeurs valides sont comprises 1024 104857600 octets autorisée.|La valeur par défaut est 102 400.|  
|PollingInterval|VT_UI4|Indiquer l'intervalle, en millisecondes, selon lequel l'adaptateur FILE va interroger l'emplacement spécifié à la recherche de nouveaux fichiers.|Les valeurs valides sont de 1000 à 3600000.|Définissez la valeur sur 1 pour désactiver l'interrogation.|  
|BatchSize|VT_UI4|Indiquez le nombre maximal de messages à soumettre en un lot.|Les valeurs valides vont de 1 à 256.|La valeur par défaut est 20.|  
|FileNetFailRetryInt|VT_UI4|Indiquer l'intervalle (en minutes) devant séparer chaque tentative d'accès à l'emplacement de réception sur le partage réseau en cas d'indisponibilité temporaire.|Les valeurs valides sont comprises entre 0 4 294 967 295.|La valeur par défaut est 5.|  
|RemoveReceivedFileDelay|VT_UI4|Indiquer l'intervalle initial en millisecondes pendant lequel l'adaptateur FILE va attendre avant de tenter de supprimer un fichier qu'il a lu et envoyé à BizTalk Server.|Cet intervalle double après chaque nouvelle tentative jusqu'à la valeur d'intervalle maximal spécifiée.<br /><br /> Les valeurs valides vont de 1 à 1000.|La valeur par défaut est 10.|  
|RenameReceivedFiles|VT_BOOL|Indiquer s'il faut renommer des fichiers avant de les extraire pour traitement.|Les valeurs valides sont :<br /><br /> -à -1 (true)<br />-0 (faux)|La valeur par défaut est 0 :|  
|FileNetFailRetryCount|VT_UI4|Indiquer le nombre de tentatives d'accès à l'emplacement de réception sur le partage réseau en cas d'indisponibilité temporaire.|Les valeurs valides sont comprises entre 0 4 294 967 295.|La valeur par défaut est 5.|  
  
 Le code suivant illustre le format de la chaîne XML que vous devez utiliser pour définir les propriétés :  
  
```  
<CustomProps>  
<RemoveReceivedFileRetryCount vt="19">5</RemoveReceivedFileRetryCount>  
<RemoveReceivedFileMaxInterval vt="19">300000</RemoveReceivedFileMaxInterval>  
<FileMask vt="8">*.xml</FileMask>  
<BatchSizeInBytes vt="19">102400</BatchSizeInBytes>  
<PollingInterval vt="19">60000</PollingInterval>  
<BatchSize vt="19">20</BatchSize>  
<FileNetFailRetryInt vt="19">5</FileNetFailRetryInt>  
<RemoveReceivedFileDelay vt="19">10</RemoveReceivedFileDelay>  
<RenameReceivedFiles vt="11">0</RenameReceivedFiles>  
<FileNetFailRetryCount vt="19">5</FileNetFailRetryCount>  
</CustomProps>  
```  
  
 Ce tableau répertorie les propriétés de configuration que vous pouvez définir pour le port d'envoi de l'adaptateur FILE.  
  
|Nom de la propriété|Type| Description|Restrictions|Commentaires|  
|-------------------|----------|-----------------|------------------|--------------|  
|Utilisateur|VT_BSTR|Spécifiez les autres informations d’identification lorsque l’instance d’hôte de l’adaptateur File ne dispose pas des droits nécessaires pour un partage réseau.|Aucune|Spécifiez le nom d’utilisateur au format \<domaine\>\username.|  
|UseTempFileOnWrite|VT_BOOL|Indique qu'il faut utiliser un fichier temporaire lors de l'écriture dans le dossier cible. Une fois l'écriture terminée, le fichier est renommé en fonction de la valeur spécifiée pour la propriété FileName.|Cette propriété peut uniquement être définie sur -1 (true) si la valeur de la propriété CopyMode est égale à 2 (Créer).<br /><br /> Les valeurs valides sont :<br /><br /> -à -1 (true)<br />-0 (faux)|La valeur par défaut est 0 (false).|  
|CopyMode|VT_UI4|Définir le mode de copie à utiliser lors de l'écriture d'un message dans un fichier.|Les valeurs valides sont :<br /><br /> -0 (ajout)<br />-1 (par écrasement)<br />-2 (créer)|La valeur par défaut est 2 (Créer).|  
|FileName|VT_BSTR|Indiquer le nom du fichier dans lequel le gestionnaire d'envoi du fichier écrit le message.|Pour plus d’informations sur les restrictions sur cette propriété, consultez [Restrictions sur le masque de fichier et les propriétés du nom de fichier](http://msdn.microsoft.com/library/d8f5afd0-a61f-4c9b-8a57-4792e3054769).|La valeur par défaut est %MessageID%.xml.|  
|AllowCacheOnWrite|VT_BOOL|Spécifie si la mise en cache du système de fichiers doit être appliquée lors de l'écriture d'un message dans un fichier.|Les valeurs valides sont :<br /><br /> -0 (ne pas utiliser la mise en cache)<br />-les -1 (mise en cache)|La valeur par défaut est 0 (pas de mise en cache).|  
|Mot de passe|VT_NULL|Spécifie le mot de passe utilisé avec la propriété Nom d'utilisateur lorsque l'instance d'hôte de l'adaptateur FILE ne dispose pas des droits d'accès au partage réseau.|Cette valeur est toujours définie sur Null lors de l'exportation d'un fichier de liaison. Ce champ doit être complété manuellement avec le mot de passe avant l'importation du fichier de liaison dans la configuration BizTalk Server cible.|Aucune|  
  
 Le code suivant illustre le format de la chaîne XML que vous devez utiliser pour définir les propriétés :  
  
```  
<CustomProps>  
<Username vt="8">Domainname\User</Username>  
<UseTempFileOnWrite vt="11">-1</UseTempFileOnWrite>  
<CopyMode vt="19">1</CopyMode>  
<FileName vt="8">%MessageID%.xml</FileName>  
<AllowCacheOnWrite vt="11">-1</AllowCacheOnWrite>  
<Password vt="1" />  
</CustomProps>  
```