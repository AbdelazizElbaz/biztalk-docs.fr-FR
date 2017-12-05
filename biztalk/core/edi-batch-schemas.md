---
title: "Schémas de lot EDI | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 26da8036-8fe0-481e-b1e9-7f2e5b090768
caps.latest.revision: "17"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 9e159734c7d6028eb7f54354140c40757cb212b3
ms.sourcegitcommit: 5abd0ed3f9e4858ffaaec5481bfa8878595e95f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="edi-batch-schemas"></a>Schémas de lot EDI
Dans le cadre du traitement d'un échange conservé, BizTalk Server utilise au moins trois schémas :  
  
-   schémas de lot (schémas XML d'échange) pour valider le nœud racine de l'échange par lot conservé (X12_BatchSchema ou Edifact_BatchSchema déployé dans le fichier BaseArtifacts.dll) ;  
  
-   schémas de service d'enveloppe pour valider les en-têtes et codes de fin de l'échange, du groupe et du document informatisé (X12ServiceSchema ou EdifactServiceSchema déployé dans le fichier BaseArtifacts.dll). Pour plus d’informations, consultez [Service EDI et des schémas de contrôle](../core/edi-service-and-control-schemas.md).  
  
-   schémas de document pour chaque type de document dans l'échange par lot (déployé dans votre projet). Pour plus d’informations, consultez [des schémas de Document EDI](../core/edi-document-schemas.md).  
  
 Lors de l'exécution, les schémas de lot permettent de valider les échanges par lot entrants et sortants qui sont conservés. Lors de la conception, ils permettent également de valider et de générer des instances de message.  
  
## <a name="batch-schemas-used-at-runtime"></a>Schémas de lot utilisés lors de l'exécution  
 Deux versions canoniques des schémas de lot : X12_BatchSchema.xsd pour X12 codage et EDIFACT_BatchSchema.xsd pour le codage EDIFACT. Ces schémas constituent des modèles qui incluent le segment de contrôle. Ils possèdent les noms de racine et les espaces de noms suivants :  
  
|schéma|Nœud racine|Espace de noms|  
|------------|---------------|---------------|  
|X12_BatchSchema|X12InterchangeXML|http://schemas.microsoft.com/Edi/X12_BatchSchema|  
|Edifact_BatchSchema|EdifactInterchangeXML|http://schemas.microsoft.com/Edi/Edifact|  
  
 Le type de document sur l’instance XML générée par le pipeline de réception est une constante (\<codage\>_BatchSchema.xml) et référence ce schéma canonique. Cette instance peut être utilisée dans un mappage d'une orchestration. Avant de procéder ainsi, vous devez toutefois modifier le type de document et l'espace de noms pour effectuer le mappage sur le schéma actuel demandé.  
  
 Il n'est pas nécessaire de spécifier le schéma de lot lors de la conception du projet car il est déployé dans le fichier BaseArtifacts.dll.  
  
## <a name="batch-schemas-in-the-schema-store"></a>Schémas de lot dans la banque de schémas  
 Les schémas de lot utilisés par BizTalk Server lors de l'exécution pour traiter les lots conservés sont déployés dans l'assembly BaseArtifacts.dll. Ceux-ci sont automatiquement disponibles pour le traitement au moment de l'exécution. Les schémas Edifact_BatchSchema et X12_BatchSchema sont également disponibles dans la banque de schémas BizTalk située dans [!INCLUDE[btsBiztalkServerPath](../includes/btsbiztalkserverpath-md.md)]XSD_Schema\EDI. Chaque schéma est uniquement utilisé lors de la conception pour valider et générer un échange. Lors de l'exécution, aucun schéma n'est requis pour effectuer la validation dans le pipeline de réception ou d'envoi.  
  
## <a name="see-also"></a>Voir aussi  
 [Schémas EDI](../core/edi-schemas.md)   
 [Traitement des lots entrants](../core/processing-incoming-batches.md)