---
title: "Prise en charge des Types de données LOB dans une base de données Oracle de diffusion en continu | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- streaming, node-value
- streaming
- LOB data
- streaming, node
ms.assetid: a4943cdf-8336-48ac-b592-52ec514e7300
caps.latest.revision: "3"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: f3f052b5051e511179ed0a3b371a619b315a16af
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="streaming-support-for-lob-data-types-in-oracle-database"></a>Prise en charge de diffusion en continu pour les Types de données LOB dans une base de données Oracle
La base de données Oracle prend en charge la diffusion en continu sur les objets volumineux (LOB) les types de données. Le [!INCLUDE[adapteroracle_short](../../includes/adapteroracle-short-md.md)]message prend en charge la diffusion en continu, qui permet de diffuser des LOB données de bout en bout entre un client de carte et de la base de données Oracle. Toutefois, diffusion en continu n'est pas prise en charge de la même manière dans tous les modèles de programmation lorsque vous utilisez l’adaptateur.  
  
 Le suivant montre comment de bout en bout de diffusion en continu de types de données LOB est pris en charge par l’adaptateur sur les modèles de programmation différents.  
  
|Opération|Modèle de canal WCF|Modèle de Service WCF|BizTalk Server|  
|---------------|-----------------------|-----------------------|--------------------|  
|Opération d’insertion de la table ou de vue|Non pris en charge|Non pris en charge|Non pris en charge|  
|Opération Select de la table ou de vue|Pris en charge|Non pris en charge|Pris en charge|  
|Opération de mise à jour de la table ou de vue|Non pris en charge|Non pris en charge|Non pris en charge|  
|Opération de suppression de la table ou de vue|Non pris en charge|Non pris en charge|Non pris en charge|  
|Opération de table ou de vue ReadLOB|Prise en charge ; Toutefois, les opérations ReadLOB apparaissent essentiellement pour prendre en charge la diffusion en continu dans le modèle de service WCF, il est déconseillé pour une utilisation dans le modèle de canal WCF. Utilisez une opération de sélection ou à l’opération SQLEXECUTE à la place.|Pris en charge|L’opération ReadLOB n’est pas prise en charge pour BizTalk Server. Utilisez une opération de sélection à la place.|  
|Opération de table ou de vue UpdateLOB|Pris en charge|Non pris en charge|Pris en charge|  
|Opération SQLEXECUTE|Prise en charge dans la réponse|Non pris en charge|Prise en charge dans la réponse|  
|Opération de procédure et la fonction stockée|Prise en charge dans la réponse|Non pris en charge|Prise en charge dans la réponse|  
|Opération de POLLINGSTMT|Pris en charge|Non pris en charge|Pris en charge|  
  
 Pour plus d’informations sur la diffusion en continu des types de données LOB est prise en charge par l’adaptateur et comment il est pris en charge lorsque vous utilisez différents modèles de programmation avec l’adaptateur, consultez [diffusion en continu des types de données LOB](../../adapters-and-accelerators/adapter-oracle-database/streaming-large-object-data-types-in-oracle-database-adapter.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Vue d’ensemble de l’adaptateur BizTalk pour base de données Oracle](../../adapters-and-accelerators/adapter-oracle-database/overview-of-biztalk-adapter-for-oracle-database.md)