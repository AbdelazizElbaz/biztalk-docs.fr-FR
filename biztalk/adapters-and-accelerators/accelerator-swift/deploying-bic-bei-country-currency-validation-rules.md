---
title: "Déploiement de règles de Validation de la devise-pays-BEI-BIC | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 2e96d416-d5eb-4597-a691-c7dbee33c7d6
caps.latest.revision: "4"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 65f1786b37194db25f0e38db7491538857f3406b
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="deploying-bicbeicountrycurrency-validation-rules"></a>Déploiement de règles de Validation de BIC/BEI/pays/devise
**Pour déployer des règles de Validation de BIC/BEI/pays/devise :**  
  
1.  Le jeu suivant de stratégies, % %Program files%\Microsoft BizTalk Accelerator pour les stratégies de Messages\Base SWIFT\SDK\MX, qui sont générique et non spécifique aux messages, devoir être publiées et déployés séparément à l’aide de l’Assistant Déploiement moteur de règles d’entreprise.  
  
    -   MX_BIC_Master_Policy.Xml  
  
    -   MX_BIC_Validation_Policy.Xml  
  
    -   MX_BEI_Validation_Policy.Xml  
  
    -   MX_DBConnection_Master_Policy.Xml  
  
    -   MX_BICPlusIBAN_Validation_Policy.Xml  
  
    -   MX_SEPA_Validation_Policy.Xml  
  
2.  Avant de déployer ces stratégies, MX_DBConnection_Master_Policy.xml et MX_BIC_Master_Policy.xml doivent avoir le nom du serveur de base de données et le nom de la base de données où les valeurs de devise/pays ont été stockées.  
  
3.  Une fois les stratégies maîtres ont été modifiés, publication, toutes les stratégies à l’aide de l’Assistant Déploiement moteur de règles d’entreprise. Utilisez l’option suivante : importer le fichier de stratégie/le vocabulaire vers la base de données.  
  
4.  Cliquez sur Programmes, cliquez sur le serveur BizTalk \<version >, sur l’éditeur des règles d’entreprise et déployez-le sur les six publiés des stratégies.