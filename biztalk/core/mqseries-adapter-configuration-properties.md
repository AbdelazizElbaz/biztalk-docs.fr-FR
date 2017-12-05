---
title: "Propriétés de Configuration de l’adaptateur MQSeries | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- MQSeries adapters, code sample
- receive locations, adapters
- MQSeries adapters, send ports
- MQSeries adapters, properties
- MQSeries adapters, receive location
- send ports, adapters
ms.assetid: 7517a8bf-aa65-4af9-aed0-7c74fb480328
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 6f7c24f15c916970926143cec4cb6bb33401efeb
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="mqseries-adapter-configuration-properties"></a>Propriétés de configuration de l'adaptateur MQSeries
Le tableau suivant répertorie les propriétés de configuration que vous pouvez définir pour l'emplacement de réception de l'adaptateur MQSeries :  
  
|Nom de la propriété|Type| Description|Restrictions|Commentaires|  
|-------------------|----------|-----------------|------------------|--------------|  
|uri|VT_BSTR|Indiquer le chemin d'accès complet à l'emplacement contrôlé par l'emplacement de réception.|L'URI d'un port d'envoi ou d'un emplacement de réception ne peut pas comporter plus de 256 caractères.|Aucune|  
|queueDetails|VT_BSTR|Spécifier les informations relatives à la file d'attente MQSeries source, notamment le serveur, le gestionnaire de file d'attente et la file d'attente.|-Aucun|Cette propriété est précédée de MQS:// pour créer la propriété de URI.|  
|transactionSupported|VT_BSTR|Indiquer si l'adaptateur MQSeries commence une transaction Microsoft DTC (Distributed Transaction Coordinator) entre BizTalk Server et MQSeries Server.|Les valeurs valides sont :<br /><br /> -Oui<br />-Aucun|Lorsque la valeur non, il n’existe aucune garantie de remise des messages.<br /><br /> La valeur par défaut est yes.|  
|suspendAsNonResumable|VT_BSTR|Indiquer si les messages suspendus peuvent être repris ou non.|Les valeurs valides sont :<br /><br /> -Oui<br />-Aucun|La valeur par défaut est no.|  
|dataOffsetForHeaders|VT_BSTR|L'adaptateur utilise les valeurs des en-têtes MQSeries (structures MQXQH, MQIIH et MQCIH) pour renseigner les propriétés de contexte BizTalk Server. Par défaut, il supprime ces propriétés MQSeries du corps du message.|Les valeurs valides sont :<br /><br /> -Oui<br />-Aucun|Définissez cette propriété sur non pour conserver les propriétés dans le corps du message.<br /><br /> La valeur par défaut est yes.|  
|pollingInterval|VT_BSTR|Définir la fréquence utilisée par le composant de réception pour interroger la file d'attente MQSeries.|Les valeurs valides vont de 1 à 10000.|pollingInterval fonctionne en conjonction avec l'intervalle d'attente de trois secondes intégré à l'adaptateur. Si la valeur de pollingInterval est définie sur une valeur inférieure à trois (3) secondes, l'intervalle d'attente est ajusté en conséquence.<br /><br /> La valeur par défaut est 3.|  
|pollingUnit|VT_BSTR|Indiquer l'unité de temps à utiliser pour la fréquence d'interrogation.|Les valeurs valides sont :<br /><br /> -heures<br />-minutes<br />-secondes|La valeur par défaut est secondes.|  
|maximumBatchSize|VT_BSTR|Définir la taille maximale d'un lot de messages, en kilo-octets (Ko).|Les valeurs valides sont comprises entre 1 et 10485760.|La valeur par défaut est 100.|  
|maximumNumberOfMessages|VT_BSTR|Définir le nombre maximal de messages dans un lot.|Les valeurs valides vont de 1 à 100000|La valeur par défaut est 100.|  
|threadCount|VT_BSTR|Spécifier le nombre de threads utilisés par emplacement de réception.|Les valeurs valides vont de 1 à 64.|La valeur par défaut est 2.|  
|fragmentationSize|VT_BSTR|Définir la taille des fragments, en kilo-octets (Ko), des messages envoyés entre MQSAgent et l'adaptateur.|Les valeurs valides vont de 1 à 1 048 576.|La valeur par défaut est 500.|  
|characterSet|VT_BSTR|Spécifier le jeu de caractères et si MQSeries doit les convertir avant d'envoyer le message à l'emplacement de réception :|Les valeurs valides sont :<br /><br /> -none. Pas de conversion.<br />-UCS-2 et UTF-16. Conversion en ces jeux de caractères. MQSeries ne fait pas de distinction entre eux.<br />UTF-8. Conversion en jeu de caractères UTF-8.|La valeur par défaut est Aucune.|  
|errorThreshold|VT_BSTR|Déterminer le nombre maximal d'erreurs à consigner. L'adaptateur continue de fonctionner et, s'il récupère, consigne l'événement dans le journal des événements.|Les valeurs valides vont de 1 à 1000.|La valeur par défaut est 10.|  
|segmentation|VT_BSTR|Indiquer si MQSeries assemble les messages segmentés ou les récupère en l'état.|Les valeurs valides sont :<br /><br /> -Aucun<br />-terminé|Spécifiez Aucune pour lire les messages de la file d'attente MQSeries sans activer la segmentation.<br /><br /> Utilisez Complète pour que les messages segmentés soient assemblés avant d'être transmis à l'adaptateur.<br /><br /> La valeur par défaut est Aucune.|  
|triées|VT_BSTR|Définir si MQSeries doit conserver l'ordre des messages au fur et à mesure de leur réception depuis la file d'attente MQSeries.|Les valeurs valides sont :<br /><br /> -Aucun<br />-noStop<br />-yesStop<br />-yesSuspend|Sélectionnez non pour ne pas tenir compte de l'ordre des messages.<br /><br /> Sélectionnez noStop pour ne pas tenir compte de l'ordre des messages et pour désactiver l'emplacement de réception en cas d'erreur.<br /><br /> Sélectionnez yesStop pour activer le classement. Cette option permet de mettre fin à la transaction et de désactiver l'emplacement de réception en cas d'erreur.<br /><br /> Sélectionnez yesSuspend pour activer le classement. Cette option place le message dans la file d'attente des messages interrompus en cas d'erreur. Cette valeur ne permet pas de conserver l'ordre en cas d'erreur, mais permet à l'emplacement de réception de continuer à recevoir des messages.<br /><br /> La valeur par défaut est no.|  
  
 Le code suivant présente le format de la chaîne que vous devez utiliser pour définir les propriétés :  
  
```  
<CustomProps><AdapterConfig vt="8"><Config xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:xsd="http://www.w3.org/2001/XMLSchema"><uri>MQS://TESTMQServer/DQM1/RQ0</uri><queueDetails>TESTMQServer/DQM1/RQ0</queueDetails><transactionSupported>yes</transactionSupported><suspendAsNonResumable>no</suspendAsNonResumable><dataOffsetForHeaders>yes</dataOffsetForHeaders><pollingInterval>1</pollingInterval><pollingUnit>seconds</pollingUnit><maximumBatchSize>100</maximumBatchSize><maximumNumberOfMessages>100</maximumNumberOfMessages><threadCount>2</threadCount><fragmentationSize>500</fragmentationSize><characterSet>none</characterSet><errorThreshold>10</errorThreshold><segmentation>none</segmentation><ordered>no</ordered></Config></AdapterConfig></CustomProps>  
```  
  
 Le tableau suivant répertorie les propriétés de configuration que vous pouvez définir pour le port d'envoi d'un adaptateur MQSeries.  
  
|Nom de la propriété|Type| Description|Restrictions|Commentaires|  
|-------------------|----------|-----------------|------------------|--------------|  
|uri|VT_BSTR|Indiquer le chemin d'accès complet de l'emplacement de réception des données.|L'URI d'un port d'envoi ou d'un emplacement de réception ne peut pas comporter plus de 256 caractères.|Aucune|  
|queueDetails|VT_BSTR|Spécifier les informations relatives à la file d'attente MQSeries cible, notamment le serveur, le gestionnaire de file d'attente et la file d'attente.|L'URI d'un port d'envoi ou d'un emplacement de réception ne peut pas comporter plus de 256 caractères.|Cette propriété est précédée de MQS:// pour créer la propriété de URI.|  
|transactionSupported|VT_BSTR|Indiquer si l'adaptateur MQSeries commence une transaction Microsoft DTC (Distributed Transaction Coordinator) entre BizTalk Server et MQSeries Server.|Les valeurs valides sont :<br /><br /> -Oui<br />-Aucun|Lorsque la valeur non, il n’existe aucune garantie de remise des messages.<br /><br /> La valeur par défaut est yes.|  
|dataConversion|VT_BSTR|Spécifier si le message doit être converti en page de code ANSI du serveur MQSeries pour Windows.|Les valeurs valides sont :<br /><br /> -Oui<br />-Aucun|La valeur par défaut est no.|  
|segmentationAllowed|VT_BSTR|Spécifier si la segmentation du gestionnaire de file d'attente MQSeries doit être utilisée si un message individuel dépasse la longueur maximale autorisée pour les messages de file d'attente MQSeries.|Valeur valide sont :<br /><br /> -Oui<br />-Aucun|La valeur par défaut est no.|  
|fragmentationSize|VT_BSTR|Définir la taille des fragments, en kilo-octets (Ko), des messages envoyés entre l'adaptateur et MQSAgent.|Les valeurs valides vont de 1 à 1 048 576.|La valeur par défaut est 500.|  
|triées|VT_BSTR|Définir si MQSeries doit conserver l'ordre des messages au fur et à mesure de leur envoi vers la file d'attente MQSeries.|Les valeurs valides sont :<br /><br /> -Oui<br />-Aucun|La valeur par défaut est no.|  
  
 Le code suivant présente le format de la chaîne que vous devez utiliser pour définir les propriétés :  
  
```  
<CustomProps><AdapterConfig vt="8"><Config xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:xsd="http://www.w3.org/2001/XMLSchema"><uri>MQS://TESTMQServer/DQM1(QM1)/SQ0</uri><queueDetails>TESTMQServer/DQM1(QM1)/SQ0</queueDetails><transactionSupported>yes</transactionSupported><dataConversion>no</dataConversion><segmentationAllowed>no</segmentationAllowed><fragmentationSize>500</fragmentationSize><ordered>no</ordered></Config></AdapterConfig></CustomProps>  
```  
  
> [!NOTE]
>  Lorsque vous spécifiez les données de configuration TransportTypeData pour un adaptateur qui est construit à l’aide de l’infrastructure d’adaptateurs, les paires nom/valeur utilisées doivent toutes être stockées dans le \<AdapterConfig\> élément. Étant donné que le \<AdapterConfig\> élément spécifie le VT_BSTR (vt = « 8 ») type de données, puis le \< \> caractères dans les données doivent être échappés.