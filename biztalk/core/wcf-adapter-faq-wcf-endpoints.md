---
title: "FAQ sur les adaptateurs WCF : Points de terminaison WCF | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ccc94b7d-b8a6-4c24-907e-922fd885b874
caps.latest.revision: "4"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 90c59c586f0d7f1d02ad406baec694cf4e22ff24
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="wcf-adapter-faq-wcf-endpoints"></a>FAQ sur les adaptateurs WCF : les points de terminaison WCF
## <a name="what-are-two-endpoints-options-can-be-created-by-the-biztalk-wcf-service-publishing-wizard"></a>Quelles sont les deux options de points de terminaison pouvant être créées par l'Assistant Publication de services WCF BizTalk ?  
 Lors de l'exécution de l'Assistant Publication de services WCF BizTalk, vous avez la possibilité de créer soit un point de terminaison de service WCF soit un point de terminaison de métadonnées uniquement WCF (MEX).  
  
 Le point de terminaison d'un service crée un emplacement Web réel hébergé dans IIS, qui expose la fonctionnalité d'un service WCF existant. Seuls les adaptateurs isolés (WCF-WsHttp, WCF-BasicHttp et WCF-CustomIsolated) peuvent être utilisés avec les points de terminaison d'un service. La fonctionnalité de ce type de point de terminaison est implémentée par une orchestration ou un schéma qui est publié en tant que service WCF.  
  
 Un point de terminaison de métadonnées uniquement correspond à un point de terminaison dont la fonctionnalité est implémentée via un emplacement de réception BizTalk.  Celui-ci exploite les services Internet ainsi qu'un adaptateur de réception WCF de type In-process plutôt qu'une orchestration exposée ou le code d'un service WCF existant. L'utilisation de l'Assistant pour générer un point de terminaison de métadonnées uniquement représente une méthode plus simple pour obtenir des informations d'intégration sur les emplacements de réception exposés à l'aide d'un adaptateur WCF de type In-process plutôt que d'effectuer l'opération manuellement à l'aide de svcutil.exe. En effet, faire appel à cet exécutable vous oblige à trouver une méthode de transfert des métadonnées à l'utilisateur de votre service pour lui permettre de l'appeler.  
  
## <a name="why-would-i-use-a-metadata-only-endpoint-in-biztalk-server"></a>Quels sont les avantages de l'utilisation d'un point de terminaison de métadonnées uniquement dans BizTalk Server ?  
 Grâce aux points de terminaison de métadonnées uniquement, il est inutile d'implémenter un service pour un service WCF existant. Au contraire, la fonctionnalité est implémentée dans un emplacement de réception BizTalk, lequel est simplement appelé en tant que service WCF par l'intermédiaire d'un point de terminaison. Par exemple, la conversion de données d'un champ de message en majuscules peut nécessiter deux schémas et un mappage. Dans ce cas, le service est publié dans les métadonnées en tant que « ConvertToUpper ». Toutefois, la fonctionnalité du service est implémentée dans l'emplacement de réception et non dans le code ou via une orchestration.  
  
 Un point de terminaison WCF comporte une adresse, une liaison et un contrat. Lorsque l'Assistant crée un point de terminaison de métadonnées uniquement, il obtient les détails concernant l'adresse et la liaison dans l'emplacement de réception existant. Les informations relatives au contrat sont définies par les schémas qui peuvent exister dans les orchestrations BizTalk. Vous pouvez également les créer manuellement à l'aide de l'Assistant. Si vous choisissez **publier des orchestrations BizTalk en tant qu’un service WCF**, le point de terminaison de métadonnées uniquement utilise les types de ports et de messages à partir de l’assembly d’orchestration pour définir le contrat.  
  
 Si vous choisissez **publier des schémas en tant que service WCF**, l’Assistant vous permet de définir une définition de service en spécifiant des noms de service et l’opération avec l’entrée existante et les schémas de sortie. L'Assistant crée un fichier .svc ainsi qu'un répertoire virtuel IIS de sorte que les métadonnées puissent être parcourues après avoir été publiées. L’Assistant de publication des services WCF BizTalk crée également un fichier web.config avec l’attribut httpGetEnabled de le \<serviceMetadata\> élément défini sur true. Cette option permet de publier les métadonnées de manière à ce qu'elles soient consultées. Si vous choisissez de publier des métadonnées de service pour l’emplacement de réception BizTalk, ces données est accessible via une demande GET via HTTP en utilisant un `?wsdl` à la fin de l’URL pour le service.  
  
## <a name="are-service-endpoints-hosted-in-iis-and-why"></a>Les points de terminaison d'un service sont-ils hébergés dans IIS et, si tel est le cas, pour quelle raison ?  
 Oui, le point de terminaison d'un service est effectivement hébergé dans IIS à l'aide de l'un des trois adaptateurs isolés :  
  
-   WCF-WsHttp  
  
-   WCF-BasicHttp  
  
-   WCF-CustomIsolated  
  
 Un point de terminaison de service est différent d'un point de terminaison de métadonnées uniquement dans le sens où sa fonctionnalité peut être appelée directement en tant que service WCF. Faire appel à l'Assistant Publication de services WCF BizTalk pour créer un point de terminaison de service entraîne la création d'un emplacement de réception dans l'application BizTalk spécifiée. Cette opération a aussi pour effet de définir un URI par l'intermédiaire duquel il est possible d'accéder à l'orchestration à l'aide d'IIS.  
  
## <a name="when-creating-a-service-endpoint-why-would-i-select-to-publish-schemas-as-a-wcf-service"></a>Lors de la création d'un point de terminaison de service, quelles sont les raisons qui peuvent m'amener à sélectionner l'option « Publier des schémas en tant que services WCF » ?  
 Choisissez cette option si votre emplacement de réception WCF fait partie d'une application BizTalk qui utilise la messagerie BizTalk uniquement. Cela signifie qu'aucune orchestration ne sera utilisée et que toutes les fonctionnalités seront exposées par l'intermédiaire de l'emplacement de réception et des ports d'envoi. Les schémas seront publiés pour spécifier les informations du contrat. Ces informations peuvent être obtenues à partir d'un assembly de schéma ou d'orchestration (malgré le fait que l'orchestration risque de ne pas être utilisée pour ce point de terminaison).