---
title: "Comprendre le système métier avec WCF LOB Adapter SDK | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a0f97846-5ef2-4530-853a-fba5469156f7
caps.latest.revision: "10"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: d777022312c8511608519d155626c948da3efdb1
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="understand-the-lob-system-with-the-wcf-lob-adapter-sdk"></a>Comprendre le système métier avec le SDK de l’adaptateur WCF LOB
Avant de développer votre adaptateur à l’aide de la [!INCLUDE[afproductnameshort](../../includes/afproductnameshort-md.md)], vous devez disposer d’une connaissance approfondie du système cible line-of-business. Si vous ne comprenez pas les fonctionnalités fournies par le système métier-, comment il est exposé et le différents niveaux de prise en charge fournie pour la sécurité, les transactions et les autres fonctionnalités, votre adaptateur peut ne pas fournit les fonctionnalités requises par l’adaptateur consommateurs. Cette section décrit les zones que vous devez comprendre pour concevoir efficacement votre adaptateur.  
  
## <a name="the-path-to-understanding"></a>Le chemin d’accès à la présentation  
 L’objectif d’un adaptateur est d’exposer des données et les opérations à partir d’un système métier-de manière cohérente et accessible conformément aux règles imposée par la spécification de l’adaptateur et/ou les API d’adaptateur. Pour connaître les opérations et les données d’exposer, vous devez comprendre ce que fait le système et comment il expose ses données et les opérations. En particulier, vous devez considérer les problèmes de conception suivants :  
  
-   **Cycle de vie de connexion.** Comment les connexions sont ouverts et fermées ? Comment sont gérées de connexions ouvertes ? Existe-t-il des conditions requises particulières pour réutiliser une connexion ? Pour plus d’informations sur les connexions, consultez `Microsoft.ServiceModel.Channels.Common.IConnection`.  
  
-   **Les métadonnées d’opération et le type exposées par le système.** Le système métier-prend en charge recherche de l’opération et de parcourir et d’un accès facile aux métadonnées, ou vous devez développer du code de prise en charge pour fournir cette fonctionnalité ? Par exemple, dans SQL Server les opérations sont des objets tels que procédures stockées. Métadonnées de type sur les colonnes, tables et autres objets sont faciles à récupérer. Systèmes line-of-business peuvent être plus difficiles à utiliser.  
  
-   **Comment les opérations et les données sont exposées par le système.** Comment l’API est exposée ? Est la prise en charge de l’API de blocage (synchrone) et non bloquant les appels (asynchrones) ? Les rappels sont pris en charge ? Est l’interface au niveau du protocole ou d’API ?  
  
-   **Prise en charge de sécurité, les transactions et la messagerie fiable.** Si l’API prend en charge ces fonctionnalités, cela signifie probablement que souhaitez les exposer au consommateur de l’adaptateur. Par exemple, SQL Server a la sécurité et transaction prend en charge bien que la messagerie fiable n’est pas pratique (mais serait avec MSMQ ou un autre système de file d’attente).  
  
-   **Les scénarios de fonctionnalité et d’utilisation sont importantes ?** Ne pas limiter votre compréhension purement technique ; Discutez et capturer les besoins de l’entreprise avec les utilisateurs expérimentés. Existe-t-il des contraintes uniques imposées sur certaines opérations ? Existe-t-il des opérations qui sont obscures encore utiles ? Certaines fonctionnalités sont rarement utilisée ?  
  
 Pour découvrir ces informations, consultez l’utilisateur et la documentation technique pour le système métier-cible. Si la documentation est incomplet ou manquant, vous pouvez également être en mesure d’en savoir plus sur les aspects techniques du système en recherchant des forums de support technique en ligne, les groupes de discussion en ligne, les blogs ou en examinant les fichiers d’installation pour les détails d’implémentation. Si vous avez accès aux fichiers de code ou aux développeurs de line-of-business, vous serez peut-être en mesure de découvrir les informations nécessaires, y compris la sémantique de la connexion, prise en charge pour la sécurité et comment les opérations sont recherchées et appelées.  
  
## <a name="see-also"></a>Voir aussi  
 [Planifier et concevoir votre adaptateur à l’aide de WCF LOB Adapter SDK](../../adapters-and-accelerators/wcf-lob-adapter-sdk/plan-and-design-your-adapter-using-the-wcf-lob-adapter-sdk.md)   
 [Prise en main l’avec WCF LOB Adapter SDK](../../adapters-and-accelerators/wcf-lob-adapter-sdk/get-started-with-the-with-the-wcf-lob-adapter-sdk.md)   
 [En sélectionnant le Framework approprié](https://msdn.microsoft.com/library/bb798089.aspx)