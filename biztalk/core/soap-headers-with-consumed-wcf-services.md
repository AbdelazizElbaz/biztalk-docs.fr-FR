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
# <a name="soap-headers-with-consumed-wcf-services"></a><span data-ttu-id="4edb4-102">En-têtes SOAP avec les services WCF utilisés</span><span class="sxs-lookup"><span data-stu-id="4edb4-102">SOAP Headers with Consumed WCF Services</span></span>
<span data-ttu-id="4edb4-103">Pour envoyer un message à un service WCF avec les en-têtes SOAP personnalisés, ces en-têtes doivent être définis dans vos orchestrations (dans la forme Expression, par exemple) et les composants de pipeline (dans le code) en tant que la propriété de contexte **OutboundCustomHeaders**.</span><span class="sxs-lookup"><span data-stu-id="4edb4-103">To send a message to a WCF service with the custom SOAP headers, these headers must be set in your orchestrations (in the Expression shape, for example) and pipeline components (in code) as the context property **OutboundCustomHeaders**.</span></span> <span data-ttu-id="4edb4-104">Cette propriété de contexte est dans l’espace de noms cible **http://schemas.microsoft.com/BizTalk/2006/01/Adapters/WCF-properties**et contient les représentations sous forme de chaîne des en-têtes SOAP personnalisés.</span><span class="sxs-lookup"><span data-stu-id="4edb4-104">This context property is in the target namespace **http://schemas.microsoft.com/BizTalk/2006/01/Adapters/WCF-properties**, and contains string representations of the custom SOAP headers.</span></span>  
  
 <span data-ttu-id="4edb4-105">Les données dans le message sortant XML suivant montrent un exemple de la représentation sous forme de chaîne des en-têtes SOAP personnalisés pour le **OutboundCustomHeaders** propriété :</span><span class="sxs-lookup"><span data-stu-id="4edb4-105">The data in the following XML outgoing message shows an example of the string representation of custom SOAP headers for the **OutboundCustomHeaders** property:</span></span>  
  
```  
<headers>  
<Origination xmlns="http://SOAPHeaderSchemas.OrigDestSOAPHeader">Home</Origination>  
<Destination xmlns="http://SOAPHeaderSchemas.OrigDestSOAPHeader">Work</Destination>  
</headers>  
```  
  
 <span data-ttu-id="4edb4-106">Les en-têtes SOAP entrants contiennent également des représentations sous forme de chaînes des en-têtes SOAP.</span><span class="sxs-lookup"><span data-stu-id="4edb4-106">Inbound SOAP headers also contain string representations of the SOAP headers.</span></span> <span data-ttu-id="4edb4-107">Les valeurs sont similaires à la création d'un en-tête SOAP de demande.</span><span class="sxs-lookup"><span data-stu-id="4edb4-107">The values are similar to creating a request SOAP header.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="4edb4-108">Dans cette section</span><span class="sxs-lookup"><span data-stu-id="4edb4-108">In This Section</span></span>  
  
-   [<span data-ttu-id="4edb4-109">Utilisation des en-têtes SOAP des Messages WCF avec les Orchestrations</span><span class="sxs-lookup"><span data-stu-id="4edb4-109">Using SOAP Headers in WCF Messages with Orchestrations</span></span>](../core/using-soap-headers-in-wcf-messages-with-orchestrations.md)  
  
-   [<span data-ttu-id="4edb4-110">Utilisation des en-têtes SOAP des Messages WCF avec les composants de Pipeline</span><span class="sxs-lookup"><span data-stu-id="4edb4-110">Using SOAP Headers in WCF Messages with Pipeline Components</span></span>](../core/using-soap-headers-in-wcf-messages-with-pipeline-components.md)  
  
## <a name="see-also"></a><span data-ttu-id="4edb4-111">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="4edb4-111">See Also</span></span>  
 <span data-ttu-id="4edb4-112">[Propriétés et schéma de propriété des adaptateurs WCF](../core/wcf-adapters-property-schema-and-properties.md) </span><span class="sxs-lookup"><span data-stu-id="4edb4-112">[WCF Adapters Property Schema and Properties](../core/wcf-adapters-property-schema-and-properties.md) </span></span>  
 [<span data-ttu-id="4edb4-113">En-têtes SOAP avec les Services WCF publiés</span><span class="sxs-lookup"><span data-stu-id="4edb4-113">SOAP Headers with Published WCF Services</span></span>](../core/soap-headers-with-published-wcf-services.md)