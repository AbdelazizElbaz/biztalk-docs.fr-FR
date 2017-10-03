---
title: "Résolution des problèmes du 2 | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- wildcard characters, in send port properties
- troubleshooting adapter
- Get.xml
- send ports, using wildcards in properties
ms.assetid: e9e0408f-5a12-4f05-83a6-37dc519ae4c5
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 991278813d2183795239d1a75c08e474b2f8159a
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="troubleshooting-the-adapter"></a>Dépannage de l’adaptateur
Cette rubrique contient des informations qui vous aident à identifier et résoudre les problèmes que vous pouvez rencontrer dans le cadre de l'utilisation de l'adaptateur Microsoft BizTalk pour PeopleSoft Enterprise.  
  
## <a name="cannot-use-wildcard-characters-in-send-port-properties"></a>Impossible d'utiliser des caractères génériques dans les propriétés de port d'envoi  
 L'adaptateur BizTalk pour PeopleSoft Enterprise ne prend pas en charge l'utilisation des caractères génériques dans les champs de propriétés de port d'envoi suivants :  
  
-   Utilisateur  
  
-   Chemin d'accès au serveur d'applications  
  
-   Java_Home  
  
-   Fichiers JAR People  
  
## <a name="getxml-data-assigns-0001-01-01-value-for-null-dates"></a>Les données Get.xml affectent la valeur 0001-01-01 aux dates Null  
 Get.xml affecte de manière incorrecte la valeur 0001-01-01 aux dates Null. Vous devez utiliser l'outil Mappeur BizTalk pour remplacer la valeur 0001-01-01 par une valeur Null.  
  
## <a name="creating-and-updating-properties-with-collections-fails"></a>Échec de la création et de la mise à jour des propriétés avec des collections  
 Lors d'une utilisation avec PeopleSoft version 8.17.02, l'adaptateur peut lire les données du serveur PeopleSoft correctement. Cependant, la création et la mise à jour échouent pour les propriétés avec des collections Il s'agit d'un problème PeopleSoft connu qui sera peut-être résolu dans une version ultérieure de PeopleSoft.  
  
## <a name="see-also"></a>Voir aussi  
 [Résolution des problèmes de PeopleSoft](../core/troubleshooting-peoplesoft.md)