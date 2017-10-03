---
title: "À l’aide de la Transformation dynamique | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e1e4aac7-242a-41b6-8df4-4881371f44d1
caps.latest.revision: "4"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 1d7f6bc57d009e558188950d9bcb0387f808f835
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="using-dynamic-transformation"></a>À l’aide de la Transformation dynamique
## <a name="overview"></a>Vue d'ensemble  
 Le [!INCLUDE[esbToolkit](../includes/esbtoolkit-md.md)] prend en charge trois mécanismes pour la transformation dynamique :  
  
-   Un agent de transformation dynamique implémenté en tant qu’orchestration  
  
-   Une transformation dynamique de service Web incluse avec les services Web principaux  
  
-   Transformations exécutées par les composants de pipeline ESB  
  
 Cette section se concentre sur l’agent de transformation implémenté en tant qu’orchestration. Pour plus d’informations sur la transformation de service Web, consultez [à l’aide des Services Web BizTalk ESB Toolkit](../esb-toolkit/using-the-biztalk-esb-toolkit-web-services.md). Pour plus d’informations sur les composants de pipeline ESB répartiteur, consultez [à l’aide de composants de prise en charge du Pipeline](../esb-toolkit/using-the-pipeline-support-components.md).  
  
## <a name="how-it-works"></a>Fonctionnement  
 L’agent de remise de transformation est une orchestration qui s’abonne aux messages où le **nom** attribut actuelles **ServiceInstance** élément dans l’itinéraire est  **Microsoft.Practices.ESB.Services.Transform**. L’agent exécute la séquence d’opérations suivante :  
  
1.  Il reçoit un message non typé (System.Xml.XmlDocument).  
  
2.  Si le nom de la carte est disponible en tant qu’une valeur statique dans l’itinéraire, l’agent tente de résoudre le nom de la carte à l’aide du Gestionnaire de programme de résolution.  
  
3.  Il applique le mappage approprié au message entrant source.  
  
4.  Elle publie la sortie de la table dans la base de données MessageBox de BizTalk.  
  
## <a name="how-to-configure-dynamic-transformation"></a>Comment configurer la Transformation dynamique  
 Pour plus d’informations sur la façon de configurer la Transformation dynamique à l’aide du Concepteur d’itinéraire, consultez [création d’itinéraires à l’aide du Concepteur de feuille de route](../esb-toolkit/creating-itineraries-using-itinerary-designer.md).  
  
## <a name="dynamic-transformation-errors"></a>Erreurs de Transformation dynamique  
 Le mécanisme de transformation dynamique sera créer et publier un message d’erreur ESB dans les cas suivants :  
  
-   Le composant de programme de résolution ne peut pas déterminer qui est mappé à appliquer.  
  
-   Le mappage spécifié n’est pas disponible (par exemple, vous spécifié un type de carte incorrect ou une carte pas encore déployé dans BizTalk Server 2009).  
  
-   Une défaillance se produit lors du mappage (par exemple, le document source n’est pas du type source correcte ou les références de carte une fonction personnalisée dans un assembly externe n’est pas déployée sur BizTalk).  
  
-   Une exception se produit pendant la résolution juste-à-temps (JIT) du type de carte.  
  
-   Aucun abonné n’existe pour le message de sortie.  
  
-   Toute exception système se produit.  
  
 Il incombe au développeur de fournir les informations de contexte utilisées pour remplir les messages d’exception et de créer des gestionnaires pour réagir à l’exception. Certaines des données est automatiquement disponible, et un gestionnaire générique prennent en charge le message d’exception si aucun gestionnaire de cible n’est spécifié ou disponible. Pour plus d’informations sur la gestion des exceptions de transformation dynamique, consultez [à l’aide de gestion des exceptions ESB](../esb-toolkit/using-esb-exception-management.md).