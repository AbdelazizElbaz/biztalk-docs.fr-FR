---
title: "Service EDI et des schémas de contrôle | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 4866571b-b12d-446c-8d27-a72fe7e479ef
caps.latest.revision: "14"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 4e9911322693f4c495925ce52bdfe62a65bf850f
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="edi-service-and-control-schemas"></a>Schémas de service et de contrôle EDI
Les schémas de contrôle sont requis pour traiter les enveloppes de message (schémas de contrôle d'en-tête) et les accusés de réception. Ces schémas sont déployés dans l'assembly Microsoft.BizTalk.Edi.BaseArtifacts.dll par le programme d'installation. Ces schémas n’ont pas à ajouter aux projets BizTalk car ils sont déployés dans BaseArtifacts.dll. Vous devez ajouter une référence à l’assembly BaseArtifacts.dll au projet contenant vos schémas pour ces schémas à utiliser.  
  
## <a name="envelope-service-schemas"></a>Schémas de service d'enveloppe  
 Les schémas de service X12ServiceSchema et EdifactServiceSchema permettent de valider les en-têtes et codes de fin de l'échange, du groupe et du document informatisé dans l'enveloppe d'un échange EDI. Cela est vrai pour tous les échanges EDI : un échange non regroupé, un échange par lot à fractionner ou un échange par lot doivent être conservés. Les espaces de noms de ces schémas sont http://schemas.microsoft.com/Edi/X12ServiceSchema et http://schemas.microsoft.com/Edi/EdifactServiceSchema.  
  
 Lorsque l'échange EDI est un échange par lot conservé, les schémas de lot X12_BatchSchema et Edifact_BatchSchema sont utilisés par le moteur d'exécution BizTalk, en plus des schémas de service. Pour plus d’informations, consultez [schémas de lot EDI](../core/edi-batch-schemas.md).  
  
 Vous pouvez personnaliser les énumérations de champ d'ID dans ces schémas. Aucune autre modification n'est autorisée. Pour plus d’informations, consultez [personnalisation des énumérations dans le schéma d’enveloppe](../core/customizing-enumerations-in-the-envelope-schema.md).  
  
## <a name="acknowledgment-control-schemas"></a>Schémas de contrôle d'accusé de réception  
 Le pipeline de réception EDI utilise les schémas d'accusé de réception pour générer des accusés de réception à envoyer et le pipeline d'envoi EDI les utilise pour traiter les accusés de réception reçus. Ces schémas incluent le schéma de notification de transactions opérationnelles 997 et le schéma d'accusé de réception d'échange TA1 pour le codage X12, ainsi que le schéma CONTRL pour le codage EDIFACT, comme indiqué dans le tableau suivant. Vous ne pouvez pas modifier ces schémas.  
  
|ACCUSÉ DE RÉCEPTION|Nom du schéma|Espace de noms cible|Root|  
|---------|-----------------|----------------------|----------|  
|X12 TA1|X12_TA1Schema|http://schemas.microsoft.com/Edi/X12|TA1<br /><br /> X12_TA1_Root|  
|X12 997|X12_997Schema|http://schemas.microsoft.com/Edi/X12|ST<br /><br /> SE<br /><br /> X12_997_Root|  
|EDIFACT CONTRL|Edifact_ContrlSchema|http://schemas.microsoft.com/Edi/Edifact|Efact_Contrl_Root<br /><br /> UCD<br /><br /> UCM<br /><br /> UCS|  
  
 Pour le codage X12, le schéma de notification de transactions opérationnelles 997 définit les en-têtes et codes de fin de l'échange, du groupe, du document informatisé/message utilisés dans l'enveloppe d'un message, ainsi que les segments AK1, AK2, AK3, AK4, AK5 et AK9 qui indiquent le résultat de la validation du corps. Le schéma d'accusé de réception technique TA1 définit l'en-tête et le code de fin de l'échange, tandis que le segment d'accusé de réception TA1 indique le résultat de la validation de l'en-tête. La convention d’affectation de noms pour ces schémas est X12_\<numéro de version > _997.xsd et X12\_\<numéro de version > _TA1.xsd. L'espace de noms cible pour ces schémas est http://schemas.microsoft.com/BizTalk/EDI/X12/2006.  
  
 EDIFACT prend en charge un paradigme d'accusé de réception en deux phases. Le premier accusé de réception est une réception d'échange créée à l'aide de trois segments du schéma CONTRL. Cet accusé de réception technique indique le résultat de la validation de l'en-tête. Le deuxième accusé de réception utilise les autres segments du schéma CONTRL. La convention d’affectation de noms pour ce schéma est EFACT_\<numéro de Version > _CONTRL.xsd. L’espace de noms cible pour ce schéma est http://schemas.microsoft.com/BizTalk/EDI/EDIFACT/2006.  
  
## <a name="see-also"></a>Voir aussi  
 [Réception des Messages EDI dans BizTalk Server](../core/how-biztalk-server-receives-edi-messages.md)   
 [Envoi des Messages EDI dans BizTalk Server](../core/how-biztalk-server-sends-edi-messages.md)