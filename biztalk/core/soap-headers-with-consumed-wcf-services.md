---
title: "En-têtes SOAP avec les Services WCF utilisés | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- consuming, WCF services
- SOAP headers, WCF services
- consuming, SOAP headers
- WCF services, SOAP headers
- SOAP headers, consuming [WCF services]
ms.assetid: 0582ee26-b549-4b50-b365-36824010dab0
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: f60e0ae7f9cf2e6a224ce9d919c7c4d5e6f3119c
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="soap-headers-with-consumed-wcf-services"></a>En-têtes SOAP avec les services WCF utilisés
Pour envoyer un message à un service WCF avec les en-têtes SOAP personnalisés, ces en-têtes doivent être définis dans vos orchestrations (dans la forme Expression, par exemple) et les composants de pipeline (dans le code) en tant que la propriété de contexte **OutboundCustomHeaders**. Cette propriété de contexte est dans l’espace de noms cible **http://schemas.microsoft.com/BizTalk/2006/01/Adapters/WCF-properties**et contient les représentations sous forme de chaîne des en-têtes SOAP personnalisés.  
  
 Les données dans le message sortant XML suivant montrent un exemple de la représentation sous forme de chaîne des en-têtes SOAP personnalisés pour le **OutboundCustomHeaders** propriété :  
  
```  
<headers>  
<Origination xmlns="http://SOAPHeaderSchemas.OrigDestSOAPHeader">Home</Origination>  
<Destination xmlns="http://SOAPHeaderSchemas.OrigDestSOAPHeader">Work</Destination>  
</headers>  
```  
  
 Les en-têtes SOAP entrants contiennent également des représentations sous forme de chaînes des en-têtes SOAP. Les valeurs sont similaires à la création d'un en-tête SOAP de demande.  
  
## <a name="in-this-section"></a>Dans cette section  
  
-   [Utilisation des en-têtes SOAP des Messages WCF avec les Orchestrations](../core/using-soap-headers-in-wcf-messages-with-orchestrations.md)  
  
-   [Utilisation des en-têtes SOAP des Messages WCF avec les composants de Pipeline](../core/using-soap-headers-in-wcf-messages-with-pipeline-components.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Propriétés et schéma de propriété des adaptateurs WCF](../core/wcf-adapters-property-schema-and-properties.md)   
 [En-têtes SOAP avec les Services WCF publiés](../core/soap-headers-with-published-wcf-services.md)