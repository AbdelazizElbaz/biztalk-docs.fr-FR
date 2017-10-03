---
title: "Utilisation de Services Web avec des en-têtes SOAP | Documents Microsoft"
ms.custom: 
ms.date: 06/08/2017
ms.prod: biztalk-server
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- SOAP headers, consuming
- Web services, consuming
- Web services, SOAP headers
- SOAP headers, Web services
ms.assetid: c2dfe7d8-e2f0-4bc6-b79c-354d06a7ffd6
caps.latest.revision: "8"
author: MandiOhlinger
ms.author: mandia
manager: anneta
ms.openlocfilehash: 45a3efa628e435092505fdc3884704baa15be34c
ms.sourcegitcommit: cb908c540d8f1a692d01dc8f313e16cb4b4e696d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2017
---
# <a name="consuming-web-services-with-soap-headers"></a>Utilisation de Services Web avec des en-têtes SOAP
Après avoir utilisé un service Web avec des en-têtes SOAP définis, ces en-têtes deviennent disponibles pour vos orchestrations et composants de pipeline en tant que propriétés de contexte. Ces propriétés de contexte contiennent des représentations de chaîne des en-têtes SOAP. Vous pouvez créer une propriété de contexte à l'aide du nom correspondant à l'élément racine de l'en-tête SOAP pour chaque en-tête SOAP dans le service Web. Toutes les propriétés du contexte des en-têtes SOAP définis sont dans le **http://schemas.microsoft.com/BizTalk/2003/SOAPHeader** espace de noms.  
  
 L’exemple suivant montre comment créer une propriété de contexte d’en-tête SOAP **OrigDest** à l’aide de l’exemple d’en-tête SOAP dans [les en-têtes SOAP avec les Services Web consommés](../core/soap-headers-with-consumed-web-services.md):  
  
```  
<?xml version="1.0" encoding="utf-16"?>  
<OrigDest xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns=" http://SOAPHeaderWS.ItemAvailability">  
   <Origination xmlns="">Home</Origination>  
      <Destination xmlns="">Work</Destination>  
</OrigDest>  
```  
  
 Les en-têtes SOAP de réponse contiennent également des représentations sous forme de chaînes des en-têtes SOAP définis. Les valeurs sont similaires à la création d'un en-tête SOAP de demande.  
  
## <a name="see-also"></a>Voir aussi  
 [En-têtes SOAP avec les Services Web utilisés](../core/soap-headers-with-consumed-web-services.md)