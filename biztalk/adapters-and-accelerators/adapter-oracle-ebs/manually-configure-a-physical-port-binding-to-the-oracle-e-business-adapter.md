---
title: "Configurer manuellement une liaison de port physique à l’adaptateur Oracle E-Business | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 07369428-7b54-4d90-8c63-ba14e67fdbdd
caps.latest.revision: "9"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 24ea54009ba97732cbcf6f248127b078c1c9ed05
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="manually-configure-a-physical-port-binding-to-the-oracle-e-business-adapter"></a>Configurer manuellement une liaison de port physique à l’adaptateur Oracle E-Business
Cette section fournit des informations sur la configuration de la [!INCLUDE[adapteroracleebusinesslong](../../includes/adapteroracleebusinesslong-md.md)] sous la forme d’une liaison WCF personnalisée ou un port WCF-OracleEBS à l’aide de la [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] console d’Administration. Après le déploiement de la carte, vous serez en mesure d’envoyer et recevoir des messages à partir d’Oracle E-Business Suite à l’aide de la [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] console d’Administration. Les étapes de déploiement de l’adaptateur varient en fonction de :  
  
-   La direction de communication entre [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] et [!INCLUDE[adapteroraclebusinessshort](../../includes/adapteroraclebusinessshort-md.md)]. Vous pouvez choisir de configurer un envoi, réception, envoi-réception ou un port d’envoi à la réception. Les choix disponibles sont résumées dans le tableau suivant.  
  
    |Direction du port|Modèle de communication|Direction de communication sélectionnables|  
    |--------------------|---------------------------|-----------------------------------------------|  
    |Send|Unidirectionnel|Toujours envoyer les messages sur ce port.|  
    |Recevoir|Unidirectionnel|Toujours recevoir les messages sur ce port.|  
    |Envoi / réception|Requête-réponse|J’ai sera envoyer une requête et recevoir une réponse.|  
    |Envoi de réception|Sollicitation-réponse|Recevoir une requête et envoyer une réponse.|  
  
     Pour plus d’informations, consultez la [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] aide à [http://go.microsoft.com/fwlink/?LinkID=101130](http://go.microsoft.com/fwlink/?LinkID=101130).  
  
-   Indique si l’adaptateur envoie des messages vers ou reçoit des messages à partir d’Oracle E-Business Suite. Selon que vous souhaitez envoyer ou recevoir des messages, vous créez un envoi ou port de réception, respectivement.  
  
    > [!NOTE]
    >  Vous pouvez également configurer l’envoi ou les ports de réception en important un fichier de configuration de liaison qui est créé par le [!INCLUDE[consumeadapterservshort](../../includes/consumeadapterservshort-md.md)] dans le cadre de la génération de métadonnées. Pour obtenir des instructions sur la configuration des ports à l’aide de ce fichier de liaison, consultez [configurer d’une liaison de Port physique à l’aide d’un fichier de liaison de Port pour Oracle E-Business Suite](../../adapters-and-accelerators/adapter-oracle-ebs/configure-a-physical-port-binding-using-a-port-binding-file-to-oracle-ebs.md).  
  
## <a name="in-this-section"></a>Dans cette section  
  
-   [Configuration d’un Port à l’aide de la WCF-Custom adaptateur et Oracle E-Business Suite](../../adapters-and-accelerators/adapter-oracle-ebs/configure-a-port-using-the-wcf-custom-adapter-and-oracle-e-business-suite.md)  
  
-   [Configuration d’un Port à l’aide de l’adaptateur WCF-OracleEBS](../../adapters-and-accelerators/adapter-oracle-ebs/configure-a-port-using-the-wcf-oracleebs-adapter.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Blocs de construction pour créer des applications d’Oracle E-Business Suite](../../adapters-and-accelerators/adapter-oracle-ebs/building-blocks-to-create-oracle-e-business-suite-applications.md)