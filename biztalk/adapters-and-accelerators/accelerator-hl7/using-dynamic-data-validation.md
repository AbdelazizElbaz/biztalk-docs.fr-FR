---
title: "Utilisation de la Validation de données dynamiques | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- dynamic data validation
- validating, dynamic data
ms.assetid: 8dac7f74-92a7-447c-97bf-b1f3ce39b614
caps.latest.revision: "5"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 3387117648329828c9276545eafddca6872c4aa2
ms.sourcegitcommit: 3fc338e52d5dbca2c3ea1685a2faafc7582fe23a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/01/2017
---
# <a name="using-dynamic-data-validation"></a>Utilisation de la Validation de données dynamiques
La validation de contenu du message par rapport à des données dynamiques, qui inclut la validation du format de message et le contenu du message est une partie importante de la validation dynamique des données. Un schéma de document, qui [!INCLUDE[btsCoName](../../includes/btsconame-md.md)]BizTalk Server implémente dans un fichier XSD, qui définit et valide les formats de message. Contenu du message, définissent des règles d’entreprise qui [!INCLUDE[btsBizTalkServerNoVersion](../../includes/btsbiztalkservernoversion-md.md)] valide via des stratégies du moteur de règles d’entreprise. Validation du contenu peut inclure que les données dans l’instance de message correspond aux données qui peuvent changer avec une fréquence relative de confirmation. [!INCLUDE[btsCoName](../../includes/btsconame-md.md)][!INCLUDE[HL7_CurrentVersion_FirstRef](../../includes/hl7-currentversion-firstref-md.md)]implémente ce type de validation de manière dynamique, afin que vous pouvez mettre à jour ces données dans un environnement de production sans avoir à recompiler le code ou l’arrêt des services.  
  
## <a name="validate-and-expose-data"></a>Valider et exposer des données  
 Il existe deux étapes pour effectuer la Validation dynamique des données (DDV) :  
  
-   Exposer les données.  
  
-   Appliquer des règles de validation à l’aide de ces données.  
  
 DDV fournit la prise en charge suivant pour le stockage, l’exposition et la mise en cache des données dynamiques :  
  
-   Le moteur de règles métier ou de la classe de Message effectue la validation.  
  
-   Le moteur de règles d’entreprise expose des données via le vocabulaire de colonne de table de base de données. Le moteur de règles d’entreprise valide cette dynamique des données contre les messages en implémentant un ensemble de règles qui s’exécute à partir d’un pipeline ou une orchestration.  
  
-   Interfaces SQL existantes, telles que SQL Enterprise Manager et l’Analyseur de requêtes, exposez les données dynamiques est passives au moment du design.  
  
-   La définition de vocabulaire de colonne de table moteur des règles d’entreprise de base de données expose des données dynamiques au moment de l’exécution.  
  
-   Le moteur de règles d’entreprise expose les données d’instance de message en cours d’exécution.  
  
-   Une définition de vocabulaire de document XML de moteur de règles métier expose les données d’instance de message au moment du design.  
  
-   Vous pouvez composer des règles au moment du design dans l’interface utilisateur de l’éditeur des règles d’entreprise ou directement dans les règles BRL (Business Language) XML dans un éditeur de texte.  
  
 Pour plus d’informations sur les règles d’entreprise et le moteur de règles d’entreprise, consultez « Développement avec des règles d’entreprise » dans l’aide de BizTalk Server.  
  
## <a name="extending-ddv"></a>Extension DDV  
 Si vous modifiez la validation de champ croisé basée sur HL7 ou validation de type de données, vous devez noter deux choses :  
  
-   Si vous modifiez une règle existante, vous n’avez pas besoin de redéployer.  
  
-   Si vous créez ou supprimez une règle qui a une incidence sur un composant de pipeline, vous devez recompiler.  
  
## <a name="see-also"></a>Voir aussi  
 [Guide de programmation](../../adapters-and-accelerators/accelerator-hl7/programming-guide1.md)   
 [Didacticiel sur l’enrichissement des messages](../../adapters-and-accelerators/accelerator-hl7/message-enrichment-tutorial.md)